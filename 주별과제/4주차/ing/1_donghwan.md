## 1. RAG(검색 증강 생성) 개요

RAG(Retrieval-Augmented Generation)는 LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법입니다.

## 2. LLM의 기존 문제점

1. 답변이 없을 때 허위 정보를 제공(환각)합니다.
2. 사용자가 구체적이고 최신의 응답을 기대할 때 오래되었거나 일반적인 정보를 제공
3. 신뢰할 수 없는 출처로부터 응답을 생성합니다.
4. 용어 혼동으로 인해 응답이 정확하지 않습니다.
   다양한 훈련 소스가 동일한 용어를 사용하여 서로 다른 내용을 설명합니다.

## 3. RAG 중요성

1. **신뢰할 수 있는 정보 소스 활용**: 검증된 외부 자료를 사용하여 응답의 신뢰성을 높입니다.
2. **사용자 신뢰도 향상**: 정확하고 최신의 정보를 제공함으로써 사용자들의 시스템에 대한 신뢰를 높입니다.

## 4. RAG 장점

1. **비용 효율적 구현**: 전체 모델을 재학습시키는 것보다 외부 데이터를 추가하는 것이 훨씬 저렴합니다.
2. **최신 정보 제공**: 실시간으로 업데이트되는 데이터 소스를 연결하여 항상 최신 정보를 제공할 수 있습니다.
3. **사용자 신뢰 강화**: 응답의 출처를 명확히 제시하여 투명성을 높이고 사용자 신뢰를 강화합니다.
4. **개발자의 제어력 향상**: 개발자가 정보 소스를 직접 관리하고 조정할 수 있어 응답의 품질을 더 잘 제어할 수 있습니다.

## 5. RAG 주요 개념

0. **외부 데이터 생성**: 다양한 소스에서 데이터를 수집하고, 이를 벡터 형태로 변환하여 저장합니다.
1. **질의 생성(Query Generation)**: 사용자 입력을 기반으로 검색에 적합한 질의를 생성합니다.
2. **정보 검색(Retrieval)**: 생성된 질의를 사용하여 데이터베이스나 인터넷에서 관련 정보를 검색합니다.
3. **응답 생성(Answer Generation)**: 검색된 정보를 컨텍스트로 사용하여 최종 응답을 생성합니다.

### 간단한 흐름

![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkwB8j%2FbtsE1FuVwnW%2FQKl0qx50wltwWi6BcKDNvK%2Fimg.png)

### 조금 더 자세한 흐름

![aws-diagram.png](https://docs.aws.amazon.com/images/sagemaker/latest/dg/images/jumpstart/jumpstart-fm-rag.jpg)

> #### 용어
>
> ##### Prompt
>
> LLM의 정확도를 올리기 위하여 사용자의 쿼리를 받아서 다양하게 재구성.
> LLM의 직접적인 최종 input
>
> ##### Query
>
> 사용자가 입력하는 raw 텍스트

## 6. + RAG 단점

- **계산 비용**: 검색 과정이 추가되어 응답 생성 시간이 늘어날 수 있습니다.
- **검색 품질 의존성**: 검색 결과의 질이 전체 시스템의 성능에 큰 영향을 미칩니다.

## 7.참고 사이트

- [aws RAG 설명](https://aws.amazon.com/ko/what-is/retrieval-augmented-generation/)

- [저번 주 호준님 조사 내용](https://github.com/ossca-24-continue/continue-mentoring/blob/main/%EC%A3%BC%EB%B3%84%EA%B3%BC%EC%A0%9C/3%EC%A3%BC%EC%B0%A8/ing/2-2_hojoon.md#rag%EA%B2%80%EC%83%89-%EC%A6%9D%EA%B0%95-%EC%83%9D%EC%84%B1--continue-chat-%EC%9D%98-%EC%A3%BC%EC%9A%94-%EA%B8%B0%EB%8A%A5)
- [LLM, RAG 용어 참고한 블로그](https://velog.io/@hyunku/%EC%9A%A9%EC%96%B4%EC%A0%95%EB%A6%AC-%ED%97%B7%EA%B0%88%EB%A6%AC%EB%8A%94-%EC%9A%A9%EC%96%B4-%EC%A0%95%EB%A6%AC)
