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
Autocomplete 모델은 입력한 코드나 텍스트의 앞뒤 내용을 토대로, 중간에 들어갈 내용을 예측해주는 모델입니다. 이 모델은 코드를 빠르게 작성해야 할 때, 다음에 나올 코드를 자동으로 제안해줄 수 있습니다. 

### Chat model
Chat 모델은 대화 형식에 응답하도록 훈련된 LLM 입니다.  사용자가 질문을 입력하면 자연스러운 대화 형식으로 답변을 제공합니다. 질문에 답하고 복잡한 코드를 짜야하기 때문에, 좋은 성능의 모델은 파라미터가 4천억개 이상 입니다. 

### Embeddings model
Embeddings 모델은 텍스트를 벡터값으로 변환해  텍스트 간의 유사도를 비교할 수 있게 해주는 모델입니다. 예시로, 검색어와 문서 간의 유사도를 계산하거나 추천 시스템에서 유사성을 비교하는 데 주로 사용됩니다.

### Reranking model
Reranking 모델은 검색 결과를 다시 정렬하는 데 사용됩니다. 기본 검색 시스템이 결과를 제공한 뒤이 모델이 관련성을 평가해, 가장 적합한 결과를 다시 상위에 배치하는 역할을 합니다. 추천 시스템과 검색 시스템에 사용될 수 있습니다. 

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

### AI 모델 배포 및 관리 도구

AI 모델을 효율적으로 배포하고 관리하기 위한 도구와 서비스입니다. 모델의 성능 최적화와 확장성을 지원합니다

Cloudflare Workers AI, HuggingFace Inference Endpoints, DeepInfra, Together, vLLM이 여기에 속합니다.

#### 예시 Provider 연동 방법

### 로컬 AI 실행 도구

개인 컴퓨터나 로컬 서버에서 AI 모델을 실행할 수 있게 해주는 소프트웨어입니다. 데이터 프라이버시와 오프라인 사용을 중요시하는 사용자들에게 유용한 서비스들입니다.

Ollama, LlamaCpp, Llamafile, LM Studio, TextGenWebUI이 여기에 속합니다.

1. Ollama (https://ollama.com/)
   
Ollama는 로컬 환경에서 LLM을 쉽게 실행할 수 있는 도구로, 주로 GPT 계열 모델을 로컬에서 실행할 수 있습니다. 클라우드 의존성 없이 AI 모델을 로컬에서 처리하므로, 민감한 데이터를 보호하고 클라우드 저장소에 의존하지 않아도 되는 것이 주요 장점입니다.
또한 다양한 LLM을 지원합니다. (Llama 3, Mistral, CodeLlama, Orca Mini 등)

연동 방법:
Ollama를 공식 웹사이트에서 다운로드하여 설치 후, 
로컬에서 Ollama API 서버를 실행
Continue의 config.json 파일에서 Ollama를Providers로 설정합니다.


2. LlamaCpp (https://github.com/ggerganov/llama.cpp)
   
LlamaCpp는 Meta의 LLaMA 모델을 C++ 기반으로 로컬에서 실행할 수 있는 도구입니다. 주로 CPU 성능을 극대화하여 고성능 LLM 추론을 지원하며, GPU 없이도 실행이 가능합니다. 특히 저사양 환경에서도 효율적으로 LLM을 로컬에서 사용할 수 있도록 설계되었습니다.

연동 방법:
GitHub 리포지토리에서 LlamaCpp를 다운로드 하여 설치 후, 
LlamaCpp 서버 바이너리를 실행하여 API 서버를 설정하고
config.json 파일에서 LlamaCpp Providers로 설정합니다.

3. Llamafile (https://github.com/Mozilla-Ocho/llamafile)
   
Llamafile은 복잡한 서버 설정이 필요 없고히 llama.cpp와 Cosmopolitan Libc의 결합을 통해 다양한 환경에서 실행 가능한 단일 빌드로 모든 기능을 패키징 하므로 복잡한 설정 없이 로컬에서 쉽게 실행할 수 있습니다. 주로 로컬 배포에 용이하게 설계되어 간편한 실행을 지원합니다.

연동 방법:
LLM을 Llamafile 형식으로 패키징하여 저장한 후, 
config.json 파일에서 Llamafile Providers를 설정합니다.

4. LM Studio (https://lmstudio.ai/)
   
LM Studio ggml 포맷을 지원하는 Llama, MPT, StarCoder 모델 어떤 것이든 호환이 가능합니다. 호환되는 모델 파일을 검색, 다운로드가 가능하고 여러개의 로컬 LLM을 동시에 로딩해 사용할 수 있습니다. 로컬 호스트에서 OpenAI와 유사한 HTTP 서버를 구동할 수 있습니다. 

연동 방법:
LM Studio 공식 사이트에서 다운로드해 설치한 후, 
LM Studio에서 원하는 모델을 다운로드하고 로컬에서 실행
config.json 파일에서 LM Studio Providers를 설정합니다.

5. Msty (https://msty.app/)
   
Msty는 Groq, Cluaude와 같은 온라인 언어 모델과 Ollama 로컬 언어 모델을 모두 지원하는 언어 모델 도구로 대화창 분할, 그룹 동시 채팅, 프롬프트 라이브러리 등 다양한 기능을 미니멀한 UI를 통해 제공합니다. 

연동 방법:
Msty 앱을 통해 모델을 실행한 후, 
config.json 파일에서 Msty를 Providers를 설정합니다.

6. TextGenWebUI (https://github.com/oobabooga/text-generation-webui)

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

### 특화된 AI 서비스

특정 분야나 기술에 특화된 AI 서비스입니다. 이들은 멀티모달 AI, 고성능 추론, 하드웨어 최적화 등 특정 니즈를 충족시키는 솔루션을 제공합니다.

Gemini, Groq, IPEX-LLM, ReplicateLLM이 여기에 속합니다.

#### 예시 Provider 연동 방법
