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

- **배경**: Continue를 특정 목적에 맞게 특화하여 사용할 수 있도록 하기 위함

- **예시**:

  ### 1. 교육용
  - **언어**: Python, C, JAVA 등 선택 가능
  - **사용 예**:
    ```python
    print("Hello World")
    ```
    위와 같이 코드를 작성해보세요.
    
    - 실행 방법: `Ctrl + Shift + F7` 또는 ▶️ 버튼을 누르세요.
    - 실행 결과: `Hello World`가 화면에 표시됩니다.
    - **설명**: `print()`는 화면에 출력을 할 때 사용하는 함수입니다.

  ### 2. 업무용
  - **예시**: 
    ```plaintext
    nodecount = 0
    ```
    위 코드를 작성했을 때, "변수 생성 규칙이 적용된 `nodeCount`를 추천합니다."라는 메시지가 나타납니다.
    
  - **변경 방법**: `Ctrl + Shift + C`를 눌러 수정  
  - **무시 방법**: `ESC`를 눌러 무시

      
