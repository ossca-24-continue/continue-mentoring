# [4조. Continue4u] 기능명: **Action & Edit**

## 1. 간단한 기능 요약

## 2. 사용법

## 3. 사용예시

### edit 사용 예시

**1. 코드 선택하기**
    
수정을 원하는 코드를 드래그한 후, Cmd/Ctrl + i를 입력

![image](https://github.com/user-attachments/assets/d3043243-30e8-4cec-85c5-8183bca02201)

코드가 선택되고 edit 입력창이 나온다.
    
**2. 명령 입력하기**
    
![image](https://github.com/user-attachments/assets/5729a483-ace0-4a9d-8eed-660374984aae)

옆에 떠오른 입력창에 원하는 수정 방향을 입력한다.
    
**3. Accept or Reject**
    
![image](https://github.com/user-attachments/assets/e458cddf-86fd-4669-8d93-6d39c9990e30)

수정된 코드의 내용 확인한 뒤, 수정을 반영할지 여부를 선택한다.

### actions 사용 예시

**1. 채팅창에 코드 추가하기**

![image](https://github.com/user-attachments/assets/c416aa7d-71d3-4878-b9ce-b577215ab4b4)

- 코드 하이라이트 이후 Cmd/Ctrl + L을 사용

![image](https://github.com/user-attachments/assets/235d4f84-f538-456b-b8fa-d142f269b304)


- 사이드바에 선택된 코드가 추가되는 것을 확인할 수 있다.

**2 슬래시(/) 명령 사용하기**

![image](https://github.com/user-attachments/assets/7639fe7d-6a76-4d12-bbb0-276a3704fc82)

슬래쉬 작성 시 나오는 다양한 명령어 중 원하는 명령어를 사용한다.

## 4. 주의사항 및 사용팁

### Edit 팁

- edit의 다른 기능과의 차별점은 IDE 입력창에서 바로 수정이 이뤄진다는 것이다. (다른 기능은 별도의 탭이 생성된다.) 따라서, 코드 내에서 즉각적인 수정이 필요할 때 용이하다.
- 다만 즉각적인 수정에 특화된 만큼 너무 과도한 내용에 대한 수정을 요청하면 오히려 품질이 저하될 수 있는 우려가 있다. (코드 일부가 누락되는 문제가 발생 가능하다.)
- edit 기능은 하이라이트된 부분에 집중하기 때문에 파일 전체에 대한 이해가 필요한 수정이면 chat이나 actions를 사용하면 좋다.

### Actions 팁

- actions 기능은 쉽게 단축키라고 생각해볼 수 있다. 많은 기능을 actions를 활용하여 별도의 프롬포트 작성 없이 바로 사용가능하다.
- actions의 장점은 커스터마이징으로 자주 사용하는 루틴한 업무는 Actions의 prompt로 정해두면 작업속도와 정확도가 크게 향상된다.
- actions prompt를 너무 길게 적으면 context를 적게 넣을 수밖에 없기 때문에 LLM 최적화 기법 등을 사용하여 최대한 간결하고 효율적인 프롬프트를 작성할 것을 추천한다.
- 특히 함수명 작성, 주석 처리 등의 프롬프트를 사용하여 같은 팀 내에서 사용한다면 생산성을 높이는 데에 도움이 될 것으로 예상한다.

### 공통

- edit, actions 모두 공통적으로  model은 파라미터가 400빌리언 이상인 것으로 사용해야 한다.

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
