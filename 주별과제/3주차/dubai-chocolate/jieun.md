# 🍫 2조\_두바이초콜릿\_3주차

## 목차

- [🍫 2조\_두바이초콜릿\_3주차](#-2조_두바이초콜릿_3주차)
  - [목차](#목차)
  - [Continue 설치](#continue-설치)
  - [Continue 설정](#continue-설정)
    - [GET API KEY Process](#get-api-key-process)
      - [OpenAI](#openai)
      - [Anthropic](#anthropic)
    - [Setting Config.json](#setting-configjson)
  - [Continue Overview](#continue-overview)
    - [Chat](#chat)
    - [Autocomplete](#autocomplete)
    - [Edit](#edit)
    - [Actions](#actions)

## Continue 설치

- VSCode Extension에서 Continue 설치
- 사용자 편의성을 위해 Continue를 오른쪽 탭으로 옮긴다

## Continue 설정

Continue에서는 Anthropic, Azure OpenAI, Amazon Bedrock, Gemini 등 많은 Provider를 제공하고 있다.

아래에서는 OpenAI랑 Anthropic을 가지고 적용한다.

### GET API KEY Process

#### OpenAI

**[OpenAI](https://platform.openai.com/docs/overview) > Setting > Billing**

- Credit을 설정한다
- 프리티어로 50회를 지원해주지만 여기서 난 최소 단위(5달러)로 크레딧을 결제한다.
- Auto recharge OFF Check

**[OpenAI](https://platform.openai.com/docs/overview) > Setting > Profile**

- User API keys > + Create new secret key
- 키를 발급받고 카피한다.

#### Anthropic

**[Anthropic](https://console.anthropic.com/) > Get API Keys > Plans & billing**

**Build/Scale** 방식이 있다고 뜨는데 **Build**로 진행하면 OpenAI 처럼 크레딧 차감 형식이 되고, **Scale**로 진행하려면 "Contact sales to upgrade to Scale" 이라고 영업부랑 컨택하라는 메세지가 나온다.

- 크레딧을 사용하기 위해 Credit을 설정한다
- 나는 프리티어로 주는 것을 사용하기 위해 결제없이 API key를 발급받았다.
- **[Anthropic](https://console.anthropic.com/) > Get API Keys**
- User API keys > + Create new secret key
- 키를 발급받고 카피한다.
-

### Setting Config.json

- VSCode로 돌아와서 cmd+L로 Continue를 연다.

<img width="520" alt="스크린샷 2024-09-22 오후 4 21 51" src="https://github.com/user-attachments/assets/9261c1ea-7746-4279-bf37-376d2c972c07">

- Add Chat model로 모델을 추가한다.

<img width="499" alt="스크린샷 2024-09-22 오후 4 23 33" src="https://github.com/user-attachments/assets/c234d531-cac2-4a1a-99c1-4abc50be4d0a">

- Provider, Model, API key를 등록하고 Connect하면 VScode상에서 config.json에 업데이트된 내역이 뜬다.

## Continue Overview

Continue README에서는 Chat, Autocomplete, Edit, Actions를 주요 기능으로 소개하고 있다.

### Chat

Continue 창은 vscode 기준 cmd+L로 열 수 있다.

그리고 검색할 모델을 설정해준 다음, 채팅으로 궁금한 점을 질문 할 수도 있고 @를 눌러서 파일을 지정해서 질문할 수 있다.

Continue에서는 @codebase라는 기능을 기본적으로 제공하여 프로젝트 내에서 코드베이스와 관련된 정보를 빠르게 검색하고 리뷰할 수 있는데, 사용자 정의 벡터 데이터베이스를 설정해 RAG(Retrieval-Augmented Generation)를 구축할 수 있다.

### Autocomplete

다른 ai coding assistant와 같이 자동완성 기능으로 실시간으로 코드 제안을 받고 키보드 조작으로 간단하게 적용할지 말지 결정할 수 있다.

### Edit

코드의 특정 부분을 선택하고 cmd+L을 누르면 오른쪽에 옮겨둔 창으로 선택한 부분이 검색되고, AI에게 개선 방안을 요청할 수 있다.

### Actions

앞에서 간단한 키보드 조작으로 제안을 수락/거절할 수 있다고 했는데, 이것 말고도 일반적인 사용 사례에 대한 단축키가 지정되어 있다.

/ 와 @가 대표적으로 이렇게 chat box에도 작성되어 있다.

사용자가 직접 프롬프트를 작성할 수도 있는데, 맨 밑의 Build a custom prompt를 누르면 작업하던 곳에서 .prompt라는 폴더가 생성된다. 그리고 그 프롬프트 폴더에서 생성한 파일의 이름은 프롬프트를 생성하는 데 사용할 슬래시 명령어의 이름이 된다.

파일에 프롬프트 내용을 작성하고, 저 chat 화면에서 /(프롬프트파일명) + ENTER 치면 프롬프트에서 지시한 내용을 따르게 된다.

그리고 현재는 vscode에서만 가능한

액션에 대한 다른 트리거
라는 기능이 있던데, 문서를 둘러보니 작업을 호출하는 또다른 방법들을 몇가지 소개하고 있다.

마우스 우클릭이나 디버그 액션, 전구 아이콘 클릭 등과 같은 일반적인 작업 사용 사례들에 더 간단히 접근할 수 있는 단축키를 제공하고 있다.

간단히 둘러보기만 했는데 Continue Docs에 잘 정리되어있어서 설치, 설정에 큰 무리없이 따라갈 수 있었다. 그리고 기능에 대한 접근도 어렵지 않은 느낌을 받았다.
