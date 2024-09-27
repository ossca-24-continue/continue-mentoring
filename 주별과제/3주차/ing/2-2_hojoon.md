# Continue의 Chat

# LLM 학습하기

1. **데이터 수집**:
    - **다양한 출처**: 인터넷 크롤링, 전자 도서, 뉴스 기사, 학술 논문, 소셜 미디어 등에서 데이터를 수집합니다.
    - **언어 다양성**: 여러 언어와 다양한 도메인의 텍스트를 포함하여 모델의 범용성을 높입니다.
2. **데이터 전처리**:
    - **토큰화(Tokenization)**: 텍스트를 단어 또는 부분 단위로 분할하여 모델이 처리할 수 있는 형태로 변환합니다.
    - **어휘 사전 구축**: 모델이 인식할 수 있는 단어 또는 토큰의 집합을 만듭니다.
    
    (일반적인 우리가 생각하는 단어 뿐만 아니라, 자주 쓰이는 문장 같은 것을 하나의 토큰 단위로도 만들 수 있습니다.)
    
3. **모델 학습**:
    - **트랜스포머 아키텍처**: 셀프 어텐션 메커니즘을 활용하여 문맥 정보를 효과적으로 학습합니다.
    - **언어 모델링**: 다음 단어 예측(Next Token Prediction) 또는 마스킹된 단어 복원(Masked Language Modeling)을 통해 언어 패턴을 학습합니다.
        
        → 이런 방법이기에 Pretrain만 되어있는 LLM 은 다음 단어만 예측할 수 있습니다. input으로 들어간 문장의 다음 것을 자연스럽게 이어주도록 예측하는 것입니다.
        (다음 단어를 예측한 것을 사용해서 계속 예측하고, 최종으로 End 토큰이 나올 때까지 계속 예측)
        
4. **미세 조정(Fine-tuning)**:
    - **특정 태스크에 맞춘 조정**: 질의 응답, 번역, 요약 등 특정 작업에 맞게 추가로 학습합니다.

## LLM을 챗봇으로 쓰기 위해서는?

LLM을 효과적인 챗봇으로 활용하기 위해서는 단순한 언어 생성 능력 외에도 사용자와의 상호작용을 원활하게 하는 추가적인 요소들이 필요합니다:

1. **대화 데이터로 미세 조정**:
    - **대화형 데이터셋 사용**: 오픈도메인 대화 데이터나 특정 도메인의 대화 데이터를 활용합니다.
    - **역할 부여**: 사용자와 챗봇의 역할을 명확히 정의하여 모델이 적절한 응답을 생성하도록 합니다.
2. **컨텍스트 유지 및 관리**:
    - **대화 히스토리 추적**: 이전 발화들을 저장하여 모델 입력에 포함시킵니다.
    - **세션 관리**: 각 사용자별로 대화 세션을 관리하여 개인화된 경험을 제공합니다.
    - **기억 능력 확장**: 장기 대화에서도 일관성을 유지하기 위해 메모리 네트워크나 외부 저장소를 활용합니다.
3. **안전하고 윤리적인 응답 생성**:
    - **필터링 및 검열**: 부적절하거나 유해한 콘텐츠를 생성하지 않도록 필터링 메커니즘을 적용합니다.
    - **편향 제거**: 데이터 편향으로 인한 불공정한 응답을 최소화하기 위해 알고리즘적 조정을 합니다.
    - **윤리 가이드라인 준수**: 사회적, 문화적 규범에 맞는 응답을 생성하도록 지침을 설정합니다.
    
    (이런 것들을 무시하기 위해 탈옥 프롬프팅과 같은 여러 시도를 하는 경우도 있습니다.)
    

## Multi-turn의 중요성…

**Multi-turn 대화**는 사용자와 챗봇 간의 여러 차례에 걸친 상호작용을 의미하며, 자연스럽고 유의미한 대화를 위해 필수적입니다. 그 중요성과 구현 방안은 다음과 같습니다:

1. **컨텍스트 이해 및 유지**:
    - **참조 해소**: 이전 발화에서 언급된 대상이나 정보를 정확히 파악합니다.
    - **주제 전환 처리**: 대화 중 주제가 바뀌더라도 일관성을 유지합니다.
    - **암시적 정보 추론**: 직접적으로 언급되지 않은 정보도 문맥을 통해 이해합니다.
2. **대화 흐름 관리**:
    - **대화 상태 추적(Dialogue State Tracking)**: 사용자 의도와 슬롯 값을 추적하여 대화의 목표를 달성합니다.
    - **대화 정책(Dialgue Policy)**: 다음에 어떤 행동이나 응답을 할지 결정하는 정책을 수립합니다.
    - **에러 처리 및 복구**: 오해나 오류가 발생했을 때 적절히 수정하고 대화를 이어갑니다.
3. **기술적 구현**:
    - **메모리 메커니즘**: RNN, LSTM, Transformer 등 모델의 구조를 활용하여 장기 의존성을 처리합니다.
    - **외부 메모리 사용**: Neural Turing Machine이나 Memory Network를 통해 더 긴 컨텍스트를 유지합니다.
    - **요약 및 압축**: 중요한 정보를 요약하여 모델 입력의 길이 제한을 극복합니다.

## RAG(검색 증강 생성) ← Continue Chat 의 주요 기능

- 검색 증강 생성(Retrieval-Augmented Generation)은 LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법입니다.
1. **개념 및 필요성**:
    - **지식 한계 극복**: LLM은 학습 시점 이후의 정보나 특정 도메인 지식이 부족할 수 있습니다.
    - **정확성 향상**: 외부 데이터를 참고하여 사실 기반의 응답을 제공합니다.
    - **업데이트 가능성**: 실시간으로 변화하는 정보를 반영할 수 있습니다.
2. **구성 요소**:
    - **질의 생성(Query Generation)**: 사용자 입력을 기반으로 검색에 적합한 질의를 생성합니다.
    - **정보 검색(Retrieval)**: 생성된 질의를 사용하여 데이터베이스나 인터넷에서 관련 정보를 검색합니다.
    - **응답 생성(Answer Generation)**: 검색된 정보를 컨텍스트로 사용하여 최종 응답을 생성합니다.
3. **장점**:
    - **사실 검증**: 생성된 응답의 정확성을 높입니다.
    - **범용성**: 다양한 주제와 도메인에 적용할 수 있습니다.
    - **효율성**: 필요한 정보만 검색하여 처리하므로 연산 자원을 절약합니다.

![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkwB8j%2FbtsE1FuVwnW%2FQKl0qx50wltwWi6BcKDNvK%2Fimg.png)

---

# Continue - Context Provider

Context Provider는 사용자가 생각하는 대부분의 것을 RAG의 형태로 chat의 Input으로 넣을 수 있습니다!

### @codebase

코드 베이스에 있는 모든 파일을 Indexing 해서 저장을 하고, 유저의 프롬프트에 따라 필요한 파일을 찾아와 함께 context로 입력으로 주어 더 정확한 답변을 생성해냅니다.

코드베이스로 들어가는 문서의 양이 많기 때문에 문서들을 embedding을 하여 vectorDB에 저장한 뒤, 사용자가 입력한 프롬프트와 비교하여 찾아오는 과정이 필요합니다. 그렇기 때문에 만약 프롬프트가 부정확하다면 적절하지 못한 파일을 찾아 올 수도 있습니다.

이럴 때에는 @Foler, 또는 더 세밀하게 @open 을 사용하면 됩니다!

(@Foler 은 한 폴더를 지정, @open은 한 파일을 지정하여 Context로 넣게 만들어주는 과정입니다.)

EX) 이런 질문을 할 수 있게 됩니다!

"서버에 새 엔드포인트를 어떻게 추가하나요?" 

"VS Code의 CodeLens 기능을 어디에서나 사용할 수 있나요?" 

"HTML을 마크다운으로 변환하기 위해 이미 작성된 코드가 있나요?”

### @**URL**

내 파일에 있는 것 뿐만 아니라 온라인 상에 있는 자료도 context에 넣고 싶다면 이 context provider을 사용하면 됩니다. URL 상에 있는 자료들을 markdown의 형태로 변환하여 context에 함께 들어가게 됩니다.

비슷하게 @google을 사용하게 된다면 구글 검색 엔진을 통해 나온 결과를 context에 포함하게 됩니다.

### @**GitHub Issues**

Github에 올라와 있는 Issues 들도 함께 context로 넣을 수 있습니다.

비슷하게 @**GitLab Merge Request @Jira Issues 도 있습니다.**

그 밖의 Context provider도 많습니다.

[https://docs.continue.dev/customize/context-providers](https://docs.continue.dev/customize/context-providers)

---

# Prompt Files: Customizing

**Prompt Files 개요**

Prompt Files는 Continue 환경에서 프롬프트를 쉽게 관리하고 사용자 맞춤형 모델을 만드는 기능을 제공합니다. 이를 통해 모델이 어떻게 행동하는지를 결정하는 프롬프트를 저장하고 수정할 수 있습니다. Prompt Files는 JSON 형식의 파일로 작성되며, 다양한 매개변수를 통해 대화형 모델의 동작을 세부적으로 제어할 수 있습니다.

**Prompt Files의 활용**
Prompt Files는 특히 특정 사용 사례에 맞춘 맞춤형 대화를 설계하거나, 특정 행동 양식을 구현할 때 유용합니다. 예를 들어, 프롬프트 파일을 사용해 특정 대화 스타일(페르소나 설정)을 유지하거나 특정 주제에 대한 모델의 집중도를 높이는 데 사용할 수 있습니다.

EX- 모든 답변을 한글로 하라는 명령을 통해, 굳이 한 번 더 “한글로 번역해줘”와 같은 수고를 덜 수 있습니다.

사용법

1. 작업 공간의 최상위 수준에 .prompts/라는 폴더를 만듭니다. 
2. 이 폴더에 test.prompt라는 파일을 추가합니다. 이 파일의 이름은 프롬프트를 생성하는 데 사용할 slash Command의 이름이 됩니다. ( /test 라고 입력창에 넣으면 기본 프롬프트가 들어가게 됩니다.)
3. test.prompt에 내용을 작성하고 저장합니다.

```
temperature: 0.5
maxTokens: 4096
---
<system>
You are an expert programmer
</system>

{{{ input }}}

Write unit tests for the above selected code, following each of these instructions:
- Use `jest`
- Properly set up and tear down
- Include important edge cases
- The tests should be complete and sophisticated
- Give the tests just as chat output, don't edit any file
- Don't explain how to set up `jest`
```

---

# Slash commands

위에서 언급된 사전에 정의 된 Prompt입니다. 

```
{
  "name": "edit",
  "description": "Edit highlighted code"
},
{
  "name": "comment",
  "description": "Write comments for the highlighted code"
}
```
