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

#### 개념

자동 완성 모델(Autocomplete model)은 중간 채우기(FIM) 기법으로 훈련된 특수한 언어 모델입니다. 이 모델은 코드 파일의 시작과 끝 부분이 주어졌을 때 중간에 들어갈 내용을 예측하도록 설계되었습니다. 이러한 특화된 작업 덕분에 상대적으로 작은 규모(3B 매개변수)의 모델로도 우수한 성능을 발휘할 수 있습니다. 반면, 일반적인 대화형 모델은 규모가 더 크더라도 이 특정 작업에서는 성능이 떨어질 수 있습니다.

Continue에서 이러한 자동 완성 모델은 주로 코드 작성 시 실시간으로 인라인 제안을 제공하는 데 활용됩니다.

#### 추천 모델

Continue에서는 자동 완성 모델로 Mistral의 [Codestral](https://docs.continue.dev/customize/model-providers/mistral) 모델을 추천하며, 로컬 모델로는 [Ollama Provider](https://docs.continue.dev/customize/model-providers/ollama)와 함께 Starcoder2-3B 모델을 사용하는 것을 권장하고 있습니다.

### Chat model

#### 개념

채팅 모델(Chat model)은 대화 형식으로 응답하도록 학습된 LLM입니다. 이 모델은 일반적인 질문에 답변하고 복잡한 코드를 생성할 수 있어야 하므로, 최고 성능의 채팅 모델은 보통 405B 이상의 매개변수를 가진 대형 모델입니다. Continue에서는 이러한 채팅 모델을 [Chat](https://docs.continue.dev/chat/how-to-use-it), [Edit](https://docs.continue.dev/edit/how-to-use-it), [Action](https://docs.continue.dev/actions/how-to-use-it) 기능에 사용합니다.

#### 추천 모델

[Claude 3.5 Sonnet](https://docs.continue.dev/customize/model-providers/anthropic)을 가장 추천하며, 다른 옵션으로는 [GPT-4o](https://docs.continue.dev/customize/model-providers/openai), [Gemini 1.5 Pro](https://docs.continue.dev/customize/model-providers/gemini), [Llama3.1 405B](https://docs.continue.dev/customize/tutorials/llama3.1)를 권장합니다.

### Embeddings model

#### 개념

임베딩 모델(Embeddings model)은 텍스트를 벡터로 변환하도록 훈련된 모델입니다. 생성된 벡터는 나중에 다른 벡터들과 빠르게 비교하여 텍스트 간의 유사성을 판단하는 데 사용됩니다. 임베딩 모델은 일반적으로 LLM보다 훨씬 작은 모델이며, 따라서 비교적으로 매우 빠르고 저렴합니다.

Continue에서는 인덱싱 과정 중에 임베딩을 생성하고, 이를 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 활용하여 코드베이스 전체에 대한 유사성 검색을 수행합니다. 이를 통해 Continue는 워크스페이스에서 가장 관련성 있는 컨텍스트를 자동으로 가져올 수 있습니다.

#### 추천 모델

어떤 모델이든 쓸 수 있다면 voyage-code-2를 추천하며, 로컬 환경에서 임베딩을 생성하고 싶다면 Ollama와 함께 nomic-embed-text를 사용하는 것을 권장합니다.

이외에 Transformers.js를 사용해 로컬 임베딩을 생성할 수 있으며, 자체 임베딩 엔드포인트를 구축하고 싶을 경우 Hugging Face Text Embeddings Inference를 사용할 수 있습니다.

OpenAI, Cohere, Gemini 공급사에서도 임베딩 모델을 제공합니다.

### Reranking model

#### 개념

리랭킹 모델(Reranking model)은 두 개의 텍스트(주로 사용자의 질문과 문서)를 입력받아 0에서 1 사이의 관련성 점수를 반환하도록 훈련된 모델입니다. 이 점수는 해당 문서가 질문에 답변하는 데 얼마나 유용할지를 측정합니다. 리랭킹 모델은 일반적으로 LLM보다 훨씬 작으며, 비교적 매우 빠르고 저렴합니다.

Continue 플랫폼에서는 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 리랭킹 모델을 사용합니다. 이는 벡터 검색 후 가장 관련성 높은 코드 스니펫을 선택하는 데 필요합니다.

#### 추천 모델

어떤 모델이든 사용할 수 있다면, Voyage AI의 rerank-1을 추천합니다. 혹은 [Cohere](https://docs.cohere.com/docs/rerank-2)에서 제공하는 리랭킹 모델을 사용할 수도 있습니다.

만약 LLM만 사용할 수 있는 상태라면 LLM 모델을 리랭킹 모델로 사용할 수는 있습니다. 하지만 훨씬 비싸고 정확도가 떨어지므로 꼭 필요한 경우가 아니면 권장하지 않습니다. 또한 Ollama와 같은 로컬 모델에서는 사용할 수 없습니다. 너무 많은 병렬 요청을 수행해야 하기 때문입니다.

Hugging Face Text Embeddings Inference로 나만의 리랭커 엔드포인트를 만들 수 있습니다.

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

### AI 모델 배포 및 서버리스 플랫폼

AI 모델을 효율적으로 배포하고 관리하기 위한 도구와 서비스입니다. 혹은 자체 모델 호스팅을 지원하여,

Cloudflare Workers AI, HuggingFace Inference Endpoints, DeepInfra, Together, vLLM이 여기에 속합니다.

- Cloudflare Workers AI : Cloudflare의 서버리스 플랫폼에서 머신러닝 모델을 실행할 수 있게 해주는 서비스입니다. 엄선한 인기 오픈 소스 모델 세트를 제공하며, 텍스트 생성/자동 음성 인식/번역/텍스트 분류/이미지 분류/임베딩 모델을 제공합니다. Cloudflare API를 통해 Continue와 연동할 수 있습니다.

- HuggingFace Inference Endpoints : 커스텀 모델, 혹은 HuggingFace 허브에 있는 모든 Transformer, Sentence-Transformer, Diffusers 모델들을 쉽고 안전하게 배포할 수 있는 서비스입니다. 배포할 클라우드를 선택할 수 있으며, 배포 후 생성된 엔드포인트는 API로 접근하여 Continue와 연동할 수 있습니다.

- DeepInfra : 낮은 가격으로 사용할 수 있는 서버리스 AI 모델 배포 서비스입니다. 다양한 유명 모델 및 오픈소스 모델을 제공하여, 인기 모델의 경우 사전 배포되어 있어 직접 배포하지 않고도 API를 통해 연동할 수 있습니다.

- Together : 다양한 AI 모델을 쉽게 사용, 조정, 배포할 수 있는 플랫폼을 제공하는 서비스입니다. 많은 인기 모델들을 서버리스 엔드포인트를 통해 호스팅하고 있어 별도의 배포 작업 없이 쉽게 활용할 수 있으며, 전용 GPU 인프라를 사용하여 자체 모델 혹은 오픈소스 모델을 직접 호스팅하는 기능도 제공합니다.

- vLLM : LLM 추론 및 서빙을 위한 오픈소스 라이브러리입니다. vLLM은 OpenAI의 Completions 및 Chat API와 호환되는 HTTP 서버를 제공하며, 이를 통해 Continue와 연동할 수 있습니다.

#### Continue와의 연동 방법

vLLM을 제외하면 API를 제공하는 서비스들이기 때문에, 모두 비슷한 방식으로 연동합니다.

1. 플랫폼 대시보드 페이지에 들어가서 가입을 하고 API key를 발급받습니다.
2. continue의 config.json 파일에 API key와 사용할 모델, provider 이름을 명시합니다. Provider에 따라 accountId 등 추가 정보를 입력해야 할 수 있습니다.

다음은 Cloudflare Workers AI에서 요구하는 config의 예시입니다.

```
{
  "models": [
    {
      "accountId": "YOUR CLOUDFLARE ACCOUNT ID",
      "apiKey": "YOUR CLOUDFLARE API KEY",
      "contextLength": 2400,
      "completionOptions": {
        "maxTokens": 500
      },
      "model": "@cf/meta/llama-3-8b-instruct", // This can be the name of any model supported by Workers AI
      "provider": "cloudflare",
      "title": "Llama 3 8B"
    },
    {
      "accountId": "YOUR CLOUDFLARE ACCOUNT ID",
      "apiKey": "YOUR CLOUDFLARE API KEY",
      "contextLength": 2400,
      "completionOptions": {
        "maxTokens": 500
      },
      "model": "@hf/thebloke/deepseek-coder-6.7b-instruct-awq",
      "provider": "cloudflare",
      "title": "DeepSeek Coder 6.7b Instruct"
    }
    ...
    "tabAutocompleteModel": {
      "accountId": "YOUR CLOUDFLARE ACCOUNT ID",
      "apiKey": "YOUR CLOUDFLARE API KEY",
      "model": "@hf/thebloke/deepseek-coder-6.7b-base-awq",
      "provider": "cloudflare",
      "title": "DeepSeek 7b"
    },
  ]
}
```

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
