# Continue란?

코딩 어시스턴트 익스텐션으로, 사용자가 AI 모델을 커스터마이징할 수 있는 점이 특징

# Continue의 제공 기능

- 코드 자동 완성 : 타이핑하는 동안 실시간으로 인라인 코드 제안을 제공
- AI 채팅 : AI와 대화하며 코드 설명이나 문제 해결법을 물어볼 수 있음
- 수정 : 코드 라인을 선택 후 수정 방식을 작성해서 편리하게 수정 가능
- 액션 : 단축어 기능. 슬래시 커맨드로 간편하게 지시를 내릴 수 있음

# 연동 가능한 플랫폼

- Anthropic, OpenAI, Mistral, Cohere 등 모델 개발 회사
- Azure OpenAI, Amazon Bedrock, AWS SageMaker 등 클라우드 AI 서비스
- HuggingFace Inference Endpoints, DeepInfra, Together 등 AI 모델 배포/서버리스 플랫폼
- Ollama, LlamaCpp 등 로컬 AI 실행 도구
- Flowise, Kindo, Msty 등 AI 워크플로우 및 통합 도구
- Groq, IPEX LLM 등 특수 AI 서비스

# LLM이란?

대용량의 매개변수를 통해 인간의 언어를 이해하고 생성할 수 있는 대규모 딥러닝 언어 모델

## LLM 선택 기준

가격, 양자화, 코딩 성능, 자연어 처리 능력 등

- 양자화 : 모델의 파라미터를 더 적은 비트로 표현하여 모델 크기를 줄이고 추론 속도를 향상시키는 기법

## LLM 벤치마크

LLM을 다양한 작업에서 성능을 평가하기 위해 사용하는 표준화된 테스트 모음. 다음과 같은 벤치마크들이 있음

### 코딩 성능 벤치마크

- HumanEval : 코드 생성 능력을 평가하는 벤치마크. 자연어 프롬프트와 테스트 케이스로 구성
- MBPP : 974개의 파이썬 프로그래밍 문제로 구성된 벤치마크
- EvalPlus : HumanEval과 MBPP를 확장한 벤치마크. 복잡한 상황에서의 성능 검증 가능
- CodeXGLUE : 코드 생성, 요약, 검색 등 다양한 코드 관련 작업을 평가하는 포괄적인 벤치마크 세트
- CRUXEval : 코드 추론, 이해 및 실행 능력을 평가하는 벤치마크
- APPS : 고급 프로그래밍 문제를 포함하는 벤치마크

### 한국어 위주 자연어 처리 벤치마크

- Ko-IFEval : 정보 추출 모델의 능력을 평가하기 위한 지표
- Ko-GSM8k : 한국어로 수학 문제 해결 능력을 평가
- KorNAT-SVA : 한국어 문장의 구조적 이해를 평가하는 지표

### FIM 능력을 판단하는 벤치마크

- SAFIM, HumanEvalFIM

## **LLM Completion Options**

언어 모델이 텍스트를 생성하는 방식을 조정하는 설정.
출력되는 텍스트의 길이, 다양성, 일관성 등에 영향을 미침

# **효과적인 프롬프트 엔지니어링**

사용자는 프롬프트 디자인의 다양한 전략과 기법을 통해 효과적으로 질문함으로써, LLM의 성능을 최적화하여 더 나은 응답 결과를 도출할 수 있음

다음과 같은 전략이 있음

- 질문할 때 생각의 연결고리(Chain of Thoughts)를 사용하게끔 단계적으로 대답을 유도
- 프롬프트에게 페르소나 부여
- 명확하고 구체적으로 지시(포맷과 방법 명시)
- 영어로 번역해서 질문
- 구분 기호 사용

# RAG

LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법

실시간 정보에 접근 가능 + 효율적인 메모리 사용이 가능하다는 장점

## RAG의 주요 단계

- Chunking : 대규모 문서를 작은 단위로 나누는 과정
- Document Embedding : 문서를 벡터로 변환하여 문서 간의 유사도를 쉽게 계산할 수 있게 함. 임베딩된 문서는 Vector DB에 저장
- Retrieval : 검색 단계. 입력 쿼리와 관련된 문서나 청크를 검색. 앞서 생성된 임베딩 벡터를 기반으로 쿼리와 문서 간의 유사도를 계산하여 가장 관련성이 높은 문서를 선택
- Reranking : 검색된 문서 중 가장 관련성 높은 것들을 선별하는 과정. 임베딩 유사도 계산 이외에 문서의 맥락, 텍스트 길이 등 다양한 요소를 고려하여 실행
- Generation : 선택된 문서를 기반으로 LLM이 답변을 생성하는 단계
