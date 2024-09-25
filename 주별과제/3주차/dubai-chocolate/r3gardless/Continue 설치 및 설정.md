# Continue 설치 및 설정

*해당 문서는 Continue 설치 및 설정하는 방법을 다룹니다.*

[Install | Continue](https://docs.continue.dev/getting-started/install)

<aside>
💡 해당 문서는 VS Code 기준으로 작성되었습니다.
</aside>

# Continue 설치

1. **VS Code MarketPlace** 에서 continue extension 를 설치합니다

![설치 화면](https://github.com/user-attachments/assets/9824910c-2caf-4c81-a071-1385f3ccaabf)


<aside>
📌  [VS Code MarketPlace](https://marketplace.visualstudio.com/items?itemName=Continue.continue) 링크를 통해서도 검색 가능합니다.

</aside>

1. 설치하면 **QuickStart 화면을** 확인할 수 있습니다.

![설치 화면2](https://github.com/user-attachments/assets/94e49729-4163-4910-895b-b733a272aadf)

### Tip

<aside>
📌 아래와 같이 드래그 하여 Secondary Side Bar 로 이동할 수 있습니다

</aside>

![move-to-right-sidebar](https://github.com/user-attachments/assets/4f13d0f0-7b09-4f9f-b568-523169692439)


<aside>
❗ Secondary Side Bar 를 닫을 경우 좌측 Activity Bar 로 다시 옮겨지지 않습니다.

- Toggle Secondary Side Bar 를 다시 열어야 활성화 됩니다.
</aside>

# Continue 설정

*Continue 에서 Chat Model 을 사용하는 방법은 다음과 같습니다.*

## 1 Model API 사용

## 1.1 Free-Trial

Continue 는 아래 Chat Model 들에 대해 **Free-Trial** 을 제공해줍니다. (최대 50번 사용 가능)

- Claude 3 Sonnet
- GPT-4o
- Llama3 70b
- Codestral

`config.json` 

```json
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

## 1.2 Open AI API 사용

[OpenAI Platform](https://platform.openai.com/docs/overview)

**Project** 를 생성하여 API Key 를 발급 받을 수 있습니다.

<img width="1507" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 26 24" src="https://github.com/user-attachments/assets/90a207ba-f951-46c1-aa03-e401ef3bdb28">


**Continue** 에 **Provider**, **Model** 과 **발급받은 API Key** 정보를 등록합니다 

<img width="500" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 28 25" src="https://github.com/user-attachments/assets/e092344c-4f82-41d9-881f-e93a9aab50b4">


<img width="250" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_11 10 04" src="https://github.com/user-attachments/assets/5cf2f422-a832-4838-a29f-61e2a4f8e48f">


`config.json` 

```json
  "models": [
    {
      "model": "gpt-4o",
      "contextLength": 128000,
      "title": "GPT-4o",
      "systemMessage": "You are an expert software developer. You give helpful and concise responses.",
      "provider": "openai",
      "apiKey": "등록받은 API Key"
    }
  ],
```

## 2 Local Model 사용

<aside>
💡 해당 문서는 **Ollama** 를 사용하였습니다. (**Ollama** 설치가 필요합니다.) https://ollama.com/download
</aside>

아래 명령어로 **Ollama Chat Model** 을 다운받을 수 있습니다.

```bash
ollama pull llama3.1:8b 
```

<img width="406" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_8 46 02" src="https://github.com/user-attachments/assets/be8c7433-e1b9-4b48-9415-df195e895384">


설치 완료 시, 위와 같이 별도의 API 연결 없이 local 모델로 실행이 가능합니다.

`config.json` 

```json
  "models": [
    {
      "title": "Llama 3.1 8B",
      "provider": "ollama",
      "model": "llama3.1:8b"
    },
    {
      "title": "Llama 3.1 8B",
      "provider": "ollama",
      "model": "llama3.1:8b"
    }
  ],
```

<aside>
💡 **설정을 완료 하였으면 사용법은 다음 문서에 있습니다**
</aside>
