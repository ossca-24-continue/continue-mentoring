# AutoComplete

## 00. How to use it

자동 완성 기능은 타이핑하는 동안 인라인 코드 제안을 제공합니다.
활성화하려면 IDE 하단 오른쪽의 상태 표시줄에 있는 "Continue" 버튼을 클릭하거나 IDE 설정에서 "Enable Tab Autocomplete" 옵션이 체크되어 있는지 확인하세요.

![autocomplete disable](https://github.com/user-attachments/assets/4c82f14d-4542-4d29-9668-95a8728b87c2)

위의 이미지에서는 이미 자동완성이 활성화 되어있기 때문에 "Disable Tab Autocomplete" 문구가 있습니다.

### 00.1 Accepting a full suggestion

Continue가 추천해준 자동완성을 모두 적용하려면 `Tab` 키를 누르면 됩니다.

### 00.2 Rejecting a full suggestion

Continue가 추천해준 자동완성을 모두 적용하려면 `Esc` 키를 누르면 됩니다.

### 00.3 Partially accepting a suggestion

`cmd/ctrl + →`를 누르면서 단어별로 자동완성을 적용할 수 있습니다.

## 01. Model setup

Continue 공식문서에서는 자동완성 기능을 사용할 때 [Mistral API](https://console.mistral.ai/)에서 제공하는 Codestral 모델을 사용하는 것을 추천하고 있습니다. 코드 맥락을 잘 이해해 고품질의 자동완성 기능을 제공하기 때문입니다.

[공식문서](https://docs.continue.dev/customize/model-types/autocomplete)를 보고 Codestral을 사용하던 중 잘못된 API KEY를 사용하고 있다는 오류를 발견했습니다.

다행히 공식문서에 해결방법이 나와있었는데요. mistral에서는 일반 API key와 Codestral의 API key가 다릅니다.
<img width="1460" alt="mistral api key" src="https://github.com/user-attachments/assets/806c2a3e-9b83-4f13-8431-706888490abd">

- TODO 이미지 추가
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

## 로컬, offLine / 혹은 자체 호스팅

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

## 대안

- 하드웨어가 좋지 않다면 `deepseek-coder:1.3b-base`를 추천합니다.
- 하드웨어가 좋다면 `deepseek-coder:6.7b-base` 모델을 사용하면 더욱 고품질의 자동완성을 제공합니다.

> LM Studio 사용자의 경우 "My Models" 섹션으로 이동하여 원하는 모델을 찾고 경로를 복사하세요(예: second-state/StarCoder2-3B-GGUF/starcoder2-3b-Q8_0.gguf). 이 경로를 config의 `model` 값으로 사용하세요.

## Other experiences

다른 모델들 링크 [here](../customize/model-types/autocomplete.md).

# Context selection

자동 완성기능은 현재 커서 위치를 기반으로 자동으로 맥락(context)을 결정합니다. 우리는 프롬프트에 포함할 내용을 결정하기 위해 다음과 같은 기술을 사용합니다

## File prefix/suffix

커서 위치 이전과 이후의 코드를 항상 포함합니다.

## Definitions from the Language Server Protocol

편집기에서 cmd/ctrl + 클릭을 사용할 수 있는 것과 유사하게, 우리는 "정의로 이동"을 위해 동일한 도구(LSP(Language Server Protocol))를 사용합니다. 예를 들어, 함수 호출을 입력하고 있다면 함수 정의를 포함할 것입니다. 또는 메서드 내부에 코드를 작성하고 있다면 매개변수나 반환 타입에 대한 타입 정의를 포함할 것입니다.

## Imported files

많은 import가 있기 때문에 모두 포함할 수는 없습니다. 대신, 커서 주변의 기호 중 일치하는 임포트가 있는 것을 찾아 맥락으로 사용합니다.

## Recent files

최근에 열었거나 편집한 파일을 자동으로 고려하여 현재 자동완성과 관련된 스니펫을 포함합니다.

## 트러블 슈팅 및 후기

- [continue 세팅후기](https://velog.io/@ehdghks12/2024-OSSCA-Continue-1)

- markdown을 작성할때 자동완성 기능이 작동해 아래와 같이 너무 많은 api 요청을 보낸다는 오류가 발생했습니다.
markdown을 작성할때에는 autuComplete 기능을 disable했는데
파일 형식에 따라 자동으로 on/Off하는 기능이 있으면 좋을 것 같습니다.
