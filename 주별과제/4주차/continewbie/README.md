# 💻 AI 코딩 어시스턴트 도구 조사 프로젝트

### Continue에서 사용하는 Model 유형, Model 연동 유형

## 📚 목차

1. [서론](#서론)

2. [Continue 모델 유형에 대한 조사](#continue-모델-유형에-대한-조사)

   - [Autocomplete model](#autocomplete-model)
   - [Chat model](#chat-model)
   - [Embeddings model](#embeddings-model)
   - [Reranking model](#reranking-model)

3. [Continue 모델 연동 유형에 대한 조사](#continue-모델-연동-유형에-대한-조사)

   - [AI 모델 제공 및 개발 플랫폼](#ai-모델-제공-및-개발-플랫폼)
   - [클라우드 AI 서비스](#클라우드-ai-서비스)
   - [AI 모델 배포 및 관리 도구](#ai-모델-배포-및-관리-도구)
   - [로컬 AI 실행 도구](#로컬-ai-실행-도구)
   - [AI 워크플로우 및 통합 도구](#ai-워크플로우-및-통합-도구)
   - [특화된 AI 서비스](#특화된-ai-서비스)

---

## 서론

오늘 발표에서는 Continue에서 사용하는 AI 모델의 유형과 이를 연동하는 방식에 대해 살펴보겠습니다.

## Continue 모델 유형에 대한 조사

Continue는 다양한 AI 작업을 수행하기 위해 여러 유형의 모델을 사용합니다. 각 모델 유형은 특정 기능을 담당하며, 이를 통해 개발자에게 종합적인 AI 지원을 제공합니다. Continue에서는 모델 유형을 크게 네 가지로 분류하고 있습니다.

### Autocomplete model

### Chat model

### Embeddings model

### Reranking model

## Continue 모델 연동 유형에 대한 조사

Continue에서 Model Provider는 AI 모델을 제공하는 서비스나 플랫폼을 의미합니다. 사용자는 Provider를 설정하여 모델과 연동할 플랫폼을 선택하고, 각 Provider가 제공하는 AI 모델을 선택할 수 있습니다.

현재 Continue에서는 free trial을 제외하고 총 28개의 Model Provider를 제공하고 있습니다. 저희 조는 Provider들을 서비스의 주요 기능, 실행 환경, 특화된 기능을 기준으로 다음 여섯 가지 유형으로 분류해 보았습니다.

### AI 모델 제공 및 개발 플랫폼

자체 AI 모델을 개발하고 API를 통해 제공하는 기업들입니다. 해당 유형의 Provider들은 자신들이 개발한 모델에 대한 API를 제공합니다.

Anthropic, OpenAI, Mistral, Cohere, DeepSeek가 여기에 속합니다.

#### 예시 Provider 연동 방법

### 클라우드 AI 서비스

대규모 클라우드 제공업체가 제공하는 AI 및 머신러닝 서비스입니다. 모델 훈련, 배포, 관리를 위한 종합적인 플랫폼을 제공해 주는 서비스들입니다.

Azure OpenAI, Amazon Bedrock, AWS SageMaker, IBM Watsonx, SambaNova Cloud가 여기에 속합니다.

#### 예시 Provider 연동 방법

### AI 모델 배포 및 관리 도구

AI 모델을 효율적으로 배포하고 관리하기 위한 도구와 서비스입니다. 모델의 성능 최적화와 확장성을 지원합니다

Cloudflare Workers AI, HuggingFace Inference Endpoints, DeepInfra, Together, vLLM이 여기에 속합니다.

#### 예시 Provider 연동 방법

### 로컬 AI 실행 도구

개인 컴퓨터나 로컬 서버에서 AI 모델을 실행할 수 있게 해주는 소프트웨어입니다. 데이터 프라이버시와 오프라인 사용을 중요시하는 사용자들에게 유용한 서비스들입니다.

Ollama, LlamaCpp, Llamafile, LM Studio, TextGenWebUI이 여기에 속합니다.

#### 예시 Provider 연동 방법

### AI 워크플로우 및 통합 도구

AI 모델을 기존 시스템이나 워크플로우에 쉽게 통합할 수 있게 해주는 도구들입니다. 해당 유형의 서비스들은 AI 기술의 접근성을 높이고 활용도를 증가시킵니다.

Flowise, Kindo, Msty, OpenRouter가 여기에 속합니다.

#### 예시 Provider 연동 방법

### 특화된 AI 서비스

특정 분야나 기술에 특화된 AI 서비스입니다. 이들은 멀티모달 AI, 고성능 추론, 하드웨어 최적화 등 특정 니즈를 충족시키는 솔루션을 제공합니다.

Gemini, Groq, IPEX-LLM, ReplicateLLM이 여기에 속합니다.

#### 예시 Provider 연동 방법
