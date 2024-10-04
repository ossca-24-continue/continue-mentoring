## RAG 커스텀 in Continue

### 1. 임베딩 모델 선택

Continue에서 추천하는 모델은 `voyage-code-2`  
(코드 임베딩 모델 중 성능이 우수)

### 2. 벡터 DB 선택

- 대부분 벡터 DB 사용해도 무방하기 때문에 사용성이 좋은 DB를 권장
- Continue 권장 DB는 `LanceDB`: 인 메모리 DB

### 3. 청킹 전략 선택

`votage-code-2` 모델은 최대 16,000 토큰

- Truncate: 넘치는 건 잘라서 버림. 1파일 1청크.
- chunks of a fixed length: 고정된 길이로 청크
- recursive, (AST)-based strategy: 정확하지만, 복잡. 소스 코드를 함수, 조건문, 블록 단위로 나눌 수 있음.

### 4. 인덱싱 스크립트 작성

: 데이터를 검색 가능하도록 구조화하여 저장하는 과정
청킹 -> 임베딩 생성 -> 벡터 DB 삽입

```python
from lancedb.pydantic import LanceModel, Vector
from lancedb.embeddings import get_registry

db = lancedb.connect("/tmp/db")
func = get_registry().get("openai").create(
    name="voyage-code-2",
    base_url="https://api.voyageai.com/v1/",
    api_key=os.environ["VOYAGE_API_KEY"],
)

class CodeChunks(LanceModel):
    filename: str
    text: str = func.SourceField()
    # 1536 is the embedding dimension of the `voyage-code-2` model.
    vector: Vector(1536) = func.VectorField()

table = db.create_table("code_chunks", schema=CodeChunks, mode="overwrite")
table.add([
    {"text": "print('hello world!')", filename: "hello.py"},
    {"text": "print('goodbye world!')", filename: "goodbye.py"}
])

query = "greetings"
actual = table.search(query).limit(1).to_pydantic(CodeChunks)[0]
print(actual.text)
```

### 5. 인덱싱 스크립트 실행

- 파일이 변경될 때 해당 파일만 자동으로 인덱싱하는 게 완벽함.
- 하지만 주기적으로 전체 인덱스를 새로 고치는 것도 충분히 효과적임.
  (일주일에 한 번, 또는 한 달에 한 번 정도도 충분할 수 있습니다.)

### 6. 서버 설정

- 커스텀 RAG에 접속하기 위한 서버를 띄워야 함.
- `[POST] /retrieve`

```python
@app.post("/retrieve")
async def create_item(item: ContextProviderInput):
    results = [] # TODO: Query your vector database here.

    # Construct the "context item" format expected by Continue
    context_items = []
    for result in results:
        context_items.append({
            "name": result.filename,
            "description": result.filename,
            "content": result.text,
        })

    return context_items
```

### 7. (옵션) 리랭킹

- Continue는 `rerank-1` 모델을 추천하나 Voyage AI는 `rerank-2` 모델을 추천함.
- 리랭킹를 위한 별도의 서버 띄어야 함. (e.g. `/rerank`)

## RAG 관련 질문

### 왜 커스텀 RAG는 별도 서버가 필요?

all embeddings are calculated locally with `all-MiniLM-L6-v2` and stored locally in `~/.continue/index`.

### RAG의 트레이드 오프는?

- 작은 청크는 원본 문서의 의미를 불완전하게 나타낼 수 있음.
- 청킹 크기를 줄이면 검색 속도가 빨라진다. 하지만 정확도가 떨어질 수 있다.(반대 관계 존재)

### 임베딩된 벡터는 보안적으로 안전할까?

- 벡터는 수치적 표현이며 데이터 그 자체가 아님.
- 벡터를 통해 유사한 원본 문서 또는 데이터를 검색하여 그것을 반환하는 것.
