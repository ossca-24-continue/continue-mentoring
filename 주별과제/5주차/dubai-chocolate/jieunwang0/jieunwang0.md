# 5주차 개인 과제

- [5주차 개인 과제](#5주차-개인-과제)
  - [1. AI Coding Assitant 도구 조사 및 비교 분석](#1-ai-coding-assitant-도구-조사-및-비교-분석)
    - [1-1. Amazon CodeWhisperer](#1-1-amazon-codewhisperer)
    - [1-2. Codex](#1-2-codex)
    - [1-3. Cursor](#1-3-cursor)
    - [1-4. Tabnine](#1-4-tabnine)
    - [1-5. Codeium](#1-5-codeium)
    - [1-6. GitHub Copilot](#1-6-github-copilot)
    - [1-7. replit GhostWriter](#1-7-replit-ghostwriter)
  - [2. Continue의 특징, 장점](#2-continue의-특징-장점)
    - [2-1. LLM, LLM benchmarks(for code), 선택가이드](#2-1-llm-llm-benchmarksfor-code-선택가이드)
    - [2-2. 도구 선택 가이드라인 및 추천](#2-2-도구-선택-가이드라인-및-추천)
  - [3. Continue 설치/설정](#3-continue-설치설정)
    - [3-1. Continue에서 사용하는 Model 유형/연동 유형](#3-1-continue에서-사용하는-model-유형연동-유형)
      - [3-1-1. Autocomplete Model](#3-1-1-autocomplete-model)
      - [3-1-2. Chat model](#3-1-2-chat-model)
      - [3-1-3. Embeddings model](#3-1-3-embeddings-model)
      - [3-1-4. Reranking model](#3-1-4-reranking-model)
    - [3-2. Continue 모델 연동 유형](#3-2-continue-모델-연동-유형)
      - [3-2-1. AI 모델 제공 및 개발 플랫폼](#3-2-1-ai-모델-제공-및-개발-플랫폼)
      - [3-2-2. 클라우드 AI 서비스](#3-2-2-클라우드-ai-서비스)
      - [3-2-3. AI 모델 배포 및 서버리스 플랫폼](#3-2-3-ai-모델-배포-및-서버리스-플랫폼)
      - [3-2-4. 로컬 AI 실행 도구](#3-2-4-로컬-ai-실행-도구)
      - [3-2-5. AI 워크플로우 및 통합 도구](#3-2-5-ai-워크플로우-및-통합-도구)
      - [3-2-6. 특화된 AI 서비스](#3-2-6-특화된-ai-서비스)
    - [3-3. Free-Trial](#3-3-free-trial)
  - [4. LLM completion options \& continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)](#4-llm-completion-options--continue에서-설정하기-챗-잘사용하기---효과적인-프롬프팅system-user)
    - [4-1. Continue에서 completionOption 설정하는 법](#4-1-continue에서-completionoption-설정하는-법)
      - [4-1-1. config.json \> completionOption](#4-1-1-configjson--completionoption)
      - [4-1-2. config.json \> models \> completionOptions](#4-1-2-configjson--models--completionoptions)
    - [4-2. Context Provider 커스텀하기](#4-2-context-provider-커스텀하기)
      - [Custom Context Provider](#custom-context-provider)
    - [4-3. Custom slash commands](#4-3-custom-slash-commands)
      - [4-3-1. .prompt 파일 생성하기](#4-3-1-prompt-파일-생성하기)
      - [4-3-2. 자연어 프롬프트 (customCommands 속성, config.json)](#4-3-2-자연어-프롬프트-customcommands-속성-configjson)
      - [4-3-3. 함수를 작성하는 프롬프트 (slashCommands 속성, config.ts)](#4-3-3-함수를-작성하는-프롬프트-slashcommands-속성-configts)
    - [4-4. 효과적인 프롬프트 엔지니어링](#4-4-효과적인-프롬프트-엔지니어링)
      - [4-4-1. LLM의 응답의 품질을 더욱 향상시키기](#4-4-1-llm의-응답의-품질을-더욱-향상시키기)
      - [4-4-2. Continue와 함께 개발에 활용하는 법](#4-4-2-continue와-함께-개발에-활용하는-법)
    - [Chat, Autocomplete](#chat-autocomplete)
      - [RAG, RAG in continue](#rag-rag-in-continue)
    - [Edit, Actions](#edit-actions)

## 1. AI Coding Assitant 도구 조사 및 비교 분석
   - 🤖 Amazon CodeWhisperer
   - 🤖 Code
   - 🤖 Cursor
   - 🤖 Tablin
   - 🤖 Codeium
   - 🤖 GitHub Copilot
   - 🤖 replit GhostWriter
  

### 1-1. Amazon CodeWhisperer
AWS 환경에서의 개발을 최적화한다는 특징을 가지고 있다.

  `주요 특징` : 자동 완성, 다양한 프로그래밍 언어 지원, 주석 기반 코드 생성, AWS 서비스와의 통합


### 1-2. Codex
현재 Github Copilot, TabNine등과 같은 AI coding assistant도 Third-party extensions로서 Codex를 사용(leverage)하고 있다.

 `주요 특징` : Coding assistant에 특화된 모델을 사용, 12개 이상의 언어, 자연어 처리

### 1-3. Cursor

Cursor는 기존 플러그인 방식이 아닌 VS Code를 기반으로 만들어진 편집기이다.

 `주요 특징` : 자동 완성, 코드 생성, 편집 및 리팩토링, Chat, 실시간 오류 감지 및 수정, 멀티 파일 분석

### 1-4. Tabnine

Tabnine은 사용자가 입력하는 코드를 공개하지 않고 정해진 범위 안에서 소프트웨어 개발을 쉽고 빠르게 할 수 있다.

 `주요 특징` :
|제목|주요기능|가격|
|---|---|---|
|PRO|*최고의 AI모델 적용, AI채팅 에이전트, 보안취약점 필터링, 개인정보보호, 영업 시간 지원*|월 $12|
|Enterprise|*SaaS 또는 On-premise에서 구축 가능, 개인화 AI 채팅 에이전트, Confluence 통합, 영업시간 지원 및 관련 교육*|월 $39|
|Basic|*무료, AI채팅(속도 제한)*|월 $ 0|


### 1-5. Codeium
전반적으로 Github Copilot와 유사한 기능들을 제공하면서 무료 티어로 사용할 수 있다.

 `주요 특징` : 자동 완성, 자연어로 Command 작성, Chat, 우클릭으로 옵션 접근 가능

### 1-6. GitHub Copilot
Github 과 밀접한 기능을 제공한다.

 `주요 특징` : 자동 완성, Chat, Pull request 요약


### 1-7. replit GhostWriter
Replit 플랫폼에서만 사용할 수 있으며, 로컬 개발 환경에서는 사용할 수 없는 대신 팀원과 실시간 협업이 가능하다는 특징이 있다.

 `주요 특징` : 자동 완성, 편집 및 리팩토링, 디버깅, 실시간 협업

## 2. Continue의 특징, 장점
Continue는 VSCode, JetBrains 등의 개발 환경과 통합되어 사용자의 코딩 작업을 지원하는 도구이다.
GitHub Copilot과 유사한 기능을 제공하면서도, 완전한 오픈소스 형태로 사용자가 AI 모델을 커스터마이징할 수 있는 점이 특징이다.

 `주요 특징` : 문맥 인식 대화, Chat, Command, Customize code, 자동 완성
 `장점` : 자동 데이터 수집, 오픈소스, 무료, 모델 선택의 유연성, 컨텍스트 다양성, 확장성


### 2-1. LLM, LLM benchmarks(for code), 선택가이드
### 2-2. 도구 선택 가이드라인 및 추천
  1. 교육 및 기술 지원 필요성
     - 기업 내에서 코드 어시스턴트 도입 시 이를 잘 활용할 수 있도록 하거나 사용 중 이슈 발생 시 해결할 수 있는 조직이 필요할 것으로 본다.
     따라서 회사에서 도입하고자 할 때에는 코드 어시스턴트 사용 방법에 대한 교육 및 이슈 지원을 받을 수 있는 코드 어시스턴트를 선택해야 한다.

  2. 보안 수준 검토
     - 개인이 취미 등으로 사용 시에는 보안 이슈가 없어 자유롭게 선택이 가능 할 것으로 본다.  
     그러나 기업에서 도입하는 경우 코드의 외부 유출 우려가 있으므로 이를 해결하기 위해 독립적으로 구성이 가능해야 하고
     회사에서 작성한 코드를 저장 및 공유 되거나 학습에 사용하지 않는 어시스턴트를 선택해야 한다.

## 3. Continue 설치/설정
**설치 :**
VSCode/JetBrains 중 사용하는 IDE에서 각 익스텐션/플러그인 탭에서 설

### 3-1. Continue에서 사용하는 Model 유형/연동 유형

- Autocomplete Model
- Chat Model
- Embeddings Model
- Reranking Model

#### 3-1-1. Autocomplete Model

중간 채우기-FIM-기법으로 훈련된 특수한 언어 모델. 코드 파일의 시작과 끝 부분이 주어졌을 때 중간에 들어갈 내용을 예측하도록 설계된 덕분에 상대적으로 작은 규모-3B  매개변수-의 모델로도 우수한 성능을 발휘할 수 있다. (반면, 일반적인 대화형 모델은 규모가 더 크더라도 이 특정 작업에서는 성능이 떨어질 수 있다.)

Continue에서는 주로 코드 작성 시 실시간으로 인라인 제안을 제공하는 데 활용된다.

**추천 모델**

Continue에서는 자동 완성 모델로 Mistral의 [Codestral](https://docs.continue.dev/customize/model-providers/mistral) 모델을 추천하며, 로컬 모델로는 [Ollama Provider](https://docs.continue.dev/customize/model-providers/ollama)와 함께 `Starcoder2-3B` 모델을 사용하는 것을 권장한다.

#### 3-1-2. Chat model

대화 형식으로 응답하도록 학습된 LLM. 일반적인 질문에 답변하고 복잡한 코드를 생성할 수 있어야 해서 최고 성능의 채팅 모델은 보통 405B 이상의 매개변수를 가진 대형 모델이다. Continue에서는 [Chat](https://docs.continue.dev/chat/how-to-use-it), [Edit](https://docs.continue.dev/edit/how-to-use-it), [Action](https://docs.continue.dev/actions/how-to-use-it) 기능에 사용한다.

**추천 모델**

[Claude 3.5 Sonnet](https://docs.continue.dev/customize/model-providers/anthropic)을 가장 추천하며, 다른 옵션으로는 [GPT-4o](https://docs.continue.dev/customize/model-providers/openai), [Gemini 1.5 Pro](https://docs.continue.dev/customize/model-providers/gemini), [Llama3.1 405B](https://docs.continue.dev/customize/tutorials/llama3.1)를 권장한다.

#### 3-1-3. Embeddings model

텍스트를 벡터로 변환하도록 훈련된 모델. 생성된 벡터는 나중에 다른 벡터들과 빠르게 비교하여 텍스트 간의 유사성을 판단하는 데 사용된다. 임베딩 모델은 일반적으로 LLM보다 훨씬 작은 모델이며, 따라서 비교적으로 매우 빠르고 저렴하다.

Continue에서는 인덱싱 과정 중에 임베딩을 생성하고, 이를 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 활용하여 코드베이스 전체에 대한 유사성 검색을 수행하는 것을 통해 가장 관련성 있는 컨텍스트를 워크스페이스에서 자동으로 가져올 수 있습니다.

**추천 모델**

어떤 모델이든 쓸 수 있다면 voyage-code-2를 추천하며, 로컬 환경에서 임베딩을 생성하고 싶다면 Ollama와 함께 nomic-embed-text를 사용하는 것을 권장한다.

이외에 Transformers.js를 사용해 로컬 임베딩을 생성할 수 있으며, 자체 임베딩 엔드포인트를 구축하고 싶을 경우 Hugging Face Text Embeddings Inference를 사용할 수 있다.

#### 3-1-4. Reranking model

리랭킹 모델(Reranking model)은 두 개의 텍스트-주로 사용자의 질문과 문서-를 입력받아 해당 문서가 질문에 답변하는 데 얼마나 유용할지 0에서 1 사이의 관련성 점수를 반환하도록 훈련된 모델입니다. 리랭킹 모델은 일반적으로 LLM보다 훨씬 작고 빠르고 저렴하다.

Continue 플랫폼에서는 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 리랭킹 모델을 사용한다. 이는 벡터 검색 후 가장 관련성 높은 코드 스니펫을 선택하는 데 필요하다.

**추천 모델**

어떤 모델이든 사용할 수 있다면, Voyage AI의 `rerank-1`을 추천한다. 혹은 [Cohere](https://docs.cohere.com/docs/rerank-2)에서 제공하는 리랭킹 모델을 사용할 수도 있다.

만약 LLM만 사용할 수 있는 상태라면 LLM 모델을 리랭킹 모델로 사용할 수는 있지만, 훨씬 비싸고 정확도가 떨어지므로 꼭 필요한 경우가 아니면 권장하지 않는다. 그리고 너무 많은 병렬 요청을 수행해야 하기 때문에 Ollama와 같은 로컬 모델에서는 사용할 수 없다. 

### 3-2. Continue 모델 연동 유형

Continue에서 사용자는 Provider를 설정하여 모델과 연동할 플랫폼을 선택하고, 각 Provider가 제공하는 AI 모델을 선택할 수 있다.

서비스의 주요 기능, 실행 환경, 특화된 기능을 기준으로 다음과 같이 여섯 가지 유형으로 분류했다.
- AI 모델 제공 및 개발 플랫폼
- 클라우드 AI 서비스
- AI 모델 배포 및 관리 도구
- 로컬 AI 실행 도구
- AI 워크플로우 및 통합 도구
- 특화된 AI 서비스

#### 3-2-1. AI 모델 제공 및 개발 플랫폼

자체 AI 모델을 개발하고 개발한 모델에 대한 API를 제공한다.

1. [**Mistral**](https://mistral.ai/)  
  
    - `Mistral Large`는 복잡한 작업에 가장 좋은 추론이 가능한 모델로 한국어를 포함해 다양한 언어를 지원하고 128K 토큰을 한번에 처리할 수 있다.(Context window)
    - `Codestra Codestra`는 코드 작업을 위해 프로그래밍 언어 80개 이상에 대해 학습한 모델로 다른 모델보다 응답이 빠르다. 32K 토큰을 처리할 수 있다.    
    - `Mistral Embed Mistral Embbed`는 텍스트를 추출하기 위해 사용되는 모델로서 현재는 영어만 지원한다.  
  
2. **[Anthropic](https://www.anthropic.com/)** 

    - Claude의 모델은 3가지로, `Haiku`는 가볍고 빠르게 사용하기 위한 모델, `Sonnet`은 성능과 속도의 적절한 수준의 모델, `Opus`는 성능이 가장 우수한 모델로 어려운 수학과 프로그래밍에 사용하는 모델이 있다.  
 
3. **[Deepseek](https://www.deepseek.com/)**   
    -  Continue에서는 채팅 모델로`deepSeek-chat`, 자동완성 모델에는 `deepseek-coder` 사용을 추천하며 임베딩, re-Ranking 모델은 제공하지 않는다.  

4. **[Gemini](https://gemini.google.com/?hl=ko)**  
    - 구글이 만든 AI 챗봇이며 Continue에서는 채팅 모델로 `Gemini 1.5 Pro`, 임베딩 모델에는 `models/text-embedding-004` 사용을 추천하며 자동완성, re-Ranking 모델은 제공하지 않는다.  

5. **[Ollama](https://ollama.com/)**
    - Ollama는 로컬에서 LLM을 구동할 수 있도록 하는 오픈소스이다. Continue에서는 채팅 모델로 `llama3.1:8`, 자동완성 모델로 `starcoder2:3b`, 임베딩 모델로 `nomic-embed-text`를 추천하며 re-Rankig 모델은 제공하지 않는다.
  
6. **[OpenAI](https://openai.com/)**  
    - OpenAI는 미국의 인공지능 기업으로 chatGPT로 유명해졌다. Continue에서는 채팅 모델로 `GPT-4o`, 자동완성 모델로 `starcoder2:3b`, 임베딩 모델로 `text-embedding-3-large`를 추천하며 re-Rankig 모델은 제공하지 않는다.


#### 3-2-2. 클라우드 AI 서비스

대규모 클라우드 제공업체가 제공하는 AI 및 머신러닝 서비스이고, 모델 훈련/배포/관리를 위한 종합적인 플랫폼을 제공해 주는 서비스이다.

다음은 대표적인 플랫폼 두 개이다. 

1. **[Azure OpenAI](https://azure.microsoft.com/ko-kr)**  
  
    - Azure는 Microsoft사의 Public Cloud 서비스를 제공하는 CSP사이다. 여러 AI 모델 공급사로부터 모델을 공급받아 서비스를 하는 형태이다.  
    - Continue에서는 채팅 모델로 `GPT-4o` 모델을 추천하며 자동완성 모델로 `Codestral`, 임베딩에는 `text-embedding-3-large` 모델 사용을 추천한다. re-Ranking 모델은 제공하지 않는다.
  
2. **[Amazon Bedrock](https://aws.amazon.com/ko/bedrock/?gclid=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB&trk=24a8f13a-f5db-4127-bcb7-8b2876aa4265&sc_channel=ps&ef_id=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB:G:s&s_kwcid=AL!4422!3!692062155749!e!!g!!amazon%20bedrock!21058131112!157173586057)** 
  
   - Amazon Bedrock은 AWS 환경에서 LLM을 개발하고 배포할 수 있는 플랫폼이다.   
   - Continue에서는 채팅 모델로 `Claude 3.5 Sonnet` 모델을 추천하며 임베딩에는 `amazon.titan-embed-text-v2:0` 모델 사용을 추천한다. 자동완성, re-Ranking 모델은 제공하지 않는다.
  
클라우드 AI 제공업체의 모델을 연동하는 방법은 주로 **API 연결**을 통해 이루어진다.

**클라우드 AI 사용의 장단점**

**장점 :**

    - 클라우드 AI Provider를 사용할 경우, 물리적인 인프라를 구축할 필요없이 사용한만큼만 지불하는 구조(Pay-as-you-go)를 통해 초기 투자 비용을 크게 절감할 수 있다.

**단점 :**

    - API를 이용해서 데이터를 전송하기 때문에 데이터가 제3자와 공유될 수 있는 위험성이 존재한다. 다만, OpenAI 엔터프라이즈 고객의 데이터를 사용하여 서비스 개선이나 모델 훈련에 사용하지 않겠다고 명시하는 등 보호 조치가 존재한다.
    - 장기적으로 볼 경우에는 사용량이 증가하면 지속적으로 발생하는 비용이 더 들 수도 있다. 


#### 3-2-3. AI 모델 배포 및 서버리스 플랫폼

- `Cloudflare Workers AI` : Cloudflare의 서버리스 플랫폼에서 머신러닝 모델을 실행할 수 있게 해주는 서비스. 엄선한 인기 오픈 소스 모델 세트와 텍스트 생성/자동 음성 인식/번역/텍스트 분류/이미지 분류/임베딩 모델을 제공한다. Cloudflare API를 통해 Continue와 연동할 수 있다.

- `HuggingFace Inference Endpoints` : 커스텀 모델, 혹은 HuggingFace 허브에 있는 모든 Transformer, Sentence-Transformer, Diffusers 모델들을 쉽고 안전하게 배포할 수 있는 서비스. 배포할 클라우드를 선택할 수 있으며 배포 후 생성된 엔드포인트는 API로 접근하여 Continue와 연동할 수 있다.

- `DeepInfra` : 낮은 가격으로 사용할 수 있는 서버리스 AI 모델 배포 서비스. 다양한 유명 모델 및 오픈소스 모델을 제공하여 인기 모델의 경우 사전 배포되어 있어 직접 배포하지 않고도 API를 통해 연동할 수 있다.

- `Together` : 다양한 AI 모델을 쉽게 사용/조정/배포할 수 있는 플랫폼을 제공하는 서비스. 많은 인기 모델들을 서버리스 엔드포인트를 통해 호스팅하고 있어 별도의 배포 작업 없이 쉽게 활용할 수 있으며 전용 GPU 인프라를 사용하여 자체 모델 혹은 오픈소스 모델을 직접 호스팅하는 기능도 제공한다.

- `vLLM` : LLM 추론 및 서빙을 위한 오픈소스 라이브러리. vLLM은 OpenAI의 Completions 및 Chat API와 호환되는 HTTP 서버를 제공하며 이를 통해 Continue와 연동할 수 있다.

**Continue와의 연동 방법**

vLLM을 제외하면 API를 제공하는 서비스들이기 때문에, 모두 비슷한 방식으로 연동한다.

1. 결제 수단 등록하기
2. API Key 발급받기
3. config.json 수정하기

#### 3-2-4. 로컬 AI 실행 도구

개인 컴퓨터나 로컬 서버에서 AI 모델을 실행할 수 있게 해주는 소프트웨어.

**1. [Ollama](https://ollama.com/)**   
  Ollama는 로컬 환경에서 LLM을 쉽게 실행할 수 있는 도구로 주로 GPT 계열 모델을 로컬에서 실행할 수 있다. 클라우드 의존성 없이 AI 모델을 로컬에서 처리하므로, 민감한 데이터를 보호하고 클라우드 저장소에 의존하지 않아도 되는 것이 주요 장점이고 다양한 LLM을 지원한다. 
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
**2. [LlamaCpp](https://github.com/ggerganov/llama.cpp)**  
  LlamaCpp는 Meta의 LLaMA 모델을 C++ 기반으로 GPU 없이도 로컬에서 실행할 수 있는 도구이다. 주로 CPU 성능을 극대화하여 고성능 LLM 추론을 지원하며, 저사양 환경에서도 효율적으로 LLM을 로컬에서 사용할 수 있다.

**3. [Llamafile](https://github.com/Mozilla-Ocho/llamafile)**   
  Llamafile은 복잡한 서버 설정이 필요 없고 llama.cpp와 Cosmopolitan Libc의 결합을 통해 다양한 환경에서 실행 가능한 단일 빌드로 모든 기능을 패키징 하므로 복잡한 설정 없이 로컬에서 쉽게 실행할 수 있다. 로컬 배포에 용이하게 설계되어 간편한 실행을 지원한다.

**4. [LM Studio](https://lmstudio.ai/)**
   
LM Studio ggml 포맷을 지원하는 Llama, MPT, StarCoder 모델 어떤 것이든 호환이 되고, 호환되는 모델 파일을 검색/다운로드가 가능하고 여러 개의 로컬 LLM을 동시에 로딩해 사용할 수 있다. 로컬 호스트에서 OpenAI와 유사한 HTTP 서버를 구동할 수 있다. 

**5. [TextGenWebUI](https://github.com/oobabooga/text-generation-webui)**

TextGenWebUI는 Gradio 기반 웹 인터페이스로 다양한 텍스트 생성 모델과 파라미터를 쉽게 선택하여 원하는 텍스트를 만들 수 있다. Conda 환경 구성 -> 소스코드 다운로드 -> 설치 및 실행 -> web ui실행-> 모델 다운로드 순의 진행을 통해 사용 가능하다. 


#### 3-2-5. AI 워크플로우 및 통합 도구

AI 모델을 기존의 시스템이나 워크플로우에 쉽게 통합할 수 있게 해주는 도구이며 해당 유형의 서비스들은 AI 기술의 접근성을 높이고 활용도를 증가시킨다.

**1. [Flowise](https://flowiseai.com/)**   
  AI 워크플로우를 드래그 앤 드롭 방식으로 설계할 수 있는 시각적 인터페이스를 제공하는 Flowise를 통해 개발자는 복잡한 워크플로우나 모델 간의 데이터 흐름을 쉽게 관리하고 설계할 수 있다.  
  협업을 강조하는 플랫폼인 Continue와 Flowise를 연결하면 팀원들이 각 워크플로우의 시각적인 구성을 손쉽게 이해하고 수정할 수 있다.


**2. [Kindo]()**   
```
"models": [
    {
      "title": "Claude 3.5 Sonnet", // 모델 이름
      "provider": "kindo",          // 제공자
      "model": "claude-3-5-sonnet-20240620", // 사용하려는 모델
      "apiKey": "<KINDO_API_KEY>"   // Kindo에서 발급받은 API 키
      }
   ]
```

#### 3-2-6. 특화된 AI 서비스

특정 분야나 기술에 특화된 AI 서비스. 멀티모달 AI, 고성능 추론, 하드웨어 최적화 등 특정 니즈를 충족시키는 솔루션을 제공한다.


**1. [Gemini]()**   
멀티모달 모델로서 가장 성공적인 모델

**2. [Groq]()**    
자체 Processor를 통해 LLM을 더 빠르고 효율적으로 사용(추론)할 수 있음

**3. [IPES LLM]()**   
Intel CPU/GPU에서 더 효율적으로 추론과 학습을 할 수 있도록 하는 Pytorch 기반 라이브러리

**4. [Replicate]()**   
LLM의 허브같은 곳, 다양한 사용자들이 만들거나 fine tuning한 모델(혹은 자신의 모델)을 올려서 사용할 수 있는 곳

### 3-3. Free-Trial

Continue는 아래 Chat Model에 대해 최대 50회 사용 가능한 **Free-Trial** 을 제공한다.

- Claude 3 Sonnet
- GPT-4o
- Llama3 70b
- Codestral

```json
"models": [
    {
      "title": "Claude 3 Sonnet (Free Trial)",
      "provider": "free-trial",
      "model": "claude-3-sonnet-20240229"
    },
  ],
```

## 4. LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

**LLM 이란**

"대규모 언어 모델"로, 굉장히 많은 데이터를 학습한 AI 모델입니다. 이를 통해 사람처럼 자연스럽게 대화하거나 다양한 글을 작성하는 능력을 가지고 있고 대표적인 LLM은 ChatGPT가 있다.

**LLM Completion Options 란**

언어 모델이 텍스트를 생성하는 방식을 조정하는 설정들로, 출력되는 텍스트의 **길이, 다양성, 일관성** 등에 영향을 미친다. 단, 각 모델들이 지원하는 Option들도 약간씩 상이하며 동일한 값을 주더라도 모델마다 응답 변화에 편차가 있을 수 있다.

### 4-1. Continue에서 completionOption 설정하는 법


Continue에서 Completion Options를 수정하고 싶다면 `config.json`를 통해 수정해야 한다.

```json
"completionOptions": {
  "stream": "boolean",
  "teperature": "number",
  "topP": "number",
  "topK": "integer",
  "presencePenalty": "number",
  "frequencePenalty": "number",
  "mirostat": "number",
  "stop": "string[]",
  "maxTokens": "number",
  "numThreads": "integer",
  "keepAlive": "integer",
}
```

- `stream` : LLM 응답을 streaming으로 받을지 선택하는 옵션
- `temperature` : 모델이 생성하는 응답의 창의성이나 랜덤성을 조정
- `topP` : LLM에서 생성할 단어를 선택하는 과정에서 확률 분포 상위 P%의 단어들만 선택하여 응답을 생성하는 방식.
- `topK` : LLM에서 응답을 생성할 때 고려할 후보 단어들의 개수를 제한하는 옵션
- `presencePenalty` : 모델이 이미 언급한 단어를 다시 사용하는 것을 얼마나 억제할지 조절하는 옵션
- `frequencePenalty` : 단어의 빈도를 억제하거나 허용할 수 있으며, 모델이 같은 단어나 문구를 반복적으로 사용하지 않도록 제어하는 옵션
- `mirostat` : LLM에서 실시간으로 응답의 일관성과 품질을 지속적으로 조정하기 위한 동적 샘플링 알고리즘
- `stop` : 모델이 텍스트를 생성하는 도중 특정 토큰이나 문자열이 등장하면 응답 생성을 중단하는 옵션
- `maxTokens` : 모델이 하나의 프롬프트에 대해 응답할 때 생성할 텍스트의 길이를 제한
- `numThreads` : 생성 과정에서 사용되는 스레드의 수를 조절하는 옵션
- `keepAlive` : 요청이 없는 경우 모델을 메모리에서 언로드하기까지의 시간. (기본 값: `60 * 30 = 30분`)


#### 4-1-1. config.json > completionOption

전역적으로 설정하는 방법. 여기서 설정한 `completionOption` 값들은 모델에 상관없이 Continue에서 모든 작업에 동일하게 적용된다.

```json
{
  "completionOptions": {
    "temperature": 0.7,
    "topP": 0.9,
    "maxTokens": 150
  }
}
```

#### 4-1-2. config.json > models > completionOptions

모든 모델에 대한 기본값이 아니라 특정 모델에 대한 설정을 별도로 정의하고 싶을 때 사용한다.

예를 들면 `Msty`와 `gpt-4o-mini`에 각각 다른 `completionOptions` 설정을 부여할 수도 있다.

```json
{
  "models": [
    {
      "title": "Msty",
      "provider": "msty",
      "model": "deepseek-coder:6.7b",
      "completionOptions": {
        "temperature": 0.9,
        "topP": 0.7,
        "maxTokens": 100
      }
    },
    {
      "title": "GPT-4o Mini",
      "provider": "openai",
      "model": "gpt-4o-mini",
      "completionOptions": {
        "temperature": 0.6,
        "topP": 0.8,
        "maxTokens": 200
      }
    }
  ]
}
```

### 4-2. [Context Provider](https://docs.continue.dev/customize/context-providers) 커스텀하기

**Context Provider 란**

LLM에 특정한 콘텐츠를 제공하는 기능으로, `@`를 입력하면 LLM에 context로 제공할 수 있는 콘텐츠 드롭다운-LLM에게 제공되는 추가 정보(파일 내용, 프로젝트 코드, 깃 변경 사항, 깃 이슈, 터미널 출력, 웹 페이지 내용, 문서 등)-을 볼 수 있다.


Continue는 기본적으로 아래와 같은 built-in context provider를 제공하며, 이 내용은 config.json이 아닌 config.ts에 작성한다.

```json
  "contextProviders": [
    {
      "name": "code",
      "params": {}
    },
    {
      "name": "docs",
      "params": {}
    },
    {
      "name": "diff",
      "params": {}
    },
    { "name": "open", "params": { "onlyPinned": true } },
    {
      "name": "issue",
      "params": {
        "repos": [
          {
            "owner": "continuedev",
            "repo": "continue"
          }
        ],
        "githubToken": "ghp_xxx"
      }
    }
    ...
  ]
```

**Built-in Context Providers :**

- `@file`: 현재 워크스페이스의 파일을 context로 제공.
- `@code`: 프로젝트 내 특정 함수나 클래스를 context로 제공.
- `@Git Diff`: 현재 브랜치의 변경 사항을 context로 제공.
- `@terminal`: IDE의 터미널 내용을 context로 제공.
- `@open`: 현재 열려 있는 파일의 내용들을 context로 제공.
- `@folder`: 현재 워크스페이스의 폴더를 context로 제공. `@codebase` 와 동일한 검색 메커니즘을 사용하지만 단일 폴더에서만 검색할 수 있다.
- `@codebase`: 워크스페이스 전체에서 가장 관련성 높은 콘텐츠를 자동으로 가져올 수 있도록 codebase 를 색인화
- `@url`: 특정 URL의 내용을 markdown 형식으로 context로 제공.
- `@issue`: GitHub issue의 대화를 context로 제공 (개인 접근 토큰 필요).
- `@docs`: Continue에서 문서와 상호 작용할 수 있게 해줌. 정적 사이트나 GitHub 페이지를 색인화하여 쉽게 접근 가능.


#### [Custom Context Provider](https://docs.continue.dev/customize/tutorials/build-your-own-context-provider)

모든 context provider는 플러그인으로, 기본으로 제공하는 플러그인 외에도 필요한 소스를 제공하지 않는 경우 새로운 context provider를 요청 혹은 개발할 수 있고, REST API를 통해 외부 데이터베이스에서 정보를 검색하고 그 결과를 받아 자신만의 `CustomContextProvider`를 구현할 수 있다.

`context provider`의 3가지 종류(`ContextProviderType`) :

1. **normal**: 기본 설정. 별도의 선택(submenu) 및 쿼리 없이 사용.
2. **query**: 유저가 텍스트 박스로 입력하여 context 항목 생성. `"type": "query"`로 설정.
3. **submenu**: 유저가 선택할 수 있는 항목을 제공. `"type": "submenu"`로 설정해야 하며, `loadSubmenuItems`와 `getContextItems` 모두 구현해야 함.

```typescript
// ~/.continue/config.ts
interface CustomContextProvider {
  title: string;
  displayTitle?: string;
  description?: string;
  renderInlineAs?: string;
  type?: ContextProviderType;
  getContextItems(
    query: string,
    extras: ContextProviderExtras
  ): Promise<ContextItem[]>;
  loadSubmenuItems?: (
    args: LoadSubmenuItemsArgs
  ) => Promise<ContextSubmenuItem[]>;
}

const RagContextProvider: CustomContextProvider = {
  title: "rag",
  displayTitle: "RAG",
  description:
    "Retrieve snippets from our vector database of internal documents",

  getContextItems: async (
    query: string,
    extras: ContextProviderExtras
  ): Promise<ContextItem[]> => {
    const response = await fetch("https://internal_rag_server.com/retrieve", {
      method: "POST",
      body: JSON.stringify({ query }),
    });

    const results = await response.json();

    return results.map((result) => ({
      name: result.title,
      description: result.title,
      content: result.contents,
    }));
  },
};

export function modifyConfig(config: Config): Config {
  if (!config.contextProviders) {
    config.contextProviders = [];
  }
  config.contextProviders.push(RagContextProvider);
  return config;
}
```


### 4-3. Custom slash commands

#### 4-3-1. [.prompt 파일 생성하기](https://docs.continue.dev/customize/deep-dives/prompt-files)

- 워크스페이스 최상단에 `.prompts/` 폴더를 직접 생성하거나, chat box 밑의 Build a custom prompt를 누르면 워크스페이스 최상단에 `.prompts`라는 폴더가 생성됩니다.
- `.prompts` 폴더에서 생성한 .prompt 파일의 이름은 프롬프트를 생성하는 데 사용할 슬래시 명령어의 이름이 됩니다. ( e.g., `test.prompt` ⇒ `/test` )
- 파일에 프롬프트 내용을 작성하면 chat 화면에서 슬래시(/)+ 프롬프트파일명 + ENTER를 통해 프롬프트에서 지시한 내용을 따르게 됩니다.

```text
temperature: 0.5
maxTokens: 4096
---
<system>
You will be acting as a senior software engineer helping a colleague document their code.
</system>
You will follow the guidelines for writing great code comments:
{{{ url "https://stackoverflow.blog/2021/12/23/best-practices-for-writing-code-comments/" }}}
---
Using this information, write a comment for the following code:
{{{ input }}}
```

- **서문** : `---` 구분 기호 위에서 YAML 구문을 사용해서 모델 매개변수를 지정할 수 있게 합니다. 필요하지 않다면 `---` 구분 기호까지 생략합니다.
- **System 태그** : 시스템 메세지를 통해 시스템에게 역할을 부여해주고, 지시, 요구사항을 알려줍니다.
- **Context Provider**: `config.json`에 추가한 모든 컨텍스트 공급자는 컨텍스트 공급자의 이름을 사용하여 참조할 수 있습니다. 입력을 받는 컨텍스트 공급자도 지원됩니다.
- **내장 변수** : 현재 사용 가능한 기본 제공 변수는 다음과 같습니다. `{{{ input }}}`, `{{{ currentFile }}}`, `{{{ ./path/to/file.js }}}`

</br>

#### 4-3-2. 자연어 프롬프트 (customCommands 속성, config.json)

`config.json` 파일에 `customCommands` 속성을 추가하는 것으로, 자연어로 작성된 명령어를 정의하는 custom slash commands를 만들 수 있다.

```json
customCommands=[{
  "name": "check",
  "description": "Check for mistakes in my code",
  "prompt": "{{{ input }}}\n\nPlease read the highlighted code and check for any mistakes. You should look for the following, and be extremely vigilant:\n- Syntax errors\n- Logic errors\n- Security vulnerabilities\n- Performance issues\n- Anything else that looks wrong\n\nOnce you find an error, please explain it as clearly as possible, but without using extra words. For example, instead of saying 'I think there is a syntax error on line 5', you should say 'Syntax error on line 5'. Give your answer as one bullet point per mistake found."
}]
```

- `name` : 슬래시 명령을 호출하는 데 입력할 이름
- `description` : 드롭다운 메뉴에 표시되는 설명
- `prompt` : Handlebars 구문을 사용한 템플릿 작성을 지원
- `input` : 슬래시 명령으로 입력한 추가 입력. 예를 들어, 를 입력하면 /test only write one test. input여기 only write one test에는 강조 표시된 코드 블록도 포함됩니다.
- `file name`: 절대 경로나 현재 작업 디렉토리를 기준으로 한 상대 경로를 제공하여 모든 파일을 참조할 수 있습니다.

</br>

#### 4-3-3. 함수를 작성하는 프롬프트 (slashCommands 속성, config.ts)

`customCommands`로 사용자 지정 명령을 작성하는 것보다 한 단계 더 나아가려면 응답을 반환하는 사용자 지정 함수를 작성할 수 있습니다.

이를 위해서는 `config.json` 대신 `config.ts`를 사용해야 하는데, 이곳에서 `slashCommands` 배열에 새로운 `slashCommand` 객체를 추가합니다.

```typescript
export function modifyConfig(config: Config): Config {
  config.slashCommands?.push({
    name: "commit",
    description: "Write a commit message",
    run: async function* (sdk) {
      const diff = await sdk.ide.getDiff();
      for await (const message of sdk.llm.streamComplete(
        `${diff}\n\nWrite a commit message for the above changes. Use no more than 20 tokens to give a brief description in the imperative mood (e.g. 'Add feature' not 'Added feature'):`,
        {
          maxTokens: 20,
        }
      )) {
        yield message;
      }
    },
  });
  return config;
}
```

### 4-4. 효과적인 프롬프트 엔지니어링

#### 4-4-1. LLM의 응답의 품질을 더욱 향상시키기

사용자는 `프롬프트 디자인의 다양한 전략과 기법`을 통해 효과적으로 질문함으로써, LLM의 성능을 최적화하여 더 나은 응답 결과를 도출할 수 있습니다.

다음은 사용자가 시도해볼 수 있는 `프롬프트 디자인의 다양한 전략과 기법`입니다.

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
- **보상 제시하기**
  - 질문에 응답할 때 동기를 부여하기 위해 보상을 제안합니다.
    - `"이 문제를 해결하면 다음 단계로 넘어갈 수 있어."`
- **처벌 언급하기**
  - 응답이 없거나 부정확할 경우의 결과를 언급하여 정확한 응답을 유도합니다.
    - `"답변이 틀리면 시간이 낭비될 거야."`
- **자연스러운 대화 유도하기**
  - 인간적인 대화 스타일을 유도하여 보다 자연스러운 답변을 요청합니다.
    - `"친근하게 이야기하듯 설명해 줘."`
- **정보 충분히 요구하기**
  - 질문이 불완전할 경우 더 많은 정보를 요청하여 정확한 답변을 얻습니다.
    - `"더 많은 세부사항을 제공해 줄 수 있어?"`
- **테스트 포함 요청하기**
  - 생성된 답변을 테스트할 수 있는 형식으로 제공받습니다.
    - `"이 코드를 실행 가능한 상태로 제공해 줘."`
- **구분 기호 사용하기**
  - 특정 단어를 강조하거나 구조화된 답변을 요청할 때 구분 기호를 사용합니다.
    - `"각 항목을 '•' 기호로 구분해서 나열해 줘."`
- **단어 반복 사용하기**
  - 특정 단어를 강조하거나 주요 개념을 반복하여 설명하도록 요청합니다.
    - `"이 개념을 여러 번 반복해서 강조해 줘."`
- **출력문 포함하기**
  - 답변이 특정 형식으로 출력되도록 지시합니다.
    - `"이 코드를 출력 형식으로 작성해 줘."`
- **자세한 내용 요청하기**
  - 더 구체적인 정보를 포함하여 글을 작성하도록 요청합니다.
    - `"좀 더 자세하게 설명해 줘."`
- **수정 요청하기**
  - 이미 생성된 내용을 수정하여 더 나은 결과를 요구합니다.
    - `"이 내용을 더 간결하게 다듬어 줘."`
- **코드 생성 요청하기**
  - 여러 파일에 걸친 코드를 작성하거나 특정 구조로 제공받습니다.
    - `"이 코드의 각 함수는 별도의 파일로 분리해 줘."`
- **특정 텍스트로 시작하기**
  - 주어진 텍스트나 문구를 바탕으로 답변을 요청합니다.
    - `"이 문장을 바탕으로 추가 설명을 작성해 줘."`
- **요구 사항 명시하기**
  - 텍스트나 코드 생성에 필요한 특정 요구 사항을 명확히 합니다.
    - `"이 요구 사항에 맞춰 텍스트를 작성해 줘."`
- **제공된 예시 기반 텍스트 생성**
  - 제공된 예시와 유사한 스타일이나 형식으로 텍스트를 생성하도록 요청합니다.
    - `"이 예시와 같은 형식으로 텍스트를 작성해 줘."`

#### 4-4-2. Continue와 함께 개발에 활용하는 법

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

> 생성형 AI를 사용하면서 느낀 점은 대체로 여러 번 질답을 거듭할수록 답변의 질이 떨어진다는 것이다. 이와 같이 초기 질문 지시사항을 어떻게 주느냐에 따라 시간과 비용이 크게 차이난다. 따라서 내가 모르는 것이 무엇이고, 어떻게 잘 도움을 받을 수 있을지에 대한 '메타 인지'가 필요하다.


**참고 자료**

- [ChatGPT에게서 좋은 대답을 이끌어 내는 방법 7가지](https://tech.kakaobank.com/posts/2312-drawing-out-good-responses-from-ai/)
- [좋은 질문을 하는 방법, 구조화 방법](https://www.gotai.co.kr/%EC%B1%97%EC%A7%80%ED%94%BC%ED%8B%B0-2/)
- [Principled Instructions Are All You Need for Questioning](https://arxiv.org/abs/2312.16171)
- [ATLAS: An LLM Inquiry Principle Benchmark](https://github.com/VILA-Lab/ATLAS)

### Chat, Autocomplete
#### RAG, RAG in continue

### Edit, Actions

