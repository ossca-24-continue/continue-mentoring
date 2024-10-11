# 3, 4주차 과제 인덱스

## AI 코딩 어시스턴트

- Github Copilot
- CodeWhisperer (Amazon)
- Codex(OpenAI)

## Continue Basic

- Chat: AI와 대화하며 코딩 질문이나 명령을 입력하여 실시간 피드백과 도움을 받을 수 있는 기능.
- Autocomplete: 코드 작성 중에 AI가 자동으로 코드를 완성해 주어 개발 속도를 높여주는 기능.
- Edit: 작성된 코드를 AI가 분석하여 수정할 부분을 제안하거나 코드 구조를 개선하는 기능.
- Actions: 채팅 창에서 코딩 작업을 자동화하거나 반복적인 작업을 줄여주는 명령형 기능. (e.g. `/edit`, `/comment`)

## Model Provider

- Anthropic
- Azure OpenAI
- Amazon Bedrock
- DeepSeek
- Gemini
- Mistral
- Ollama
- OpenAI

## LLM Basic

- LLM: 대용량의 데이터 셋(매개변수)를 통해 인간의 언어를 이해하고 생성할 수 있는 대규모 딥러닝 언어 모델
- `@`로 Context 제공 가능(e.g. `@@codebase`: 코드베이스 내용을 제공)

## RAG

- RAG: RAG(Retrieval-Augmented Generation)는 LLM이 자체 지식 기반 외에도 외부 데이터베이스나 검색 엔진을 활용하여 더 정확하고 최신의 정보를 제공하는 방법

## LLM for Code

- Chat 추천 모델: Claude Sonnet 3.5 from Anthropic / (로컬) Starcoder2-3B with Ollama.
- Autocomplete 추천 모델: Codestral through the Mistral API / (로컬) Llama3.1 405B
- Edit 추천 모델: Chat 모델과 동일
- Actions 추천 모델: Chat 모델과 동일
- Embedding 추천 모델: voyage-code-2 / (로컬) nomic-embed-text with Ollama
- Reranking 추천 모델: rerank-1 by Voyage AI

## 컨트리뷰션 아이디어

아이디어: Continue 공식 문서의 리랭킹 모델 rerank-1 추천을 rerank-2로 변경

리랭크 모델에서 continue 공식 문서에서는 Voyage AI의 rerank-1 모델을 추천함.

> If you have the ability to use any model, we recommend rerank-1 by Voyage AI,

https://docs.continue.dev/customize/model-types/reranking

그런데 Voyage AI 에서는 rerank-2 모델을 추천함.

> The following are our earlier models, which are still accessible from our API. We recommend using the new models above for better quality and efficiency. Our latest models listed in the above table will be strictly better than the legacy models in all aspects, such as quality, context length, latency, and throughput.

https://docs.voyageai.com/docs/reranker
