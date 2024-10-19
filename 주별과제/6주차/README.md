# 6주차 정기 모임
- 6주차 과제 리뷰
- 멘토링 프로그램 회고

## 6주차 과제 리뷰
이영주 멘티 첫 기여후 회고중  
> 오픈소스 기여라고 하면 흔히 “대단한 무언가를 해야 한다”라는 압박감을 가지기 쉽다.
> 하지만 오픈소스 기여는 대단한 개발 실력보다는 ‘소통’이라는 행위 그 자체에 더 큰 의미가 있다는 것을 깨달았다.
> 처음부터 모든 것을 완벽하게 이해하려고 하기보다는 일단 그냥 시작을 해보자!!

https://www.youtube.com/watch?v=bRU5SIOk-qo

### 조별 과제 
- 조별로 컨트리뷰선 진행할 과제 1개 이상 선정 > 구현
- 구현후 컨티뉴 제출 전에 멘토와 리뷰하기
- 선정 과제 유형
  - 아이디어 제출
  - 구현
  - 공식 문서 업데이트

#### 1조

- 진행 내용
  - Model Provider에 간략한 설명 추가 : 4주차 과제를 하며 Provider를 조사할 때, Continue Providers 공식 문서에 각 Provider가 어떤 서비스인지에 대한 설명이 없는 경우가 많았음. 만약 각 Provider마다 간략한 설명이 있다면, AI 서비스에 익숙지 않은 사용자가 자신의 상황과 맞는 Provider를 선택하는 데 도움이 될 거라고 생각함.
  - Model Provider 연동 과정 구체화 : 현재의 Model Provider 문서들은 대부분이 config 형식만 제공하는 형태여서, Provider를 직접 연동하는 과정에서 헤매는 경우가 있음. 일부 연동에 어려움이 있는 Provider의 경우 연동 과정을 구체화하여 작성하고, 사전작업에 대한 안내가 아예 누락된 Provider의 경우 간략하게 추가하여 다른 문서들과의 형식을 맞추고자 함.
- PR 링크 : https://github.com/continuedev/continue/pull/2575

#### 2조

- **Fix Android Studio troubleshooting issue link**

  - [PR 링크](https://github.com/continuedev/continue/pull/2514)
  - 문제: 공식 문서 내 Android Studio Operation 관련 링크 에러
  - 해결: `Actions > Choose Boot runtime for the IDE`로 수정

- **refactor: Prevent Unrecognized DOM Prop Warning for showAbove in ModeSelect**
  - [PR 링크](https://github.com/continuedev/continue/pull/2508), [블로그 링크](https://tomymoon.tistory.com/163)
  - 문제: React does not recognize the `showAbove` prop on a DOM element.
  - 원인: styled-components를 사용해서 스타일링하고 있는데 props가 전달될 때 HTML 요소에 직접 전달되어 경고창이 출력되고 있었다.
  - 해결: ModelSelect.tsx의 모든 `showAbove` props 이름을 `$showabove`로 변경하면 콘솔창에 경고가 출력되지 않는다.

#### 3조

#### 4조

*(Contribution Idea 등록 예정)*

1. **Continue 진행 중인 내역 가시성 증가**
   - Autocomplete, Edit 기능 사용 중 에러 및 진행사항 관련 내용이 눈에 잘 띄지 않는다는 점을 고려함. 현재 우하단의 작은 아이콘을 통해 로딩이나 에러 상태가 표현되고 있으나, 에러 발생 시 패널을 통해 이를 명확하게 보여줌으로써 가시성을 증대시키는 방안을 제안하고자 함.

*(PR 후 머지 완료)*

1. **Docs의 shortcut 관련 내용 추가**
   - Autocomplete 기능을 on/off 할 수 있는 단축키가 이미 존재하지만, 문서에서 소개되지 않았음. 이를 반영하여 해당 내용을 문서에 추가하는 작업을 진행하였으며, PR을 제출하고 머지까지 완료하였음.

*(추후 PR 예정)*

1. **@files 관련 버그 수정**
   - 현재 IDE 상에서 파일 추가 및 삭제와 같은 변동 사항이 발생할 경우, @files를 통한 확인은 가능하나 파일명을 직접 검색할 때 새로운 파일이 표시되지 않는 문제가 있음. IDE가 최초 실행 시에만 파일에 대한 검색을 수행하는 것이 문제의 원인임을 파악하였으나, FileContextProvider.ts의 로직에 대한 이해가 부족하여 이번 주 내에는 해결하지 못하였음. 추후 추가적인 탐색을 통해 문제 해결 후 PR하거나, Bug report로 기여할 계획임.

2. **Docs의 Customize 부분 수정**
   - 지난주 발표에서 동일한 주제를 진행하는 멘티가 있어 이번 주에는 진행하지 않았으나, 담당자가 없는 만큼 해당 부분을 수정하여 PR을 진행할 예정임.


## 회고 3M
지난 6주동안 멘토링 프로그램에 참여하며
- Me(나에게) : 
- Mentee(함께한 동료멘티들에게) :
- Mentor(멘토에게) : 


## 공지
### 멘티 활동 보고서 작성
- 10월 21일 월요일 18시까지
- 멘토링 프로그램 수료 필수 조건(+출석)

### Contribution MVP
- 기여했어요 스레드에 공유해준 모든 멘티
- 스벅(멘토사비ㅋ)

### 멘토링 저장소 public 전환

## 사진촬영
