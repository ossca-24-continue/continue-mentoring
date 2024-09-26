# [4조. Continue4u] 기능명: **Action & Edit**

## 1. 개요 및 사용법

### Edit

**개요**

Edit 기능은 현재 파일을 벗어나지 않고 코드 수정을 쉽게 할 수 있는 방법이에요.

원하는 코드 블록을 하이라이트하고 프롬프트를 입력하면, 원하는 변경 사항이 인라인으로 파일에 스트리밍되어 나타나고, 이를 accept / reject 할 수 있어요.

**사용 방법**

1. 코드 블록 하이라이트 : 수정하려는 코드 블록을 드래그한 후, cmd/ctrl + i 단축키로 edit 창을 활성화할 수 있어요.
2. 변경 사항 설명 : 하이라이트한 코드에 대해 원하는 변경 사항을 프롬프트에 작성하면 돼요. 간단한 작업에는 edit을, 복잡한 작업에는 Chat을 사용하는 것을 권장해요.
3. 변경 사항 수용 또는 거부 :

- 제안된 변경 사항은 강조된 텍스트 내에서 인라인 diff로 나타나요.
- 각 제안된 변경 사항을 탐색하면서, accept `cmd`/`ctrl` + `opt` + y 하거나 reject `cmd`/`ctrl` + `opt` + n 할 수 있어요.
- 모든 변경 사항을 한 번에 적용하려면 `cmd`/`ctrl` + `shift` + `enter`, 모두 거부하려면 `cmd`/`ctrl` + `shift` + `delete를` 누르면 돼요.

4. 새로운 제안 요청: 같은 코드 블록에 대해 새로운 제안을 요청하려면 다시 `cmd`/`ctrl` + i를 눌러 모델에 새로 프롬프트를 입력하면 돼요.

> 💡 Context Selection
>
> - **하이라이트된 코드**:
>   - 사용자가 선택한 강조 표시된 코드는 프롬프트에 포함되며, 모델이 수정할 코드 섹션이 돼요.
>   - 모델은 이 코드 블록만을 대상으로 작업을 수행하게 돼요.
> - **현재 파일**:
>   - 하이라이트한 코드가 포함된 파일의 전체 내용이 추가적인 컨텍스트로 제공돼요.
>   - 이는 모델이 코드 수정 시 더 적절한 판단을 하도록 돕는 역할을 해요.
>   - 만약 파일이 너무 커서 컨텍스트 창에 맞지 않는 경우, 파일 내용을 잘라내어 처리하는 방식으로 진행해요.

**사용 예**

- **주석 추가**
- **단위 테스트 생성**
- **함수 리팩토링**

즉, 작은 수정이나 빠른 변경에 특화된 기능이에요.

> 💡 추가적으로 `inlineEdit` 속성 수정해서 특정 모델로 설정할 수도 있어요!

### Actions

**개요**

**Actions**는 자주 사용하는 작업(예: 코드 리뷰, 주석 추가 등)을 빠르게 수행할 수 있는 단축키 기능이에요.

**사용 방법**

**1. Slash 명령어 사용하기**:

- Slash 명령어는 가장 일반적인 방법으로, `/`를 입력하면 드롭다운 메뉴가 나타나요.
- 예를 들어, `/edit` 명령어를 사용하면 편집을 직접 에디터에 스트리밍할 수 있어요.

기본적으로 사용할 수 있는 유용한 명령어는 `/edit`, `/comment`, `/share`가 있어요.

더 많은 옵션을 사용하려면 해당 명령어 라이브러리를 활성화해야 해요.

- **Slash 명령어 설명 모음**
  - **`/edit`**: 선택한 코드를 수정하고 변경 사항을 나란히 비교해줘요.
  - **`/comment`**: 선택한 코드에 대한 주석을 자동으로 작성해줘요.
  - **`/share`**: 현재 채팅 기록을 공유 가능한 마크다운 형식으로 내보내줘요. 저장 경로는 매개변수로 지정할 수 있어요.
  - **`/cmd`**: 자연어로 쉘 명령어를 생성하고 VS Code에서 자동으로 터미널에 붙여넣어줘요.
  - **`/commit`**: 현재 git diff를 보여주고, 커밋 메시지를 생성해줘요.
  - **`/http`**: 사용자 지정 HTTP 엔드포인트에서 업데이트를 스트리밍하는 커스텀 명령어를 작성해줘요.
  - **`/issue`**: 문제 설명을 입력하면 잘 정리된 제목과 본문을 생성하고 드래프트 링크를 제공해줘요.
  - **`/so`**: StackOverflow에서 질문에 대한 답변을 자동으로 검색하고 링크를 인용해줘요.
  - **`/onboard`**: 새로운 프로젝트에 대한 구조 분석 및 주요 폴더, README, 종속 파일 등을 설명해줘요.

Continue의 내장 Slash 명령어는 특정 작업을 빠르게 수행할 수 있는 단축키 기능이에요. 이를 사용하려면 `~/.continue/config.json` 파일에서 `slashCommands` 목록에 추가해야 해요.

**2. 프롬프트 파일 사용하기**:

- `.prompt` 파일을 작성해서 파일, URL, 강조된 코드 등을 참조하는 자신만의 Slash 명령어를 정의할 수 있어요.
  - 예: `test.prompt` 파일을 만들어 `jest`를 사용하는 단위 테스트 생성 명령어를 정의할 수 있어요.
- 빠른 시작을 위해 제공된 `.prompt` 파일 라이브러리를 사용할 수도 있어요.

**기타 트리거**

**1. Quick Actions**

- 상위 클래스나 함수 위에 버튼 형태로 나타나며, 한 번의 클릭으로 액션을 수행할 수 있어요.
- `.prompt` 파일을 사용해 커스텀 퀵 액션을 설정할 수 있어요.
- 기본적으로 비활성화 상태이며, VS Code 설정에서 "Continue: Enable Quick Actions"를 통해 활성화할 수 있어요.

**2. Right Click Actions**

- 원하는 코드 블록을 강조하고, 오른쪽 클릭 후 액션을 선택하여 실행할 수 있어요.

**3. Debug Action**

- 터미널의 내용을 빠르게 복사하고, `cmd/ctrl + shift + R`을 눌러 채팅 사이드바에 붙여넣어 디버깅 조언을 받을 수 있어요.

**4. Quick Fixes**

- 코드에 빨간색/노란색 밑줄이 있을 경우, 근처에 커서를 놓으면 전구 아이콘이 나타나요.
- 전구를 클릭하거나 `cmd/ctrl + .`을 눌러 퀵 픽스를 활성화하고, "Ask Continue" 액션을 선택하면 문제 해결을 시도해줘요.

**장점**

- **빠른 액세스**: 자주 사용하는 작업을 빠르게 수행할 수 있어서 생산성이 향상돼요.
- **커스터마이징 가능**: `.prompt` 파일을 사용해 개인화된 명령어와 액션을 쉽게 추가할 수 있어요.
- **통합**: VS Code와의 깊은 통합을 통해 디버깅, 코드 수정, 테스트 등이 더욱 편리해져요.

**단점**

- **제한된 에디터**: 현재 VS Code 전용으로 제공되며, 다른 코드 편집기에서는 사용할 수 없어요.
- **복잡성**: 프롬프트 파일 설정은 초보자에게 다소 복잡할 수 있어요.

## 2. 사용 예시

### Continue와 함께 인지 복잡도 낮추기 (문희님 실제 업무에 활용 사례)

- **정적 코드 분석 도구**: Sonarqube
- **인지 복잡도**: 코드를 이해하기 어려운 정도를 측정하는 지표로, 코드의 가독성과 유지 보수성을 평가하는데 사용돼요.
- **Edit 기능을 사용한 이유**: 작은 Chat이기 때문에 코드 변경 사항이 적은 부분에 적합하기 때문이에요.

**사용 방법**

1. Sonarqube를 통해 인지 복잡도 계산 후 코드 내 어느 부분에서 해당 계산 결과가 나왔는지 확인하고, 수정할 부분을 체크해요.

![이미지](https://github.com/user-attachments/assets/d299dbee-33e5-4688-b069-dc40e0e826b7)

- 현재 코드에 대한 SonarQube 인지 복잡도 리포트 결과 (현재 인지 복잡도 27이기에 15로 낮춰야 해요)

![이미지](https://github.com/user-attachments/assets/db73ab64-3fe1-4a7a-a27c-2c2e3a79209f)

![이미지](https://github.com/user-attachments/assets/80525960-1b3b-4956-ba11-560082145cf4)

2. 인지 복잡도 개선이 필요한 부분에 대해 코드 선택 (하이라이트) 후 edit 프롬프트를 실행해요.

![이미지](https://github.com/user-attachments/assets/64b1f13d-22b0-4915-a828-d41a0f853f4a)

3. 결과 - Sonarqube 실행 후 파일 리포트 확인 결과 인지 복잡도가 15 이하로 감소했어요.

![image](https://github.com/user-attachments/assets/cbc66dd1-02f4-40d9-a68d-a6128f1bd926)

### edit 사용 예시

**1. 코드 선택하기**

수정하고 싶은 코드를 드래그한 후, `Cmd/Ctrl + i`를 입력했어요.

![image](https://github.com/user-attachments/assets/d3043243-30e8-4cec-85c5-8183bca02201)

코드가 선택되고 edit 입력창이 나왔어요.

**2. 명령 입력하기**

![image](https://github.com/user-attachments/assets/5729a483-ace0-4a9d-8eed-660374984aae)

옆에 나타난 입력창에 원하는 수정 방향을 입력했어요.

**3. Accept or Reject**

![image](https://github.com/user-attachments/assets/e458cddf-86fd-4669-8d93-6d39c9990e30)

수정된 코드 내용을 확인한 후, 수정을 반영할지 여부를 선택했어요.

### actions 사용 예시

**1. 채팅창에 코드 추가하기**

![image](https://github.com/user-attachments/assets/c416aa7d-71d3-4878-b9ce-b577215ab4b4)

코드를 하이라이트한 다음 `Cmd/Ctrl + L`을 사용했어요.

![image](https://github.com/user-attachments/assets/235d4f84-f538-456b-b8fa-d142f269b304)

사이드바에 선택된 코드가 추가된 것을 확인할 수 있었어요.

**2 슬래시(/) 명령 사용하기**

![image](https://github.com/user-attachments/assets/7639fe7d-6a76-4d12-bbb0-276a3704fc82)

슬래시 `/`를 입력하면 나오는 다양한 명령어 중에서 원하는 명령어를 사용했어요.

## 3. 주의사항 및 사용팁

### Edit 팁

- edit의 다른 기능과 차별화되는 점은 IDE 입력창에서 바로 수정이 이루어진다는 것이에요. (다른 기능은 별도의 탭이 생성돼요.) 그래서 코드 내에서 즉각적인 수정이 필요할 때 유용해요.
- 그러나 즉각적인 수정에 특화된 만큼, 너무 과도한 수정 요청은 오히려 품질 저하로 이어질 수 있으니 주의해야 해요. (코드 일부가 누락될 가능성도 있어요.)
- edit 기능은 하이라이트된 부분에 집중하므로, 파일 전체에 대한 이해가 필요한 수정이라면 chat이나 actions를 사용하는 것이 좋아요.

### Actions 팁

- actions 기능은 쉽게 단축키와 비슷하게 생각할 수 있어요. 다양한 기능을 actions로 활용해 별도의 프롬프트 작성 없이 바로 사용할 수 있어요.
- actions의 장점은 커스터마이징이 가능하다는 거예요. 자주 사용하는 반복적인 작업을 Actions의 prompt로 정해두면 작업 속도와 정확도가 크게 향상될 수 있어요.
- actions prompt를 너무 길게 작성하면 context를 적게 넣을 수밖에 없으니 LLM 최적화 기법 등을 활용해 간결하고 효율적인 프롬프트를 작성하는 것을 추천해요.
- 특히 함수명 작성, 주석 처리 등의 프롬프트를 사용하면 같은 팀 내에서 생산성을 크게 높일 수 있을 거예요.
- actions를 활용하면 터미널에서 발생한 오류에 대해서도 continue를 사용할 수 있어요.

### 공통

- edit, actions 모두 공통적으로 파라미터가 400빌리언 이상인 모델을 사용해야 해요.

---

### 스터디원 조사 자료 및 참고자료

- [https://velog.io/@sjmh0507/Continue-Edit-Actions-기능-리뷰](https://velog.io/@sjmh0507/Continue-Edit-Actions-%EA%B8%B0%EB%8A%A5-%EB%A6%AC%EB%B7%B0) : 스터디원 문희님의 Continue Edit 와 Actions 실제 활용 리뷰 및 기능 분석 (기술 블로그)
- [https://bitter-cloth-1a0.notion.site/Continue-Edit-Actions-10c196bee1fc8096b65df46cb5cc4460?pvs=4](https://www.notion.so/10c196bee1fc8096b65df46cb5cc4460?pvs=21) : 스터디원 김민지의 Continue Edit과 Actionss 기능 분석 (노션)
- [https://mire-fossa-a65.notion.site/Continue-10c2008295f780aeb480fddb3beaca7c?pvs=4](https://www.notion.so/10c2008295f780aeb480fddb3beaca7c?pvs=21) : 스터디원 우정주님의 Continue Edit과 Actionss 기능 분석 (노션)
- [https://faceted-numeric-2fc.notion.site/Edit-Actions-10dfb7c1463380f28a1eef686ab057bd](https://www.notion.so/Edit-Actions-10dfb7c1463380f28a1eef686ab057bd?pvs=21) : 스터디원 박범수님의 Continue Edit과 Actions 기능 분석 (노션)

---

- https://docs.continue.dev/: Continue Official Docs
- https://github.com/continuedev/continue/blob/main/docs/docs/customize/slash-commands.md: Continue Github Docs 중 Actions slash command
- https://aipure.ai/kr/products/continue: Continue 에 대한 간단한 소개가 있는 AI 도구 소개 웹 사이트 AIPURE
