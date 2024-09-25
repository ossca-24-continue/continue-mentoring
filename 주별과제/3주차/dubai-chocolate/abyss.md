# 📝 Continue 두바이초콜릿 팀 3주차 과제

> 작성: _이영주_([@abyss-s](https://github.com/abyss-s))

## Continue 설치

1. Vscode 익스텐션에서 Continue를 검색
2. Install 버튼을 눌러 설치
3. 설치가 완료되면 왼쪽 사이드바에 Continue 아이콘이 생성됨

## Continue 설정

사용할 모델과 그 모델을 사용하기 위한 API 키가 필요합니다.
저는 OpenAI(ChatGPT)와 Anthropic(Claude)를 사용하여 설정했습니다.

[OpenAI 문서 링크](https://platform.openai.com/docs/overview)
[Anthropic 콘솔 링크](https://console.anthropic.com/settings/keys)

### 1. 결제 수단 등록하기

- Billing을 선택해 결제 수단을 등록합니다. (최소 5달러)
- 해외 결제가 가능한 카드로 등록해야 합니다.
- 카드 정보 및 개인 정보를 입력하고 최소 한도인 5달러로 설정합니다.
- 비용 부과를 방지하기 위하여 자동 결제를 비활성화합니다.
- 결제 수단이 성공적으로 등록되면 5달러가 설정된 것을 확인할 수 있습니다.

### 2. API Key 발급하기

- Create new secret key를 눌러 새로운 키를 발급받고 복사해둡니다.
  - 한번 발급된 키를 다시 확인할 수 없으므로 반드시 **복사 or 백업**해두어야 합니다.

### config.json 파일에 키 등록

- config.json에 모델 정보와 함께 키를 등록합니다.

- 익스텐션에서 add 버튼을 눌러 자동 추가하거나, json 파일을 직접 수정할 수 있습니다.

> 설정파일 예시

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
  "tabAutocompleteModel": {
    "title": "Tab Autocomplete",
    "provider": "free-trial",
    "model": "codestral-latest"
  },
  "embeddingsProvider": {
    "provider": "free-trial"
  },
  "reranker": {
    "name": "free-trial"
  }
}
```

[Customize에 관한 공식문서 바로가기 링크](https://docs.continue.dev/customize/overview)

free-trial은 키를 등록하지 않아도 사용 가능하지만, 최대 50번밖에 사용할 수 없기 때문에 공부를 위해서는 부족할 수도 있습니다.

따라서 이렇게 키를 등록해주면 공부할 만큼은 충분히 사용할 수 있습니다.

## 주요 기능 오버뷰

### 1. Chat

- 가장 핵심적인 기능으로, 일반적인 생성형 AI 모델과 같이 다양한 기능을 수행할 수 있습니다.
- 다양한 모델을 선택하여 코드 작성, 디버깅, 아이디어 추천 받기 등의 목적으로 활용할 수 있습니다.

### 2. Autocomplete

- 코드 작성 시 작성하던 코드를 기반으로 회색 글씨로 자동완성됩니다.
- 마음에 든다면 TAP키를 눌러 해당 파일에서 바로 적용 가능하고, 아니라면 esc를 눌러 거부할 수 있습니다.
- 함수 이름, 변수 이름, 코드 스니펫 등을 자동으로 제안해주어 생산성을 높일 수 있습니다.

### 3. Edit

- ctrl+L 또는 /edit 명령을 통해 실행합니다.
- 코드를 드래그하여 AI 모델에게 적절한 코드 수정을 요청할 수 있습니다.
- 새로운 diff 창이 열리면서 변경사항을 확인하고 원하는 부분만 허용하거나 수락하여 빠른 수정이 가능합니다.

### 4. Actions

- 슬래시(/)를 입력하면 사용 가능한 내장 명령어 목록을 확인할 수 있습니다.
- Build a custom prompt를 누르면 자신만의 커스텀 명령어를 생성할 수 있습니다.

- `/comment`
  - /edit과 똑같이 작동하지만, 자동으로 코드에 주석을 달도록 요청합니다.
- `/share`
  - 현재 채팅 기록의 공유 가능한 마크다운 사본을 생성합니다.
- `/cmd`
- VS Code에서만 가능한 명령어로, 채팅으로 입력한 명령어를 shell 스크립트로 변환해 터미널에 입력합니다.
- `/commit`
  - gif diff를 통해 변경사항을 파악하고 커밋 메시지를 생성합니다.

---
