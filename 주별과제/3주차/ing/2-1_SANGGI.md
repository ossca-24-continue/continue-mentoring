# Chat: How it works

## 챗은 어떻게 동작할까?

1. 에디터 창에서 `cmd + L` 또는 사이드바 채팅창에서 `@`로 Context를 전달한다.
1. 사이드 바에서 추가적인 Prompt를 전달한다.
1. LLM 모델은 전달받은 `Context`와 `Prompt`를 기반으로 응답을 스트리밍한다.

## FAQ

### '그게 아니고~' 식으로 코드는 안 보내고 후속 조치만 보내면 어떻게 될까?

이전 세션 컨텍스트도 일부 포함된다.  
추가 Context를 제공하는 게 아니라 모델이 대화의 흐름과 맥락을 기억하고 있음.

### 받은 응답을 어떻게 적용할까?

응답에 포함된 코드는 해당 블록에 배치되며 `현재 파일에 적용`, `커서에 삽입`, `복사`를 선택할 수 있다.

### 지금까지 맥락을 무효화하고 새로운 세션을 시작하고 싶다면?

`cmd + L` 또는 사이드바 채팅창에서 `새로운 채팅`을 클릭한다.

### 채팅 모델 중에 전송된 프롬프트를 볼 수 있을까?

A. 터미널 옆에 `Output` 열기
B. 드롭다운에서 `Continue - LLM Prompts/Completions` 선택
C. 전송된 프롬프트 확인

### 개발과 무관한 내용을 요청하면? (e.g. 김치찌개 레시피 알려줘)

Continue는 매우 성실하게 알려줌중.
Copilot은 `"Sorry, I can't assist with that."` 라고 응답.

# How to customize

4가지 커스텀 방법이 있다.

1. `@codebase` 설정

- 프로젝트 전체 코드베이스를 대상으로 정보를 검색하거나, 특정 폴더를 대상으로 할 수 있음.
- 벡터 데이터베이스에서 `가져올 결과`, `사용할 경과`, `재랭킹 기능 사용 여부` 를 설정할 수 있음.

1. 커스텀 RAG 생성

- 임베딩 모델 선택, 벡터 데이트베이스 설정, 텍스트 청킹 전략 조절

1. `@docs` 설정

- 특정 문서를 제공
- 라이브러리 공식문서 URL을 지정 등에 활용
  e.g. `@docs API endpoints for Continue`

1. `context provider` 생성

- 고유한 프로바이더를 생성할 수 있음.
  e.g. 회사 내부의 매뉴얼을 컨텍스트로 제공하는 프로바이더 생성 등

> 핵심은 Chat에서 사용할 Context를 어떻게 제공할지 결정하는 것!
