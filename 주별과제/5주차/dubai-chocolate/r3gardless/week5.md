# 5주차 과제 주차 전체 정리

## 목차

- [💻 AI Coding Assistant 도구 조사](#-ai-coding-assistant-도구-조사)
- [💻 Continue 설치, 설정](#-continue-설치-설정)
- [💻 Continue 기능](#-continue-기능)
  - [💬 Chat](#-chat)
  - [🔄 Autocomplete](#-autocomplete)
  - [✏️ Edit](#-edit)
  - [⚙️ Actions](#-actions)


## 💻 AI Coding Assistant 도구 조사

### 1. AI Coding Assistant 중요성

AI 코딩 어시스턴트는 생산성 향상, 코드 품질 개선, 학습 지원, 오류 감소, 협업 강화, 비용 절감의 장점을 가짐.

- **생산성 향상**: 반복적인 코딩 작업을 자동화하고, 코드 제안을 통해 개발 속도를 크게 향상시킵니다.
- **코드 품질 개선**: 최신 프로그래밍 패턴과 모범 사례를 기반으로 한 제안을 통해 전반적인 코드 품질을 향상시킵니다.
- **학습 지원**: 새로운 프로그래밍 언어나 프레임워크를 배우는 개발자들에게 실시간 예제와 설명을 제공합니다.
- **오류 감소**: 잠재적인 버그와 보안 취약점을 사전에 식별하여 오류를 줄이는 데 도움을 줍니다.
- **협업 강화**: 팀 내에서 일관된 코딩 스타일과 패턴을 유지하는 데 도움을 주어 협업 효율성을 높입니다.
- **비용 절감**: 개발 시간 단축과 버그 감소로 인한 유지보수 비용 절감 효과를 가져옵니다.

### 2. AI Coding Assistant 도구

- **Amazon CodeWhisperer**: AWS에서 제공하는 AI 기반 코딩 어시스턴트로, AWS 환경에서의 개발을 최적화하는 기능을 가지고 있습니다.

- **Codex**: OpenAI에서 개발한 AI 코딩 어시스턴트로, 다양한 프로그래밍 언어를 지원하며 자연어 처리가 뛰어납니다.

- **Cursor**: AI 기반 코드 에디터로, 자연어 명령을 통해 코드 자동완성, 리팩토링, 코드 수정이 가능합니다.

- **Tabnine**: 사용자의 코드를 공개하지 않고, 다양한 IDE에서 소프트웨어 개발을 쉽게 할 수 있도록 돕는 AI 코드 어시스턴트입니다.

- **Codeium**: 인공지능 기반의 코딩 어시스턴트 익스텐션 서비스로, 무료 티어로 제공되며 다양한 기능을 지원합니다.

- **GitHub Copilot**: GitHub, OpenAI, Microsoft가 합작하여 만든 AI 코딩 어시스턴트로, 코드 자동완성 및 새로운 코드 블록 생성을 지원합니다.

- **Replit GhostWriter**: 코드 자동완성, 코드 설명 및 이해, 코드 개선 및 최적화, 디버깅 지원, 실시간 협업 기능을 제공하는 AI 코딩 어시스턴트입니다.

### 3. Continue
VSCode, JetBrains 개발 환경과 통합되어 사용자의 코딩 작업을 지원하는 오픈소스 도구입니다.
- **주요 기능**: 문맥 인식 대화, 자연어 기반 코드 재작성, 모델 커스터마이징, 채팅, 자동완성.

- **차별화 특징**: 개발 데이터 수집, 오픈 소스, 무료 제공, 모델 선택의 유연성, 다양한 컨텍스트 지원, 높은 확장성.

## 💻 Continue 설치, 설정

### 1. Continue 설치

Continue는 VSCode와 IntelliJ에서 플러그인 형식으로 설치할 수 있습니다:

- **VSCode**: Extensions 탭에서 Continue를 검색 후 설치합니다. 설치 후 우측 하단에 Chat 기능 탭이 표시됩니다.
- **IntelliJ**: 플러그인 탭에서 설치합니다. 설치 후 우측 상단에 Chat 기능 탭이 나타납니다.


### 2. Continue 설정

1. **Free-Trial**: Claude 3 Sonnet, GPT-4o, Llama3 70b 등 모델을 최대 50회 무료로 사용할 수 있습니다.
2. **API Key 발급**: OpenAI, Anthropic API Key를 `config.json`에 등록합니다.
3. **Local Model 설정**: Ollama를 설치 후 로컬 모델을 실행하고, `config.json`을 수정하여 설정합니다.

## 💻 Continue 기능

### 💬 Chat
IDE 내에서 AI와 대화하며 문제를 해결할 수 있습니다. 
코드 하이라이팅, 제안 적용, 모델 변경 등의 기능을 제공합니다.

- **모델 설정**: Claude Sonnet 3.5, GPT-4o 등 다양한 고성능 AI 모델을 지원하며, 로컬 환경에서도 사용할 수 있습니다.


### 🔄 Autocomplete
Tab 키로 자동완성을 수락하고, Esc 키로 거부할 수 있습니다. 
단어 단위로 부분 수락도 가능합니다.

- **모델 설정**: Codestral 모델을 사용해 고품질 자동완성을 제공합니다. 로컬 및 오프라인 환경에서는 StarCoder2-3b 모델을 추천합니다.


### ✏️ Edit
코드 블록을 하이라이트한 후 수정 사항을 제안하고, 이를 수용(accept)하거나 거부(reject)할 수 있는 기능입니다.

- **모델 설정**: Claude Sonnet 3.5, GPT-4o 등 다양한 고성능 AI 모델을 지원하며, 로컬 환경에서도 사용할 수 있습니다.
- **사용법**:
  - 코드를 하이라이트하고 단축키로 Edit 창을 활성화합니다.
  - 수정 사항을 탐색하여 수용 또는 거부합니다.
  - 새로운 제안 요청 시 다시 Edit 기능을 활성화합니다.

### ⚙️ Actions
코드 리뷰, 주석 추가, 커밋 등 자주 사용하는 작업을 빠르게 수행할 수 있는 단축키 기능입니다.

- **모델 설정**: Claude Sonnet 3.5, GPT-4o 등 다양한 고성능 AI 모델을 지원하며, 로컬 환경에서도 사용할 수 있습니다.
- **사용법**:
  - `/` 명령어로 다양한 액션을 수행할 수 있습니다.
  - `.prompt` 파일을 작성해 자신만의 명령어를 정의할 수 있습니다.
- **주요 Slash 명령어**:
  - `/edit`: 코드 수정.
  - `/comment`: 주석 추가.
  - `/share`: 채팅 기록 공유.
  - `/commit`: Git 커밋 메시지 생성.
  - `/so`: StackOverflow 질문 검색.

## 📄 Continue에서 사용하는 Model 유형, Model 연동 유형


## 📄 LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

## 📄 RAG, RAG in continue


## 📄 LLM, LLM benchmarks(for code), 선택가이드