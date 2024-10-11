## 공식문서 구체화
- 모델 연동에 필요한 내용 추가
- VSCode 확장자 내에서 추가적인 가이드라인 필요

## 모델 연동 기능 추가
- 화면 UI를 통한 모델 연동(config.json 자동 입력)
- AI 서비스에 맞추어 화면 구성

## 개인화된 AI 모델 연동
- 개인이 직접 구성한 AI/LLM 모델을 third-party 제공사 없이 바로 continue에 연동

## 한국어 번역(다국어 지원)  
 - [Continue 공식 문서](https://docs.continue.dev/)의 한글화   
  
## Continue-C (Continue Change, GPTs 유사)
- 배경 : Continue를 특정 목적에 특화하여 사용할 수 있도록  
- 예 :  
  1. 교육용
     교육용 모드로 선택하면 일정 수준의 커리큘럼에 따라 프로그래밍 언어를 공부하는 사람이 안내대로 따라하면서 공부할 수 있도록 함   
     언어 : Python, C, JAVA 등 선택  
     사용 : "print("Hello World") 라고 써보세요.  ctrl + shift + F7 또는 ▷ 버튼을 누르세요.    
     실행 : Hello World 표시됩니다. Print()는 화면에 출력할 때 사용합니다.  
        
  2. 업무용
     업무용 모드로 선택하면 나와 다른 직원들의 코드를 보고 변수명, 코드 스타일 등 추천 
     nodecount = 0     "변수 생성 규칙이 적용된 nodeCount를 추천합니다."    
     변경 : ctrl + shift + c, 무시 : ESC
