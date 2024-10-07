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
    - [Continue에서 사용하는 Model 유형/연동 유형](#continue에서-사용하는-model-유형연동-유형)
    - [Autocomplete Model](#autocomplete-model)
      - [추천 모델](#추천-모델)
    - [Chat model](#chat-model)
      - [추천 모델](#추천-모델-1)
    - [Embeddings model](#embeddings-model)
      - [추천 모델](#추천-모델-2)
    - [Reranking model](#reranking-model)
      - [추천 모델](#추천-모델-3)
  - [Continue 모델 연동 유형](#continue-모델-연동-유형)
    - [AI 모델 제공 및 개발 플랫폼](#ai-모델-제공-및-개발-플랫폼)
    - [클라우드 AI 서비스](#클라우드-ai-서비스)
      - [클라우드 AI 사용의 장단점](#클라우드-ai-사용의-장단점)
    - [AI 모델 배포 및 서버리스 플랫폼](#ai-모델-배포-및-서버리스-플랫폼)
      - [Continue와의 연동 방법](#continue와의-연동-방법)
    - [로컬 AI 실행 도구](#로컬-ai-실행-도구)
      - [1. Ollama](#1-ollama)
      - [2. LlamaCpp](#2-llamacpp)
      - [3. Llamafile](#3-llamafile)
      - [4. LM Studio](#4-lm-studio)
      - [5. TextGenWebUI](#5-textgenwebui)
    - [AI 워크플로우 및 통합 도구](#ai-워크플로우-및-통합-도구)
      - [1. Flowise](#1-flowise)
      - [2. Kindo](#2-kindo)
    - [특화된 AI 서비스](#특화된-ai-서비스)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법)
    - [Free-Trial](#free-trial)
    - [LLM completion options \& continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)](#llm-completion-options--continue에서-설정하기-챗-잘사용하기---효과적인-프롬프팅system-user)
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
  

#### 1-1. Amazon CodeWhisperer
AWS 환경에서의 개발을 최적화한다는 특징을 가지고 있다.

  `주요 특징` : 자동 완성, 다양한 프로그래밍 언어 지원, 주석 기반 코드 생성, AWS 서비스와의 통합


#### 1-2. Codex
현재 Github Copilot, TabNine등과 같은 AI coding assistant도 Third-party extensions로서 Codex를 사용(leverage)하고 있다.

 `주요 특징` : Coding assistant에 특화된 모델을 사용, 12개 이상의 언어, 자연어 처리

#### 1-3. Cursor

Cursor는 기존 플러그인 방식이 아닌 VS Code를 기반으로 만들어진 편집기이다.

 `주요 특징` : 자동 완성, 코드 생성, 편집 및 리팩토링, Chat, 실시간 오류 감지 및 수정, 멀티 파일 분석

#### 1-4. Tabnine

Tabnine은 사용자가 입력하는 코드를 공개하지 않고 정해진 범위 안에서 소프트웨어 개발을 쉽고 빠르게 할 수 있다.

 `주요 특징` :
|제목|주요기능|가격|
|---|---|---|
|PRO|*최고의 AI모델 적용, AI채팅 에이전트, 보안취약점 필터링, 개인정보보호, 영업 시간 지원*|월 $12|
|Enterprise|*SaaS 또는 On-premise에서 구축 가능, 개인화 AI 채팅 에이전트, Confluence 통합, 영업시간 지원 및 관련 교육*|월 $39|
|Basic|*무료, AI채팅(속도 제한)*|월 $ 0|


#### 1-5. Codeium
전반적으로 Github Copilot와 유사한 기능들을 제공하면서 무료 티어로 사용할 수 있다.

 `주요 특징` : 자동 완성, 자연어로 Command 작성, Chat, 우클릭으로 옵션 접근 가능

#### 1-6. GitHub Copilot
Github 과 밀접한 기능을 제공한다.

 `주요 특징` : 자동 완성, Chat, Pull request 요약


#### 1-7. replit GhostWriter
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

### Continue에서 사용하는 Model 유형/연동 유형

- Autiocomplete Model
- Chat Model
- Embedding Model
- Reranking Model

### Autocomplete Model

중간 채우기(FIM) 기법으로 훈련된 특수한 언어 모델입니다.  모델은 코드 파일의 시작과 끝 부분이 주어졌을 때 중간에 들어갈 내용을 예측하도록 설계되었습니다. 이러한 특화된 작업 덕분에 상대적으로 작은 규모(3B 매개변수)의 모델로도 우수한 성능을 발휘할 수 있습니다. 반면, 일반적인 대화형 모델은 규모가 더 크더라도 이 특정 작업에서는 성능이 떨어질 수 있습니다

Continue에서 이러한 자동 완성 모델은 주로 코드 작성 시 실시간으로 인라인 제안을 제공하는 데 활용됩니다.

#### 추천 모델

Continue에서는 자동 완성 모델로 Mistral의 [Codestral](https://docs.continue.dev/customize/model-providers/mistral) 모델을 추천하며, 로컬 모델로는 [Ollama Provider](https://docs.continue.dev/customize/model-providers/ollama)와 함께 Starcoder2-3B 모델을 사용하는 것을 권장하고 있습니다.

### Chat model

채팅 모델(Chat model)은 대화 형식으로 응답하도록 학습된 LLM입니다. 이 모델은 일반적인 질문에 답변하고 복잡한 코드를 생성할 수 있어야 하므로, 최고 성능의 채팅 모델은 보통 405B 이상의 매개변수를 가진 대형 모델입니다. Continue에서는 이러한 채팅 모델을 [Chat](https://docs.continue.dev/chat/how-to-use-it), [Edit](https://docs.continue.dev/edit/how-to-use-it), [Action](https://docs.continue.dev/actions/how-to-use-it) 기능에 사용합니다.

#### 추천 모델

[Claude 3.5 Sonnet](https://docs.continue.dev/customize/model-providers/anthropic)을 가장 추천하며, 다른 옵션으로는 [GPT-4o](https://docs.continue.dev/customize/model-providers/openai), [Gemini 1.5 Pro](https://docs.continue.dev/customize/model-providers/gemini), [Llama3.1 405B](https://docs.continue.dev/customize/tutorials/llama3.1)를 권장합니다.

### Embeddings model

임베딩 모델(Embeddings model)은 텍스트를 벡터로 변환하도록 훈련된 모델입니다. 생성된 벡터는 나중에 다른 벡터들과 빠르게 비교하여 텍스트 간의 유사성을 판단하는 데 사용됩니다. 임베딩 모델은 일반적으로 LLM보다 훨씬 작은 모델이며, 따라서 비교적으로 매우 빠르고 저렴합니다.

Continue에서는 인덱싱 과정 중에 임베딩을 생성하고, 이를 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 활용하여 코드베이스 전체에 대한 유사성 검색을 수행합니다. 이를 통해 Continue는 워크스페이스에서 가장 관련성 있는 컨텍스트를 자동으로 가져올 수 있습니다.

#### 추천 모델

어떤 모델이든 쓸 수 있다면 voyage-code-2를 추천하며, 로컬 환경에서 임베딩을 생성하고 싶다면 Ollama와 함께 nomic-embed-text를 사용하는 것을 권장합니다.

이외에 Transformers.js를 사용해 로컬 임베딩을 생성할 수 있으며, 자체 임베딩 엔드포인트를 구축하고 싶을 경우 Hugging Face Text Embeddings Inference를 사용할 수 있습니다.

OpenAI, Cohere, Gemini 공급사에서도 임베딩 모델을 제공합니다.

### Reranking model

리랭킹 모델(Reranking model)은 두 개의 텍스트(주로 사용자의 질문과 문서)를 입력받아 0에서 1 사이의 관련성 점수를 반환하도록 훈련된 모델입니다. 이 점수는 해당 문서가 질문에 답변하는 데 얼마나 유용할지를 측정합니다. 리랭킹 모델은 일반적으로 LLM보다 훨씬 작으며, 비교적 매우 빠르고 저렴합니다.

Continue 플랫폼에서는 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 리랭킹 모델을 사용합니다. 이는 벡터 검색 후 가장 관련성 높은 코드 스니펫을 선택하는 데 필요합니다.

#### 추천 모델

어떤 모델이든 사용할 수 있다면, Voyage AI의 rerank-1을 추천합니다. 혹은 [Cohere](https://docs.cohere.com/docs/rerank-2)에서 제공하는 리랭킹 모델을 사용할 수도 있습니다.

만약 LLM만 사용할 수 있는 상태라면 LLM 모델을 리랭킹 모델로 사용할 수는 있습니다. 하지만 훨씬 비싸고 정확도가 떨어지므로 꼭 필요한 경우가 아니면 권장하지 않습니다. 또한 너무 많은 병렬 요청을 수행해야 하기 때문에 Ollama와 같은 로컬 모델에서는 사용할 수 없습니다. 

Hugging Face Text Embeddings Inference로 나만의 리랭커 엔드포인트를 만들 수 있습니다.


## Continue 모델 연동 유형

Continue에서 사용자는 Provider를 설정하여 모델과 연동할 플랫폼을 선택하고, 각 Provider가 제공하는 AI 모델을 선택할 수 있다.

서비스의 주요 기능, 실행 환경, 특화된 기능을 기준으로 다음과 같이 여섯 가지 유형으로 분류했다.
- AI 모델 제공 및 개발 플랫폼
- 클라우드 AI 서비스
- AI 모델 배포 및 관리 도구
- 로컬 AI 실행 도구
- AI 워크플로우 및 통합 도구
- 특화된 AI 서비스

### AI 모델 제공 및 개발 플랫폼

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


### 클라우드 AI 서비스

대규모 클라우드 제공업체가 제공하는 AI 및 머신러닝 서비스이고, 모델 훈련/배포/관리를 위한 종합적인 플랫폼을 제공해 주는 서비스이다.

다음은 대표적인 플랫폼 두 개이다. 

1. **[Azure OpenAI](https://azure.microsoft.com/ko-kr)**  
  
    - Azure는 Microsoft사의 Public Cloud 서비스를 제공하는 CSP사이다. 여러 AI 모델 공급사로부터 모델을 공급받아 서비스를 하는 형태이다.  
    - Continue에서는 채팅 모델로 `GPT-4o` 모델을 추천하며 자동완성 모델로 `Codestral`, 임베딩에는 `text-embedding-3-large` 모델 사용을 추천한다. re-Ranking 모델은 제공하지 않는다.
  
2. **[Amazon Bedrock](https://aws.amazon.com/ko/bedrock/?gclid=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB&trk=24a8f13a-f5db-4127-bcb7-8b2876aa4265&sc_channel=ps&ef_id=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB:G:s&s_kwcid=AL!4422!3!692062155749!e!!g!!amazon%20bedrock!21058131112!157173586057)** 
  
   - Amazon Bedrock은 AWS 환경에서 LLM을 개발하고 배포할 수 있는 플랫폼이다.   
   - Continue에서는 채팅 모델로 `Claude 3.5 Sonnet` 모델을 추천하며 임베딩에는 `amazon.titan-embed-text-v2:0` 모델 사용을 추천한다. 자동완성, re-Ranking 모델은 제공하지 않는다.
  
클라우드 AI 제공업체의 모델을 연동하는 방법은 주로 **API 연결**을 통해 이루어진다.

#### 클라우드 AI 사용의 장단점
**장점**

    - 클라우드 AI Provider 를 사용할 경우, 물리적인 인프라를 구축할 필요없이 사용한만큼만 지불하는 구조(Pay-as-you-go)를 통해 초기 투자 비용을 크게 절감할 수 있다.

**단점**

    - API를 이용해서 데이터를 전송하기 때문에 데이터가 제3자와 공유될 수 있는 위험성이 존재한다. 다만, OpenAI 엔터프라이즈 고객의 데이터를 사용하여 서비스 개선이나 모델 훈련에 사용하지 않겠다고 명시하는 등 보호 조치가 존재한다.
    - 장기적으로 볼 경우에는 사용량이 증가하면 지속적으로 발생하는 비용이 더 들 수도 있다. 


### AI 모델 배포 및 서버리스 플랫폼

- `Cloudflare Workers AI` : Cloudflare의 서버리스 플랫폼에서 머신러닝 모델을 실행할 수 있게 해주는 서비스. 엄선한 인기 오픈 소스 모델 세트를 제공하며, 텍스트 생성/자동 음성 인식/번역/텍스트 분류/이미지 분류/임베딩 모델을 제공합니다. Cloudflare API를 통해 Continue와 연동할 수 있다.

- `HuggingFace Inference Endpoints` : 커스텀 모델, 혹은 HuggingFace 허브에 있는 모든 Transformer, Sentence-Transformer, Diffusers 모델들을 쉽고 안전하게 배포할 수 있는 서비스. 배포할 클라우드를 선택할 수 있으며 배포 후 생성된 엔드포인트는 API로 접근하여 Continue와 연동할 수 있다.

- `DeepInfra` : 낮은 가격으로 사용할 수 있는 서버리스 AI 모델 배포 서비스. 다양한 유명 모델 및 오픈소스 모델을 제공하여 인기 모델의 경우 사전 배포되어 있어 직접 배포하지 않고도 API를 통해 연동할 수 있다.

- `Together` : 다양한 AI 모델을 쉽게 사용/조정/배포할 수 있는 플랫폼을 제공하는 서비스. 많은 인기 모델들을 서버리스 엔드포인트를 통해 호스팅하고 있어 별도의 배포 작업 없이 쉽게 활용할 수 있으며 전용 GPU 인프라를 사용하여 자체 모델 혹은 오픈소스 모델을 직접 호스팅하는 기능도 제공한다.

- `vLLM` : LLM 추론 및 서빙을 위한 오픈소스 라이브러리. vLLM은 OpenAI의 Completions 및 Chat API와 호환되는 HTTP 서버를 제공하며 이를 통해 Continue와 연동할 수 있다.

#### Continue와의 연동 방법

vLLM을 제외하면 API를 제공하는 서비스들이기 때문에, 모두 비슷한 방식으로 연동합니다.

1. 플랫폼 대시보드 페이지에 들어가서 가입을 하고 API key를 발급받습니다.
2. continue의 config.json 파일에 API key와 사용할 모델, provider 이름을 명시합니다. Provider에 따라 accountId 등 추가 정보를 입력해야 할 수 있습니다.

### 로컬 AI 실행 도구

개인 컴퓨터나 로컬 서버에서 AI 모델을 실행할 수 있게 해주는 소프트웨어.

#### 1. [Ollama](https://ollama.com/)
   
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
#### 2. [LlamaCpp](https://github.com/ggerganov/llama.cpp)
   
LlamaCpp는 Meta의 LLaMA 모델을 C++ 기반으로 GPU 없이도 로컬에서 실행할 수 있는 도구이다. 주로 CPU 성능을 극대화하여 고성능 LLM 추론을 지원하며, 저사양 환경에서도 효율적으로 LLM을 로컬에서 사용할 수 있다.

#### 3. [Llamafile](https://github.com/Mozilla-Ocho/llamafile)
   
Llamafile은 복잡한 서버 설정이 필요 없고 llama.cpp와 Cosmopolitan Libc의 결합을 통해 다양한 환경에서 실행 가능한 단일 빌드로 모든 기능을 패키징 하므로 복잡한 설정 없이 로컬에서 쉽게 실행할 수 있다. 로컬 배포에 용이하게 설계되어 간편한 실행을 지원합니다.

#### 4. [LM Studio](https://lmstudio.ai/)
   
LM Studio ggml 포맷을 지원하는 Llama, MPT, StarCoder 모델 어떤 것이든 호환이 가능합니다. 호환되는 모델 파일을 검색, 다운로드가 가능하고 여러개의 로컬 LLM을 동시에 로딩해 사용할 수 있습니다. 로컬 호스트에서 OpenAI와 유사한 HTTP 서버를 구동할 수 있습니다. 

#### 5. [TextGenWebUI](https://github.com/oobabooga/text-generation-webui)

TextGenWebUI는 Gradio 기반 웹 인터페이스로 다양한 텍스트 생성 모델과 파라미터를 쉽게 선택하여 원하는 텍스트를 만들 수 있다. Conda 환경 구성 -> 소스코드 다운로드 -> 설치 및 실행 -> web ui실행-> 모델 다운로드 순의 진행을 통해 사용 가능합니다. 


### AI 워크플로우 및 통합 도구

AI 모델을 기존의 시스템이나 워크플로우에 쉽게 통합할 수 있게 해주는 도구이며 해당 유형의 서비스들은 AI 기술의 접근성을 높이고 활용도를 증가시킨다.

#### 1. [Flowise](https://flowiseai.com/)

Flowise는 AI 워크플로우를 드래그 앤 드롭 방식으로 설계할 수 있는 시각적 인터페이스를 제공합니다.  
이를 통해 개발자는 복잡한 워크플로우나 모델 간의 데이터 흐름을 쉽게 관리하고 설계할 수 있습니다.  
Continue는 협업을 강조하는 플랫폼인데, Flowise와 연결하면 팀원들이 각 워크플로우의 시각적인 구성을 손쉽게 이해하고 수정할 수 있습니다.

<img width="1114" alt="스크린샷 2024-10-04 오후 9 26 47" src="https://github.com/user-attachments/assets/85c32e40-cfbb-4feb-a1ed-08a55beb8d34">

드래그 앤 드롭만으로, 에이전트 AI를 만들수 있는 툴 입니다.

1. https://github.com/FlowiseAI/Flowise 에서 Flowise를 clone 한다.
<img width="1329" alt="스크린샷 2024-10-04 오후 8 37 21" src="https://github.com/user-attachments/assets/83e5db82-d7a9-4fc9-830d-5732876bcbb7">

2. 클론 후, 해당 flowise README.md 에서 나온대로 따라해서 docker로 실행시키고 localhost:3000 으로 접속후, chatflow로 가서 나만의 chatflow를 설정할 수있다.
   
<img width="1087" alt="스크린샷 2024-10-04 오후 8 39 15" src="https://github.com/user-attachments/assets/704e5e05-768e-4f6e-ac8f-9270f08f5b41">

3. 우상단 </> 를 누르면, curl 의 url로 api를 이용 할 수있다.

   <img width="1390" alt="image" src="https://github.com/user-attachments/assets/08ba1c69-2c98-4e2a-b312-f7c6dbb09184">

4. 하단의 configure continue 를 누르고, config.json에
```
   "models": [
       {
         "provider": "flowise",
         "title": "Flowise",
         "model": "<MODEL>",
         "apiBase": "<API_BASE>"
       }
     ]
```
를 등록하면 연결이 된다.

<img width="975" alt="image" src="https://github.com/user-attachments/assets/bf8b3b15-d0da-4f5e-a1dd-e800da07c005">



#### 2. [Kindo]()

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

### 특화된 AI 서비스

특정 분야나 기술에 특화된 AI 서비스입니다. 이들은 멀티모달 AI, 고성능 추론, 하드웨어 최적화 등 특정 니즈를 충족시키는 솔루션을 제공합니다.

Gemini, Groq, IPEX-LLM, ReplicateLLM이 여기에 속합니다.

- **Gemini**: 멀티모달 모델로서 가장 성공적인 모델
- **Groq**: 자체 Processor를 통해 LLM을 더 빠르고 효율적으로 사용(추론)할 수 있음
- **IPEX LLM**: Intel CPU/GPU에서 더 효율적으로 추론과 학습을 할 수 있도록 하는 Pytorch 기반 라이브러리
- **Replicate**: LLM의 허브같은 곳, 다양한 사용자들이 만들거나 fine tuning한 모델(혹은 자신의 모델)을 올려서 사용할 수 있는 곳

#### 예시 Provider 연동 방법
**IPEX LLM** 예시
https://github.com/intel-analytics/ipex-llm/blob/main/docs/mddocs/Quickstart/ollama_quickstart.md 사이트에서 Ollama 모델을 IPEX 위에서 작동할 수 있도록 설정한 후 config.json 파일에 입력한다.
```json
{
  "models": [
    {
      "title": "IPEX-LLM",
      "provider": "ollama",
      "model": "AUTODETECT"
    }
  ]
}
```
**Replicate 예시**

https://replicate.com/collections/streaming-language-models 사이트에서 원하는 모델을 선택하여 API Key를 생성하고 이를 config.json에 입력함
```json
{
  "models": [
    {
      "title": "Replicate CodeLLama",
      "provider": "replicate",
      "model": "codellama-13b",
      "apiKey": "YOUR_API_KEY"
    }
  ]
}
```

### Free-Trial

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

### LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

### Chat, Autocomplete
#### RAG, RAG in continue

### Edit, Actions

