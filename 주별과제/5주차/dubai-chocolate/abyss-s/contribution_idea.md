# Contribution Idea

## 1. TrelloBoardContextProvider

- 모듈: ContextProvider
- 설명 : 협업 도구인 Trello의 보드 내용을 AI 모델에 컨텍스트로 제공합니다.

- 배경: Trello는 Jira와 비슷하지만 조금 더 사용이 간편하고 직관적인 칸반보드 스타일 프로젝트 일정 관리도구입니다.  
  현재 [Jira용 context provider](https://docs.continue.dev/customize/context-providers#jira)는 공식문서에서 제공하고 있지만, Trello용은 존재하지 않습니다.

  > 잔디의 마케팅 팀이 사용하는 Trello 예시

![jandi](https://i0.wp.com/blog.jandi.com/ko/wp-content/uploads/sites/4/2021/08/t-mkt.png?w=1000&ssl=1)

- Trello에 대해 좀 더 알아보자🫡

  - 보통 프로젝트 보드는 할 일, 하는 중인 일, 완료된 일 등의 리스트로 구분됩니다.
  - 각 리스트는 여러 카드들로 구성될 수 있음.
  - [참고링크](https://blog.jandi.com/ko/2021/08/19/how-to-trello-like-a-pro/)

- 동작:

  - `@Trello` 명령어 입력 시 연결된 Trello 보드의 내용을 불러옵니다.
  - 보드의 리스트(예: 할 일, 진행 중, 완료)와 각 리스트 내 카드들 정보를 제공합니다.
    - 카드에 할당된 담당자, 기한, 라벨 등의 메타 정보 등..

- 사용 케이스
  - 프로젝트 현황 보고서 or 회고 작성
  - 팀원 역할 분배 유리, 생산성 증대
    - 멤버별 할당된 작업 확인
    - 작업 우선순위 결정
    - 굳이 Trello에 접속 안해도 IDE에서 바로 할 일 확인하고 작업 가능하기 때문!

## 2. make_repo_readme.prompt

- 모듈: prompt

- 설명: GitHub 레포지토리의 README 파일을 자동으로 생성하는 프롬프트 파일

- 배경:
  이번 멘토링을 하면서 다들 리드미를 많이 작성해보셨을 것이라고 생각합니다.  
  README.md는 프로젝트의 첫인상을 결정짓는 중요한 문서이지만, 빈 마크다운 상태에서 작성을 시작한다면 시간이 많이 소요될 수 있어요.  
  따라서 리드미를 자동으로 생성해주는 프롬프트가 있다면 어떨지 고안해보았습니다.

## 동작

1. `@codebase`를 통해 프로젝트 레포의 코드 전체를 분석합니다.
2. Github URL이나 REST API를 이용하여 프로젝트 레포 전체를 context provider로 설정합니다.
3. 분석된 정보를 바탕으로 다음 항목들(예시)을 포함한 README를 생성합니다.

   ```
   - 프로젝트 이름
   - 프로젝트 설명
   - 주요 기능 소개
   - 기여자 목록
   - 설치 및 실행 방법
   ```

- 사용케이스
  - 새로운 프로젝트 시작 시 README 초안 작성 시
  - 기존 프로젝트의 README 업데이트를 급하게 작성해야 할 때
  - 오픈소스 프로젝트의 리드미 작성 자동화
