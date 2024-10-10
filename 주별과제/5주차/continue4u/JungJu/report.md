# 3주차

## Coding Assistant란?

### 정의

말 그대로, 코딩을 도와주는 툴

사실 설계를 제외하면 코딩은 반복적인 작업이긴 함.

때문에, 개발자가 진짜 머리를 써야 하는 작업 외를 자동화하는 데에 Coding Assistant의 본질적 효능이 있음.

그 중, AI Coding Assistant는 AI를 활용하여, 개발자가 코드를 짜는 데에 여러 종류의 도움을 주는 것을 이야기 함.

생산성 향상, 오류 감소, 비용 절감 등의 이점이 있으며, 요즘은 도입하는 기업들 역시 늘어나는 추세

### 종류

- AWS Q : AWS와의 연계가 좋음. indivisual에게 무료
- Github Copilot : 메이저, 한 달에 10$. Github 기반으로 학습하여 코드의 퀄리티 좋음, 인라인 코드 완성 좋음, workspace기능이 약점
- Cursor : VScode를 기반으로 만든 ‘편집기 프로그램’. workspace 기능이 장점, 폐쇄형 LLM 사용 불가

### Continue의 특징

- 자유도 : 다른 Coding Assistant가 모델의 제한이 있는 반면, Continue는 사용자가 원하는 모델을 얼마든지 자유롭게 선택할 수 있음
- 커스터마이징 : 기능을 사용자가 원하는대로 수정하여 사용 가능
- 무료 : 오픈 소스 프로젝트인 만큼, 무료임.(LLM 사용비용은 별도)

## Conitnue의 기능들

### Chat

GPT, Cluade를 위해 창을 열어서 했어야 하는 질문이 IDE 안으로 편입된 기능.

chat box를 기반으로 LLM 모델에게 다양한 질문을 할 수 있음

### Autocomplete

말 그대로 자동 완성 기능

키보드에서 손이 떨어진 이후 일정 시간 이후 자동으로 빈 코드를 채워줌

항상 reliable code가 나오는 건 아니기 때문에, 다양한 filtering 수단이 있으며, config에서 다양한 요소들을 사용자 개인화 가능

### Edit —> Contribution Idea : Edit 사용 중에도 RAG가 가능하게?

간단한 수정 기능.

에디터 페이지 안에서 수정과 삭제가 모두 일어남

다만, Context의 한계 등이 있음으로 너무 많은 범위의 수정은 No.

다양한 Context를 주지 못한다는 점 때문에 자주 쓰지 않음

### Actions

단축키 기능이라 생각하면 됨

다양한 기능을 slash를 통하여 사용 가능함

Prompt를 만들어, 사용자에게 특화된 Action을 만들어 사용가

# 4주차

## Continue를 더 잘 쓰려면?

### 상황에 맞는 Model 선택

Chat, Autocomplete만 해도 더욱 좋은 효율을 보여주 모델이 따로 있음.

Chat은 다국어 지원 및 문맥 파악이 더욱 중요할 것이고, Autocomplete는 FiM 성능이나 코드의 신뢰도 및 속도가 더욱 중요할 것.

때문에, 이러한 다양한 요소(비용, 속도, 사이즈, 벤치마크)들을 고려하여 사용자 개인에게 적합한 모델을 찾는 것이 중요하며.

이 과정에서 사용자에게 효과적인 모델을 찾는 데에 다양한 Benchmark를 활용할 수 있음.

- 벤치마크 예시 : HumanEval(코드 생성 능력 평가), MBPP(프로그래밍 문제 시험), CRUXEval(코드 추론, 이해 능력 평가)
- 간단한 추천 모델
    1. Chat : Sonnet, Llam3.1 405B 등
    2. Codestral : codestral, starcoder2-3B 등
    3. Embedding Model : voyage의 Code2 , Upstage의 Solar-embedding-1, all-MiniLM-L6-v2 등
    4. Reranker : voyage의 rerank-1 , bge-reranker, cohere의 reranker 등

### 효과적인 Prompt 짜기

- LLM에게 효과적인 답변 듣는 법 : LLM의 답변 품질 세팅하기 or Prompt 잘 쓰기 or RAG
    1. LLM 답변 세팅
        1. stream : 답변을 streaming으로 받기
        2. topP : 확률 분포 상위 P% 이상의 답변만 받음
        3. topK : 후보 단어의 개수 제한. 적을수록 예측가능 답변 많을수록 다양한 답변
        4. 단어 재사용 빈도수 조절
        5. 이외에도 mirostat, maxTokens, ContextLength 등의 설정값이 있음
    2. 프롬프트 엔지니어링
        1. CoT : 생각의 사슬 구조를 통해 논리 전개를 차근차근 제시하여 LLM의 추론 성능 향상 가능
        2. 페르소나 부여 : 모델에게 역할을 부여하여 좀더 Specific 답변 획득 가능
        3. 명확하고 구체적인 지시
        4. 조상 제시하기
        5. 영어로 질문
        6. 이 외에도 추가적인 대화, 수정 요청, 특정 문구 제시 등이 있음
        

### RAG 시스템 도입

RAG란? Retrieval-Augmented Generation의 약자로 모델이 자체 학습 데이터 외에도 활용할 수 있는 추가적인 지식을 제공하는 방법.

환각, 오래된 정보 제공, 출처 미상의 정보 제공 등 기존 LLM이 가진 문제를 해결할 수 있는 좋은 방안임

추가로, 모델의 재학습을 하지 않고 추가적인 정보 제공이 가능하기에 비용 효율적이기도 함

https://camo.githubusercontent.com/8b1b94f401aba8f7af5fce5b3d86340105ea17847f161b196770403eb0651ca7/68747470733a2f2f696d67312e6461756d63646e2e6e65742f7468756d622f523132383078302f3f73636f64653d6d746973746f72793226666e616d653d6874747073253341253246253246626c6f672e6b616b616f63646e2e6e6574253246646e2532466b7742386a2532466274734531467556776e57253246514b6c3071783530776c747757693642634b444e764b253246696d672e706e67

<간단한 RAG 시스템의 구조도>

**RAG in Continue**

Continue에서는 @codebase / @folder 를 통해 RAG시스템을 지원함

그 과정에서 알맞은 임베딩, 리랭크 모델을 선정하여 답변의 퀄리티를 높일 수 있음

**사용법**

1. 코드 베이스에 대한 분석 및 질문
2. 기존 샘플 활용 질문
3. @folder를 활용한 특정 스페이스에 대한 질문

**비추천**

1. 코드 베이스의 모든 파일에 대한 정보 요청
2. 리팩토링
