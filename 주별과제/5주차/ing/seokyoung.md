## Contribution Idea (팀 과제)

### 1. [공식 문서](https://docs.continue.dev/customize/tutorials/build-your-own-context-provider) 예제 코드 개선

#### 동기

`type:submenu` 예제 코드 적용 시 어려움이 있었습니다. 유사한 상황이 다른 유저들에게도 충분히 있었던 것으로 보이고 해당 유틸 함수가 IDE 내에서 제거된 것으로 보여 이에 맞게 문서를 업데이트하는 것이 좋을 것이라고 판단했습니다.

![seokyoung-01.png](./image/seokyoung-01.png)

#### 목적

- 다른 사용자의 continue 학습 편의성 개선
- 빠르게 업데이트되는 프로덕트에 맞춘 공식 문서 업데이트

#### 주요 내용

제거된 `listWorkspaceContents` 대신 `getWorkspaceDir`를 사용해 `type:submenu` 예제 코드 정상 출력

| as-is                                         | to-be                                         |
| --------------------------------------------- | --------------------------------------------- |
| ![seokyoung-02.png](./image/seokyoung-02.png) | ![seokyoung-03.png](./image/seokyoung-03.png) |

### 2. Custom Context Provider

워크스페이스 안에서 `config.ts`로 이동 및 기본 가이드가 워크스페이스 내에서 동작하는 기능

#### 동기

Action(`/`)의 경우 드롭다운 최하단의 `Build a custom prompt`를 클릭 시 바로 `./prmopts`가 만들어지며, prompt 커스텀을 위한 기본 가이드가 자동으로 세팅됩니다.

![seokyoung-04.png](./image/seokyoung-04.png)

Context(`@`)의 경우 드롭다운 최하단에 `Add more context providers`가 있지만 클릭하면 공식문서로 넘어가게 됩니다.

![seokyoung-05.png](./image/seokyoung-05.png)

개인적으로 코드 작업 시 화면 스위칭이 없다는 점이 Continue를 사용했을 때 강력한 장점으로 보았기 때문에 Continue 사용 시 최대한 워크스페이스를 떠나지 않는 게 좋다고 봅니다.

이러한 이유로 Context Provider를 커스텀 및 관리를 위한 기능이 드롭다운에 숏컷으로 변경 혹은 추가되었으면 좋겠다고 생각되어 제안합니다.

#### 목적

- Actions의 커스텀 안내 기능과 기능 통일화
- 화면 스위칭 없이 워크 스페이스 작업 유지
- Context Provider 관리 및 커스터마이징 편의

#### 주요 내용

- Context Select에 Custom Context Provider 옵션 추가
- `config.json` 혹은 `config.ts`로 바로 이동
- 빌트인 / 커스텀 구분해서 이동이 필요할 수도 있음

## Review (개인 과제)

### AI 코딩 어시스턴트

> [!NOTE]
>
> AI 코딩 어시스턴트는 **인공지능**을 활용하여 **프로그래밍 작업**을 지원하는 도구입니다. 코드 작성, 디버깅, 코드 리뷰, 문서 생성 등 개발 프로세스의 다양한 측면을 주요 사용자인 개발자에게 도움을 줍니다.
>
> AI 코딩 어시스턴트의 예로는 GitHub Copilot, Cursor, 그리고 Continue와 같은 도구들이 있습니다.

#### AI 코딩 어시스턴트의 장점

- 생산성 향상, 코드 품질 개선, 비용 절감

### Continue의 특징 및 장점

#### 특징

오픈소스 기반으로 사용자가 선택한 LLM 모델을 연동해 맞춤형 AI 코딩 경험을 제공

> 즉, 커스터마이징이 용이합니다.

#### 장점

- **자동완성**: 코드 작성 시 실시간 제안 제공
- **리팩토링**: 코드 개선 및 중복 제거 작업 지원
- **코드 분석**: 코드 내 문제점을 파악하고 수정 방법 제안
- **다양한 LLM 사용 가능**: 사용자의 필요에 맞춰 다양한 AI 모델을 연동 가능

### Chat

- Chat 기능을 통해 코드를 작성하는 IDE를 떠나지 않고 LLM과 대화를 할 수 있음 → 화면 스위칭이 줄어들어 개발 시 효율적
- 원하는 Context를 전달하여 제공 가능 - `@`

### Autocomplete

- 개발자의 코드를 이해한 뒤, 자동완성으로 코드를 인라인으로 제안
- Timing: 요청 수를 줄이기 위해, 사용자가 입력을 마칠 때까지 대기하며 이전에 생성된 완성을 재사용
- Context: 코드베이스에서 관련 스니펫을 찾기 위해 여러 검색 방법을 사용
- Filtering: 높은 응답의 품질을 위해 특수 토큰을 제거하고 들여쓰기를 수정하는 등 사후 처리 작업 수행

### Edit

- 코드 블록을 하이라이팅하고 변경 사항을 설명하면, 수정된 내용을 파일에 인라인으로 제안
- 수락 혹은 거부를 통해 코드 적용 가능
- 간단하고 빠른 작업에 권장(주석 추가, 유닛 테스트 생성, 함수 리팩토링 등)

### Actions

- 자주 사용하는 작업을 숏컷 형태로 빠르게 호출하는 기능
- 반복적인 작업에 추천하며, `/`를 사용하여 호출
- Continue에서 기본적으로 제공하는 빌트인 Actions도 있고, 커스터마이징도 가능

### Continue 모델 유형

#### Autocomplete Model

- 중간 채우기(FIM) 기법으로 훈련된 특수한 언어 모델
- Continue에서 가장 권장하는 모델은 Mistral의 Codestral
- 로컬 모델로는 Ollama Provider와 함께 Starcoder2-3B 모델 권장

#### Chat Model

- 대화 형식에 응답하도록 훈련된 LLM
- 질문에 답하고 복잡한 코드를 짜야하기 때문에, 좋은 성능의 모델 필요
  - 파라미터 400B+ 추천
- 가장 추천하는 모델은 Claude 3.5 Sonnet
- GPT-4o, Gemini 1.5 Pro, Llama-3.1-405B 또한 권장

#### Embeddings Model

- 텍스트를 벡터값으로 변환해 텍스트 간의 유사도를 비교할 수 있게 해주는 모델
- 임베딩 모델은 일반적으로 LLM보다 훨씬 작은 모델이며, 따라서 비교적으로 매우 빠르고 비용이 저렴
- 어떤 모델이든 쓸 수 있다면 voyage-code-2를 추천
- 로컬 환경에서 임베딩을 생성하고 싶다면 Ollama와 함께 nomic-embed-text를 사용하는 것을 권장

#### Reranking Model

- 검색 결과를 다시 정렬하는 데 사용
- 기본 검색 시스템이 결과를 제공한 뒤에 모델이 관련성을 평가해, 가장 적합한 결과를 다시 상위에 배치하는 역할
- Continue 플랫폼에서는 `@codebase` 기능에서 리랭킹 모델을 사용
- 어떤 모델이든 사용할 수 있다면, Voyage AI의 rerank-1을 추천
- 혹은 Cohere에서 제공하는 리랭킹 모델을 사용 가능
- 다만, 로컬 모델에서는 사용할 수 없음 → 많은 병렬 요청 수행이 필요하기 때문

---

### LLM Completion Options

> [!NOTE]
>
> **언어 모델이 텍스트를 생성하는 방식**을 조정하는 설정들로, 출력되는 텍스트의 **길이, 다양성, 일관성** 등에 영향을 미칩니다.

#### Continue에서 Completion Options 수정하기

- `config.json`에서 옵션들로 다양하게 수정 가능

### 원하는 구조로 출력 커스텀

#### Context Provider

- 빌트인 Context Provider: `~/.continue/config.json`의 `contextProviders` 에 추가
- 커스텀 Context Provider: `normal`, `query`, `submenu` 타입을 정해서 목적에 맞게 커스터마이징 가능

#### Prompt

- 기본적으로 Continue에서 제공하는 `config.json`의 `completetionOptions`로 설정 가능
- `.prompt` 파일을 생성해 시스템에 직접 프롬프트를 전달

---

### **RAG(Retrieval-Augmented Generation)**

> [!NOTE]
>
> LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법입니다.
>
> LLM의 기존 문제점인 최신의 정보를 제공하지 못하거나, 허위 정보를 제공하는 환각 현상을 보완할 수 있습니다. 비용 또한 LLM을 직접 학습시키는 방법과 비교하면 적게 듭다.

### RAG in Continue

> Continue는 주로 `@codebase` 검색 시 RAG를 사용합니다.

- 경량화된 로컬 임베딩과 RAG
- 필요에 따라 NLP로 Reranking 보완 (BM25, Repo Map)
- LLM prompt를 이용한 Reranking

### RAG 워크플로 주요단계

1. 인덱싱 프로세스 (문서 전처리)

> 계획 → 파일 청킹 → 임베딩 생성 → 벡터 DB 저장 → 전문 검색 인덱스 생성

2. 쿼리 프로세스

> 사용자 쿼리 접수 → 유사도 검색 → 전문 검색(Full-text Search) → LLM 저장소 맵 → 재순위화 → 최종 결과

---

### LLM(Large Language Model)

> [!NOTE]
>
> LLM은 대용량의 데이터 셋(매개변수)를 통해 인간의 언어를 이해하고 생성할 수 있는 대규모 딥러닝 언어 모델입니다.

- LLM의 주요 작업은 자연어 처리(NLP)
- NLP(Natural Language Processing): 사람들이 사용하는 일상 언어의 의미, 문법, 문맥 등을 컴퓨터가 이해할 수 있는 형식으로 바꾸고 그 의미를 분석하는 과정
- Code-LLM: 코드 생성과 자동 완성에 특화 LLM
- 양자화(Quantization): 모델의 파라미터를 더 적은 비트로 표현하여 모델 크기를 줄이고 추론 속도를 향상시키는 기법

### **LLM 벤치마크(for code)**

- LLM을 다양한 작업에서 성능을 평가하기 위해 사용하는 성능 평가 지표
- 벤치마크 종류
  - HumanEval: 코드 생성 능력을 평가하는 벤치마크
  - MBPP: 974개의 Python 프로그래밍 문제로 구성되어 Code-LLM의 실제 코딩 문제 해결 능력 평가하는 벤치마크
  - EvalPlus: HumanEval과 MBPP를 확장한 벤치마크
  - CodeXGLUE: 코드 생성, 요약, 검색 등 다양한 코드 관련 작업을 평가하는 포괄적인 벤치마크 세트
  - CRUXEval: 코드 추론, 이해 및 실행 능력을 평가하는 벤치마크
  - APPS: 고급 프로그래밍 문제를 포함하는 벤치마크로, 복잡한 문제 해결 능력을 평가

> [!TIP]
>
> #### 선택 가이드
>
> - 가격
> - 양자화(모델 크기나 F1 점수)
> - 코딩 성능
