# Continue 설치, 설정, 주요 기능 오버뷰

## 목차

- [Continue 설치, 설정, 주요 기능 오버뷰](#continue-설치-설정-주요-기능-오버뷰)
  - [목차](#목차)
  - [팀 소개](#팀-소개)
    - [🍫 두바이초콜릿(dubai-chocolate)](#-두바이초콜릿dubai-chocolate)
  - [Continue 설치](#continue-설치)
    - [1. VSCode](#1-vscode)
    - [2. IntelliJ](#2-intellij)
  - [Continue 설정](#continue-설정)
    - [1. Free-Trial](#1-free-trial)
    - [2. API Key](#2-api-key)
      - [2-1. 결제 수단 등록하기](#2-1-결제-수단-등록하기)
      - [2-2. API Key 발급받기](#2-2-api-key-발급받기)
      - [2-3. config.json 수정하기](#2-3-configjson-수정하기)
    - [3. Local Model](#3-local-model)
      - [3-1. Ollama 설치하기](#3-1-ollama-설치하기)
      - [3-2. Ollama 실행하기](#3-2-ollama-실행하기)
      - [3-3. config.json 수정하기](#3-3-configjson-수정하기)
  - [주요 기능](#주요-기능)
    - [Chat](#chat)
    - [Autocomplete](#autocomplete)
    - [Edit](#edit)
    - [Actions](#actions)
      - [Slash (/) Command](#slash--command)
      - [Build a custom prompt](#build-a-custom-prompt)

## 팀 소개

### 🍫 두바이초콜릿(dubai-chocolate)

| 정승화                                                        | 김민성                                     | 이영주                                                       | 송영욱                                                       | 왕지은                                                        | 최은정                                                       |
| ------------------------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------------ |
| ![img](https://avatars.githubusercontent.com/u/62323657?v=4) | ![img](https://avatars.githubusercontent.com/u/169263118?v=4)    | ![img](https://avatars.githubusercontent.com/u/77565980?v=4) | ![img](https://avatars.githubusercontent.com/u/48237469?v=4) | ![img](https://avatars.githubusercontent.com/u/134492810?v=4) | ![img](https://avatars.githubusercontent.com/u/31675683?v=4) |
| [@JSH-data](https://github.com/JSH-data)            | [@GreenIdealist](https://github.com/GreenIdealist) | [@abyss-s](https://github.com/abyss-s)                       | [@R3gardless](https://github.com/R3gardless)                 | [@Jieunwang0](https://github.com/Jieunwang0)                  | [@rovin0805](https://github.com/rovin0805)                   |

## Continue 설치

Continue는 오픈 소스 기반의 AI 코드 어시스턴트입니다. 현재 Microsoft의 VSCode와 Jetbrains의 Intellj에서 플러그인 형식으로 다운받고 실행할 수 있습니다.


### 1. VSCode

Extensions 탭을 선택합니다.

<img width="1024" alt="스크린샷 2024-09-22 오후 4 18 46" src="https://github.com/user-attachments/assets/85821619-6d38-422b-9323-5fc2f9fed861">

검색 창에 Continue를 입력하고 설치를 진행합니다.

<img width="1024" alt="스크린샷 2024-09-26 오후 7 36 44" src="https://github.com/user-attachments/assets/282f7bc9-d9e3-4743-bb68-60cd5740b9f3">


설치가 완료되면 우측 하단에 Continue 마크가 표시되며 클릭 시 Continue의 Chat 기능을 위한 별도의 탭이 나타납니다.


<img width="1024" alt="스크린샷 2024-09-22 오후 4 20 12" src="https://github.com/user-attachments/assets/abf692c4-a7fc-4ef4-96e0-1a48d28f109e">

### 2. IntelliJ
먼저 `cmd/ctrl + ,`를 통해 설정 화면에 들어가서 플러그인 탭을 선택합니다.

![jsh-1](https://github.com/user-attachments/assets/a965cdb8-66c0-4e8f-88df-9dd815a316ac)

검색 창에 Continue를 입력하고 설치를 진행합니다.

![jsh-2](https://github.com/user-attachments/assets/b1660680-663c-472b-b6bb-bc6b7cff0019)

설치가 완료되면 우측 상단에 Continue 마크가 표시되며 클릭 시 Continue의 Chat 기능을 위한 별도의 탭이 나타납니다.

![jsh-3](https://github.com/user-attachments/assets/fe5921f2-5ecf-4137-b356-0d3d2bd02234)

## Continue 설정

Continue에서 제공하는 기능을 자유롭게 사용하려면 Model과 그 Model을 사용하기 위한 API Key가 필요합니다.

### 1. Free-Trial

Continue는 아래 Chat Model에 대해 최대 50회 사용 가능한 **Free-Trial** 을 제공합니다.

- Claude 3 Sonnet
- GPT-4o
- Llama3 70b
- Codestral

```json
// config.json

"models": [
    {
      "title": "Claude 3 Sonnet (Free Trial)",
      "provider": "free-trial",
      "model": "claude-3-sonnet-20240229"
    },
    {
      "title": "GPT-4o (Free Trial)",
      "provider": "free-trial",
      "model": "gpt-4o",
      "systemMessage": "You are an expert software developer. You give helpful and concise responses."
    },
    {
      "title": "Llama3 70b (Free Trial)",
      "provider": "free-trial",
      "model": "llama3-70b",
      "systemMessage": "You are an expert software developer. You give helpful and concise responses. Whenever you write a code block you include the language after the opening ticks."
    },
    {
      "title": "Codestral (Free Trial)",
      "provider": "free-trial",
      "model": "codestral"
    }
  ],
```

### 2. API Key

*해당 문서에서는 **[OpenAI](https://platform.openai.com/docs/overview)** 와 **[Anthropic](https://console.anthropic.com/)** 를 사용하여 설정했습니다.

#### 2-1. 결제 수단 등록하기

- Billing을 선택해 결제 수단을 등록합니다.
- 해외 결제가 가능한 카드로 등록해야 합니다.
- 카드 정보 및 개인 정보를 입력하고 금액을 설정합니다.
- 비용 부과를 방지하기 위하여 자동 결제를 비활성화합니다.
- 결제 수단이 성공적으로 등록되면 설정한 금액이 등록된 것을 확인할 수 있습니다.

#### 2-2. API Key 발급받기

- Create new secret key를 눌러 새로운 키를 발급받고 복사합니다.
- 한번 발급된 키를 다시 확인할 수 없으므로 반드시 **복사 or 백업** 합니다.

#### 2-3. config.json 수정하기

- config.json에 모델 정보와 함께 키를 등록합니다.

- Extension에서 add 버튼을 눌러 자동으로 추가되도록 하거나, config.json 파일을 직접 수정할 수 있습니다.

```json
{
  "models": [
    {
      "model": "gpt-4o-mini",
      "contextLength": 128000,
      "title": "GPT-4o Mini",
      "provider": "openai",
      "apiKey": "발급받은 OpenAI API 키"
    },
    {
      "model": "claude-3-sonnet-20240229",
      "contextLength": 200000,
      "title": "Claude 3 Sonnet",
      "apiKey": "발급받은 Anthropic API 키",
      "provider": "anthropic"
    }
  ],
}
```

[Customize에 관한 Continue 공식 문서](https://docs.continue.dev/customize/overview)

### 3. Local Model

*해당 문서에서는 Ollama를 사용하여 진행했습니다.

실행 환경 :
- Device: Macbook Air M2
- OS: MacOS 15.0
- Ram: 16GB

#### 3-1. Ollama 설치하기

**[Ollama](https://ollama.com)** 에 접속합니다.

![jsh-4](https://github.com/user-attachments/assets/f888da94-2b3e-402e-8ef5-c57bdc38c039)


다운로드된 파일을 실행시켜 설치를 진행합니다.

![jsh-5](https://github.com/user-attachments/assets/734d8e90-5bba-4c9e-8d1e-530a0eb81543)

#### 3-2. Ollama 실행하기
설치가 정상적으로 진행되었다면 터미널을 열고 `ollama run llama3.1:8b`를 입력합니다.

![jsh-6](https://github.com/user-attachments/assets/94b5167e-0c27-45b2-9e28-9b5310e215ff)

터미널을 통해 바로 Ollama와 대화할 수 있습니다.


![jsh-7](https://github.com/user-attachments/assets/63984c46-206a-4b93-bacd-67c13e500a0e)


#### 3-3. config.json 수정하기

이제 Continue와 로컬에서 실행 중인 Ollama를 연결하기 위해 Continue의 config.json 파일을 아래와 같이 수정합니다.

```json 
{  
  "models": [  
    {  
      "title": "Llama 3.1 8b",  
      "provider": "ollama",  
      "model": "llama3.1-8b"  
    }  
  ],
}
```

## 주요 기능

### [Chat](https://docs.continue.dev/chat/how-to-use-it)

Continue의 Chat 탭에 질문을 넣으면 AI가 해당 질문에 대한 대답을 반환합니다. 

1. 단축키(cmd+L)를 통해 특정 코드를 chat box에 추가하고 AI에게 질문합니다.
  
<img width="1049" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 13 40" src="https://github.com/user-attachments/assets/1f62e3d9-5ee9-4360-8e20-bedc1568fefe">

2. LLM을 통해 피드백을 받을 수 있습니다.

<img width="1272" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_101602" src="https://github.com/user-attachments/assets/fe8a759d-764b-48e7-b46d-51370e036388">


### [Autocomplete](https://docs.continue.dev/autocomplete/how-to-use-it)

Autocomplete를 사용하려면 config.json에 다음과 같이 Model을 설정합니다.

```json
 {
  "tabAutocompleteModel":     {
    "title": "GPT-4o (Free Trial)",
    "provider": "free-trial",
    "model": "gpt-4o",
    "systemMessage": "You are an expert software developer. You give helpful and concise responses."
  },
 }
```

<img width="368" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 40 00" src="https://github.com/user-attachments/assets/b741a4c5-5749-42c4-b4d9-5c35109b607a">

<img width="302" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 52 59" src="https://github.com/user-attachments/assets/5aa35389-dec5-48dd-ad73-18b53a07da26">


AutoComplete에 사용하는 단축키는 다음과 같습니다.

- `Tab` : code suggestion을 모두 사용합니다.
- `Esc` : code suggestion을 사용하지 않습니다.
- `cmd/ctrl + →` : code suggestion 중 word 단위로 사용합니다.


### [Edit](https://docs.continue.dev/edit/how-to-use-it)

Edit 기능으로 현재 파일을 벗어나지 않고 IDE 상에서 코드를 편리하게 수정할 수 있습니다.

1. Edit 기능을 사용하고 싶은 코드 라인을 선택 후 `cmd/ctrl + I` , 그리고 대화창에 원하는 수정 방식을 작성합니다.

  <img width="578" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 54 00" src="https://github.com/user-attachments/assets/57b194b6-52c9-49a0-b9c9-1ad027de537d">

2. AI가 수정된 코드를 반환합니다. 

  <img width="466" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 54 46" src="https://github.com/user-attachments/assets/29cce4fc-a07c-4933-ac7d-cc4fe2967e21">

3. 다음과 같은 단축키를 사용하여 원하는 부분을 수정합니다.
- `cmd/ctrl + opt + y` : 해당 부분에 대한 변경 사항을 반영합니다.
- `cmd/ctrl + opt + n` : 해당 부분에 대한 변경 사항을 거절합니다.
- `cmd/ctrl + shift + enter` : 모든 변경 사항을 반영합니다.
- `cmd/ctrl + shift + delete` : 모든 변경 사항을 거절합니다.

<img width="942" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 47 00" src="https://github.com/user-attachments/assets/7b6922e6-b2ee-4dc5-8db9-92708c50514c">


### [Actions](https://docs.continue.dev/getting-started/overview)

Actions 기능은 단축어 기능과 유사합니다. 

임의의 코드 블록을 드래그한 뒤 `cmd/ctrl + L`을 누르면 우측 Continue 탭에서 Actions 기능을 위한 별도의 화면이 나타납니다. 

<img width="464" alt="스크린샷 2024-09-23 오전 12 11 28" src="https://github.com/user-attachments/assets/789ec1ca-08ee-48ef-8c01-a717d02ef536">


'/'를 타이핑하여 원하는 Action을 선택하고 실행시키면 AI가 해당 Action을 실행합니다. 

아래는 /edit와 /comment의 예시입니다.

**/edit**

1. 특정 코드를 질문에 추가하고 `/edit` 을 사용

<img width="939" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 47 21" src="https://github.com/user-attachments/assets/8755d4bc-c17d-40e7-8e85-6345e8ec69cd">
하여 원하는 내용을 반영하게 합니다.

2. 변경 사항을 반영 혹은 거절할 수 있습니다.

<img width="934" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 48 31" src="https://github.com/user-attachments/assets/1720b889-8376-4ab7-b208-f9b706655528">

**/comment**

1. 특정 코드를 질문에 추가하고 `/comment` 을 사용하여 주석을 추가합니다.

<img width="973" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 48 52" src="https://github.com/user-attachments/assets/1ef388f1-7084-4e0b-850d-689cc88db900">

2. 변경 사항을 반영 혹은 거절할 수 있습니다.

![0f842101-535d-4590-bfcb-902b7b232ec8](https://github.com/user-attachments/assets/ac4bbd4a-f2c8-4369-8d0f-0b5562596d23)

#### Slash (/) Command

다음과 같은 **slashCommands** 를 기본적으로 제공합니다.

- `edit` : 선택된 코드 블럭에 주어진 입력을 반영해서 변경합니다.
- `comment` : 선택된 코드 블럭에 주석을 추가합니다.
- `share` : 현재 Chat session 을 markdown 으로 내보냅니다.
- `cmd` : 주어진 입력에 맞는 cmd 명령어를 생성합니다.
- `commit` : **git diff** 제공 시 git commit 메시지를 생성합니다.

설정은 config.json에서 가능합니다.

```json
{
  "slashCommands": [
    {
      "name": "edit",
      "description": "Edit selected code"
    },
    {
      "name": "comment",
      "description": "Write comments for the selected code"
    },
    {
      "name": "share",
      "description": "Export the current chat session to markdown"
    },
    {
      "name": "cmd",
      "description": "Generate a shell command"
    },
    {
      "name": "commit",
      "description": "Generate a git commit message"
    }
  ],
}
```

#### Build a custom prompt

**.prompt** 파일을 통해 커스텀 슬래쉬 명렁어를 생성할 수 있습니다.

1. 워크스페이스 최상단에 `.prompts/` 폴더를 직접 생성하거나, chat box 밑의 Build a custom prompt를 누르면 워크스페이스 최상단에 .prompt라는 폴더가 생성됩니다.
   
2. 프롬프트 폴더에서 생성한 파일의 이름은 프롬프트를 생성하는 데 사용할 슬래시 명령어의 이름이 됩니다.
  ( e.g., `test.prompt` ⇒ `/test` )

파일에 프롬프트 내용을 작성하면 chat 화면에서 슬래시(/)+ 프롬프트파일명 + ENTER를 통해 프롬프트에서 지시한 내용을 따르게 됩니다.
