[ 2장 ]

* 가변 그리드 공식
  - (가변 크기로 만들 박스의 가로 너비 ÷ 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비) × 100 = 가변 크기의 % 값
  - wrap, wrapper로 아이디를 사용하면 해당 id로 포함된 웹요소에 대해서 일괄적으로 변경이 가능함

* 서로 다른 크기의 박스를 가변 크기로 변환하기 예제    
<DOCTYPE HTML>
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
  height: 500px;
  margin: 0 auto;
  border: 4px solid #000;
}

.container {
  width: 93.75%;
  height: 492px;
  margin: 0 auto;
  border: 4px solid #000;
}

.container div {
  display: inline-block;
  height: 100%;
}

.container div:first-child {
  width: 33.33%;
  background: #e75d5d;
}

.container div:first-child + div {
  width: 66.66%;
  background: #2dcc70;
}
</style>
</head>
<body>
  <div id="wrap">
    <div class="container">
      <div></div><div></div>
    </div>
  </div>
</body>
</html>

* 마진과 패딩
  - 마진 : 물체와 물체 사이의 빈 공간
  - 패딩 : 두께

* 가변 패딩 적용 방법()
  - (가변 패딩을 적용할 패딩값 / 적용할 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 패딩 % 값
  - 기본적으로 공식은 동일함
    - (가변을 원하는 적용값) / (가변 내용을 감싸는 전체 크기 - 보통은 witdh ) * 100 = 적용 퍼센트 값 
    ex) 아래의 예제를 설정하면 첫번쨰 색의 네모칸 오른쪽에 마진의 크기를 960px중 360px만큼 채우려고 하면 360 / 960 * 100 = 37.5 로 하면 된다. 

* 가운데 마진(공간)을 만들고 양옆에 색 영역을 만든 반응형 예제
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title>Document</title>
<style>
* {
  margin:0; padding:0;
}

#wrap{
  width:90%;
  height:500px;
  margin:0 auto;
  border:4px solid #000;
}

#wrap div{
  display:inline-block;
  width:31.25%;
  height:100%;
}

#wrap div:first-child{
  margin-right:37.5%;
  background:#1f518b;
}

#wrap div:first-child + div{
  background:#f7e041;
}
</style>
</head>
<body>
  <div id="wrap">
    <div></div><div></div>
  </div>
</body>
</html>

* 가변 패딩 적용한 반응형 예제
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
height: 500px;
margin: 0 auto;
border: 4px solid #000;
}

#wrap div {
width: 31.25%;  /* 가변박스 적용 : 300 / 960 * 100 = 31.25 */
display: inline-block;
}

/* 첫번째 박스 가변 패딩 적용 */
#wrap div:first-child {
/* 가변패딩 적용 : 50 / 960 * 100 = 5.2 */
/* 두 개로 표현할 때, 상하는 px로 좌우는 %로 표현 가능 */
padding: 50px 5.2%;
background: #f00;
}

/* 두번째 박스 가변 패딩 적용 */
/* + div 는 바로 다음 div를 말함 */
#wrap div:first-child + div {
/* 가변패딩 적용 : 130 / 960 * 100 = 13.5*/
padding: 130px 13.551%;
background: #0f0;
}
</style>
</head>
<body>
  <div id="wrap">
    <div></div><div></div>
  </div>
</body>
</html>

* 가변폰트 이용하기
  - 픽셀은 모니터의 해상도를 기준으로 하기 때문에 화면이 확대/축소되는 환경이 부적합
  - 이 때는 상대적인 단위인 em을 사용하는 것이 좋음(1em = 16px)
  - 공식
    - (가변 폰트를 적용할 글자 크기 / 적용할 요소를 감싸고 있는 요소의 글자 크기) = 가변 폰트 값
  - 가변 폰트 크기 계산 URL(http://pxtoem.com/)

* 가변폰트 이용 예제
  !DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title>Document</title>
<style>
* {
  margin: 0;
  padding: 0;
  font-size: 100%;
}

#para {
font-size: 6em;
}

#para p{
/* 64 / 96 = 0.67*/
/* font-size: 4em; --> 이렇게 하면 안되는 이뉴는 #para에 감싸여 있기 때문 */
font-size:0.67em;
}

/* 아래와 같이 #para에 포함되지 않으면 4em으로 하면 '#para p' 와 같은 크기로 표현됨 */
#para2 {
font-size: 4em;
}

</style>
</head>
<body>
	<div id="para">
	가변적인 폰트1
		<p>가변적인 폰트2</p>
	</div>
  <div id="para2">가변적인 폰트3</div>
</body>
</html>

* 진정한 가변 폰트 - vw, vh, vim, vmax 단위
  1. vw
     - vw 단위는 웹 브라우저의 너비를 100을 기준으로 하여 크기를 결정하는 단위
     - (vw 단위를 적용할 글자 크기 * 브라우저 너비) / 100 = 너비
  2. vh
     - vh 단위는 웹 브라우저의 높이를 100을 기준으로 하여 크기를 결정하는 단위
     - (vh 단위를 적용할 글자 크기 * 브라우저 높이) / 100 = 높이
  3. vmin
     - vmin 단위는 웹 브라우저의 너비와 높이 중 짧은 쪽을 기준으로 크기 결정하는 단위
  4. vmax
     - vmax 단위는 웹 브라우저의 너비와 높이 중 큰 쪽을 기준으로 크기 결정하는 단위
 

* 웹브라우져 크기 변경에 따른 폰트 변경 예제
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title>Document</title>
<style>
* {
  margin: 0;
  padding: 0;
  font-size:100%;
}

p {
font-size: 5vw;
}
</style>
</head>
<body>
  <!-- 웹브라우져의 크기를 변경함에 따라 폰트의 크기가 변경됨 -->
  <!-- 이는 이전의 em단위로 글자의 크기를 세팅후, 웹브라우져의 크기를 변경하였을 경우는 폰트의 크기가 그대로임 -->
	<p>vw단위!</p>
</body>
</html>


* 이미지와 동영상을 가변적으로 작동하게 만드는 예제
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title></title>
<style>
* {
  margin: 0;
  padding: 0;
}

video, iframe {
width: 100%;
max-width: 100%;
}

/* 동영상을 가변적으로 만들기 위한 공식같은 느낌 */
#wrap {
position: relative;
padding-bottom: 56.25%;    /* 9 ÷ 16 */
/* 상/하 퍼센트 패딩은 부모 요소의 높이가 아닌 너빗값을 기준으로 함(스펙명시) */
height: 0;
overflow: hidden;
}

iframe {
position: absolute;
top: 0;
left: 0;
height: 100%;
}
</style>
</head>
<body>
    <div id="wrap">
        <iframe src="https://player.vimeo.com/video/192526798?byline=0&badge=0" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
    </div>
</body>
</html>

* fitvids 스크립트를 사용 예제 (스타일 요소중 #wrap, iframe를 생각하여 작성가능)
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title></title>
<style>
* {
  margin: 0;
  padding: 0;
}

video, iframe {
width:100%;
max-width:100%;
}
</style>
</head>
<body>
  <div id="wrap">
    <iframe src="https://player.vimeo.com/video/203671501" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
  </div>
  <script src="source/jquery.min.js"></script>
  <script src="source/jquery.fitvids.js"></script>
  <script>
    $("#wrap").fitVids();
  </script>
</body>
</html>
