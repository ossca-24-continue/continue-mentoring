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

#### 예시 Provider 연동 방법

### AI 워크플로우 및 통합 도구

AI 모델을 기존 시스템이나 워크플로우에 쉽게 통합할 수 있게 해주는 도구들입니다. 해당 유형의 서비스들은 AI 기술의 접근성을 높이고 활용도를 증가시킵니다.

Flowise, Kindo, Msty, OpenRouter가 여기에 속합니다.

#### 예시 Provider 연동 방법

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
      



### 특화된 AI 서비스

특정 분야나 기술에 특화된 AI 서비스입니다. 이들은 멀티모달 AI, 고성능 추론, 하드웨어 최적화 등 특정 니즈를 충족시키는 솔루션을 제공합니다.

Gemini, Groq, IPEX-LLM, ReplicateLLM이 여기에 속합니다.

#### 예시 Provider 연동 방법
