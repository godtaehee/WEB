**확장 가능한 벡터 그래픽(Scalable Vector Graphics)**

XML 기반의 2차원 그래픽

아이콘, 이미지, 그래프, 사용자 인터페이스(UI)에 널리 쓰임

DOM의 일부로서 각 개체별로 HTML 엘리먼트가 추가됨

→ svg, path, rect, circle 등등 HTML 태그로써 존재한다는 말

벡터이기 때문에 이미지의 크기에 상관없이 선명하게 유지되고 모양이 많이 복잡하지 않은 경우 파일 사이즈도 작다

→ ***크기가 크다고 파일사이즈가 큰게아니다*** 이미지가 복잡하면 파일사이즈가 큰거지 크다고해서 파일사이즈가 크진않다. XML코드를 보면 이해가된다 수많은 숫자 계산으로 되어있기때문에 이 계산이 많아지면 크기가 커진다.

CSS와 자바스크립트를 이용해서 조작이 가능하다.

크기(width/height)가 큰 이미지 표현에 유리 << 현수막같이 큰 글씨필요한거

모양이 복잡하고 개체수가 많을 수록 성능이 떨어짐

→ awwwards사이트에 나와있는 다양한 인터렉티브 웹사이트들 로딩시간이 상당히 길다 화려한건 좋지만 과연 이렇게 많은 로딩시간이 걸리는게 맞는건가 싶다.

SVG는 캔버스와 비교된다.

## Canvas

비트맵 기반 그래픽

→ 픽셀로 이루어진 이미지, 픽셀 하나하나 조정 가능하다

이미지나 비디오의 픽셀 조작, 게임, 퍼포먼스가 중요한 이미지 조작 등에 쓰임

<canvas>라는 단일태그 하나로 동작 가능

→ svg는 svg,path,rect 등등의 태그들로 동작을한다

**CSS로 조작 불가**, 자바스크립트로 조작가능

픽셀 단위의 조작이 가능해서 일반 HTML 엘리먼트로는 불가능한 다양한 표현들이 가능

→ 하지만 할수있는 일들은 많다.

크기가 커질수록 성능이 떨어짐

→ width,height가 많아질수록 성능이 떨어짐 (Pixel 개수가 많아진다)

## SVG를 HTML에 넣는 방법

1. <img> 태그
2. CSS Background
3. SVG 요소들을 직접 inline으로 삽입
4. <object>태그

```html
<!-- 이미지 태그를 이용함, 반응형으로 크기가 동작 -->
 <img src="img/face.svg" alt="">

<!-- CSS로 넣기 (css background img로 넣음) -->
 <div class="svg"></div>

<!-- Inline으로 바로 넣어버리기 -->
<svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 571 625.5">
    <circle cx="286.5" cy="354.5" r="251" stroke-width="40" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <circle cx="175" cy="380.5" r="42.5"/>
    <circle cx="397" cy="380.5" r="42.5"/>
    <path d="M422 476.16a181.3 181.3 0 0 1-135.48 60.59H286a181.3 181.3 0 0 1-135.48-60.59" stroke-width="30" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <ellipse cx="168.5" cy="210.5" rx="168.5" ry="121.5"/>
    <ellipse cx="428.5" cy="198.5" rx="142.5" ry="123.5"/>
    <ellipse cx="245.5" cy="103" rx="151.5" ry="103"/>
</svg>

<!-- object 태그 쓰기 -->
<object data="img/face.svg" type="image/svg+xml"></object>
```

## SVG 크기 설정

svg 라는것을 도화지라고 생각하고 그 안에 넣을 도형들(rect,circle,etc..)등등을 넣는다.

svg가 크기가 width 500px, height 500px 이렇게 구체적인 수치로 정해져버리면 svg는 인터렉티브하게 동작되지 않는다. 

그러니 크기를 아예 설정 안하면 인터렉티브 하게 이미지가 움직인다.

위처럼 구체적인 숫자말고 상대적인 크기를 정해줄수 있는데 그 방법이 바로 **viewbox 이다. >> svg태그에 설정**

```html
<svg viewbox="0 0 500 500">
    <rect x="0" y="0" width="100" height="100"></rect>
    <rect x="100" y="0" width="100" height="100"></rect>
    <rect x="200" y="0" width="100" height="100"></rect>
    <rect x="300" y="0" width="100" height="100"></rect>
    <rect x="400" y="0" width="100" height="100"></rect>
</svg>
```

## viewbox

보이는 뷰의 크기

```html
<!-- CSS -->
svg {
	width:500px;
	height: 500px;
}

<!-- HTML -->
<svg viewbox="0 0 500 500">
```

CSS의 svg의 전체 크기는 500px * 500px로 되어있고,

svg의 viewbox의 크기는 500 500이라고 되어있으므로 비율이 1:1이다

그런데 여기서 viewbox의 크기를 1000 1000으로 하고 svg안에 width,height가 100인 직사각형이 있다면 ?

```html
<!-- CSS -->
svg {
	width:500px;
	height: 500px;
}

<!-- HTML -->
<svg viewbox="0 0 1000 1000">
	<rect x="0" y="0" width="100" height="100"></rect>
</svg>
```

이렇게되면 500px을 1000으로 본다는것이 되고,

직사각형은 가로세로 10개씩 총 100개가 있으면 svg박스가 꽉차게 되며

rect의 실제 크기는 50px * 50px이 된다

svg의 width,height값에 각각 (svg안의 도형의 값(100) /viewbox의 값(1000))

을 곱해주면된다 즉, 비율로 곱해주면된다는 도형의 실제크기가 나온다는뜻이다

500px * (100/1000) = 50px

비율이니까 단위가 없다

## SVG 압축하기

**svgomg**라고 치면 svg 압축웹페이지가 있다.

## CSS적용하기

일반 우리가 HTML Tag에 클래스를 적용하듯이 똑같이 적용하면 되고

HTML에서는 background-color 혹은 color를 쓰는데 svg에서는

fill이라는것을 사용한다 텍스트나 이미지나 svg로 만들어진것들은 무조건 fill을 사용

- 헤어색 변경

```html
<!-- CSS -->
.face {
        width: 200px;
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        margin: auto;
}
.face-hair {
    fill: brown;
}
.face-hair:nth-of-type(1) {
    fill: blue;
}

<!-- HTML -->

<svg class="face" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 571 625.5">
    <circle cx="286.5" cy="354.5" r="251" stroke-width="40" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <circle cx="175" cy="380.5" r="42.5"/>
    <circle cx="397" cy="380.5" r="42.5"/>
    <path d="M422 476.16a181.3 181.3 0 0 1-135.48 60.59H286a181.3 181.3 0 0 1-135.48-60.59" stroke-width="30" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <ellipse class="face-hair" cx="168.5" cy="210.5" rx="168.5" ry="121.5"/>
    <ellipse class="face-hair" cx="428.5" cy="198.5" rx="142.5" ry="123.5"/>
    <ellipse class="face-hair" cx="245.5" cy="103" rx="151.5" ry="103"/>
</svg>
```

- 눈 애니메이션

```html
<!-- CSS -->
@keyframes bounce {
  from {
      transform: scale(0.9);
  }
  to {
      transform: scale(1.1);
  }
}
.face {
    width: 200px;
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    margin: auto;
}
.face-hair {
    fill: brown;
}
.face-hair:nth-of-type(1) {
    fill: blue;
}
.face-eye {
    animation: bounce 0.5s alternate infinite;
    transform-origin: center center;
}

<!-- HTML -->

<svg class="face" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 571 625.5">
    <circle cx="286.5" cy="354.5" r="251" stroke-width="40" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <circle class="face-eye" cx="175" cy="380.5" r="42.5"/>
    <circle class="face-eye" cx="397" cy="380.5" r="42.5"/>
    <path d="M422 476.16a181.3 181.3 0 0 1-135.48 60.59H286a181.3 181.3 0 0 1-135.48-60.59" stroke-width="30" fill="none" stroke="#000" stroke-miterlimit="10"/>
    <ellipse class="face-hair" cx="168.5" cy="210.5" rx="168.5" ry="121.5"/>
    <ellipse class="face-hair" cx="428.5" cy="198.5" rx="142.5" ry="123.5"/>
    <ellipse class="face-hair" cx="245.5" cy="103" rx="151.5" ry="103"/>
</svg>

```

transform-origin의 center 기준은 svg 박스를 기준 body아님

```html
.face-eye:nth-of-type(2) {
    transform-origin: 175px 380px;
}
.face-eye:nth-of-type(3) {
    transform-origin: 397px 380px;
}
```

눈 기준으로 하기, 175 이런 값들은 원의 중심좌표

svg파일 자체에 css적용을 하려면 아래와 같이 svg 태그안에 defs 태그 안에 style을 작성할수 있다.

```html
<svg class="face" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 571 625.5">
  <defs>
      <style>
          @keyframes bounce {
              from {
                  transform: scale(0.9);
              }
              to {
                  transform: scale(1.1);
              }
          }
          .face {
              width: 200px;
              position: absolute;
              top: 0;
              right: 0;
              left: 0;
              bottom: 0;
              margin: auto;
          }
          .face-hair {
              fill: brown;
          }
          .face-hair:nth-of-type(1) {
              fill: blue;
          }
          .face-eye {
              animation: bounce 0.5s alternate infinite;
              transform-origin: center center;
          }
          .face-eye:nth-of-type(2) {
              transform-origin: 175px 380px;
          }
          .face-eye:nth-of-type(3) {
              transform-origin: 397px 380px;
          }
      </style>
  </defs>

  <circle cx="286.5" cy="354.5" r="251" stroke-width="40" fill="none" stroke="#000" stroke-miterlimit="10"/>
  <circle class="face-eye" cx="175" cy="380.5" r="42.5"/>
  <circle class="face-eye" cx="397" cy="380.5" r="42.5"/>
  <path d="M422 476.16a181.3 181.3 0 0 1-135.48 60.59H286a181.3 181.3 0 0 1-135.48-60.59" stroke-width="30" fill="none" stroke="#000" stroke-miterlimit="10"/>
  <ellipse class="face-hair" cx="168.5" cy="210.5" rx="168.5" ry="121.5"/>
  <ellipse class="face-hair" cx="428.5" cy="198.5" rx="142.5" ry="123.5"/>
  <ellipse class="face-hair" cx="245.5" cy="103" rx="151.5" ry="103"/>
</svg>
```
