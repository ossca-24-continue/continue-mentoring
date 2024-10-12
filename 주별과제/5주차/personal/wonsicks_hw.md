# Continue 설치 및 설정 #  
### Continue 설치 ###
Continue는 오픈 소스 AI 코딩 어시스턴트로, VSCode와 IntelliJ에서 플러그인으로 설치 가능.  
### 설정 방법 ###
Free-Trial: GPT-4o, Claude 3 Sonnet, Llama3 70b 등 최대 50회 사용 가능한 무료 모델 제공.  
API Key 설정: OpenAI 및 Anthropic API 키를 발급받아 config.json에 입력.  
로컬 모델 설정: Ollama 설치 후 Llama 모델을 로컬에서 실행 가능.  
### 주요 기능 ###
Chat: 코드를 추가하여 질문을 입력하면 AI가 답변 제공.  
Autocomplete: 코드 자동 완성 기능 제공.  
Edit: 코드 블록을 수정하고 변경 사항을 반영할 수 있음.  
Actions: 다양한 명령어로 자동화 작업을 실행 가능.  
AI 코딩 어시스턴트의 중요성: 생산성 향상, 코드 품질 개선, 오류 감소, 학습 지원 등의 이점이 있으며, 기업 내 도입이 급증하는 추세입니다.  
### 조사한 도구들 ###:
Amazon CodeWhisperer: AWS와 통합된 무료 AI 어시스턴트.  
Codex: OpenAI 기반의 AI 모델로 다양한 언어 지원.  
Cursor: 자연어 기반 코드 수정과 리팩토링.  
Tabnine: 개인 데이터 보안을 강조한 코드 어시스턴트.  
Codeium: 무료로 다양한 기능 제공.  
GitHub Copilot: 코드 자동 완성 및 협업에 최적화.  
Replit GhostWriter: 실시간 협업 지원.  
### Continue 도구 ###  
오픈소스 도구로 코드 자동완성, 자연어 기반 코드 재작성 기능을 제공하며, 다양한 AI 모델을 자유롭게 선택 및 커스터마이즈할 수 있습니다.  
결론: AI 코딩 어시스턴트는 소프트웨어 개발의 필수 도구로 자리 잡을 것이며, 도입 시 교육 지원과 보안 검토가 필요합니다.  
### Action & Edit 요약 ###
Edit 기능은 코드를 하이라이트한 후, 자연어로 수정 요청을 입력해 코드 블록을 바로 수정할 수 있는 기능입니다. 사용자는 제안된 수정사항을 accept 또는 reject할 수 있으며, 단축키로 쉽게 수정 작업을 진행할 수 있습니다. 주요 기능으로는 주석 추가, 함수 리팩토링 등이 있으며, 복잡한 작업에는 Chat 기능 사용을 권장합니다.
Actions 기능은 자주 사용하는 작업을 빠르게 수행할 수 있는 단축키 기능입니다. /edit, /comment, /share 등의 명령어를 통해 코드 수정, 주석 추가, 채팅 기록 내보내기 등을 할 수 있으며, .prompt 파일을 사용해 사용자 맞춤 명령어를 생성할 수도 있습니다. Quick Actions, Right Click Actions 등을 통해 더 빠르게 액션을 실행할 수 있습니다.
주요 팁: Edit 기능은 빠른 수정 작업에 적합하고, Actions는 반복 작업을 자동화하는 데 유용하며, 프롬프트를 간결하게 작성하는 것이 중요합니다.

# Continue의 주요 기능 #
### Chat ###
How to use it: IDE 내에서 AI와 대화하며 코드 문제를 해결할 수 있습니다. 코드 블록을 하이라이트하거나 문서, IDE 정보 등을 포함하여 질문하고, AI가 응답합니다.  
Model setup: 다양한 AI 모델(GPT-4, Llama 3.1, Claude 3.5 등)을 지원하며, 로컬 및 클라우드 모델 설정이 가능합니다.  
Context selection: 프로젝트 파일, 코드베이스 등을 컨텍스트로 선택해 AI의 응답 정확도를 높일 수 있습니다.  
How it works: 컨텍스트와 프롬프트를 기반으로 AI가 응답을 생성합니다.  
Customization: 코드베이스, 문서, URL 등을 컨텍스트로 추가할 수 있고, Prompt Files로 AI의 동작을 조정할 수 있습니다.  
### Autocomplete ###
How to use it: 코드 작성 중 자동 완성 기능을 제공하며, Tab 키로 적용, Esc로 거부할 수 있습니다.  
Model setup: Codestral 등의 고성능 모델을 사용하거나, 로컬 환경에서는 StarCoder2-3b를 추천합니다.  
Context selection: 커서 위치 기반으로 코드 블록 앞뒤 맥락을 자동으로 감지하여 컨텍스트로 사용합니다.  
How it works: 입력 후 딜레이를 두고 자동완성 작업이 실행되며, 캐싱과 필터링으로 성능을 최적화합니다.  
Customization: config.json을 통해 자동완성 기능을 세부적으로 조정할 수 있습니다.  
### 주요 포인트 ###
Chat: AI와의 대화를 통해 코드 문제를 해결, 다양한 모델 및 컨텍스트 지원.  
Autocomplete: 코드 작성 중 자동 완성 지원, 모델과 기능 커스터마이징 가능.  

# Continue에서 사용하는 모델 유형 및 연동 유형 요약 #
### 모델 유형 ###
Continue는 다양한 AI 모델을 사용하여 코드 자동 완성, 대화형 AI, 유사성 검색, 검색 결과 재정렬 등을 제공합니다.  
주요 모델 유형:
Autocomplete model: 코드 자동 완성을 위해 사용됩니다. 모델은 중간 채우기(FIM) 기법을 활용하여 실시간 인라인 제안을 제공합니다.   
주로 Mistral의 Codestral 모델이나 로컬에서는 Starcoder2-3B를 사용합니다.  
Chat model: 대화형 AI로 복잡한 질문에 답하고 코드를 생성하는 데 사용됩니다. Claude 3.5 Sonnet, GPT-4o 등 대형 모델을 추천합니다.  
Embeddings model: 텍스트나 코드 간 유사성을 계산하는 모델로, 검색 기능이나 추천 시스템에 사용됩니다. OpenAI, Cohere 등의 임베딩 모델을 활용할 수 있습니다.  
Reranking model: 검색 결과를 다시 정렬하여 가장 관련성 있는 항목을 상위에 배치하는 모델입니다. Voyage AI의 rerank-1 모델 등이 추천됩니다.  

## 모델 연동 유형 ##
Continue는 다양한 방식으로 AI 모델을 연동할 수 있으며, 주로 다음과 같은 방법들이 있습니다:  
AI 모델 제공 및 개발 플랫폼: Anthropic, OpenAI, Mistral, Cohere 등 자체 AI 모델을 제공하는 플랫폼과 연동합니다. API 키를 통해 연결할 수 있습니다.  
클라우드 AI 서비스: Azure OpenAI, Amazon Bedrock 등 클라우드 기반 AI 서비스를 통해 모델을 제공받아 사용할 수 있습니다.  
AI 모델 배포 및 서버리스 플랫폼: HuggingFace, Cloudflare Workers AI 등을 통해 모델을 배포하거나 API로 연결해 사용할 수 있습니다.  
로컬 AI 실행 도구: Ollama, LlamaCpp, LM Studio 등을 통해 로컬에서 AI 모델을 실행하며, API 서버를 통해 Continue와 연동합니다.  
AI 워크플로우 및 통합 도구: Flowise, Kindo 등의 도구를 사용하여 AI 워크플로우를 설계하고 쉽게 연동할 수 있습니다.  
특화된 AI 서비스: Gemini, Groq, IPEX-LLM, Replicate 등 특정 기술이나 분야에 특화된 AI 모델을 연동하여 사용합니다.  

# LLM (Large Language Model) 및 선택 가이드 #
LLM은 대규모 언어 모델로, 인간 언어를 이해하고 생성할 수 있습니다. CodeLLM은 코드 생성과 자동완성에 특화된 LLM입니다.  
### 주요 기능 ###
코드 자동 완성: 코드 작성 중에 자동 제안  
코드 생성: 자연어 요구사항에 맞는 전체 코드 생성  
디버깅: 코드 오류 수정 및 분석  
다양한 언어 지원  
양자화(Quantization)는 모델 크기를 줄이고 속도를 높이기 위한 기법입니다. INT4와 INT8 양자화가 이를 지원하며, 모델의 효율성을 높이는 데 기여합니다.  
LLM 벤치마크  
LLM의 성능을 평가하는 여러 벤치마크:  
HumanEval: Python 코드를 기반으로 코딩 능력을 평가  
MBPP: 다양한 프로그래밍 문제로 구성된 벤치마크  
EvalPlus: 복잡한 상황에서의 성능을 평가  
CodeXGLUE: 코드 생성, 요약, 검색 등 다양한 작업을 평가  
CRUXEval: 코드 추론 및 실행 능력을 평가  
APPS: 복잡한 프로그래밍 문제 해결 능력을 평가  
### LLM 선택 가이드 ###
가격  
양자화: 모델 크기, F1 점수  
코딩 성능 (HumanEval, MBPP 등)  
DeepSeek-Coder-V2-Instruct가 성능이 높음  
다른 고려 모델: CodeLlama-70b, Phind-CodeLlama-34B-v2  
Chat 모델 선택:  
한국어 처리 능력이 중요한 경우, 논리적 문제 해결 능력을 평가하는 지표인 Ko-IFEval이나 Ko-GSM8k를 고려합니다.  
Autocomplete 모델 선택:  
FIM(Fill-In-the-Middle) 형식으로 코드의 중간을 예측하는 기법  
Continue에서 Codestral(클라우드), Starcoder2-3B(로컬)를 추천  
Embedding 모델:  
텍스트나 코드를 벡터화하여 유사도 검색 등에 사용합니다. Continue에서 추천하는 모델:  
Voyage AI의 voyage-code-2  
Ollama의 nomic-embed-text  
OpenAI의 text-embedding-3-large  
Reranking 모델:  
검색 후 적합한 결과를 정렬하는 모델입니다. Voyage AI의 rerank-1이 추천되며, bge reranker는 한국어 처리에 유리하지만 코드 이해 성능이 약간 떨어질 수 있습니다.  

# LLM Completion Options & 효과적인 프롬프팅 #
### LLM Completion Options ###
LLM: 대규모 언어 모델로, 자연스러운 대화와 텍스트 생성이 가능함.  
Completion Options: LLM이 응답을 생성하는 방식을 조정하는 설정으로, temperature, topP, presencePenalty 등을 통해 응답의 창의성, 다양성, 길이 등을 조절할 수 있음.  
### Continue에서 Completion 설정 ###
Continue에서는 config.json 파일을 통해 completionOptions를 설정할 수 있음. 원하는 모델별로 각기 다른 설정을 부여할 수 있음.  
예: temperature로 창의성을 높이거나, maxTokens로 응답 길이 조절 가능.  
Context Provider  
Context Providers는 코드, 문서, URL 등 다양한 외부 정보를 LLM에 제공하여 응답 품질을 높임.  
Continue에서는 기본적으로 @file, @code, @docs 등 여러 context를 지원하며, 커스텀 context도 추가 가능함.  
효과적인 프롬프팅  
### 프롬프트를 더 효과적으로 작성하려면 ###
구체적이고 명확하게 지시: 질문 범위를 좁히고 구체적으로 요구.  
페르소나 부여: LLM에게 역할을 설정해 더 정확한 응답 유도.  
문체와 난이도 지시: 원하는 응답의 문체나 난이도 설정.  
연속적 지시: 복잡한 작업을 단계별로 요청해 답변 품질 향상.  
### Custom Slash Commands ###
Continue에서 customCommands나 slashCommands를 활용해 자연어 명령을 정의하고 특정 응답을 커스터마이징할 수 있음.  

# RAG (검색 증강 생성) #
### RAG 개요 ###
RAG는 LLM(대형 언어 모델)이 외부 데이터베이스나 검색 엔진을 사용해 정확하고 최신 정보를 제공하는 방법입니다.  
LLM 자체의 한계를 보완해 환각이나 신뢰성 부족 문제를 해결합니다.  
### RAG의 중요성과 장점 ###
신뢰성: 검증된 외부 자료를 사용해 응답의 정확성을 높입니다.  
비용 효율성: 모델 재학습 대신 외부 데이터를 연결하는 방식으로 비용 절감.  
최신 정보 제공: 실시간으로 업데이트된 데이터 소스를 연결하여 최신 정보를 제공합니다.  
### RAG 작동 방식 ###
데이터 수집: 외부 소스에서 데이터를 청크로 분할.  
임베딩 생성: 문서를 벡터로 변환해 저장.  
정보 검색: 사용자의 쿼리를 바탕으로 관련 정보를 벡터 데이터베이스에서 검색.  
응답 생성: 검색된 정보를 바탕으로 LLM이 응답을 생성.  
### RAG 활용 예시 ###
고객 지원 챗봇: FAQ 검색 후 관련 답변 제공.   
법률/의료 분야: 최신 데이터를 바탕으로 정확한 정보 제공.   
연구 보조 도구: 논문이나 기사를 검색해 요약 제공.   
### RAG의 단점 ###
계산 비용 증가: 검색 과정이 추가되어 응답 시간이 늘어날 수 있음.  
검색 품질 의존: 검색된 정보가 응답의 품질에 영향을 미침.  
### Continue에서의 RAG ###
Continue는 코드베이스 검색 시 RAG를 사용하여 빠른 검색 결과를 제공하고, 필요 시 LLM 기반 재순위화를 통해 정확도를 높입니다.  
SQLite와 LanceDB를 사용해 데이터를 관리하고, 로컬에서 임베딩과 검색을 수행합니다.  
###RAG 커스텀 in Continue ###
임베딩 모델: Continue는 voyage-code-2를 추천합니다.  
벡터 DB: 인 메모리 DB로 LanceDB를 사용합니다.  
청킹 전략: 문서를 작은 청크로 나누어 임베딩 후 벡터 DB에 저장.  
RAG는 실시간 정보 제공과 메모리 효율성을 극대화하면서도, 검색 품질과 성능을 유지하는 데 중요한 역할을 합니다.  
