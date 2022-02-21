## 1장

### 반응형 웹
- 정의
  - PC, TV, 내비게이션, 스마트 기기 등 기기마다 또는 환경마가 최적화된 웹사이트를 제공해주는 것   


- 만들면 좋은 이유
  - 유지보수 편해짐
  - 모바일 점유율 증가에 따른 트렌드 반영
  - 마케팅 유리
  - 검색엔진 최적화 가능
  - 미리 지향적 기술

### 반응형 웹 제작을 위한 핵심 기술
- 가변 그리드(Fluid Grid)
  - 픽셀(px) 대신 퍼센트(%)로 제작하는 기술
- 예제
  <details>
    <summary>가변 그리드 기술 - 고정 크기의 박스를 가변 크기의 박스로 변환하기</summary>
  
    ```html
    <!DOCTYPE HTML>
    <html lang="ko">
    <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
        div { 
          height: 500px;
          margin: 10px;
          border: 4px solid black;
        }
      </style>
    </head>
    <body>
      <div style="width: 950px;"></div>
      <div style="width: 90%;"></div>
    </body>
    </html>
    ``` 
  </details>   

### 미디어 쿼리와 뷰포트
- 미디어 쿼리
  - 미디어(컴퓨터)를 감지하여 웹사이트를 변경하는 기술
  - 예제
    <details>
      <summary>적용 CSS 코드</summary>
      
      ```html
      <head>
        <style>
          @media all and (min-width:320px) {
            body {
              background: #e65d5d;
            }
          }
          @media all and (min-width:768px) {
            body {
              background: #2dcc70;
            }
          }
          @media all and (min-width:960px) {
            body {
              background: #6fc0d1;
            }
          }
        </style>
      </head>
      ```
    </details>
- 뷰포트
  - 스마트 기기의 보이는 영역을 기기의 실제 화면 크기로 변경하여 미디어 쿼리가 기기의 화면 크기를 정확하게 감지할 수 있도록 하는 기술 
  - 적용 태그
    <details>
      <summary>예제</summary>
    
      ```html
      <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
      ```
    </details>

- 플렉서블 박스
  - 가변적인 박스를 만드는 기술인 동시에 웹사이트의 구조 설계를 위한 기술 







