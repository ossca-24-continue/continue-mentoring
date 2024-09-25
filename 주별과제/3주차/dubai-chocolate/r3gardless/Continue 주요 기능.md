# Continue 주요 기능

*해당 문서는 Continue 주요 기능에 대한 설명을 다룹니다.*

[Overview | Continue](https://docs.continue.dev/getting-started/overview)

<aside>
💡 해당 문서는 VS Code 기준으로 작성되었습니다.

</aside>

# Chat

[Chat](https://docs.continue.dev/chat/how-to-use-it) 기능은 IDE 에서 나가지 않고도 LLM 에게 도움을 받을 수 있습니다.

<aside>
💡 코드를 질문에 추가하는 단축키는 VS Code 기준 cmd/ctrl + L 입니다.

</aside>

1. 단축키를 통해 특정 코드를 질문에 추가하고 틀린 부분을 물어봅니다.
  
<img width="1049" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 13 40" src="https://github.com/user-attachments/assets/1f62e3d9-5ee9-4360-8e20-bedc1568fefe">

2. LLM 을 통해 틀린 부분에 대한 피드백을 받을 수 있습니다.

<img width="1272" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 16 02" src="https://github.com/user-attachments/assets/fe8a759d-764b-48e7-b46d-51370e036388">



# Autocomplete

[Autocomplete](https://docs.continue.dev/autocomplete/how-to-use-it) 기능은 입력 시 inline code suggestion 을 할 수 있습니다. 

<img width="368" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 40 00" src="https://github.com/user-attachments/assets/b741a4c5-5749-42c4-b4d9-5c35109b607a">

<img width="302" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 52 59" src="https://github.com/user-attachments/assets/5aa35389-dec5-48dd-ad73-18b53a07da26">

Autocomplete 하는 `key` 는 다음과 같습니다.

- `Tab` : code suggestion 을 모두 사용합니다.
- `Esc` : code suggestion 을 사용하지 않습니다.
- `cmd/ctrl + →` : code suggestion 중 word 단위로 사용합니다.

`config.json`

<aside>
💡 Autocomplete Model 을 사용합니다.

</aside>

```json
  "tabAutocompleteModel":     {
    "title": "GPT-4o (Free Trial)",
    "provider": "free-trial",
    "model": "gpt-4o",
    "systemMessage": "You are an expert software developer. You give helpful and concise responses."
  },
```

# Edit

[Edit](https://docs.continue.dev/edit/how-to-use-it) 기능은 현재 파일을 벗어나지 않고 코드를 편리하게 수정할 수 있습니다.

<aside>
💡 Chat Model 과 동일한 모델을 사용합니다!

</aside>

Edit 하는 `key` 는 다음과 같습니다.

- `cmd/ctrl + I` : 코드를 드래그하고 사용합니다.
1. Edit 기능을 사용하고 싶은 코드 라인을 선택 후 `key` 를 누른 후 원하는 내용을 작성합니다.

<img width="578" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 54 00" src="https://github.com/user-attachments/assets/57b194b6-52c9-49a0-b9c9-1ad027de537d">

2. `submit`  을 누르면 다음과 같이 표시됩니다.

<img width="466" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10 54 46" src="https://github.com/user-attachments/assets/29cce4fc-a07c-4933-ac7d-cc4fe2967e21">

3. 다음과 같은 `key` 를 사용하여 원하는 부분을 수정합니다.
- `cmd/ctrl + opt + y` : 해당 부분에 대한 변경 사항을 반영합니다.
- `cmd/ctrl + opt + n` : 해당 부분에 대한 변경 사항을 거절합니다.
- `cmd/ctrl + shift + enter` : 모든 변경 사항을 반영합니다.
- `cmd/ctrl + shift + delete` : 모든 변경 사항을 거절합니다.

<img width="942" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 47 00" src="https://github.com/user-attachments/assets/7b6922e6-b2ee-4dc5-8db9-92708c50514c">

# Actions

[Actions](https://docs.continue.dev/getting-started/overview) 기능은 일반적으로 사용할 때 단축키를 제공합니다.

<aside>
💡 Chat Model 과 동일한 모델을 사용합니다!

</aside>

### edit

1. 특정 코드를 질문에 추가하고 `/edit` 을 사용

<img width="939" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 47 21" src="https://github.com/user-attachments/assets/8755d4bc-c17d-40e7-8e85-6345e8ec69cd">
하여 원하는 내용을 반영하게 합니다.

2. 변경 사항을 반영 혹은 거절할 수 있습니다.

<img width="934" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 48 31" src="https://github.com/user-attachments/assets/1720b889-8376-4ab7-b208-f9b706655528">

### comment

1. 특정 코드를 질문에 추가하고 `/comment` 을 사용하여 주석을 추가합니다.

<img width="973" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-09-25_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7 48 52" src="https://github.com/user-attachments/assets/1ef388f1-7084-4e0b-850d-689cc88db900">

2. 변경 사항을 반영 혹은 거절할 수 있습니다.

![0f842101-535d-4590-bfcb-902b7b232ec8](https://github.com/user-attachments/assets/ac4bbd4a-f2c8-4369-8d0f-0b5562596d23)

다음과 같은 `SlashCommands` 를 기본적으로 제공합니다.

- `edit` : 선택된 코드 블럭에 주어진 입력을 반영해서 변경합니다.
- `comment` : 선택된 코드 블럭에 주석을 추가합니다.
- `share` : 현재 Chat session 을 markdown 으로 내보냅니다.
- `cmd` : 주어진 입력에 맞는 cmd 명령어를 생성합니다.
- `commit` : `git diff` 제공 시 git commit 메시지를 생성합니다.

설정은 다음과 같이 `config.json` 에서 할 수 있습니다. 

```json
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
```
