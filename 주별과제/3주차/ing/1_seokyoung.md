## How to use it

- Chat 기능은 IDE 내에서 개발자들이 AI와 자연스러운 대화를 통해 문제를 해결할 수 있도록 도와줍니다.
- 코드와 관련된 정보를 포함해서 작업을 보내면, 가장 가능성 있는 텍스트 혹은 코드로 응답해줍니다.
- 만약 원하는 답변을 받지 못했으면 메세지를 주고받으며 작업이 완료될 때까지 조정할 수 있습니다.

> [!TIP]
>
> **공식에서 Chat 기능을 추천하는 상황**
>
> - 코드를 이해하거나 반복하기
> - 검색 엔진 쿼리 대체하기

### 주요 기능

기본적인 사용 방법은 사이드바의 확장 기능을 통해 쉽게 접근 가능합니다.

#### 코드 하이라이팅

코드 블록이 필요한 구문을 드래그한 뒤, `cmd/ctrl+L`(VS Code) 혹은 `md/ctrl+L`(JetBrains)를 이용하여 대화 안에 포함합니다.

> [!TIP]
> 간혹 가다 키보드 숏컷 충돌로 `cmd+L` 인식이 안 되는 경우가 있었습니다.
>
> - 대안 1) `shift+cmd+L`를 시도
> - 대안 2) `코드 드래그 후 → 우클릭 → Continue → Add Highlighted Code to Context` 시도

#### 레퍼런스하기

`@`를 이용해 코드베이스, 문서, IDE, 혹은 서드파티의 정보를 컨텍스트에 포함시킬 수 있습니다.

### 제안 코드 적용하기

답변받은 코드를 간편하게 적용할 수 있습니다. 적용 방식은 코드 블럭 우측 상단 아이콘에 따라 선택할 수 있습니다.

- Apply to current file: 파일 전체를 읽고 비교하면서 코드 블록에 해당하는 부분에 적용합니다.
- Insert at cursor: 커서 위치에 코드 블록을 입력합니다.
- Copy: 코드 블록을 복사해 수동으로 적용합니다.

### 새로운 세션 시작하기

대화창에서 다시 `cmd/ctrl+L`(VS Code) 혹은 `md/ctrl+L`(JetBrains)를 입력하면 새로운 세션이 시작합니다. 이렇게 하면 세션별로 작업에 관련된 컨텍스트만 제공해줄 수 있습니다.

### 모델 변경하기

드롭다운을 사용하거나 `cmd/ctrl + ’` 을 입력하여 설치한 모델을 전환할 수 있습니다.

> 처음에 몰라서 드롭다운만 사용했었는데 과제하면서 단축키를 알아서 편하게 스위칭할 수 있었습니다. **🤗**

## Model Setup

### 최적 환경 구성

> [!NOTE]
> 전반적인 채팅 환경을 최적화하려면 **400B+ 매개 변수 모델 또는 프론티어 모델 중 하나를 사용**하는 것이 좋습니다.
>
> - 프론티어 AI: 고도화된, 고성능 모델
> - Continue 공식 권장 모델: Claude Sonnet 3.5 (Anthropic)

### 지원 모델

Continue는 open-weight/open-source model 모두 지원합니다.

- open-weight model: 만드는 법, 모델 구조, 사용한 데이터 제반 내용 모두를 공개하지 않고 완성된 모델
- open source model: 만드는 법, 모델 구조, 사용한 데이터 등 모델과 관련된 대부분의 내용을 공개하여 공유하는 모델

### 모델 종류

- Claude Sonnet 3.5 (Anthropic)
- Llama 3.1 405B(Meta. open-weight model 선호시)
- GPT-4o (OpenAI)
- Gemini 1.5 Pro (Google)

각 모델 별 config 설정은 [공식 문서](https://docs.continue.dev/chat/model-setup#best-overall-experience)에 있습니다.

### 로컬, 오프라인 환경 구성

로컬 및 오프라인 채팅 환경을 위해서는 용량이 크지만 충분히 빠른 모델을 사용하는 것을 추천합니다.

공식에서는 컴퓨터의 성능에 따라 두 가지 모델을 권장하고 있습니다.

- Llama 3.1 8B (8B 파라미터 모델을 실행할 수 있는 경우)
  - `provider`는 Ollama나 LM Studio 사용
- DeepSeek Coder 2 16B (16B 파라미터 모델을 실행할 수 있는 경우)
  - `provider`는 Ollama나 LM Studio 사용

### 그외...

그 외에도 [커스텀 모델](https://docs.continue.dev/customize/model-types/chat)을 사용하는 법도 공식 문서에 나와있습니다.

## Context Selection

> [!NOTE]
>
> 채팅은 사용자가 현재 작업 중인 문맥(context)을 선택할 수 있습니다. 이는 Chat의 응답 정확도와 관련이 깊습니다.

입력창에 질문이나 입력하는 것이 유일한 필수 문맥입니다. 아래에 나열된 추가 컨텍스트를 선택하고 포함하는 다른 모든 방법은 선택 사항입니다.

- 컨텍스트 관리
  - 자동 컨텍스트: 프로젝트 파일, 코드베이스 등의 정보를 자동으로 컨텍스트로 포함할 수 있습니다.
  - 수동 컨텍스트: 필요한 경우 사용자가 직접 컨텍스트를 지정해 AI의 응답을 조정할 수 있습니다.

### 컨텍스트 최적화 방법

- 작업 중인 파일이나 코드베이스를 정확히 설정해 두면 관련된 내용에 더 정확하게 답할 수 있습니다.
- 불필요한 컨텍스트를 최소화하여 하는 게 중요!

### 입력 심볼

- 하이라이팅 코드 블럭: `cmd/ctrl + L(VS Code)` 또는 `cmd/ctrl + J(JetBrains)`
- 현재 실행 파일: `cmd/ctrl + opt + enter`
- 특정 파일: `@files`
- 특정 폴더: `@directory`
- 전체 코드베이스: `@codebase`
- 문서 사이트: `@docs`
- IDE 내 터미널: `@terminal`
- Git diff: `@diff`
