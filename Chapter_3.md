## 3장 

### 미디어 쿼리
- 화면 해상도, 기기 방향 등의 조건으로 HTML에 적용하는 스타일을 전환할 수 있는 CSS3의 속성 중 하나
- 기본 문법
  - @media [only 또는 not] [미디어 유형] [and 또는 ,] (조건문) {실행문}
  - 대/소문자 구별하지 않음
- [only 또는 not]
  - 미디어 쿼리를 지우너하는 브라우저에서만 미디어 쿼리를 해석하게 해주는 키워드
  - not tv : tv를 제외한 모든 미디어 유형에만 적용
- 미디어 유형
  - all : 모든 장치
  - screen : 컴퓨터 화면 장치 또는 스마트 기기의 화면
  - tv : 영상과 음성이 동시에 출력되는 장치
- [and 또는 ,]
  - and는 앞뒤 조건이 참일 때 실행
  - , 는 하나만 참이어도 실행
  - 생략 가능
- (조건문)
  - @media (min-width:320px) and (max-width:768) {실행문}
    - 가로 320px 이상, 세로 768이하 일때 실행문 실행
- {실행문}
  - 일반적으로 사용하는 CSS 코드를 작성
- 미디어 쿼리 적용방식 - 링크 방식
  1. ```html
     <link rel="stylesheet" href="mediaqueries.css">
     ```
  2. ```html 
     <link rel="stylesheet" media="all and (min-width:320px)" href="style320px.css">
     ```
     - 비추천
     - 조건이 여러 개로 나눠지면 css파일을 여러 번 불러오게 되어 비효율적
    
### 미디어 쿼리 사용 시 주의 사항
- 띄어쓰기 주의
  - @media all and(min-width: 320px) {실행문}
    - and와 괄호'(' 사이에 공백이 없기에 작동안함  
- min을 사용시 크기가 작은 순서대로 작성
- max을 사용시 크기가 큰 순서대로 작성
- 미디어 쿼리는 보이는 영역을 뜻하는 뷰포트 크기를 기준으로 감지함

### 미디어 쿼리 사용해 웹사이트 구조 변경 예제
```html
<!DOCTYPE HTML>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
    <title>Document</title>
    <style>
* {
  margin:0;
  padding:0;
}

#wrap {
  width: 90%;
  margin: 0 auto;
  border: 4px solid #000;
}

#wrap div {
  display: inline-block;
  height: 100px;
  margin-bottom: -4px;
}

#wrap div:first-child {
  background:#f45750;
}

#wrap div:nth-child(2) {
  background:#40b0f9;
}

#wrap div:nth-child(3) {
  background:#00d2a5;
}

#wrap div:nth-child(4) {
  background:#ff884d;
}

#wrap div:last-child {
  background:#464646;
}

@media all and (min-width:320px) {
  #wrap div {
    width: 100%;
  }
}

@media all and (min-width:768px) {
  #wrap div {
    width: 50%;
  }
}

#wrap div:last-child {
  width: 100%;
}

@media all and (min-width:1024px) {
  #wrap div {
    width: 20%;
  }
}

#wrap div:last-child {
  width: 20%;
}

</style>
</head>
<body>
<div id="wrap">
  <div></div><div></div><div></div><div></div><div></div>
</div>
</body>
</html>
```

### 뷰포트
- 데스크톱에서 뷰포트
  - 사용자가 설정한 해상도
- 스마트 기기
  - 기본으로 설정되어 있는 값
  - 이로 인하여 미디어 쿼리가 정상적으로 작동하지 않는 문제가 발생할 수 있음
- 뷰포트 속성
  - width : 뷰포트의 너비
  - height : 뷰포트의 높이
  - initial-scale : 뷰포트의 초기 배율(기본값 : 1)
  - user-scalable : 뷰포트 확대/축소여부(기본값 : yes)
  - minimum-scale : 최소 축소 비율(기본값 : 0.25)
  - maximum-scale : 최대 축소 비율(기본값 : 5.0)
- 스마트 기기의 뷰포트 영역 확인 방법
  - 뷰포트 영역을 확인할 목적으로 개발된 웹사이트에 접속해서 뷰포트 영역을 확인해야 함 
  - https://viewportsizer.com/devices/

### 표준 방식으로 뷰포트를 사용하는 방법
```html
<head>
<style>
@viewport {
  width: device-width;      /* width 속성 */
  zoom: 1;                  /* initial-scale 속성 */
  min-zoom: 1;              /* minimum-scale 속성 */
  max-zoom: 1;              /* maximum-scale 속성 */
  user-zoom: zoom;          /* user-scaleable 속성 */  
}
</style>
</head>
```

 

