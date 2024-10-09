# contribution idea 브레인스토밍

## 1. `@codebase` pop-up 기능

- .
<!--
- 정보 베이스
- 첫 사용 때 accept를 받아내는 기능
- 내 코드베이스를 로컬 말고 원격에 보내기 싫어하는 사람이 있을 수 있으니 ...

## 2. FTS 버그 수정

- FTS 버그, 유니코드 잘 못 쪼갬
  -->

# Introducing Continue: A Narrative Script

> week3, week4 내용을 narrative하게 서술합니다.

## AI Assistant for Coding

- Copilot으로 대표되는 AI Assistant는 반복되는 코딩 작업을 자동화하는 등 개발자의 생산성을 높이는 도구입니다.
- 보통 in-IDE autocomplete 기능과 코딩 특화 LLM Chat 기능을 제공합니다.
- 현재 시장에는 구독형 IDE Extension인 MS Copilot, Amazon CodeWhisperer와, 독립적인 AI IDE인 Cursor 등이 있습니다.
- 한편, **오픈 소스**로 AI coding Assistant를 구현하고자 하는 움직임도 있습니다.

## Continue, open-source leading AI code assistant

- Continue는 오픈 소스 AI code assistant 분야를 leading하는 IDE Extension입니다. (17.8k stars)
- 언어 모델을 편의대로 연결할 수 있다는 점, Context 로직이 코드 질의에 최적화되었다는 점이 장점입니다.

## 기능 1. `Chat`

- `Chat`은 IDE 내부에서 코드 기반 LLM Chat을 사용할 수 있는 기능입니다.
- 코드를 하이라이팅하고, 질문 텍스트와 함께 LLM에 요청하면 답변을 얻는 멀티턴 챗입니다.
- 입력 심볼(`@`)을 통해 Context를 수동으로 선택해 제공할 수 있습니다.

### Context Provider에서의 RAG 사용

- `@codebase` 심볼 사용 시 로컬 codebase를 지식 베이스로 RAG를 실행합니다.
- 일반 RAG와 동일하게 `1. Indexing Process`, `2. Query Process` 워크플로를 가집니다.

1. Indexing Process

- codebase 모든 코드를 청킹해 로컬 임베딩 모델을 거쳐 VectorDB에 저장합니다.

2. Query Process

- 먼저 쿼리의 벡터와 Indexed VectorDB 간 유사도 검색을 거칩니다.
- 이후 검색 결과에 대응하는 코드를 가져와 질의에 첨부, Chat LLM의 답변을 얻습니다.
- 한편, `Raranking`을 활성화하여 RAG 정확도를 올릴 수도 있습니다.
  - BM25 기반 전문 검색, Repo-Map을 리랭킹 근거로 사용할 수 있습니다.

## 기능 2. `Autocomplete`

- `Autocomplete`는 개발자가 타이핑할 코드를 예측해 자동완성하는 기능입니다.
- 활성화 시 커서의 앞뒤 코드를 LLM에 문맥으로 제공해 중간을 채웁니다.(FIM, Fill-In-the-Middle)

## 기능 3. `Edit`

- `Edit`은 현재 파일을 벗어나지 않고 코드를 수정하는 기능입니다.
- 코드블록을 하이라이팅 한 뒤 요청을 제공하면, AI가 생성한 변경 사항을 Accept 또는 Reject합니다.
- 주석 추가, unit-test 생성, 함수 리팩터링에 사용하기 좋습니다.

## 기능 4. `Actions`

- `Actions`는 자주 사용하는 작업을 slash(`/`)를 통해 빠르게 호출하는 기능입니다.
- 코드를 수정하는 `/edit`, 주석을 생성하는 `/comment` 등 preset이 있습니다.
- 커스텀 프롬프트를 생성해(`.prompt`) 원하는 기능을 만들 수 있습니다.

## Model Types for Continue

1. `Chat Model`

- 멀티 턴 대화 형식으로 훈련된(Instructed) LLM입니다.
- 질문에 답하고 코드를 짜야 하기 때문에, 좋은 성능의 모델이 필요합니다. (400B+)
- `Claude 3.5 Sonnet`, `GPT-4o`, `Llama-3.1-405B`를 권장합니다.

2. `Autocomplete Model`

- 중간을 채우는 방식(Fill-In-the-Middle)으로 훈련된 LLM입니다.
- FIM task에 특화되었기 때문에, 작은 규모로도 괜찮은 성능을 보입니다. (3B)
- API는 `Codestral`, 로컬로는 `Starcoder2-3B` 을 권장합니다.

3. `Embedding Model`

- text sentence에서 특징을 추출해 벡터로 표현하는 언어 모델입니다.
- context provider RAG 인덱싱 단계에 사용합니다.
- 기본 모델은 로컬 `all-minilm-l6-v2`이며, `voyage-code-2` API를 권장합니다.

4. `Reranking Model`

- context 검색 결과에서 질의와의 관련성을 평가해 재정렬(Rerank)하는 모델입니다.
- context provider RAG 쿼리 단계에 사용합니다.
- `rerank-1`을 권장하며, Chat LLM 모델 또한 사용할 수 있습니다.
