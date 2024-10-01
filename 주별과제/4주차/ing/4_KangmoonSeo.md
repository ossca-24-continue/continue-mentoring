# Continue의 RAG (Retrieval-Augmented Generation) 워크플로

## 개요

Continue는 주로 `@codebase` 검색 시 RAG를 사용합니다. continue에서의 RAG 시스템의 주요 특징은 다음과 같습니다.

1. **경량화된 로컬 임베딩과 RAG**
   - 유사도 검색에 가볍고 상대적으로 정확도가 낮은 로컬 임베딩 모델을 사용합니다.
   - sentence transformer ``
2. **필요에 따라 NLP task로 Reranking을 보완**
   - BM25 기반 전문 검색(Full-Text Search)
   - LLM 기반 "저장소 맵"을 분석
3. **LLM prompt를 이용한 Reranking**
   - LLM 기반 Reranking을 통해 최종 결과의 정확도를 높입니다.

- 기본적으로 가벼운 임베딩 모델을 사용해 Naive RAG를 경량화했습니다.
- 사용자가 원하면 Reranking과 NLP task를 활성화해 정확도를 높이는 전략을 세웠습니다.

## 사용 데이터베이스

Continue의 RAG 시스템은 두 가지 유형의 데이터베이스를 활용합니다:

1. **관계형 데이터베이스 (RDBMS)**: SQLite
   - 인덱싱된 파일 기록 유지
   - 전문 검색(Full-Text-Search) 인덱스 저장 및 사용
     - BM25 알고리즘 활용
   - LanceDB 캐시 관리 (lance_db_cache 테이블)
     - uuid를 key로, `List[number]` 형태의 vector를 포함한 모든 정보 저장

2. **벡터 데이터베이스**: LanceDB
   - 문서 chunk의 임베딩 벡터 저장
   - 사용자 query와 문서 chunk 간 유사도 검색 수행

## RAG 워크플로 다이어그램

```mermaid
graph TD
    subgraph "1.Indexing Process"
    A[Planning Layer] -->|SQLite| B[File Chunking]
    B --> C[Embedding Generation]
    C --> D[Vector DB Storage]
    B --> E[Full-text Index]
    end
    subgraph "2.Query Process"
    F[User Query] --> G[Similarity Search]
    F --> H[Full-text Search]
    F --> I[LLM Repo Map]
    G & H & I --> J[Reranker]
    J --> K[Top Results]
    end
    D -.-> G
    E -.-> H
```

## 주요 단계

### 1. 인덱싱 프로세스 (문서 전처리)

1. **계획 단계 (Planning Layer)**
   - SQLite를 사용하여 이미 인덱싱된 파일들의 기록 유지
   - 브랜치 변경이나 윈도우 리로드 시 중복 작업 방지 (95%의 파일은 변경되지 않음)

2. **파일 청킹 (File Chunking)**
   - 문서를 LLM 입력에 적합한 크기의 작은 부분(chunk)으로 분할

3. **임베딩 생성 (Embedding Generation)**
   - 각 chunk에 대한 임베딩 계산
   - 로컬 임베딩: `transformers.js` 라이브러리 사용
   - API 임베딩 모델: 선택적으로 `voyage-code-2` API 사용 가능

4. **벡터 DB 저장 (Vector DB Storage)**
   - 생성된 임베딩을 로컬 벡터 데이터베이스(LanceDB)에 저장
   - SQLite의 lance_db_cache 테이블에서 캐싱
   - ![alt text](assets/4_lance_db_cache.png)
     - 위 sqlite의 `lance_db_cache` 테이블에서 vector가 `embedding vector`, contents가 `text chunk`라고 보시면 됩니다.

5. **전문 검색 인덱스 생성 (Full-text Index)**
   - 결과 보강을 위한 전문 검색 인덱스를 SQLite에 생성 및 저장

### 2. 쿼리 프로세스

1. **사용자 쿼리 접수 (User Query)**
   - `@codebase` 감지 시 RAG 프로세스를 시작합니다.
   - query를 chunking하고, 저장한 벡터와 비교할 수 있도록 임베딩합니다.

2. **유사도 검색 (Similarity Search)**
   - 벡터 데이터베이스(LanceDB)에서 유사도 기반 검색으로 결과를 가져옵니다.

3. **전문 검색 (Full-text Search)**
   - SQLite의 전문 검색 인덱스를 활용하여 추가 결과를 검색합니다.
   - BM25 알고리즘 기반으로 랭킹합니다.
   - `fts` 테이블 기준으로 `fts_metadata` 테이블 등을 JOIN해 사용합니다.

4. **LLM 저장소 맵 (LLM Repo Map)**
   - LLM에 "저장소 맵"을 제시하고 관련 파일 식별 요청
   - 후보 파일의 세 번째 소스로 활용
   - `requestFilesFromRepoMap` 함수를 통해 LLM의 분석 결과를 가져옵니다.
   - 이런 프롬프트를 사용합니다.
    - ```ts
       const prompt = `${repoMap}

        Given the above repo map, your task is to decide which files are most likely to be relevant in answering a question. Before giving your answer, you should write your reasoning about which files/folders are most important. This thinking should start with a <reasoning> tag, followed by a paragraph explaining your reasoning, and then a closing </reasoning> tag on the last line.

        After this, your response should begin with a <results> tag, followed by a list of each file, one per line, and then a closing </results> tag on the last line. You should select between 5 and 10 files. The names that you list should be the full path from the root of the repo, not just the basename of the file.

        This is the question that you should select relevant files for: "${input}"`;
        ```

5. **재순위화 (Reranker)**
   - 이전 단계에서 얻은 모든 후보 파일(FTS, 임베딩, 최근 편집 파일, 저장소 맵)의 순위 재조정
   - LLM 기반 재순위화 모델 사용
   - 사용자 입력과 각 chunk의 관련성을 정밀하게 평가
   - 낮은 점수의 결과 필터링
   - 이런 few-shot 프롬프트를 사용합니다.
     - ```ts
        const prompt = `You are an expert software developer responsible for helping detect whether the retrieved snippet of code is relevant to the query. For a given input, you need to output a single word: "Yes" or "No" indicating the retrieved snippet is relevant to the query.

          Query: Where is the FastAPI server?
          Snippet:
          \`\`\`/Users/andrew/Desktop/server/main.py
          from fastapi import FastAPI
          app = FastAPI()
          @app.get("/")
          def read_root():
              return {{"Hello": "World"}}
          \`\`\`
          Relevant: Yes

          Query: Where in the documentation does it talk about the UI?
          Snippet:
          \`\`\`/Users/andrew/Projects/bubble_sort/src/lib.rs
          fn bubble_sort<T: Ord>(arr: &mut [T]) {{
              for i in 0..arr.len() {{
                  for j in 1..arr.len() - i {{
                      if arr[j - 1] > arr[j] {{
                          arr.swap(j - 1, j);
                      }}
                  }}
              }}
          }}
          \`\`\`
          Relevant: No

          Query: ${query}
          Snippet:
          \`\`\`${documentId}
          ${document}
          \`\`\`
          Relevant: 
          `;
          ```

6. **최종 결과 제공 (Top Results)**
   - 재순위화 및 확장된 결과 중 상위 결과 반환
   - 사용자 쿼리에 가장 관련성 높은 코드 chunk 제공


이렇게 NLP task를 복합한 워크플로를 통해, Continue는 경량 로컬 모델의 효율성과 다양한 검색 방법의 장점을 결합하여 높은 정확도의 코드 검색 결과를 제공합니다.


