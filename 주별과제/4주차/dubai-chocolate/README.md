# LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

## 목차

- [LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)](#llm-completion-options--continue에서-설정하기-챗-잘사용하기---효과적인-프롬프팅system-user)
  - [목차](#목차)
  - [팀 소개](#팀-소개)
    - [🍫 두바이초콜릿(dubai-chocolate)](#-두바이초콜릿dubai-chocolate)
  - [LLM completion options 알아보기](#llm-completion-options-알아보기)
  - [원하는 구조로 출력 커스텀](#원하는-구조로-출력-커스텀)
    - [context-provider 커스텀하기](#context-provider-커스텀하기)
    - [prompt 커스텀하기](#prompt-커스텀하기)
  - [효과적인 프롬프트 엔지니어링](#효과적인-프롬프트-엔지니어링)
    - [system 측면](#system-측면)
    - [user 측면](#user-측면)

## 팀 소개

### 🍫 두바이초콜릿(dubai-chocolate)

| 정승화                                                       | 김민성                                                        | 이영주                                                       | 송영욱                                                       | 왕지은                                                        | 최은정                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------------ |
| ![img](https://avatars.githubusercontent.com/u/62323657?v=4) | ![img](https://avatars.githubusercontent.com/u/169263118?v=4) | ![img](https://avatars.githubusercontent.com/u/77565980?v=4) | ![img](https://avatars.githubusercontent.com/u/48237469?v=4) | ![img](https://avatars.githubusercontent.com/u/134492810?v=4) | ![img](https://avatars.githubusercontent.com/u/31675683?v=4) |
| [@JSH-data](https://github.com/JSH-data)                     | [@GreenIdealist](https://github.com/GreenIdealist)            | [@abyss-s](https://github.com/abyss-s)                       | [@R3gardless](https://github.com/R3gardless)                 | [@Jieunwang0](https://github.com/Jieunwang0)                  | [@rovin0805](https://github.com/rovin0805)                   |

## LLM completion options 알아보기

## 원하는 구조로 출력 커스텀

### context-provider 커스텀하기

### prompt 커스텀하기

## 효과적인 프롬프트 엔지니어링

### system 측면

### user 측면

- **질문하기 전 생각 구조화하기**
  - 질문을 하기 전에 생각의 연결고리(Chain-of-Thought, CoT)를 통해 대답을 유도합니다.
    - `"차근차근 단계적으로 생각해 줘"`
- **프롬프트에게 페르소나 부여하기**

  - 프롬프트에게 역할, 맥락과 배경을 부여합니다.
    - `"너는 ~ 역할이고, 나는 이러한 답변이 필요한 ~ 사람이야."`
  - 답변 난이도를 결정하는 문체를 지정하면 더욱 좋습니다.
    - `"졸업 논문에 작성할 수 있을 정도로 전문적으로 알려줘" 또는 "초등학생도 쉽게 이해할 수 있을 정도로 설명해줘"`

- **명확하고 구체적으로 지시하기**

  - 범위를 좁혀서 질문합니다.
  - 어떤 포맷으로 출력할지 명시합니다.
  - 어떤 방법으로 추출할지 명확히 합니다.
    - `"300자 이내의 서론, 본론, 결론으로 알려줘", "표로 알려줘", "~ 관련해서 10가지를 알려줘"`

- **영어로 번역해서 질문하기**
  - 대부분의 AI가 영어를 기반으로 작성되었기 때문에 영어로 질문할 때 답변의 퀄리티가 더 좋을 때가 많습니다.
  - 특히 전문 분야의 경우, 한국어 질문에 대한 답변이 아쉬울 때는 영어로 질문하고, 생성된 영어 답변을 다시 한글로 번역해봅시다.

#### Continue와 함께 개발에 활용하는 법

- **@Codebases, @Files**
  - 특정 함수 내용 등 코드 분석
  - 버그나 에러 찾기
- **Comment**
  - 주석 작성
- **@Docs**
  - 공식 문서 예제를 바로 참고하여 작성
- **/Build a custom propmpt or command**
  - 테스트 케이스 작성 및 검사
  - 반복해야 하는 작업을 자동화
- **/Chat, /Autocomplete**
  - 개발 문서나 양식 초안 작성

> 생성형 AI를 사용하면서 느낀 점은 대체로 여러 번 질답을 거듭할수록 답변의 질이 떨어진다는 것이었습니다. 따라서 초기 질문 지시사항을 어떻게 주느냐에 따라 시간과 비용이 크게 차이납니다. 내가 모르는 것이 무엇이고, 어떻게 잘 도움을 받을 수 있을지에 대한 '메타인지'를 기릅시다😊

#### 참고자료

- [ChatGPT에게서 좋은 대답을 이끌어 내는 방법 7가지](https://tech.kakaobank.com/posts/2312-drawing-out-good-responses-from-ai/)
- [좋은 질문을 하는 방법, 구조화 방법](https://www.gotai.co.kr/%EC%B1%97%EC%A7%80%ED%94%BC%ED%8B%B0-2/)
