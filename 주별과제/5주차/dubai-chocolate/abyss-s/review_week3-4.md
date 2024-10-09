# 주차별 조별 과제 개인 리뷰

## 목차

### 3주차 리뷰

1. [1조](#1조)
2. [2조](#2조)
3. [3조](#3조)
4. [4조](#4조)

### 4주차 리뷰

1. [1조](#1조)
2. [2조](#2조)
3. [3조](#3조)
4. [4조](#4조)

---

## 3주차 리뷰

### 1조

#### AI 코딩 어시스턴트 도구 조사 및 비교 분석

- 여러 AI 도구 소개

  - Amazon CodeWhisperer
  - Codex
  - Cursor
  - Tabline
  - Codeium
  - GitHub Copilot
  - replit GhostWriter

- Comtinue만의 차별화 요소
  - 개발환경에 통합되어 있으면서도 사용자가 AI 모델을 커스텀 가능
  - 컨텍스트 프로바이더, 모델 선택이 자유롭기 때문에 확장성이 무궁무진함
  - 무엇보다 오픈소스이기 때문에 개발자 커뮤니티 지원과 참여가 활발하다는 것이 가장 큰 장점이라고 생각함

### 2조

#### Continue 설치 및 설정과 주요 기능에 대한 오버뷰

- 설치
  - vscode에서 익스텐션을 통해 간단 설치 가능
  - jetbrains 툴도 익스텐션 제공
- 설정
  - `config.json` 파일 통해 로컬 모델이나 설정 커스텀 가능
- 주요 기능
  - chat
  - autocomplete
  - edit
  - actions

### 3조

#### Continue chat 및 autocomplete 기능 상세 리뷰

- chat
  - 선택한 모델과 챗봇 대화 기능 제공
  - '@' 명령어를 통해 참고 파일이나 문서, context Provider도 커스텀 가능
- autocomplete
  - 커서 위치 기반 자동완성 기능 제공 (TAP키 사용)
  - 기본적으로 Codestral 모델 추천, 물론 변경 가능
  - `config.json`의 tabAutocompleteOptions 을 통해 커스텀 가능

### 4조

#### Continue edit 및 actions 기능 상세 리뷰

- edit
  - 원하는 코드 블록 하이라이트하면 해당 파일 수정 사항 제안
  - 작은 수정이나 빠른 변경 특화
- actions
  - 자주 사용하는 작업을 슬래시 명령어로 등록 가능
  - 다양한 명령어 라이브러리 존재
  - 자신만의 커스텀 프롬프트도 만들고 이용 가능

---

## 4주차 리뷰

### 1조

#### Continue에서 사용하는 Model 유형과 연동 방식 조사

- Chat model
  - Claude 3.5 Sonnet
  - GPT-4o
- Embeddings model
  - 텍스트 벡터값으로 변환하여 유사도 비교
  - voyage-code-2, Ollama 등
- Reranking model

  - 모델 적합성 관련성 평가에 유용
  - Continue: `@codebase` 명령어 입력 시 가장 관련성 높은 코드 스니펫을 선택하는데 사용
  - Voyage AI의 rerank-1 등

- 연동방식
  model, context provider, action provider 등 모두 아래 방식으로 연동 가능
  1. api key 얻기
  2. add chat model or `config.json`에서 직접 추가

### 2조

#### LLM completion options 및 효과적인 프롬프트 설계

- LLM completion options
- 모델 생성 방식을 커스텀할 때 건드릴 수 있는 옵션
- [Continue's completionOptions](https://docs.continue.dev/customize/config)

  - 전역 설정: 모델에 상관없이 모든 작업에 동일하게 적용
  - 특정 모델만 설정

- Custom slash commands(prompt)

  - 자세한 내용을 블로그 글로 작성: [링크](https://tomymoon.tistory.com/156)
  - `slashCommands`, `customCommands` 등의 옵션도 활용 가능

- custom context provider

  - LLM에 특정한 콘텐츠를 제공하여 응답에 대해 관련성과 적합성을 높여서 생성하는데 사용
    - REST API를 통해 외부 데이터베이스에서 정보를 검색할 수 있도록 구현 가능
  - 기본적으로 플러그인이므로 기본 제공 이외, 본인이 커스텀하거나 요청하여 새로운 context provider 생성 가능
  - `contextProviders` 옵션 활용
    - [공식문서 링크 참조](https://docs.continue.dev/customize/tutorials/build-your-own-context-provider)

- 효과적인 프롬프트 사용법
  - Chain-of-Thought: 생각을 구체화하여 차근차근 지시
  - ai에게 페르소나(맥락, 역할 등) 부여하기
  - 최대한 명확하고 구체적인 질문을 해야 이에 맞는 답변 받을 수 있음

### 3조

#### RAG와 Continue에서의 활용 방법

- RAG(검색 증강 생성)
  - 자체 지식뿐만아니라 외부 데이터베이스나 검색 엔진을 통해 최신 정보를 제공하도록 하는 방법
  - 수집된 외부 데이터를 벡터 데이스베이스에 저장하는 과정 필요
  - 장점
    - 실시간 정보 업데이트 가능
    - 외부 참조이므로 효율적인 메모리 사용 가능
- RAG 작동방식

1. Chunking: 대규모 문서룰 여러개의 작은 chunk로 나눔

- 고정된 길이로 자르는 방식
- 문맥을 인지하여 자르는 방식
- 위 두 방식을 혼합하는 방식
  사용 목적과 규모 등에 따라 적절한 방식을 선택하면 됨

2. Document Embedding: 각 chunk를 벡터로 변환하여 벡터 DB에 저장
   사전 학습된 Transformer 기반 모델 사용
3. Retrieval: 유사도 측정

- Sparse Retriever
- Dense Retriever

4. Reranking
   관련성 높은것만 묶어서 필요한 것만 넣어 최종 상위 문서 결정
   유사도 뿐만 아니라 맥락, 텍스트 길이 등을 고려해야 함
5. Generation: 최종 문서를 기반으로 답변 생성

- Continue에서의 RAG 활용 방법
  - 관계형 데이터베이스: SQLite
  - 벡터 데이터베이스: LanceDB
  - 임베딩 모델 선택: Continue에서 추천하는 모델은 `voyage-code-2`
  - 인덱싱 스크립트 작성: 검색가능하도록 구조화하여
    - 스크립트 실행: 자동 or 주기 설정
- 커스텀 RAG는 별도 서버 필요 ex. `/rerank`

### 4조

#### LLM 벤치마크 분석 및 선택 가이드.
