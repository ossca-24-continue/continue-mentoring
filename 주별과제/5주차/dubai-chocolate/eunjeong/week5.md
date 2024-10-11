# 3, 4주차 전체 주제 정리

## 목차

- [3, 4주차 전체 주제 정리](#3-4주차-전체-주제-정리)
  - [목차](#목차)
  - [3주차](#3주차)
    - [📄 ai coding assistant 도구 조사 및 비교 분석, continue의 특,장점 정리](#-ai-coding-assistant-도구-조사-및-비교-분석-continue의-특장점-정리)
    - [📄 continue 설치, 설정, 주요기능 오버뷰](#-continue-설치-설정-주요기능-오버뷰)
    - [📄 continue chat, autocomplete 기능 상세 리뷰](#-continue-chat-autocomplete-기능-상세-리뷰)
    - [📄 continue edit, actions 기능 상세 리뷰](#-continue-edit-actions-기능-상세-리뷰)
  - [4주차](#4주차)
    - [📄 Continue에서 사용하는 Model 유형, Model 연동 유형](#-continue에서-사용하는-model-유형-model-연동-유형)
    - [📄 LLM completion options \& continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)](#-llm-completion-options--continue에서-설정하기-챗-잘사용하기---효과적인-프롬프팅system-user)
    - [📄 RAG, RAG in continue](#-rag-rag-in-continue)
    - [📄 LLM, LLM benchmarks(for code), 선택가이드](#-llm-llm-benchmarksfor-code-선택가이드)

## 3주차

### 📄 ai coding assistant 도구 조사 및 비교 분석, continue의 특,장점 정리

1. **서론**
   - AI 코딩 어시스턴트는 생산성 향상, 코드 품질 개선, 학습 지원, 오류 감소, 협업 강화, 비용 절감의 장점을 가짐.
   - 63%의 기업이 AI 어시스턴트를 도입, 2028년까지 75%로 증가 예상.
2. **AI 코딩 어시스턴트 도구 조사**
   - **Amazon CodeWhisperer**: AWS 환경 최적화, 다양한 언어 지원, 무료 플랜 제공.
   - **Codex**: OpenAI 모델 기반, 자연어 처리 능력 탁월, 12개 언어 지원.
   - **Cursor**: VSCode 기반, 설치 필요 없이 AI 도움 제공, 다중 파일 분석 가능.
   - **Tabnine**: 보안 중심, 다양한 IDE 지원, 사용자 데이터 보호.
   - **Codeium**: 무료 플랜 제공, 자연어 기반 코드 편집, 70개 이상 언어 지원.
   - **GitHub Copilot**: GitHub 및 OpenAI 협력, 코드 자동완성 및 협업 지원.
   - **Replit GhostWriter**: 실시간 협업 및 초보자 친화적 환경 제공, 웹 기반.
3. **Continue 도구의 특징**
   - **개요**: 오픈소스 기반, 커스터마이즈 가능, VSCode 및 JetBrains와 통합.
   - **주요 기능**: 문맥 인식 대화, 자연어 기반 코드 수정, 모델 커스터마이징 가능.
   - **차별화 특징**: 다양한 컨텍스트 데이터 지원, 확장성 및 오픈소스 제공.
4. **결론**
   - AI 코딩 어시스턴트는 코드 품질 향상 및 시간 절감에 기여하며, 보안 문제는 SaaS나 On-Premise로 해결 가능.
   - 도구 선택 시 교육 및 기술 지원, 보안 수준 검토가 필요.

### 📄 continue 설치, 설정, 주요기능 오버뷰

**Continue 설치**

Continue는 VSCode와 IntelliJ에서 플러그인 형식으로 설치 가능:

- **VSCode**: Extensions 탭에서 Continue 검색 후 설치. 설치 후 우측 하단에 Chat 기능 탭 표시.
- **IntelliJ**: 플러그인 탭에서 설치. 설치 후 우측 상단에 Chat 기능 탭이 나타남.

**Continue 설정**

1. **Free-Trial**: Claude 3 Sonnet, GPT-4o, Llama3 70b 등 모델 최대 50회 무료 사용.
2. **API Key 발급**: OpenAI, Anthropic API Key를 `config.json`에 등록.
3. **Local Model 설정**: Ollama 설치 후 로컬 모델 실행, `config.json` 수정하여 설정.

**주요 기능**

1. **Chat**: AI와 코드 관련 질문과 답변 가능.
2. **Autocomplete**: Tab 키로 코드 자동 완성.
3. **Edit**: 코드 블럭 선택 후 AI에게 수정 요청 가능.
4. **Actions**: Slash 명령어나 단축키로 코드 관련 명령어 실행 가능.
   - **Slash (/) Command**: `/edit`, `/comment`, `/share` 등 사용 가능, `config.json`에서 설정 가능.
   - **Custom Prompt**: `.prompt` 파일로 커스텀 명령어 생성 가능.

### 📄 continue chat, autocomplete 기능 상세 리뷰

**Chat 기능**

1. **사용 방법**: IDE 내에서 AI와 대화로 문제 해결 가능. 코드 하이라이팅, 제안 적용, 모델 변경 등의 기능 제공.
2. **모델 설정**: Claude Sonnet 3.5, GPT-4o 등 다양한 고성능 AI 모델을 지원하며, 로컬 환경에서도 사용 가능.
3. **컨텍스트 관리**: 자동/수동으로 프로젝트 파일을 컨텍스트에 포함해 정확도 향상. 특정 파일을 지정해 질문 가능.
4. **작동 원리**: 입력된 컨텍스트와 프롬프트를 바탕으로 대화형 응답 생성.
5. **커스터마이즈 방법**: 코드베이스, 문서 등 다양한 소스를 컨텍스트로 설정 가능.
6. **LLM 작동 원리**: 트랜스포머 모델을 통해 학습하고, 대화 흐름을 유지하며, 검색 증강 생성(RAG) 기술 사용.
7. **Context Provider**: 코드베이스, URL, GitHub Issues 등의 다양한 정보를 컨텍스트로 추가하여 응답 정확성 향상.
8. **Prompt Files**: 사용자 맞춤형 프롬프트 설정 가능, JSON 형식으로 모델 행동 제어.

**Autocomplete 기능**

1. **사용 방법**: Tab 키로 자동완성 수락, Esc 키로 거부 가능. 단어 단위로 부분 수락도 가능.
2. **모델 설정**: Codestral 모델을 사용해 고품질 자동완성 제공. 로컬 및 오프라인 환경에서는 StarCoder2-3b 모델 추천.
3. **컨텍스트 선택**: 커서 위치를 기준으로 코드 전후 문맥을 분석해 정확한 자동완성 제공.
4. **문제 해결**: API Key 문제, 파일 형식에 따른 기능 제어, 단축키 충돌 해결 제안.
5. **작동 원리**: Debounce와 Caching을 통해 성능 최적화, 불필요한 응답 필터링.
6. **커스터마이즈 방법**: `config.json`에서 자동완성 옵션을 설정하여 사용자 맞춤 기능 가능.

### 📄 continue edit, actions 기능 상세 리뷰

**Edit 기능**

- **개요**: 코드를 인라인으로 빠르게 수정하는 기능. 코드 블록을 하이라이트한 후 수정 사항을 제안하고, 이를 수용(accept)하거나 거부(reject)할 수 있음.
- **사용법**:
  - 코드를 하이라이트하고 단축키로 Edit 창 활성화 후 수정 사항 제안.
  - 수정 사항을 탐색하여 수용 또는 거부 가능.
  - 새로운 제안 요청 시 다시 Edit 기능 활성화.
- **특징**: 주석 추가, 함수 리팩토링, 테스트 생성 등 간단한 수정에 적합.
- **팁**: 큰 수정이 필요한 경우에는 Chat이나 Actions 기능 사용 권장.

**Actions 기능**

- **개요**: 코드 리뷰, 주석 추가, 커밋 등 자주 사용하는 작업을 빠르게 수행할 수 있는 단축키 기능.
- **사용법**:
  - `/` 명령어로 다양한 액션 수행 가능.
  - `.prompt` 파일을 작성해 자신만의 명령어 정의 가능.
- **주요 Slash 명령어**:
  - `/edit`: 코드 수정.
  - `/comment`: 주석 추가.
  - `/share`: 채팅 기록 공유.
  - `/commit`: Git 커밋 메시지 생성.
  - `/so`: StackOverflow 질문 검색.
- **장점**: 작업 효율성을 높여주는 빠른 액세스 및 커스터마이징.
- **팁**: 자주 사용하는 반복 작업을 정의해 작업 속도 향상 가능.

## 4주차

### 📄 Continue에서 사용하는 Model 유형, Model 연동 유형

**Continue에서 사용하는 모델 유형**

Continue는 다양한 AI 작업을 지원하기 위해 4가지 유형의 모델을 활용.

1. **Autocomplete 모델**:
   - **개념**: 코드나 텍스트를 자동완성하는 모델로, 중간 채우기(FIM) 기법을 사용.
   - **용도**: 코드 작성 시 실시간 자동완성 제안.
   - **추천 모델**: Codestral, Starcoder2-3B.
2. **Chat 모델**:

   - **개념**: 대화형 응답을 제공하는 고성능 LLM.
   - **용도**: 코드 생성, 편집, 복잡한 질문 응답.
   - **추천 모델**: Claude 3.5 Sonnet, GPT-4o, Gemini 1.5 Pro.

3. **Embeddings 모델**:

   - **개념**: 텍스트를 벡터화해 유사도를 비교.
   - **용도**: 코드베이스에서 유사한 코드 검색.
   - **추천 모델**: voyage-code-2, nomic-embed-text.

4. **Reranking 모델**:
   - **개념**: 검색 결과의 관련성을 평가해 적합한 결과 상위 배치.
   - **용도**: 코드 스니펫을 관련성에 따라 정렬.
   - **추천 모델**: Voyage AI의 rerank-1, Cohere 리랭킹 모델.

**Continue의 모델 연동 유형**

Continue는 AI 모델을 제공하는 다양한 Provider와 연동되며, 28개의 Provider를 6가지 유형으로 분류.

1. **AI 모델 제공 및 개발 플랫폼**:

   - **정의**: 자체 AI 모델 개발 및 API 제공.
   - **주요 제공자**: Mistral, Anthropic, OpenAI, Gemini 등.

2. **클라우드 AI 서비스**:

   - **정의**: 클라우드 업체가 제공하는 AI 서비스.
   - **주요 제공자**: Azure OpenAI, Amazon Bedrock.
   - **장점/단점**: 비용 효율적이지만, 데이터 보안 우려.

3. **AI 모델 배포 및 서버리스 플랫폼**:

   - **정의**: AI 모델 배포 및 관리 지원 도구.
   - **주요 제공자**: Cloudflare Workers AI, HuggingFace, DeepInfra.

4. **로컬 AI 실행 도구**:

   - **정의**: 개인 컴퓨터나 로컬 서버에서 AI 모델 실행.
   - **주요 제공자**: Ollama, LlamaCpp, LM Studio.

5. **AI 워크플로우 및 통합 도구**:

   - **정의**: AI 모델을 시스템에 통합하는 도구.
   - **주요 제공자**: Flowise 등.

6. **특화된 AI 서비스**:
   - **정의**: 특정 분야에 맞춘 AI 솔루션.
   - **주요 제공자**: Gemini, Groq, IPEX-LLM.

Continue는 다양한 모델 유형과 Provider를 통해 효율적인 AI 솔루션을 제공하며, 사용자 요구에 맞춘 다양한 AI 기술을 활용할 수 있음.

### 📄 LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

**LLM Completion Options**

LLM의 텍스트 생성 방식을 조정하는 설정들로, 출력 텍스트의 길이, 다양성, 일관성 등에 영향을 미침. 모델마다 지원하는 옵션이 다를 수 있음.

- **stream**: LLM 응답을 점진적으로 받을지 선택.
- **temperature**: 응답의 창의성이나 랜덤성 조정. 값이 높을수록 창의적인 응답.
- **topP**: 생성할 단어를 선택할 때 확률 분포 상위 P%의 단어만 선택.
- **topK**: 응답 생성 시 고려할 후보 단어의 개수 제한.
- **presencePenalty**: 이미 언급한 단어의 재사용 억제.
- **frequencyPenalty**: 특정 단어의 반복 사용 빈도 조절.
- **mirostat**: 응답의 일관성과 품질을 실시간으로 조정.
- **stop**: 응답을 중지할 시점을 지정.
- **maxTokens**: 생성할 수 있는 최대 토큰 수.
- **numThreads**: 생성 과정에서 사용되는 스레드 수 조절.
- **keepAlive**: 요청 없는 경우 모델을 메모리에서 언로드하기까지의 시간.

**커스텀 출력 구조 설정**

**1) Context Provider 커스터마이즈**

LLM에 특정 콘텐츠를 제공하는 기능으로, `@`를 입력하면 콘텐츠 드롭다운을 볼 수 있음. 기본 제공 플러그인 외에도 새로운 context provider를 요청 또는 개발 가능.

context provider 에는 아래의 총 3가지 종류가 존재

- **normal**: 기본 설정.
- **query**: 유저가 텍스트 박스로 입력.
- **submenu**: 유저가 선택할 수 있는 항목 제공.

**2) Prompt 커스터마이즈**

- **Completion Option 설정**: `config.json`을 통해 전역 또는 특정 모델에 대한 설정 가능.
- **Custom Slash Commands**: 자연어로 명령어를 정의하거나 사용자 지정 함수를 작성.

**효과적인 프롬프트 엔지니어링**

프롬프트 디자인의 다양한 전략을 통해 LLM 성능 최적화 가능.

- 질문하기 전 생각 구조화.
- 프롬프트에 페르소나 부여.
- 명확하고 구체적으로 지시.
- 영어로 번역하여 질문.
- 보상 제시.
- 그 외 여러 전략

### 📄 RAG, RAG in continue

**1. RAG 정의 및 중요성**

- **RAG (Retrieval-Augmented Generation)**: LLM이 외부 데이터베이스나 검색 엔진을 사용하여 더 정확하고 최신 정보를 제공하는 방법.
- **문제점**: LLM은 허위 정보, 오래된 정보, 신뢰할 수 없는 출처의 정보 등을 제공할 수 있음.
- **중요성**: 신뢰할 수 있는 정보 소스를 활용하여 사용자 신뢰도를 향상시키고, 비용 효율적이며 최신 정보를 제공.

**2. RAG 작동 방식**

1. **청킹(Chunking)**: 대규모 문서를 작은 청크로 나누기.
   - 방법: 고정 길이, 내용 기반, 재귀적 청킹.
2. **문서 임베딩**: 문서를 벡터로 변환하여 유사도 계산.
3. **검색(Retrieval)**: 입력 쿼리에 맞는 관련 문서 검색.
   - 기술: Sparse Retriever(희소 벡터)와 Dense Retriever(밀집 임베딩).
4. **재정렬(Reranking)**: 검색된 문서 중 가장 관련성이 높은 것을 선택하여 최종 답변 생성.
5. **생성(Generation)**: 최종 선택된 문서 기반으로 응답 생성.

**3. Continue에서의 RAG 활용**

- Continue는 RAG를 활용하여 코드 검색의 정확도를 높임.
- **주요 특징**:
  - 경량화된 로컬 임베딩 모델 사용.
  - BM25 기반 전문 검색과 LLM 기반 저장소 맵 분석 결합.
- **사용 데이터베이스**
  - **관계형 데이터베이스**: SQLite 사용, 인덱싱 및 BM25 알고리즘 기반 검색.
  - **벡터 데이터베이스**: LanceDB, 문서 청크의 임베딩 벡터 저장 및 유사도 검색 수행.
- **주요 단계**
  1. **인덱싱 프로세스**: 문서 전처리 및 임베딩 생성.
  2. **쿼리 프로세스**: 사용자 쿼리 수집 및 유사도 기반 검색.
  3. **최종 결과 제공**: 최종 순위에 따라 관련 코드 청크 제공.

**3. Continue에서 Custom RAG**

1. **임베딩 모델**: `voyage-code-2` 추천.
2. **벡터 DB**: `LanceDB` 추천.
3. **청킹 전략**: Truncate, Fixed length, Recursive 등 선택 가능.
4. **인덱싱 스크립트 작성 및 실행**: 데이터를 검색 가능하도록 구조화 및 자동 인덱싱.
5. **서버 설정**: Custom RAG에 접속하기 위한 서버 설정 필요.
6. **리랭킹(옵션)**: `rerank-1` 및 `rerank-2` 모델 사용 가능.

Continue의 Custom RAG는 효과적인 데이터 검색을 구현하고 리랭킹을 통해 검색 결과의 정확도를 높일 수 있는 기능을 제공함.

### 📄 LLM, LLM benchmarks(for code), 선택가이드

**1. LLM (Large Language Model)**

- **정의**: 대규모 딥러닝 모델로 인간 언어 이해 및 생성.
- **주 작업**: 자연어 처리(NLP).

- **CodeLLM :**
- **정의**: 코드 생성 및 자동 완성에 특화된 LLM.
- **주요 기능**:

  - 코드 자동 완성
  - 코드 생성
  - 디버깅 지원
  - 다양한 프로그래밍 언어 지원

- **양자화 (Quantization) :**
- **정의**: 모델의 파라미터를 적은 비트로 표현.
- **유형**:
  - **INT4**: 경량화, 정확도 저하 우려.
  - **INT8**: 더 높은 정확도 유지.

**2. LLM 벤치마크**

- **HumanEval** : 코드 생성 능력 평가
- **MBPP** : 974개의 Python 문제.
- **EvalPlus** : HumanEval 및 MBPP 확장.
- **CodeXGLUE** : 다양한 코드 작업 평가.
- **CRUXEval** : 코드 추론 및 실행 능력 평가.
- **APPS** :고급 프로그래밍 문제 포함.

**3. LLM 선택 가이드**

- **공통 요소** : 가격, 양자화, 코딩 성능

- **Chat 성능 평가 기준** : 한국어 자연어 처리 능력.

- **Autocomplete**

  - 기능: 코드 입력 중 적절한 제안.
  - 모델 추천: Codestral, Starcoder2.
  - Autocomplete 지원 모델 :
    - Codestral: 연구 및 비상업적 무료.
    - StableCode: 무료 사용 가능.
    - Starcoder2: 다양한 모델 크기 무료 제공.

- **GPT 계열 모델 사용 제한** : 전문성 부족 및 응답 시간 문제.

- **LLM 선택 시 고려 사항** : 맥락 길이, 성능 평가 기준.

- **Embedding** :

  - 임베딩 모델 정의 :텍스트나 코드를 고정된 크기의 벡터로 변환.
  - 주요 특징 : 차원 축소 및 의미 보존.
  - 활용 : 유사도 검색, 분류 및 추천.

- **Rerank** :
  - Continue에서 Rerank 사용 : @codebase: 코드베이스 인덱싱 및 관련성 분석.
  - Reranker 필요한 요소 : 문맥 파악 능력, 속도, 코딩 능력.
  - Reranker 모델 추천 : Voyage AI의 rerank-1 모델 추천.
