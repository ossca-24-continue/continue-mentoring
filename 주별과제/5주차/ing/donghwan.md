# ai coding assitant 도구 조사 및 비교 분석, continue의 특,장점 정리

## AI 코딩 어시스턴트 장점

생산성 향상, 코드 품질 개선 ,학습 지원 ,오류 감소 ,협업 강화 , 비용 절감

## 다른 AI 코딩 어시스턴트 도구들

Amazon CodeWhisperer, Codex, Cursor, GitHub Copilot, replit GhostWriter

## Continue 특징

Continue는 VSCode, JetBrains 등의 개발 환경과 통합되어 사용자의 코딩 작업을 지원하는 도구이다. GitHub Copilot과 유사한 기능을 제공하면서도, 완전한 오픈소스 형태로 사용자가 AI 모델을 커스터마이징할 수 있는 점이 특징이다. 주로 코드 자동 완성, 대화형 코드 설명, 자연어 기반 코드 수정 등의 기능을 제공한다.

### 다른 도구와 차별점

- 개발 데이터 수집 : 자동으로 .continue/dev_data 디렉토리에 데이터를 수집해 팀의 AI 어시스턴트를 지속적으로 개선할 수 있습니다.
- 오픈 소스 : 오픈 소스 프로젝트로 운영되는 만큼 커뮤니티의 참여와 지원을 받을 수 있습니다.
- 무료 : Continue는 무료로 제공되어 비용 부담 없이 활용할 수 있습니다.
- 모델 선택의 유연성 : Continue는 연결할 모델을 직접 선택할 수 있어 사용자의 요구사항에 맞춘 솔루션을 만들 수 있습니다.
- 컨텍스트의 다양성 : 대부분의 코드 어시스턴트 도구가 컨텍스트로 제공할 수 있는 데이터가 코드베이스 및 현재 레포지토리의 파일에 한정되어 있는 반면, Continue는 컨텍스트로 다양한 데이터를 선택할 수 있습니다. 여기엔 url, Github/Jira 이슈, 데이터베이스 테이블, 구글 검색 결과 등이 포함됩니다.
- 확장성 : Continue는 높은 커스터마이즈 기능을 제공하여 확장할 수 있는 자유도가 높습니다.

# continue 주요기능

Continue는 오픈 소스 기반의 AI 코드 어시스턴트입니다. 현재 Microsoft의 VSCode와 Jetbrains의 Intellj에서 플러그인 형식으로 다운받고 실행할 수 있습니다.

1. chat : Continue의 Chat 탭에 질문을 넣으면 AI가 해당 질문에 대한 대답을 반환합니다.
2. autocomplete : 자동완성 기능을 제공합니다.
3. Edit: 현재 파일을 벗어나지 않고 IDE 상에서 코드를 편리하게 수정할 수 있습니다.
4. Action : Actions 기능은 단축어 기능과 유사합니다.

# LLM, LLM benchmarks(for code), 선택가이드

## LLM (Large Language Model)

대용량의 데이터 셋(매개변수)를 통해 인간의 언어를 이해하고 생성할 수 있는 대규모 딥러닝 언어 모델

> CodeLLM이란?

- 일반적인 LLM의 개념을 코드 생성과 자동 완성에 특화한 모델
- 다양한 프로그래밍 언어의 코드를 학습해 개발자들에게 코드 자동완성, 버그 수정, 코드 리팩토링, 코드 설명 등의 도움을 줌

- CodeLLM의 주요 기능
- 코드 자동 완성 (Autocomplete) : 작성 중인 코드의 맥락을 이해하고 맞는 코드를 자동 제안
- 코드 생성 : 자연어로 설명된 요구사항에 맞는 전체 코드 생성
- 디버깅 지원 : 코드의 오류를 찾아 수정하거나 코드의 문제점을 분석
- 다양한 언어 지원 : 여러 프로그래밍 언어에 대해 지원

## LLM 벤치마크

LLM을 다양한 작업에서 성능을 평가하기 위해 사용하는 표준화된 테스트 모음 (다양한 상황의 데이터셋을 준비하고 모델이 문제를 읽고 내놓는 답을 평가하는 방법)

### 종류

HumanEval, MBPP, EvalPlus, CodeXGLUE, CRUXEval, APPS

## LLM 선택 가이드

### 공통

가격, 양자화, 모델 크기, F1 점수, 코딩 성능

### Chat

논리 구조 파악 능력과 문제 해결 능력에 초점을 둔 지표가 중요

Ko-IFEval, Ko-GSM8k ,KorNAT-SVA

### Autocomplete

FIM 지원 여부, Latency, 모델의 크기와 정확도

### 임베딩 모델

### Rerank

조금 더 적합한 정보를 찾는 데 사용

문맥파악능력, 속도, 코딩 능력, 한국어 능력이 중요

기본적으로 rerank-1 추천, bge reranker의 경우 한국어 처리 능력이 더욱 좋고 무료

# LLM completion options & continue에서 설정하기, 챗 잘사용하기 - 효과적인 프롬프팅(system, user)

## LLM completion options

언어 모델이 텍스트를 생성하는 방식을 조정하는 설정

## Continue의 completionOptions

```json
"completionOptions": {
  "stream": "boolean",
  "teperature": "number",
  "topP": "number",
  "topK": "integer",
  "presencePenalty": "number",
  "frequencePenalty": "number",
  "mirostat": "number",
  "stop": "string[]",
  "maxTokens": "number",
  "numThreads": "integer",
  "keepAlive": "integer",
}
```

## Continue 원하는 구조로 출력 커스텀

Context Provider를 이용해 LLM에 특정한 콘텐츠를 제공

### 기본으로 제공하는 built-in Context Provider

- `@file`: 현재 워크스페이스의 파일을 context로 제공.
- `@code`: 프로젝트 내 특정 함수나 클래스를 context로 제공.
- `@Git Diff`: 현재 브랜치의 변경 사항을 context로 제공.
- `@terminal`: IDE의 터미널 내용을 context로 제공.
- `@open`: 현재 열려 있는 파일의 내용들을 context로 제공.
- `@folder`: 현재 워크스페이스의 폴더를 context로 제공. @codebase 와 동일한 검색 메커니즘을 사용하지만 단일 폴더에서만 검색할 수 있음.
- `@codebase`: 워크스페이스 전체에서 가장 관련성 높은 콘텐츠를 자동으로 가져올 수 있도록 codebase 를 색인화
- `@url`: 특정 URL의 내용을 markdown 형식으로 context로 제공.
- `@issue`: GitHub issue의 대화를 context로 제공 (개인 접근 토큰 필요).
- `@docs`: Continue에서 문서와 상호작용할 수 있게 해줌. 정적 사이트나 GitHub 페이지를 색인화하여 쉽게 접근 가능.

> Custom Provider를 만들어서 적용 가능

## LLM의 응답의 품질을 더욱 향상시키기

- 질문하기 전 생각 구조화
- 프롬프트에게 페르소나 부여하기
- 명확하고 구체적으로 지시하기
- 영어로 번역해서 질문하기
- 보상 제시하기
- etc..

# RAG, RAG in continue

## RAG

RAG(Retrieval-Augmented Generation)는 LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법

## RAG in continue

- Continue에서 추천하는 모델은 voyage-code-2

- Continue 권장 DB는 LanceDB: 인 메모리 DB

### RAG의 트레이드 오프는

작은 청크는 원본 문서의 의미를 불완전하게 나타낼 수 있음.
청킹 크기를 줄이면 검색 속도가 빨라진다. 하지만 정확도가 떨어질 수 있다.(반대 관계 존재)

# 기여 아이디

1. 프론트엔드 UI 개발 도구 storybook에서 lodash를 토스의 es-toolkit으로 마이그레이션했어요.
   continue에서도 lodash를 사용하고 있는데 es-toolkit으로 마이그레이션하면 좋을 것 같다는 생각이 들었습니다.

[관련 storybook PR](https://github.com/storybookjs/storybook/pull/28981)

2. 전체적으로 테스트 코드가 적다고 느꼈습니다. jest나 vitest를 이용한 유닛테스트부터 react-testing-libaray를 사용한 통합 테스트 코드를 보완하면 좋을 것 같습니다.
