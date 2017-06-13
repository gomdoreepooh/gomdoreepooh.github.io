---
title: CSS 방법론 (SMASS, BEM, OOCSS)
updated : 2017-03-17 19:20
---

## 알아보기

CSS의 역할이 커지면서 CSS를 보다 효율적으로 작성하는 여러가지 아이디어들이 생겼다. SMACSS, BEM, OOCSS 등이 있는데, 개인적으로 각자의 특징을 한 단어로 표현하자면, SMACSS=5형제, BEM=네이밍, OOCSS=재사용이라고 생각한다.

아래 4가지는 여러 CSS 방법론들이 공통적으로 지향하는 목표이며, 이를 위해 대부분 CSS 선택자로 아이디와 타입(태그)을 사용하지 말 것을 권장한다. 아이디는 재사용이 불가능한 요소이고, 태그에 스타일을 매기면 마크업이 수정될 경우 스타일도 다시 손봐야 하기 때문이다(의존적).

1. 쉬운 유지보수
2. 코드의 재사용
3. 확장 가능
4. 직관적인 네이밍

### SMACSS
* 작성할 CSS를 비슷한 5가지 종류로 나눈다. Base, Layout, Module, State, Theme
* Base는 기본 스타일이다. Reset, Variable 등을 포함한다. !important를 쓰지 않는다.
* Layout은 suffix &quot;l-&quot;을 붙인다. Layout은 ID 선택자를 사용해도 된다.
* Module은 table, icon, box 같이 재사용성이 높은 요소를 정의한다.
* State는 상태를 나타난다. active나 disable 등이며 suffix &quot;is-&quot;나 &quot;s-&quot;를 붙인다.
* Theme는 전반적인 Look and feel을 정의하며 suffix &quot;theme-&quot;를 붙인다.

### BEM
* 화면에 보여질 블록(block)을 기준으로 첫번째 순서의 네이밍을 작성한다.
* 그 다음에 블록 안의 요소(elements)들을 &quot;__&quot;으로 연결해서 네이밍을 작성한다.
* 그 다음에 수식어(모양이나 상태)를 &quot;--&quot;으로 연결한 뒤 네이밍을 작성한다.
* 수식어는 boolean이나 key-value 형태로 넣을 수 있다. (-disable, -color-red)
* 예를 들면 .header__logo 또는 .form__button--disabled과 같은 식이다.
* 클래스명이 용도와 형태를 의미하므로 직관적인 것이 장점, 길고 복잡해지는 것이 단점이다.

### OOCSS
* BEM이 역할-요소-상태 순으로 정리한다면, OOCSS는 구조와 스타일을 분리한다.
* 중복되는 디자인 요소를 따로 빼내어 반복적으로 사용한다. (공통 스타일 추상화)
* 컨테이너와 콘텐츠를 분리하고 위치에 의존적인 스타일을 정의하지 않는다.
* 코드 재사용성이 높아져 코드량이 줄고 성능이 향상되며 유지보수성도 높아지는 장점이 있다.
* 반면, 마크업에서 동일한 클래스를 여러 곳에 사용하므로 코드가 지저분해지는 단점이 있다.
* 이 단점을 보완한 것이 OOSass로, 마크업의 복잡함을 프리프로세서 내에서 대신 처리한다.

<div class="divider"></div>

## 응용
아래는 마크업과 퍼블리싱을 하면서 개인적으로 CSS를 정리해오던 방법으로, CSS 방법론을 모를 때부터 써왔기 때문에 어느 한 가지에 꼭 들어맞지는 않는다. 위의 이해를 바탕으로 설명하자면 OOSass가 메인이지만 SMACSS의 장점도 일부 섞여있다. 참고로 Less를 주로 사용하기 때문에 엄밀히 말하면 OOLess라고 부르는 게 맞을 것 같다.

### 1. 자주 사용하는 속성은 utility class로 만든다.
SMACSS의 Base처럼 공통적으로 적용할 속성을 작성한다. 아래처럼 utility class를 만들면 타이핑하는 코드량을 줄이면서 손쉽게 css 속성을 재사용할 수 있다. 클래스 형태로 두면 less를 css로 변환해도 그대로 남아있기 때문에 마크업에서도 동일하게 사용할 수 있다. 반대로 Less에서는 사용하되 변환 이후의 css에는 남겨놓고 싶지 않을 경우 뒤에 ()를 붙여 함수형태로 바꿔 사용한다.

```css
// li tag
ul,ol {margin:0; padding:0}
ul li {list-style-type: none;}

// font-weight
._100 {font-weight: 100!important;}
._200 {font-weight: 200!important;}
._300 {font-weight: 300!important;}
._400 {font-weight: 400!important;}
._500 {font-weight: 500!important;}
._600 {font-weight: 600!important;}
._700 {font-weight: 700!important;}
._800 {font-weight: 800!important;}
._900 {font-weight: 900!important;}

// letter-spacing
.ls0 {letter-spacing: 0!important;}
.ls-xs {letter-spacing: -0.03rem!important;}
.ls-sm {letter-spacing: -0.05rem!important;}
.ls-md {letter-spacing: -0.07rem!important;}
.ls-lg {letter-spacing: -0.09rem!important;}
.ls-xl {letter-spacing: -0.11rem!important;}
.ls(@value) {letter-spacing: -@value!important;}

// opacity
.opacity {opacity: 0.6;}
.opacity0 {opacity: 0;}
.opacity1 {opacity: 0.1;}
.opacity2 {opacity: 0.2;}
.opacity3 {opacity: 0.3;}
.opacity4 {opacity: 0.4;}
.opacity5 {opacity: 0.5;}
.opacity6 {opacity: 0.6;}
.opacity7 {opacity: 0.7;}
.opacity8 {opacity: 0.8;}
.opacity9 {opacity: 0.9;}
.opacity-full {opacity: 1;}
.opacity(@value) {opacity: @value;}

// text-option
.italic {font-style: italic;}
.uppercase {text-transform: uppercase;}
.capitalize {text-transform: capitalize;}
.lowercase {text-transform: lowercase;}
.pointer {cursor: pointer;}
.break {word-break:break-all;}
```

```css
.title {
	._600;
	.ls-sm;
	.opacity5;
	.capitalize;
}
```

### 2. 프리프로세서의 문법과 기능을 활용한다.

Less의 연산, 변수, 함수 등의 기능을 활용하면 코드량을 더 줄이고, 복잡한 효과도 쉽게 추가할 수 있다. 예를 들면 .gradation-x(#FF0000,#FFFF00)와 같이 함수로 만든 클래스를 이용하면 해당 영역에 빨간색부터 노란색까지 가로방향으로 진행하는 그라데이션 배경색을 추가할 수 있다. .transition(opacity)처럼 전환효과를 줄 개별 속성을 선택하게 만들 수도 있다.

```css
// Gradation
.gradation(@start,@end) {
    background-color: @start; /* 그레디언트가 지원되지 않는 경우의 색상(fallback color) */
    background-image: -webkit-linear-gradient(top, @start, @end);
    background-image:    -moz-linear-gradient(top, @start, @end); /* Fx 3.6 부터 Fx 15 까지 처리 */
    background-image:     -ms-linear-gradient(top, @start, @end); /* IE 10 Platform Previews, Consumer Preview */
    background-image:      -o-linear-gradient(top, @start, @end); /* Opera 11.1 부터 12.0 까지 처리 */ 
    justify-content: center;
    align-items:center;
    flex-wrap:wrap;
    padding:0;
    margin:0;
    color: #fff;
}
.gradation-y(@start,@end) { 
    .gradation(@start,@end);
    background-image: linear-gradient(to bottom, @start, @end);
}
.gradation-x(@start,@end) { 
    .gradation(@start,@end);
    background-image: linear-gradient(to right, @start, @end);
}
.gradation-rt(@start,@end) { 
    .gradation(@start,@end);
    background-image: linear-gradient(to right top, @start, @end)
}
.gradation-rb(@start,@end) { 
    .gradation(@start,@end);
    background-image: linear-gradient(to right bottom, @start, @end)
}

// transition
.transition {-webkit-transition: all 0.5s, -webkit-transform 0.5s; transition: all 0.5s, transform 0.5s;}
.transition-slow {-webkit-transition: all 0.8s, -webkit-transform 0.8s; transition: all 0.8s, transform 0.8s;}
.transition-fast {-webkit-transition: all 0.2s, -webkit-transform 0.2s; transition: all 0.2s, transform 0.2s;}
.transition(@option) {-webkit-transition: @option 0.5s, -webkit-transform 0.5s; transition: @option 0.5s, transform 0.5s;}
.transition-slow(@option) {-webkit-transition: @option 0.8s, -webkit-transform 0.8s; transition: @option 0.8s, transform 0.8s;}
.transition-fast(@option) {-webkit-transition: @option 0.2s, -webkit-transform 0.2s; transition: @option 0.2s, transform 0.2s;}
```
```css
.layer {
	.gradation-x(#FF0000, #FFFF00);
}
```

### 3. State는 .is-active처럼 suffix를 활용한다.
클래스는 CSS 외에도 javascript에서도 사용한다. 특히 상태를 표현할 때 주로 쓰는데, 요소에 클래스를 toggle하여 보여주거나 숨기는 기능을 구현하면서 .is-active 클래스명을 쓰는 것을 예로 들 수 있다. suffix를 생략한 채 .active로 사용하기도 한다.

```css
// element control
.dp-block {display: block!important;}
.dp-none {display: none!important;}
.hidden {visibility: hidden;}
.visible {visibility: visible;}
```

```css
.layer {
	.dp-none;
}
.layer.is-active {
	.dp-block;
}
```


### 4. 공통된 스타일은 별도의 클래스로 만들고 재사용한다.
OOCSS를 설명할 때 대개 facebook과 twitter 버튼을 만드는 예제를 사용한다. 거기에 HTML 마크업이 늘어나는 것을 명시적으로 보여주기 위해 .btn-block 클래스를 추가했다. 적용할 공통 속성이 늘어나면 그만큼 HTML 마크업도 늘어난다. 그래서 실제로는 그 다음에서 설명하는 OOSass의 방식을 사용한다.

```css
.btn {
	border: 0;
	outline: none;
	text-align: center;
	font-size: 1rem;
	color: #fff;
	border-radius: 3px;
}
.btn-block {
	width: 100%;
	height: 3rem;
	line-height: 3rem;
}
.facebook {
	background-color: #3b5998;
}
.twitter {
	background-color: #00aced;
}
```
```html
<button class="facebook btn btn-block">페이스북로 공유</button>
<button class="twitter btn btn-block">트위터로 공유</button>
```

### 5. HTML에서는 클래스명을 하나로 주고, Less에서 중복 클래스명을 처리한다.
Less의 중첩 규칙을 이용해 Less 안에서 중복 클래스를 묶어 하나의 클래스명을 만들고 HTML 마크업 요소에 연결한다. (중첩 규칙은 Sass도 mixin 문법으로 유사하게 사용할 수 있다) 쉬운 유지보수, 코드의 재사용과 확장, 직관적인 네이밍 모두 가능한 가장 효율적인 방법이라고 생각한다.
```css
.btn {
	border: 0;
	outline: none;
	text-align: center;
	font-size: 1rem;
	color: #fff;
	border-radius: 3px;
}
.btn-block {
	.btn;
	width: 100%;
	height: 3rem;
	line-height: 3rem;
}
.facebook {
	background-color: #3b5998;
}
.twitter {
	background-color: #00aced;
}
.fb-btn {
	.facebook;
	.btn-block;
}
.tw-btn {
	.twitter;
	.btn-block;
}
```
```html
<button class="fb-btn">페이스북로 공유</button>
<button class="tw-btn">트위터로 공유</button>
```

## 주의사항
1. 여러 사람이 협업할 때는 utility class를 작성하는 기준(일종의 [코딩 컨벤션](https://spoqa.github.io/2012/08/03/about-python-coding-convention.html))을 통일해야 한다.
2. 다른 UI framework와 같이 사용할 경우 클래스명이나 효과가 중첩되지 않도록 작성해야 한다.
2. 간단한 속성을 주는 것에도 중첩 규칙을 사용하면 오히려 작업량이 늘어난다. 상황에 따라 적절하게 복합선택자(하위, 자식, 형제 등)를 사용해야 한다.
3. React와 같이 구성요소를 컴포넌트로 만들 경우 컴포넌트 단위로 스타일을 분리하는데, 그럴 경우 utility class가 포함된 less 파일은 최상위에 두고 import로 불러와 사용한다. 빌드 과정에서 프리프로세서를 컴파일하기 때문에 릴리즈 버전은 영향을 받지 않지만, 개발 환경에서는 약간의 성능저하가 생길 수 있다.
<div class="divider"></div>

## 참고
* 스키머(schemr), [CSS 방법론 (1) — BEM (Block Element Modifier)](https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1)
* 스키머(schemr), [CSS 방법론 (2) — OOCSS(Object Oriented CSS)](https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-2-oocss-object-oriented-css-4064e1119354)
* NTS UIT BLOG, [[CSS방법론] SMACSS, BEM, OOCSS](http://wit.nts-corp.com/2015/04/16/3538)