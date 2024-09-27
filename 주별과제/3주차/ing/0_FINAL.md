# 목차

## 1. Chat

- How to use it
- Model setup
- Context selection
- How it works
- How to customize

## 2. Autocomplete

- How to use it
- Model setup
- Context selection
- How it works
- How to custumize

---

# Detail

## [Chat] How to use it

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

## [Chat] Model Setup

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

## [Chat] Context Selection

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

## [Chat] How it works

### 챗은 어떻게 동작할까?

1. 에디터 창에서 `cmd + L` 또는 사이드바 채팅창에서 `@`로 Context를 전달한다.
1. 사이드 바에서 추가적인 Prompt를 전달한다.
1. LLM 모델은 전달받은 `Context`와 `Prompt`를 기반으로 응답을 스트리밍한다.

### FAQ

#### '그게 아니고~' 식으로 코드는 안 보내고 후속 조치만 보내면 어떻게 될까?

이전 세션 컨텍스트도 일부 포함된다.  
추가 Context를 제공하는 게 아니라 모델이 대화의 흐름과 맥락을 기억하고 있음.

#### 받은 응답을 어떻게 적용할까?

응답에 포함된 코드는 해당 블록에 배치되며 `현재 파일에 적용`, `커서에 삽입`, `복사`를 선택할 수 있다.

#### 지금까지 맥락을 무효화하고 새로운 세션을 시작하고 싶다면?

`cmd + L` 또는 사이드바 채팅창에서 `새로운 채팅`을 클릭한다.

#### 채팅 모델 중에 전송된 프롬프트를 볼 수 있을까?

A. 터미널 옆에 `Output` 열기
B. 드롭다운에서 `Continue - LLM Prompts/Completions` 선택
C. 전송된 프롬프트 확인

#### 개발과 무관한 내용을 요청하면? (e.g. 김치찌개 레시피 알려줘)

Continue는 매우 성실하게 알려줌중.
Copilot은 `"Sorry, I can't assist with that."` 라고 응답.

## [Chat] How to customize

4가지 커스텀 방법이 있다.

#### `@codebase` 설정

- 프로젝트 전체 코드베이스를 대상으로 정보를 검색하거나, 특정 폴더를 대상으로 할 수 있음.
- 벡터 데이터베이스에서 `가져올 결과`, `사용할 경과`, `재랭킹 기능 사용 여부` 를 설정할 수 있음.

#### 커스텀 RAG 생성

- 임베딩 모델 선택, 벡터 데이트베이스 설정, 텍스트 청킹 전략 조절

#### `@docs` 설정

- 특정 문서를 제공
- 라이브러리 공식문서 URL을 지정 등에 활용
  e.g. `@docs API endpoints for Continue`

#### `context provider` 생성

- 고유한 프로바이더를 생성할 수 있음.
  e.g. 회사 내부의 매뉴얼을 컨텍스트로 제공하는 프로바이더 생성 등

> 핵심은 Chat에서 사용할 Context를 어떻게 제공할지 결정하는 것!

## [Chat] Deep dive about LLM

### LLM 학습하기

1. **데이터 수집**:
   - **다양한 출처**: 인터넷 크롤링, 전자 도서, 뉴스 기사, 학술 논문, 소셜 미디어 등에서 데이터를 수집합니다.
   - **언어 다양성**: 여러 언어와 다양한 도메인의 텍스트를 포함하여 모델의 범용성을 높입니다.
2. **데이터 전처리**:

   - **토큰화(Tokenization)**: 텍스트를 단어 또는 부분 단위로 분할하여 모델이 처리할 수 있는 형태로 변환합니다.
   - **어휘 사전 구축**: 모델이 인식할 수 있는 단어 또는 토큰의 집합을 만듭니다.

   (일반적인 우리가 생각하는 단어 뿐만 아니라, 자주 쓰이는 문장 같은 것을 하나의 토큰 단위로도 만들 수 있습니다.)

3. **모델 학습**:
   - **트랜스포머 아키텍처**: 셀프 어텐션 메커니즘을 활용하여 문맥 정보를 효과적으로 학습합니다.
   - **언어 모델링**: 다음 단어 예측(Next Token Prediction) 또는 마스킹된 단어 복원(Masked Language Modeling)을 통해 언어 패턴을 학습합니다.
     → 이런 방법이기에 Pretrain만 되어있는 LLM 은 다음 단어만 예측할 수 있습니다. input으로 들어간 문장의 다음 것을 자연스럽게 이어주도록 예측하는 것입니다.
     (다음 단어를 예측한 것을 사용해서 계속 예측하고, 최종으로 End 토큰이 나올 때까지 계속 예측)
4. **미세 조정(Fine-tuning)**:
   - **특정 태스크에 맞춘 조정**: 질의 응답, 번역, 요약 등 특정 작업에 맞게 추가로 학습합니다.

### LLM을 챗봇으로 쓰기 위해서는?

LLM을 효과적인 챗봇으로 활용하기 위해서는 단순한 언어 생성 능력 외에도 사용자와의 상호작용을 원활하게 하는 추가적인 요소들이 필요합니다:

1. **대화 데이터로 미세 조정**:
   - **대화형 데이터셋 사용**: 오픈도메인 대화 데이터나 특정 도메인의 대화 데이터를 활용합니다.
   - **역할 부여**: 사용자와 챗봇의 역할을 명확히 정의하여 모델이 적절한 응답을 생성하도록 합니다.
2. **컨텍스트 유지 및 관리**:
   - **대화 히스토리 추적**: 이전 발화들을 저장하여 모델 입력에 포함시킵니다.
   - **세션 관리**: 각 사용자별로 대화 세션을 관리하여 개인화된 경험을 제공합니다.
   - **기억 능력 확장**: 장기 대화에서도 일관성을 유지하기 위해 메모리 네트워크나 외부 저장소를 활용합니다.
3. **안전하고 윤리적인 응답 생성**:

   - **필터링 및 검열**: 부적절하거나 유해한 콘텐츠를 생성하지 않도록 필터링 메커니즘을 적용합니다.
   - **편향 제거**: 데이터 편향으로 인한 불공정한 응답을 최소화하기 위해 알고리즘적 조정을 합니다.
   - **윤리 가이드라인 준수**: 사회적, 문화적 규범에 맞는 응답을 생성하도록 지침을 설정합니다.

   (이런 것들을 무시하기 위해 탈옥 프롬프팅과 같은 여러 시도를 하는 경우도 있습니다.)

### Multi-turn의 중요성…

**Multi-turn 대화**는 사용자와 챗봇 간의 여러 차례에 걸친 상호작용을 의미하며, 자연스럽고 유의미한 대화를 위해 필수적입니다. 그 중요성과 구현 방안은 다음과 같습니다:

1. **컨텍스트 이해 및 유지**:
   - **참조 해소**: 이전 발화에서 언급된 대상이나 정보를 정확히 파악합니다.
   - **주제 전환 처리**: 대화 중 주제가 바뀌더라도 일관성을 유지합니다.
   - **암시적 정보 추론**: 직접적으로 언급되지 않은 정보도 문맥을 통해 이해합니다.
2. **대화 흐름 관리**:
   - **대화 상태 추적(Dialogue State Tracking)**: 사용자 의도와 슬롯 값을 추적하여 대화의 목표를 달성합니다.
   - **대화 정책(Dialgue Policy)**: 다음에 어떤 행동이나 응답을 할지 결정하는 정책을 수립합니다.
   - **에러 처리 및 복구**: 오해나 오류가 발생했을 때 적절히 수정하고 대화를 이어갑니다.
3. **기술적 구현**:
   - **메모리 메커니즘**: RNN, LSTM, Transformer 등 모델의 구조를 활용하여 장기 의존성을 처리합니다.
   - **외부 메모리 사용**: Neural Turing Machine이나 Memory Network를 통해 더 긴 컨텍스트를 유지합니다.
   - **요약 및 압축**: 중요한 정보를 요약하여 모델 입력의 길이 제한을 극복합니다.

### RAG(검색 증강 생성) ← Continue Chat 의 주요 기능

- 검색 증강 생성(Retrieval-Augmented Generation)은 LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법입니다.

1. **개념 및 필요성**:
   - **지식 한계 극복**: LLM은 학습 시점 이후의 정보나 특정 도메인 지식이 부족할 수 있습니다.
   - **정확성 향상**: 외부 데이터를 참고하여 사실 기반의 응답을 제공합니다.
   - **업데이트 가능성**: 실시간으로 변화하는 정보를 반영할 수 있습니다.
2. **구성 요소**:
   - **질의 생성(Query Generation)**: 사용자 입력을 기반으로 검색에 적합한 질의를 생성합니다.
   - **정보 검색(Retrieval)**: 생성된 질의를 사용하여 데이터베이스나 인터넷에서 관련 정보를 검색합니다.
   - **응답 생성(Answer Generation)**: 검색된 정보를 컨텍스트로 사용하여 최종 응답을 생성합니다.
3. **장점**:
   - **사실 검증**: 생성된 응답의 정확성을 높입니다.
   - **범용성**: 다양한 주제와 도메인에 적용할 수 있습니다.
   - **효율성**: 필요한 정보만 검색하여 처리하므로 연산 자원을 절약합니다.

![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkwB8j%2FbtsE1FuVwnW%2FQKl0qx50wltwWi6BcKDNvK%2Fimg.png)

---

## [Chat] Deep dive about Context Provider

Context Provider는 사용자가 생각하는 대부분의 것을 RAG의 형태로 chat의 Input으로 넣을 수 있습니다!

#### @codebase

코드 베이스에 있는 모든 파일을 Indexing 해서 저장을 하고, 유저의 프롬프트에 따라 필요한 파일을 찾아와 함께 context로 입력으로 주어 더 정확한 답변을 생성해냅니다.

코드베이스로 들어가는 문서의 양이 많기 때문에 문서들을 embedding을 하여 vectorDB에 저장한 뒤, 사용자가 입력한 프롬프트와 비교하여 찾아오는 과정이 필요합니다. 그렇기 때문에 만약 프롬프트가 부정확하다면 적절하지 못한 파일을 찾아 올 수도 있습니다.

이럴 때에는 @Foler, 또는 더 세밀하게 @open 을 사용하면 됩니다!

(@Foler 은 한 폴더를 지정, @open은 한 파일을 지정하여 Context로 넣게 만들어주는 과정입니다.)

EX) 이런 질문을 할 수 있게 됩니다!

"서버에 새 엔드포인트를 어떻게 추가하나요?"

"VS Code의 CodeLens 기능을 어디에서나 사용할 수 있나요?"

"HTML을 마크다운으로 변환하기 위해 이미 작성된 코드가 있나요?”

#### @**URL**

내 파일에 있는 것 뿐만 아니라 온라인 상에 있는 자료도 context에 넣고 싶다면 이 context provider을 사용하면 됩니다. URL 상에 있는 자료들을 markdown의 형태로 변환하여 context에 함께 들어가게 됩니다.

비슷하게 @google을 사용하게 된다면 구글 검색 엔진을 통해 나온 결과를 context에 포함하게 됩니다.

#### @**GitHub Issues**

Github에 올라와 있는 Issues 들도 함께 context로 넣을 수 있습니다.

비슷하게 @**GitLab Merge Request @Jira Issues 도 있습니다.**

그 밖의 Context provider도 많습니다.

[https://docs.continue.dev/customize/context-providers](https://docs.continue.dev/customize/context-providers)

---

## [Chat] Deep dive about Prompt Files

**Prompt Files 개요**

Prompt Files는 Continue 환경에서 프롬프트를 쉽게 관리하고 사용자 맞춤형 모델을 만드는 기능을 제공합니다. 이를 통해 모델이 어떻게 행동하는지를 결정하는 프롬프트를 저장하고 수정할 수 있습니다. Prompt Files는 JSON 형식의 파일로 작성되며, 다양한 매개변수를 통해 대화형 모델의 동작을 세부적으로 제어할 수 있습니다.

**Prompt Files의 활용**
Prompt Files는 특히 특정 사용 사례에 맞춘 맞춤형 대화를 설계하거나, 특정 행동 양식을 구현할 때 유용합니다. 예를 들어, 프롬프트 파일을 사용해 특정 대화 스타일(페르소나 설정)을 유지하거나 특정 주제에 대한 모델의 집중도를 높이는 데 사용할 수 있습니다.

EX- 모든 답변을 한글로 하라는 명령을 통해, 굳이 한 번 더 “한글로 번역해줘”와 같은 수고를 덜 수 있습니다.

사용법

1. 작업 공간의 최상위 수준에 .prompts/라는 폴더를 만듭니다.
2. 이 폴더에 test.prompt라는 파일을 추가합니다. 이 파일의 이름은 프롬프트를 생성하는 데 사용할 slash Command의 이름이 됩니다. ( /test 라고 입력창에 넣으면 기본 프롬프트가 들어가게 됩니다.)
3. test.prompt에 내용을 작성하고 저장합니다.

```
temperature: 0.5
maxTokens: 4096
---
<system>
You are an expert programmer
</system>

{{{ input }}}

Write unit tests for the above selected code, following each of these instructions:
- Use `jest`
- Properly set up and tear down
- Include important edge cases
- The tests should be complete and sophisticated
- Give the tests just as chat output, don't edit any file
- Don't explain how to set up `jest`
```

---

### Slash commands

위에서 언급된 사전에 정의 된 Prompt입니다.

```
{
  "name": "edit",
  "description": "Edit highlighted code"
},
{
  "name": "comment",
  "description": "Write comments for the highlighted code"
}
```

## [Autocomplete] How to use it

자동 완성 기능은 타이핑하는 동안 인라인 코드 제안을 제공합니다.
활성화하려면 IDE 하단 오른쪽의 상태 표시줄에 있는 "Continue" 버튼을 클릭하거나 IDE 설정에서 "Enable Tab Autocomplete" 옵션이 체크되어 있는지 확인하세요.

아래 이미지에서는 이미 자동완성이 활성화 되어있기 때문에 "Disable Tab Autocomplete" 문구가 있습니다.

![autocomplete disable](https://github.com/user-attachments/assets/4c82f14d-4542-4d29-9668-95a8728b87c2)

### Accepting a full suggestion

Continue가 추천해준 자동완성을 모두 적용하려면 `Tab` 키를 누르면 됩니다.

### Rejecting a full suggestion

Continue가 추천해준 자동완성을 모두 적용하려면 `Esc` 키를 누르면 됩니다.

### Partially accepting a suggestion

`cmd/ctrl + →`를 누르면서 단어별로 자동완성을 적용할 수 있습니다.

## [Autocomplete] Model setup

Continue 공식문서에서는 자동완성 기능을 사용할 때 [Mistral API](https://console.mistral.ai/)에서 제공하는 Codestral 모델을 사용하는 것을 추천하고 있습니다. 코드 맥락을 잘 이해해 고품질의 자동완성 기능을 제공하기 때문입니다.

[공식문서](https://docs.continue.dev/customize/model-types/autocomplete)를 보고 Codestral을 사용하던 중 잘못된 API KEY를 사용하고 있다는 오류를 발견했습니다.

다행히 공식문서에 해결방법이 나와있었는데요. mistral에서는 일반 API key와 Codestral의 API key가 다릅니다.

_Mistral API Key_
<img width="1460" alt="mistral api key" src="https://github.com/user-attachments/assets/806c2a3e-9b83-4f13-8431-706888490abd">

_Codestral API Key_
<img width="1436" alt="codestral api key" src="https://github.com/user-attachments/assets/98cfbb83-e6af-46dc-8931-6e43747700f0">

Codestral의 API key를 넣어야 하는데 mistral의 API key를 넣어서 발생했습니다.

```json title="config.json""
{
  "tabAutocompleteModel": {
    "title": "Codestral",
    "provider": "mistral",
    "model": "codestral-latest",
    "apiKey": "YOUR_API_KEY"
  }
}
```

만약 팀과 api key를 공유하거나 mistral api를 사용하려면 아래처럼 apiBase를 설정해야 합니다.

```json title="config.json""
{
  "tabAutocompleteModel": {
    "title": "Codestral",
    "provider": "mistral",
    "model": "codestral-latest",
    "apiKey": "YOUR_API_KEY",
    "apiBase": "https://api.mistral.ai/v1" // 이부분 추가
  }
}
```

### 로컬, offLine / 혹은 자체 호스팅

로컬과 자체 호스팅에서는 `StarCoder2-3b` 모델을 추천합니다.

```json title="config.json""
{
  "tabAutocompleteModel": {
    "title": "StarCoder2-3b",
    "model": "starcoder2:3b",
    "provider": "ollama"
  }
}
```

### 대안

- 하드웨어가 좋지 않다면 `deepseek-coder:1.3b-base`를 추천합니다.
- 하드웨어가 좋다면 `deepseek-coder:6.7b-base` 모델을 사용하면 더욱 고품질의 자동완성을 제공합니다.

> LM Studio 사용자의 경우 "My Models" 섹션으로 이동하여 원하는 모델을 찾고 경로를 복사하세요(예: second-state/StarCoder2-3B-GGUF/starcoder2-3b-Q8_0.gguf). 이 경로를 config의 `model` 값으로 사용하세요.

### 다른 모델들

다른 모델들 링크 [here](../customize/model-types/autocomplete.md).

## [Autocomplete] Context selection

자동 완성기능은 현재 커서 위치를 기반으로 자동으로 맥락(context)을 결정합니다. 우리는 프롬프트에 포함할 내용을 결정하기 위해 다음과 같은 기술을 사용합니다

### File prefix/suffix

커서 위치 이전과 이후의 코드를 항상 포함합니다.

### Definitions from the Language Server Protocol

편집기에서 cmd/ctrl + 클릭을 사용할 수 있는 것과 유사하게, 우리는 "정의로 이동"을 위해 동일한 도구(LSP(Language Server Protocol))를 사용합니다. 예를 들어, 함수 호출을 입력하고 있다면 함수 정의를 포함할 것입니다. 또는 메서드 내부에 코드를 작성하고 있다면 매개변수나 반환 타입에 대한 타입 정의를 포함할 것입니다.

> LSP 간단 설명
> 프로그래밍을 할 때 자동 완성, 정의로 이동, 모든 참조 찾기와 같은 똑똑한 도구들을 쉽게 지원하기 위해서 사용되는 프로토콜이라고 합니다.

### 파일들 Import

모든 import를 포함할 수는 없습니다. 대신, 커서 주변의 변수 중 일치하는 임포트가 있는 것을 찾아 맥락(context)으로 사용합니다.

### 최근 파일들

최근에 열었거나 편집한 파일을 자동으로 고려하여 현재 자동완성과 관련된 스니펫을 포함합니다.

## [Autocomplete] 트러블 슈팅 및 후기

- [continue 세팅후기](https://velog.io/@ehdghks12/2024-OSSCA-Continue-1)

- markdown을 작성할때 자동완성 기능이 작동해 아래와 같이 너무 많은 api 요청을 보낸다는 오류가 발생했습니다.
  markdown을 작성할때에는 autuComplete 기능을 disable했는데 파일 형식에 따라 자동으로 on/Off하는 기능이 있으면 좋을 것 같습니다.

- vscode 기본 단축키와 겹치는게 몇개 있었습니다. ex) cmd + i

- 자동완성 기능은 vscode의 IntelliCode 확장과 비슷하게 사용할 수 있어 금방 적응할 수 있었습니다.

<!-- [auto] how it works ~ how to customize -->

## [Autocomplete] How it works

### Timing : Too many Request를 줄이는 전략

1. `debounce`

- autocomplete task는 키 입력이 끝난 후 설정한 시간이 지난 후에 실행됩니다.
- 연속된 입력 이벤트를 하나로 처리하는 전략인 debounce를 사용합니다.
- 기본은 350ms 입니다.
  - 즉, 키 입력 이후 350ms만큼 기다린 후에 autocomplete task가 실행됩니다.
- `debounceDelay: number` 옵션으로 제어할 수 있습니다.

2. `caching`

- 경량 데이터베이스인 `sqlite3`에 autocomplete 결과를 캐싱하는 전략입니다.

  ```ts
  // core/autocomplete/cache.ts
  import { Mutex } from "async-mutex";
  import { open } from "sqlite";
  import sqlite3 from "sqlite3";
  import { DatabaseConnection } from "../indexing/refreshIndex.js";
  import { getTabAutocompleteCacheSqlitePath } from "../util/paths.js";

  export class AutocompleteLruCache {
    private static capacity = 1000;
    private mutex = new Mutex();

    db: DatabaseConnection;

    constructor(db: DatabaseConnection) {
      this.db = db;
    }
    // ...
  ```

1. autocomplete task 이후, 프롬프트의 prefix를 key로 설정해 답변을 `cache` 테이블에 저장합니다.

```ts
// core/autocomplete/cache.ts
await this.db.run(
  "INSERT INTO cache (key, value, timestamp) VALUES (?, ?, ?)",
  prefix,
  completion,
  Date.now()
);
```

2. 동일한 요청을 보내기 전, cache 테이블에 저장된 결과를 확인해 사용합니다.

```ts
const result = await this.db.get(
  "SELECT key, value FROM cache WHERE ? LIKE key || '%' ORDER BY LENGTH(key) DESC LIMIT 1",
  prefix
);
```

- SELECT 쿼리 내용: `prefix`로 시작하는 모든 결과를 고려하되, 가장 key가 긴 결과 1개를 읽습니다.
- `useCache: bool` 옵션으로 제어할 수 있습니다.

### Filtering : 불완전한 LLM 응답을 보완하는 전략

- LLM은 쓸만한 outcome을 출력하지만 항상 Instruction을 지키지는 않습니다.
- 그래서 `continue`에서는 LLM outcome을 regex 수준으로 필터링하고 사용합니다.

  ```ts
  // core/autocomplete/completionProvider.ts
  // ...
  const outcome = await this.getTabCompletion(token, options, llm, input);

  if (!outcome?.completion) {
    return undefined;
  }

  // Filter out unwanted results
  if (isOnlyPunctuationAndWhitespace(outcome.completion)) {
    return undefined;
  }
  // ...
  ```

  ```ts
  // core/autocomplete/filter.ts
  // 구둣점(...)하고 whitespace만 있는지 필터링하는 함수
  export function isOnlyPunctuationAndWhitespace(completion: string): boolean {
    const punctuationAndWhitespaceRegex = /^[^\w\d\}\)\]]+$/;
    return punctuationAndWhitespaceRegex.test(completion);
  }
  ```

- 또, LLM별 이상한 버릇을 직접 교정하기도 합니다.
- 예를 들어, CodeLlama가 가진 버릇으로 첫 줄에 2칸 들여쓰기를 하는 경우에 잘라버리는 코드입니다.

  ```ts
  // core/autocomplete/lineStream.ts

  /**
   * Removes leading indentation from the first line of a CodeLlama output.
   * @param {LineStream} lines - The input stream of lines.
   * @yields {string} Lines with the first line's indentation fixed if necessary.
   */
  export async function* fixCodeLlamaFirstLineIndentation(lines: LineStream) {
    let isFirstLine = true;

    for await (const line of lines) {
      if (isFirstLine && line.startsWith("  ")) {
        yield line.slice(2);
        isFirstLine = false;
      } else {
        yield line;
      }
    }
  }
  ```

## [Autocomplete] How to customize

- `config.json`의 `tabAutocompleteOptions` 을 통해 autocomplete를 제어할 수 있습니다.
- 기본 옵션은 다음과 같습니다.

```ts
export const DEFAULT_AUTOCOMPLETE_OPTS: TabAutocompleteOptions = {
  disable: false,
  useCopyBuffer: false,
  useFileSuffix: true,
  maxPromptTokens: 1024,
  prefixPercentage: 0.85,
  maxSuffixPercentage: 0.25,
  debounceDelay: 350,
  multilineCompletions: "auto",
  slidingWindowPrefixPercentage: 0.75,
  slidingWindowSize: 500,
  maxSnippetPercentage: 0.6,
  recentlyEditedSimilarityThreshold: 0.3,
  useCache: true,
  onlyMyCode: true,
  useOtherFiles: true,
  useRecentlyEdited: true,
  recentLinePrefixMatchMinLength: 7,
  disableInFiles: undefined,
  useImports: true,
};
```

- `multilineCompletions`
  - 옵션을 통해 multi-line으로 출력할지(`always`) single-line만 출력할지(`never`) outcome length를 정할 수 있습니다.
- `disableInFiles`
  - 파일 확장자 별로 autocomplete를 비활성화할지 여부를 결정할 수 있습니다.
  - `"disableInFiles": ["*.md", "*.json"]`: .md, .json 파일에서는 autocomplete를 사용하지 않습니다.
