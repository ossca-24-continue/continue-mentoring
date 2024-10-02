#### LLM의 Completion Option이란?
LLM의 Completion Option은 **언어 모델이 텍스트를 생성하는 방식**을 조정하는 설정들로, 출력되는 텍스트의 **길이, 다양성, 일관성** 등에 영향을 미칩니다. **continue**의 config.json 수정을 통해 이를 직접 수정할 수 있습니다.
#### continue의 completionOptions
아래는 continue에서 수정 가능한 옵션들입니다.
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
##### 옵션의 세부 설명
|       name       |   type   | Default |
| :--------------: | :------: | ------- |
|      stream      | boolean  | true    |
|    teperature    |  number  |         |
|       topP       |  number  |         |
|       topK       | integer  |         |
| presencePenalty  |  number  |         |
| frequencePenalty |  number  |         |
|     mirostat     |  number  |         |
|       stop       | string[] |         |
|    maxTokens     |  number  | 600     |
|    numThreads    | integer  |         |
|    keepAlive     | integer  |         |
##### stream
LLM 응답을 stream으로 받는 옵션입니다. `anthroic`에서만 제공됩니다.
##### temperature
온도는 모델이 생성하는 응답의 창의성이나 랜덤성을 조정하는 매개변수입니다. 숫자로 표현되며 일반적으로 0에서 1사이의 값을 가집니다.
##### topP
`topP` 옵션은 LLM에서 생성할 단어를 선택하는 과정에서 확률 분포의 일부를 자르는 방식을 의미합니다.

`topP`는 일반적으로 "누적 확률 기반 샘플링 (nucleus sampling)"이라고 불리며, 확률 분포에서 상위 P%에 해당하는 후보들만 고려한 후 그 안에서 랜덤하게 단어를 선택합니다. 확률이 높은 일부 단어들만 대상으로 하므로, 모델의 출력을 더 제어할 수 있습니다.
###### Example
- **`topP = 1`** 완전 무작위 샘플링을 통해 단어를 생성합니다. 가장 창의적인 응답을 얻을 수 있게 됩니다.
- **`topP = 0.5`** 확률 분포에서 상위 50%에 해당하는 단어들만 선택 대상으로 하고, 그 이하의 확률을 가진 단어들은 무시합니다.
##### topK
`topK` 옵션은 LLM에서 **응답을 생성할 때 고려할 후보 단어들의 개수를 제한하는 옵션**입니다.
###### Example
- **`topK = 1`** 가장 확률이 높은 단어 하나만 선택됩니다. 즉, 모델은 항상 **가장 결정적인** 응답을 생성합니다.
- **`topK = 5`** 확률이 높은 상위 5개의 단어들만 선택 후보에 들어가며, 그 안에서 무작위로 단어를 고릅니다.
- **`topK = 0`** 모든 단어가 선택될 수 있는 완전 무작위 샘플링을 통해 단어를 생성합니다. 이 경우 창의적인 응답을 얻을 수 있지만, 응답이 비논리적이거나 예측 불가능할 수 있습니다.
##### presencePenalty
`presencePenalty` 옵션은 모델이 이미 언급한 단어를 다시 사용하는 것을 얼마나 억제할지 조절합니다. 이 옵션을 통해 **같은 단어를 반복하는 것을 방지하거나 반복하도록 유도**할 수 있습니다.
##### frequencePenalty
`frequencyPenalty` 옵션은 모델이 특정 단어를 얼마나 자주 반복해서 사용할지 조절합니다. 이 옵션을 통해 **단어의 빈도를 억제하거나 허용**할 수 있으며, 모델이 같은 단어나 문구를 반복적으로 사용하지 않도록 제어할 수 있습니다.
##### mirostat
`microstat` 옵션은 **LLM에서 응답의 일관성과 품질을 지속적으로 조정하기 위한 동적 샘플링 알고리즘입니다.** 모델이 생성하는 텍스트의 정보량을 일정하게 유지하면서 질문이나 주제에 적합한 수준의 다양성과 결정성을 지속적으로 조절합니다.

`microstat`은 다른 옵션들(`teperature`, `topK`)과는 다르게 **응답생성과정에서 모델의 출력을 실시간으로 모니터링하고 수정합니다.** 이를 통해 대화의 흐름이나 맥락에 맞춰 **적절한 창의성**을 유지하면서도 **논리적인 응답**을 생성하는 데 도움이 됩니다.

현재 `Ollama`,  `LM Studio`, `llama.cpp`에서만 활용이 가능합니다.
##### stop
`stop` 옵션은 LLM이 **응답을 중지해야 할 시점을 지정**하는 기능입니다. 즉, 모델이 텍스트를 생성하는 도중 **특정 토큰이나 문자열이 등장하면 응답 생성을 중단**하도록 설정할 수 있습니다.
##### maxTokens
`maxTokens` 옵션은 모델이 생성할 수 있는 **최대 토큰 수**를 의미합니다. 이 옵션은 모델이 하나의 프롬프트에 대해 응답할 때 생성할 텍스트의 길이를 제한하는 역할을 합니다.
##### numThreads
`numThreads` 옵션은 생성 과정에서 사용되는 스레드의 수를 조절합니다. `Ollama`에서만 활용됩니다.
##### keepAlive
`keepAlive` 옵션은 요청이 없는 경우 모델을 메모리에서 언로드하기까지의 시간입니다. 기본 값은 `60 * 30 = 30분` 입니다.



TODO: 각 인공지능의 옵션
TODO: 답변의 차이
