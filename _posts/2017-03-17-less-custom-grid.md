---
title: Less로 Grid 커스터마이징하기
updated : 2017-03-17 19:20
---

## 개요

UI Framework 중에서 [Bootstrap](http://getbootstrap.com/)과 [Semantic UI](https://semantic-ui.com/)를 주로 사용한다. 둘 모두 비슷한 요소들을 갖추고 있기 때문에 하나만 쓰는 것이 좋다.[^1] [아임포트 홈페이지](http://iamport.kr/)에는 Bootstrap을 썼고, [통계분석](http://analytics.iamport.kr/)에는 Semantic UI를 썼다. 통계분석에서 Semantic UI를 쓴 건 [React에서 더 쉽게](http://react.semantic-ui.com/introduction) 쓸 수 있기 때문이다.

하지만 반응형 웹을 위한 Grid를 그릴 때에는 Semantic UI보다 Bootstrap의 방식이 작업하기에 익숙하였기 때문에 그 부분만 떼서 프로젝트에 추가했다. 그리고 4K, 5K와 같은 고해상도 모니터들이 출시되는 추세를 반영해 이에 대응하는 코드도 추가했다.[^2] 마지막으로 코드를 간결하게 쓸 수 있도록 Less의 변수로 정리했다.

<div class="divider"></div>

## 해상도 분기

Less에서 해상도의 Break Point를 아래와 같이 지정한다. [Bootstrap의 Grid](http://getbootstrap.com/css/#grid)와 [Semantic UI의 Grid](https://semantic-ui.com/elements/container.html) 모두 공통된 Break Point를 가지고 있다. xs부터 xl까지는 [Bootstrap v4의 Grid](https://v4-alpha.getbootstrap.com/layout/grid/)와 동일하며, 그 이상은 보편적인 해상도의 이름을 선택했다. 먼저 최소값과 최대값을 아래와 같이 정의했다.

```css
@sm-min 	: 576px;
@md-min 	: 768px;
@lg-min 	: 992px;
@xl-min 	: 1200px;
@hd-min 	: 1600px;
@fhd-min 	: 1920px;
@qhd-min 	: 2560px;
@uhd-min 	: 3840px;
@4k-min 	: 4096px;
@5k-min 	: 5120px;

@xs-max 	: (@sm-min - 1);
@sm-max 	: (@md-min - 1);
@md-max 	: (@lg-min - 1);
@lg-max 	: (@xl-min - 1);
@xl-max 	: (@hd-min - 1);
@hd-max 	: (@fhd-min - 1);
@fhd-max 	: (@qhd-min - 1);
@qhd-max 	: (@uhd-min - 1);
@uhd-max 	: (@4k-min - 1);
@4k-max 	: (@5k-min - 1);
```

위에서 정한 범위에 맞춰 아래와 같이 변수를 만든다. -down과 -up은 [Bootstrap Responsive Utilites](https://v4-alpha.getbootstrap.com/layout/responsive-utilities/)에 나오는 개념인데, 써보니 유용해서 같이 추가했다.

```css
@xs: 	~'only screen and (max-width: @{xs-max})';
@sm:    ~"only screen and (min-width: @{sm-min}) and (max-width: @{sm-max})";
@md:    ~"only screen and (min-width: @{md-min}) and (max-width: @{md-max})";
@lg:    ~"only screen and (min-width: @{lg-min}) and (max-width: @{lg-max})";
@xl:    ~"only screen and (min-width: @{xl-min}) and (max-width: @{xl-max})";
@hd:    ~"only screen and (min-width: @{hd-min}) and (max-width: @{hd-max})";
@fhd:   ~"only screen and (min-width: @{fhd-min}) and (max-width: @{fhd-max})";
@qhd:   ~"only screen and (min-width: @{qhd-min}) and (max-width: @{qhd-max})";
@uhd:   ~"only screen and (min-width: @{uhd-min}) and (max-width: @{uhd-max})";
@4k:    ~"only screen and (min-width: @{4k-min}) and (max-width: @{4k-max})";
@5k:    ~"only screen and (min-width: @{5k-min})";

@xs-down:   ~"only screen and (max-width: @{xs-max})";
@sm-down:   ~"only screen and (max-width: @{sm-max})";
@md-down:   ~"only screen and (max-width: @{md-max})";
@lg-down:   ~"only screen and (max-width: @{lg-max})";
@xl-down:   ~"only screen and (max-width: @{xl-max})";
@hd-down:   ~"only screen and (max-width: @{hd-max})";
@fhd-down:  ~"only screen and (max-width: @{fhd-max})";
@qhd-down:  ~"only screen and (max-width: @{qhd-max})";
@uhd-down:  ~"only screen and (max-width: @{uhd-max})";
@4k-down:   ~"only screen and (max-width: @{4k-max})";

@sm-up:    	~"only screen and (min-width: @{sm-min})";
@md-up:    	~"only screen and (min-width: @{md-min})";
@lg-up:    	~"only screen and (min-width: @{lg-min})";
@xl-up:    	~"only screen and (min-width: @{xl-min})";
@hd-up:    	~"only screen and (min-width: @{hd-min})";
@fhd-up:   	~"only screen and (min-width: @{fhd-min})";
@qhd-up:   	~"only screen and (min-width: @{qhd-min})";
@uhd-up:   	~"only screen and (min-width: @{uhd-min})";
@4k-up:    	~"only screen and (min-width: @{4k-min})";
@5k-up:    	~"only screen and (min-width: @{5k-min})";
```

이제 Less에서 미디어쿼리를 사용할 때 아래와 같이 간단하게 쓸 수 있다.

```css
@media @sm-down {
	// 여기에 모바일용 코드를 넣고
}
@media @md-up {
	// 여기에 데스크탑용 코드를 넣는다
}
```
<div class="divider"></div>

## 마크업

만드는 김에 Bootstrap에서 편하게 썼던 클래스들을 몇개 추가했다. 아래와 같이 만들면 다른 요소에 쉽게 포함시킬 수 있고 마크업에서도 쉽게 사용할 수 있다. 참고로 만약 CSS파일의 용량을 줄이기 위해 Less 안에서는 쓰되, 변환된 CSS에는 제외하고 싶을 경우에는 클래스이름 뒤에 함수처럼 ()를 붙이면 된다. [[자세히]](https://opentutorials.org/course/277/1751)

```css
.text-center {text-align: center}
.text-left {text-align: left}
.text-right {text-align: right}
.dp-block {display: block}
.dp-none {display: none}
.hidden {visibility: hidden;}
.visible {visibility: visible;}
```

이제 별도의 CSS를 작성하지 않고도 마크업에서 해상도에 따라 내용을 보여주거나 숨기는 효과를 쉽게 줄 수 있도록 아래 코드를 추가한다.

```css
.visible-xs{.dp-none;}
.visible-sm{.dp-none;}
.visible-md{.dp-none;}
.visible-lg{.dp-none;}
.visible-xl{.dp-none;}
.hidden-xs{.dp-block;}
.hidden-sm{.dp-block;}
.hidden-md{.dp-block;}
.hidden-lg{.dp-block;}
.hidden-xl{.dp-block;}

@media @xs { .visible-xs {.dp-block;} .hidden-xs {.dp-none;}}
@media @sm { .visible-sm {.dp-block;} .hidden-sm {.dp-none;}}
@media @md { .visible-md {.dp-block;} .hidden-md {.dp-none;}}
@media @lg { .visible-lg {.dp-block;} .hidden-lg {.dp-none;}}
@media @xl { .visible-xl {.dp-block;} .hidden-xl {.dp-none;}}
@media @hd { .visible-hd {.dp-block;} .hidden-hd {.dp-none;}}
@media @fhd { .visible-fhd {.dp-block;} .hidden-fhd {.dp-none;}}
@media @qhd { .visible-qhd {.dp-block;} .hidden-qhd {.dp-none;}}
@media @uhd { .visible-uhd {.dp-block;} .hidden-uhd {.dp-none;}}
@media @4k { .visible-4k {.dp-block;} .hidden-4k {.dp-none;}}
@media @5k { .visible-5k {.dp-block;} .hidden-5k {.dp-none;}}

@media @sm-up { .visible-sm-up {.dp-block;} .hidden-sm-up {.dp-none;}}
@media @md-up { .visible-md-up {.dp-block;} .hidden-md-up {.dp-none;}}
@media @lg-up { .visible-lg-up {.dp-block;} .hidden-lg-up {.dp-none;}}
@media @xl-up { .visible-xl-up {.dp-block;} .hidden-xl-up {.dp-none;}}
@media @hd-up { .visible-hd-up {.dp-block;} .hidden-hd-up {.dp-none;}}
@media @fhd-up { .visible-fhd-up {.dp-block;} .hidden-fhd-up {.dp-none;}}
@media @qhd-up { .visible-qhd-up {.dp-block;} .hidden-qhd-up {.dp-none;}}
@media @uhd-up { .visible-uhd-up {.dp-block;} .hidden-uhd-up {.dp-none;}}
@media @4k-up { .visible-4k-up {.dp-block;} .hidden-4k-up {.dp-none;}}
@media @5k-up { .visible-5k-up {.dp-block;} .hidden-5k-up {.dp-none;}}

@media @xs-down { .visible-xs-down {.dp-block;} .hidden-xs-down {.dp-none;}}
@media @sm-down { .visible-sm-down {.dp-block;} .hidden-sm-down {.dp-none;}}
@media @md-down { .visible-md-down {.dp-block;} .hidden-md-down {.dp-none;}}
@media @lg-down { .visible-lg-down {.dp-block;} .hidden-lg-down {.dp-none;}}
@media @xl-down { .visible-xl-down {.dp-block;} .hidden-xl-down {.dp-none;}}
@media @hd-down { .visible-hd-down {.dp-block;} .hidden-hd-down {.dp-none;}}
@media @fhd-down { .visible-fhd-down {.dp-block;} .hidden-fhd-down {.dp-none;}}
@media @qhd-down { .visible-qhd-down {.dp-block;} .hidden-qhd-down {.dp-none;}}
@media @uhd-down { .visible-uhd-down {.dp-block;} .hidden-uhd-down {.dp-none;}}
@media @4k-down { .visible-4k-down {.dp-block;} .hidden-4k-down {.dp-none;}}
```

<div class="divider"></div>

# Row와 Column

Bootstrap에서 쓰는 Row와 Column 방식을 추가한다. [Bootstrap Customize](http://getbootstrap.com/customize/)에서 Grid System만 체크한 뒤 페이지 최하단의 Compile and Download를 누르면 [Bootstrap의 Grid](http://getbootstrap.com/css/#grid)의 내용만 있는 CSS 파일을 다운로드할 수 있다. css/bootstrap.css 파일을 열어 301줄부터 마지막까지를 복사해 프로젝트의 Less 파일에 붙여넣었다.

많은 내용을 좀 더 쉽게 보면서 편집하기 위해 [레벨을 High로 해서 압축](http://csscompressor.com/)했다. 그리고 코드량을 줄이기 위해 공통된 부분은 .col()로 빼냈다. 마지막으로 유사한 방식으로 고해상도 부분을 추가했는데, 고해상도에서 offset은 잘 쓰지 않아서 제외했다.

```css
@col-padding : 15px;
.col(){position:relative;min-height:1px;padding-right:@col-padding;padding-left:@col-padding;float:left;}
.container{margin-left: auto; margin-right: auto; padding-left: @col-padding; padding-right: @col-padding; &::after{content: ""; display: table; clear: both;}}
.container-fluid{margin-left: auto; margin-right: auto; padding-left: @col-padding; padding-right: @col-padding; &::after{content: ""; display: table; clear: both;}}
.row{margin-left: -@col-padding; margin-right: -@col-padding; &::after{content: ""; display: table; clear: both; }}
.col-xs-1{.col;width:8.33333%}
.col-xs-2{.col;width:16.66667%}
.col-xs-3{.col;width:25%}
.col-xs-4{.col;width:33.33333%}
.col-xs-5{.col;width:41.66667%}
.col-xs-6{.col;width:50%}
.col-xs-7{.col;width:58.33333%}
.col-xs-8{.col;width:66.66667%}
.col-xs-9{.col;width:75%}
.col-xs-10{.col;width:83.33333%}
.col-xs-11{.col;width:91.66667%}
.col-xs-12{.col;width:100%}
.offset-xs-1{margin-left:8.33333%}
.offset-xs-2{margin-left:16.66667%}
.offset-xs-3{margin-left:25%}
.offset-xs-4{margin-left:33.33333%}
.offset-xs-5{margin-left:41.66667%}
.offset-xs-6{margin-left:50%}
.offset-xs-7{margin-left:58.33333%}
.offset-xs-8{margin-left:66.66667%}
.offset-xs-9{margin-left:75%}
.offset-xs-10{margin-left:83.33333%}
.offset-xs-11{margin-left:91.66667%}

@media @sm-up {
.container{max-width:576px}
.col-sm-1{.col;width:8.33333%}
.col-sm-2{.col;width:16.66667%}
.col-sm-3{.col;width:25%}
.col-sm-4{.col;width:33.33333%}
.col-sm-5{.col;width:41.66667%}
.col-sm-6{.col;width:50%}
.col-sm-7{.col;width:58.33333%}
.col-sm-8{.col;width:66.66667%}
.col-sm-9{.col;width:75%}
.col-sm-10{.col;width:83.33333%}
.col-sm-11{.col;width:91.66667%}
.col-sm-12{.col;width:100%}
.offset-sm-0{margin-left:0}
.offset-sm-1{margin-left:8.33333%}
.offset-sm-2{margin-left:16.66667%}
.offset-sm-3{margin-left:25%}
.offset-sm-4{margin-left:33.33333%}
.offset-sm-5{margin-left:41.66667%}
.offset-sm-6{margin-left:50%}
.offset-sm-7{margin-left:58.33333%}
.offset-sm-8{margin-left:66.66667%}
.offset-sm-9{margin-left:75%}
.offset-sm-10{margin-left:83.33333%}
.offset-sm-11{margin-left:91.66667%}
}
@media @md-up {
.container{max-width:720px}
.col-md-1{.col;width:8.33333%}
.col-md-2{.col;width:16.66667%}
.col-md-3{.col;width:25%}
.col-md-4{.col;width:33.33333%}
.col-md-5{.col;width:41.66667%}
.col-md-6{.col;width:50%}
.col-md-7{.col;width:58.33333%}
.col-md-8{.col;width:66.66667%}
.col-md-9{.col;width:75%}
.col-md-10{.col;width:83.33333%}
.col-md-11{.col;width:91.66667%}
.col-md-12{.col;width:100%}
.offset-md-0{margin-left:0}
.offset-md-1{margin-left:8.33333%}
.offset-md-2{margin-left:16.66667%}
.offset-md-3{margin-left:25%}
.offset-md-4{margin-left:33.33333%}
.offset-md-5{margin-left:41.66667%}
.offset-md-6{margin-left:50%}
.offset-md-7{margin-left:58.33333%}
.offset-md-8{margin-left:66.66667%}
.offset-md-9{margin-left:75%}
.offset-md-10{margin-left:83.33333%}
.offset-md-11{margin-left:91.66667%}
}
@media @lg-up {
.container{max-width:940px}
.col-lg-1{.col;width:8.33333%}
.col-lg-2{.col;width:16.66667%}
.col-lg-3{.col;width:25%}
.col-lg-4{.col;width:33.33333%}
.col-lg-5{.col;width:41.66667%}
.col-lg-6{.col;width:50%}
.col-lg-7{.col;width:58.33333%}
.col-lg-8{.col;width:66.66667%}
.col-lg-9{.col;width:75%}
.col-lg-10{.col;width:83.33333%}
.col-lg-11{.col;width:91.66667%}
.col-lg-12{.col;width:100%}
.offset-lg-0{margin-left:0}
.offset-lg-1{margin-left:8.33333%}
.offset-lg-2{margin-left:16.66667%}
.offset-lg-3{margin-left:25%}
.offset-lg-4{margin-left:33.33333%}
.offset-lg-5{margin-left:41.66667%}
.offset-lg-6{margin-left:50%}
.offset-lg-7{margin-left:58.33333%}
.offset-lg-8{margin-left:66.66667%}
.offset-lg-9{margin-left:75%}
.offset-lg-10{margin-left:83.33333%}
.offset-lg-11{margin-left:91.66667%}
}
@media @xl-up {
.container{max-width:1140px}
.col-xl-1{.col;width:8.33333%}
.col-xl-2{.col;width:16.66667%}
.col-xl-3{.col;width:25%}
.col-xl-4{.col;width:33.33333%}
.col-xl-5{.col;width:41.66667%}
.col-xl-6{.col;width:50%}
.col-xl-7{.col;width:58.33333%}
.col-xl-8{.col;width:66.66667%}
.col-xl-9{.col;width:75%}
.col-xl-10{.col;width:83.33333%}
.col-xl-11{.col;width:91.66667%}
.col-xl-12{.col;width:100%}
.offset-xl-0{margin-left:0}
.offset-xl-1{margin-left:8.33333%}
.offset-xl-2{margin-left:16.66667%}
.offset-xl-3{margin-left:25%}
.offset-xl-4{margin-left:33.33333%}
.offset-xl-5{margin-left:41.66667%}
.offset-xl-6{margin-left:50%}
.offset-xl-7{margin-left:58.33333%}
.offset-xl-8{margin-left:66.66667%}
.offset-xl-9{margin-left:75%}
.offset-xl-10{margin-left:83.33333%}
.offset-xl-11{margin-left:91.66667%}
}

@media @hd-up {
.container{max-width:1920px}
.col-hd-1{.col;width:8.33333%}
.col-hd-2{.col;width:16.66667%}
.col-hd-3{.col;width:25%}
.col-hd-4{.col;width:33.33333%}
.col-hd-5{.col;width:41.66667%}
.col-hd-6{.col;width:50%}
.col-hd-7{.col;width:58.33333%}
.col-hd-8{.col;width:66.66667%}
.col-hd-9{.col;width:75%}
.col-hd-10{.col;width:83.33333%}
.col-hd-11{.col;width:91.66667%}
.col-hd-12{.col;width:100%}
}

@media @fhd-up {
.container{max-width:2560px}
.col-fhd-1{.col;width:8.33333%}
.col-fhd-2{.col;width:16.66667%}
.col-fhd-3{.col;width:25%}
.col-fhd-4{.col;width:33.33333%}
.col-fhd-5{.col;width:41.66667%}
.col-fhd-6{.col;width:50%}
.col-fhd-7{.col;width:58.33333%}
.col-fhd-8{.col;width:66.66667%}
.col-fhd-9{.col;width:75%}
.col-fhd-10{.col;width:83.33333%}
.col-fhd-11{.col;width:91.66667%}
.col-fhd-12{.col;width:100%}
}

@media @qhd-up {
.container{max-width:3840px}
.col-qhd-1{.col;width:8.33333%}
.col-qhd-2{.col;width:16.66667%}
.col-qhd-3{.col;width:25%}
.col-qhd-4{.col;width:33.33333%}
.col-qhd-5{.col;width:41.66667%}
.col-qhd-6{.col;width:50%}
.col-qhd-7{.col;width:58.33333%}
.col-qhd-8{.col;width:66.66667%}
.col-qhd-9{.col;width:75%}
.col-qhd-10{.col;width:83.33333%}
.col-qhd-11{.col;width:91.66667%}
.col-qhd-12{.col;width:100%}
}

@media @uhd-up {
.container{max-width:3840px}
.col-uhd-1{.col;width:8.33333%}
.col-uhd-2{.col;width:16.66667%}
.col-uhd-3{.col;width:25%}
.col-uhd-4{.col;width:33.33333%}
.col-uhd-5{.col;width:41.66667%}
.col-uhd-6{.col;width:50%}
.col-uhd-7{.col;width:58.33333%}
.col-uhd-8{.col;width:66.66667%}
.col-uhd-9{.col;width:75%}
.col-uhd-10{.col;width:83.33333%}
.col-uhd-11{.col;width:91.66667%}
.col-uhd-12{.col;width:100%}
}
```

## 결론

* 기존에 널리 쓰이는 Grid 체계와 호환된다.
* Less에서 media query 부분을 간편하게 쓸 수 있다.
* sm-down, md-up 같은 축약 형태를 사용할 수 있다.
* 4k, 5k와 같은 고해상도의 CSS도 제어할 수 있다.
* Bootstrap v4에 추가된 push, pull은 손에 익지 않아 제외했다.
* hidden-, visible-도 사용빈도가 적어 제외했다.

<div class="divider"></div>

[^1]: 사실 대부분의 UI Framework들은 서로 호환되지 않으므로 같이 쓸 수 없다.
[^2]: 일반적인 웹사이트는 정렬과 여백을 적절히 활용하기 때문에 고해상도에 대응하는 CSS에 대한 니즈가 거의 없다. 다만, 아임포트 통계분석처럼 가로 풀사이즈 레이아웃을 쓰는 특수한 상황에서는 필요하다.