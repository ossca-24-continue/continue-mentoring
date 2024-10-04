# 💻 AI 코딩 어시스턴트 도구 조사 프로젝트

### Continue에서 사용하는 Model 유형, Model 연동 유형

## 📚 목차

- [💻 AI 코딩 어시스턴트 도구 조사 프로젝트](#-ai-코딩-어시스턴트-도구-조사-프로젝트)
    - [Continue에서 사용하는 Model 유형, Model 연동 유형](#continue에서-사용하는-model-유형-model-연동-유형)
  - [📚 목차](#-목차)
  - [서론](#서론)
  - [Continue 모델 유형에 대한 조사](#continue-모델-유형에-대한-조사)
    - [Autocomplete model](#autocomplete-model)
    - [Chat model](#chat-model)
    - [Embeddings model](#embeddings-model)
    - [Reranking model](#reranking-model)
  - [Continue 모델 연동 유형에 대한 조사](#continue-모델-연동-유형에-대한-조사)
    - [AI 모델 제공 및 개발 플랫폼](#ai-모델-제공-및-개발-플랫폼)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법)
    - [클라우드 AI 서비스](#클라우드-ai-서비스)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법-1)
    - [AI 모델 배포 및 관리 도구](#ai-모델-배포-및-관리-도구)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법-2)
    - [로컬 AI 실행 도구](#로컬-ai-실행-도구)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법-3)
    - [AI 워크플로우 및 통합 도구](#ai-워크플로우-및-통합-도구)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법-4)
    - [특화된 AI 서비스](#특화된-ai-서비스)
      - [예시 Provider 연동 방법](#예시-provider-연동-방법-5)

---

## 서론

오늘 발표에서는 Continue에서 사용하는 AI 모델의 유형과 이를 연동하는 방식에 대해 살펴보겠습니다.

## Continue 모델 유형에 대한 조사

Continue는 다양한 AI 작업을 수행하기 위해 여러 유형의 모델을 사용합니다. 각 모델 유형은 특정 기능을 담당하며, 이를 통해 개발자에게 종합적인 AI 지원을 제공합니다. Continue에서는 모델 유형을 크게 네 가지로 분류하고 있습니다.

### Autocomplete model
Autocomplete 모델은 입력한 코드나 텍스트의 앞뒤 내용을 토대로, 중간에 들어갈 내용을 예측해주는 모델입니다. 이 모델은 코드를 빠르게 작성해야 할 때, 다음에 나올 코드를 자동으로 제안해줄 수 있습니다. 

#### 개념

자동 완성 모델(Autocomplete model)은 중간 채우기(FIM) 기법으로 훈련된 특수한 언어 모델입니다. 이 모델은 코드 파일의 시작과 끝 부분이 주어졌을 때 중간에 들어갈 내용을 예측하도록 설계되었습니다. 이러한 특화된 작업 덕분에 상대적으로 작은 규모(3B 매개변수)의 모델로도 우수한 성능을 발휘할 수 있습니다. 반면, 일반적인 대화형 모델은 규모가 더 크더라도 이 특정 작업에서는 성능이 떨어질 수 있습니다.

Continue에서 이러한 자동 완성 모델은 주로 코드 작성 시 실시간으로 인라인 제안을 제공하는 데 활용됩니다.

#### 예시

Google 검색창에서 "best restaurant in..."을 입력하면 "New York", "Los Angeles" 등의 문구를 자동으로 추천해주는 기능, 혹은 개발자 코드의 일부를 작성하면 코드 편집기가 함수 이름이나 변수명을 자동으로 추천하는 기능

#### 추천 모델

Continue에서는 자동 완성 모델로 Mistral의 [Codestral](https://docs.continue.dev/customize/model-providers/mistral) 모델을 추천하며, 로컬 모델로는 [Ollama Provider](https://docs.continue.dev/customize/model-providers/ollama)와 함께 Starcoder2-3B 모델을 사용하는 것을 권장하고 있습니다.

### Chat model
Chat 모델은 대화 형식에 응답하도록 훈련된 LLM 입니다.  사용자가 질문을 입력하면 자연스러운 대화 형식으로 답변을 제공합니다. 질문에 답하고 복잡한 코드를 짜야하기 때문에, 좋은 성능의 모델은 파라미터가 4천억개 이상 입니다. 

#### 개념

채팅 모델(Chat model)은 대화 형식으로 응답하도록 학습된 LLM입니다. 이 모델은 일반적인 질문에 답변하고 복잡한 코드를 생성할 수 있어야 하므로, 최고 성능의 채팅 모델은 보통 405B 이상의 매개변수를 가진 대형 모델입니다. Continue에서는 이러한 채팅 모델을 [Chat](https://docs.continue.dev/chat/how-to-use-it), [Edit](https://docs.continue.dev/edit/how-to-use-it), [Action](https://docs.continue.dev/actions/how-to-use-it) 기능에 사용합니다.

#### 예시

챗봇, AI비서

#### 추천 모델

[Claude 3.5 Sonnet](https://docs.continue.dev/customize/model-providers/anthropic)을 가장 추천하며, 다른 옵션으로는 [GPT-4o](https://docs.continue.dev/customize/model-providers/openai), [Gemini 1.5 Pro](https://docs.continue.dev/customize/model-providers/gemini), [Llama3.1 405B](https://docs.continue.dev/customize/tutorials/llama3.1)를 권장합니다.

### Embeddings model
Embeddings 모델은 텍스트를 벡터값으로 변환해  텍스트 간의 유사도를 비교할 수 있게 해주는 모델입니다. 예시로, 검색어와 문서 간의 유사도를 계산하거나 추천 시스템에서 유사성을 비교하는 데 주로 사용됩니다.

#### 개념

임베딩 모델(Embeddings model)은 텍스트를 벡터로 변환하도록 훈련된 모델입니다. 생성된 벡터는 나중에 다른 벡터들과 빠르게 비교하여 텍스트 간의 유사성을 판단하는 데 사용됩니다. 임베딩 모델은 일반적으로 LLM보다 훨씬 작은 모델이며, 따라서 비교적으로 매우 빠르고 저렴합니다.

Continue에서는 인덱싱 과정 중에 임베딩을 생성하고, 이를 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 활용하여 코드베이스 전체에 대한 유사성 검색을 수행합니다. 이를 통해 Continue는 워크스페이스에서 가장 관련성 있는 컨텍스트를 자동으로 가져올 수 있습니다.

#### 예시

Spotify에서 사용자에게 추천 곡을 제공할 때, 사용자가 들었던 곡들을 임베딩하여 의미적으로 유사한 음악들을 추천

#### 추천 모델

어떤 모델이든 쓸 수 있다면 voyage-code-2를 추천하며, 로컬 환경에서 임베딩을 생성하고 싶다면 Ollama와 함께 nomic-embed-text를 사용하는 것을 권장합니다.

이외에 Transformers.js를 사용해 로컬 임베딩을 생성할 수 있으며, 자체 임베딩 엔드포인트를 구축하고 싶을 경우 Hugging Face Text Embeddings Inference를 사용할 수 있습니다.

OpenAI, Cohere, Gemini 공급사에서도 임베딩 모델을 제공합니다.

### Reranking model
Reranking 모델은 검색 결과를 다시 정렬하는 데 사용됩니다. 기본 검색 시스템이 결과를 제공한 뒤이 모델이 관련성을 평가해, 가장 적합한 결과를 다시 상위에 배치하는 역할을 합니다. 추천 시스템과 검색 시스템에 사용될 수 있습니다. 

#### 개념

리랭킹 모델(Reranking model)은 두 개의 텍스트(주로 사용자의 질문과 문서)를 입력받아 0에서 1 사이의 관련성 점수를 반환하도록 훈련된 모델입니다. 이 점수는 해당 문서가 질문에 답변하는 데 얼마나 유용할지를 측정합니다. 리랭킹 모델은 일반적으로 LLM보다 훨씬 작으며, 비교적 매우 빠르고 저렴합니다.

Continue 플랫폼에서는 [@codebase](https://docs.continue.dev/customize/deep-dives/codebase) 기능에서 리랭킹 모델을 사용합니다. 이는 벡터 검색 후 가장 관련성 높은 코드 스니펫을 선택하는 데 필요합니다.

#### 예시

추천시스템

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


1. Mistral(미스트랄) (https://mistral.ai/)   
  
미스트랄은 프랑스 회사로 한국어에도 꽤 좋은 성능을 보이는 알려졌다.  
Continue 문서에는 채팅에는 'Mistral Large' 모델 적용, 자동완성에는 'Codestra', 임베딩에는 'Mistral Embed' 모델을 추천한다.  
Continue에 미스트랄의 모델 사용을 하기 위해서는 api key를 등록해야 하며 정책에 따라 과금된다. (과금 정보 : https://mistral.ai/technology/#pricing)  
  
- Mistral Large Mistral Large 모델은 복잡한 작업에 가장 좋은 추론이 가능한 모델로 한국어를 포함해 다양한 언어를 지원 128K 토큰을 한번에 처리할 수 있으며(Context window)   
  80개 이상의 프로그래밍 언어에서 수준 높은 코딩 능력을 갖추었다.   
- Codestra Codestra는 코드 작업을 위해 만들어진 모델로 Python, java, C, C++, PHP와 같은 프로그래밍 언어 80개 이상에 대해 학습한 모델로 다른 모델보다 응답이 빠르다. 32K 토큰을 처리할 수 있다.    
- Mistral Embed Mistral Embed는 텍스트를 추출하기 위해 사용되는 모델로서 현재는 영어만 지원하고 있다.  

2. Anthropic(앤트로픽) (https://www.anthropic.com/)   
  
Anthropic은 미국의 인공지능 회사로 OpenAI 퇴사자가 설립한 회사로 대화형 인공지능 Claude가 있다.  
모델은 3가지로 Haiku는 가볍고 빠르게 사용하기 위한 모델, Sonnet은 성능과 속도의 적절한 수준의 모델, Opus는 성능이 가장 우수한 모델로 어려운 수학과 프로그래밍에 사용하는 모델이 있다.  
Continue에 적용 시 api키를 발급받아 사용해야 하며 과금 체계에 따라 과금된다. (과금 정보 : https://www.anthropic.com/pricing#anthropic-api)  
  
3. Azure OpenAI (https://azure.microsoft.com/ko-kr)   
  
Azure는 Microsoft사의 Public Cloud 서비스를 제공하는 CSP사이다. 여러 AI 모델 공급사로부터 모델을 공급받아 서비스를 하는 형태이다.  
Continue에서는 채팅 모델로 'GPT-4o' 모델을 추천하며 자동완성 모델로 'Codestral', 임베딩에는 'text-embedding-3-large' 모델 사용을 추천한다.   
Azure OpenAI에서 re-Ranking 모델은 제공하지 않는다. 사용을 위해서는 api key를 발급받아 적용해야 사용이 가능하며 과금 체계에 따라 과금 된다.   
(과금 정보 : https://azure.microsoft.com/ko-kr/pricing/details/cognitive-services/openai-service/#pricing)  
  
4. Amazon Bedrock (https://aws.amazon.com/ko/bedrock/?gclid=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB&trk=24a8f13a-f5db-4127-bcb7-8b2876aa4265&sc_channel=ps&ef_id=Cj0KCQjwmOm3BhC8ARIsAOSbapXJzJtKJf-adSQvzrKZ32ICT4sj4d8cLZGrvUvXJD6VpAV5i8Zy1ZIaAreUEALw_wcB:G:s&s_kwcid=AL!4422!3!692062155749!e!!g!!amazon%20bedrock!21058131112!157173586057)  
  
AWS는 Azure와 같이 amazon사의 Public Cloud 서비스를 제공하는 곳이며 Amazon Bedrock(아마존 베드록)은 AWS 환경에서 LLM을 개발하고 배포할 수 있는 플랫폼이다.   
Continue에서는 채팅 모델로 'Claude 3.5 Sonnet' 모델을 추천하며 임베딩에는 'amazon.titan-embed-text-v2:0' 모델 사용을 추천한다.   
Amazon Bedrock에서 자동완성, re-Ranking 모델은 제공하지 않으며 사용자가 정의한 모델을 사용할 경우에는 'config.json' 파일에 모델을 지정해야 한다.  
  
5. Deepseek(딥시크) (https://www.deepseek.com/)   
딥시크는 중국의 스타트업이다. Continue에서는 채팅 모델로 'deepSeek-chat', 자동완성 모델에는 'deepseek-coder' 사용을 추천하며 임베딩, re-Ranking 모델은 제공하지 않는다.  
api key 사용을 위해서는 키를 발급 받아 적용해야 하고 과금 체계에 따라 과금된다.  
  
6. Gemini(제미니) (https://gemini.google.com/?hl=ko)  
제미니는 구글이 만든 AI 챗봇이다. Continue에서는 채팅 모델로 'Gemini 1.5 Pro', 임베딩 모델에는 'models/text-embedding-004' 사용을 추천하며 자동완성, re-Ranking 모델은 제공하지 않는다.  
api key 사용을 위해서는 키를 발급 받아 적용해야 하고 과금 체계에 따라 과금되는데 일부 사용에 대해 무료로 사용할 수 있는 것 같다.  
(과금 정보 : https://ai.google.dev/pricing?hl=ko) 다만 코드 어시스턴트 특성상 자동완성과 채팅이 지원되지 않는 것은 아쉽다.  
  
7. Ollama  
Ollama는 로컬에서 LLM을 구동할 수 있도록 하는 오픈소스이다. Continue에서는 채팅 모델로 'llama3.1:8b', 자동완성 모델로 'starcoder2:3b', 임베딩 모델로 'nomic-embed-text'를 추천하며  
re-Rankig 모델은 제공하지 않는다. 오픈소스이므로 apikey를 발급받아 설정하거나 할 필요는 없고 해당 모델을 다운로드 받아 Continue의 config에 해당 모델 사용을 적용이 필요할 것으로 보인다.  
  
8. OpenAI (https://openai.com/)  
OpenAI는 미국의 인공지능 기업으로 chatGPT로 유명해졌다. Continue에서는 채팅 모델로 'GPT-4o', 자동완성 모델로 'starcoder2:3b', 임베딩 모델로 'text-embedding-3-large'를 추천하며  
re-Rankig 모델은 제공하지 않는다. 사용하기 위해서는 apikey 발급하여 적용해야 하며 과금 체계에 따라 과금된다. (과금 정보 : https://openai.com/api/pricing/)  
  
이외에도 Cloudflare, 캐나다의 coHere 등 다양한 모델을 제공하는 회사가 있다.  

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

#### 1. Ollama (https://ollama.com/)
   
Ollama는 로컬 환경에서 LLM을 쉽게 실행할 수 있는 도구로, 주로 GPT 계열 모델을 로컬에서 실행할 수 있습니다. 클라우드 의존성 없이 AI 모델을 로컬에서 처리하므로, 민감한 데이터를 보호하고 클라우드 저장소에 의존하지 않아도 되는 것이 주요 장점입니다.
또한 다양한 LLM을 지원합니다. (Llama 3, Mistral, CodeLlama, Orca Mini 등)

연동 방법:
Ollama를 공식 웹사이트에서 다운로드하여 설치 후, 
로컬에서 Ollama API 서버를 실행
Continue의 config.json 파일에서 Ollama를Providers로 설정합니다.


#### 2. LlamaCpp (https://github.com/ggerganov/llama.cpp)
   
LlamaCpp는 Meta의 LLaMA 모델을 C++ 기반으로 로컬에서 실행할 수 있는 도구입니다. 주로 CPU 성능을 극대화하여 고성능 LLM 추론을 지원하며, GPU 없이도 실행이 가능합니다. 특히 저사양 환경에서도 효율적으로 LLM을 로컬에서 사용할 수 있도록 설계되었습니다.

연동 방법:
GitHub 리포지토리에서 LlamaCpp를 다운로드 하여 설치 후, 
LlamaCpp 서버 바이너리를 실행하여 API 서버를 설정하고
config.json 파일에서 LlamaCpp Providers로 설정합니다.

#### 3. Llamafile (https://github.com/Mozilla-Ocho/llamafile)
   
Llamafile은 복잡한 서버 설정이 필요 없고히 llama.cpp와 Cosmopolitan Libc의 결합을 통해 다양한 환경에서 실행 가능한 단일 빌드로 모든 기능을 패키징 하므로 복잡한 설정 없이 로컬에서 쉽게 실행할 수 있습니다. 주로 로컬 배포에 용이하게 설계되어 간편한 실행을 지원합니다.

연동 방법:
LLM을 Llamafile 형식으로 패키징하여 저장한 후, 
config.json 파일에서 Llamafile Providers를 설정합니다.

#### 4. LM Studio (https://lmstudio.ai/)
   
LM Studio ggml 포맷을 지원하는 Llama, MPT, StarCoder 모델 어떤 것이든 호환이 가능합니다. 호환되는 모델 파일을 검색, 다운로드가 가능하고 여러개의 로컬 LLM을 동시에 로딩해 사용할 수 있습니다. 로컬 호스트에서 OpenAI와 유사한 HTTP 서버를 구동할 수 있습니다. 

연동 방법:
LM Studio 공식 사이트에서 다운로드해 설치한 후, 
LM Studio에서 원하는 모델을 다운로드하고 로컬에서 실행
config.json 파일에서 LM Studio Providers를 설정합니다.

#### 5. TextGenWebUI (https://github.com/oobabooga/text-generation-webui)

TextGenWebUI는 Gradio 기반 웹 인터페이스로 다양한 텍스트 생성 모델과 파라미터를 쉽게 선택하여 원하는 텍스트를 만들 수 있습니다. Conda 환경 구성, 소스코드 다운로드, 설치 및 실행, web ui실행, 모델 다운로드 순의 진행을 통해 사용 가능합니다. 

연동 방법:
TextGenWebUI 설치 후, OpenAI 호환 서버 플러그인을 설치
로컬에서 TextGenWebUI API 서버를 실행한 후, 
config.json 파일에서 TextGenWebUI Providers를 설정합니다.

#### 예시 Provider 연동 방법
```
{
  "providers": {
   // Ollama, LlamaCpp, Llamafile 등 로컬 AI 실행도구 설정
    "textgenwebui": { 
      "url": "http://localhost:port_number",  // 로컬 AI 실행도구 API 서버 주소
      "model": "your_model_name"
    }
  }
}
```


### AI 워크플로우 및 통합 도구

AI 모델을 기존 시스템이나 워크플로우에 쉽게 통합할 수 있게 해주는 도구들입니다. 해당 유형의 서비스들은 AI 기술의 접근성을 높이고 활용도를 증가시킵니다.

Flowise, Kindo, Msty, OpenRouter가 여기에 속합니다.

#### 예시 Provider 연동 방법

Flowise 란? https://flowiseai.com/
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



장점 : Flowise는 AI 워크플로우를 드래그 앤 드롭 방식으로 설계할 수 있는 시각적 인터페이스를 제공합니다.  
이를 통해 개발자는 복잡한 워크플로우나 모델 간의 데이터 흐름을 쉽게 관리하고 설계할 수 있습니다.  
Continue는 협업을 강조하는 플랫폼인데, Flowise와 연결하면 팀원들이 각 워크플로우의 시각적인 구성을 손쉽게 이해하고 수정할 수 있습니다.

참조 : (flowise api 등록) https://docs.continue.dev/customize/model-providers/more/flowise  
      (flowise api 튜토리얼) https://www.youtube.com/watch?v=9R5zo3IVkqU&t=305s  
      (flowise git hub) https://github.com/FlowiseAI/Flowise  


Kindo 설정 동일

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
 Msty, OpenRouter도 비슷하다 https://docs.continue.dev/customize/model-providers/more  
 공식문서 ModelProvider -> more 에서 참고


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