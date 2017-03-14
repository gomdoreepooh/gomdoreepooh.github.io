---
title: SVG 아이콘 라이브러리 만들기
updated: 2017-01-04 23:37
---

## 아이콘 라이브러리

이번에는 활용도가 높은 "자주 쓰는 웹요소 아이콘 세트"를 React 컴포넌트로 만들어서 쉽게 사용하는 과정을 살펴보자.

물론 웹요소 아이콘 세트는 굳이 이러한 방식으로 만들지 않더라도 더 쉽고 간편하게 쓸 수 있는 대안이 존재한다. [Font Awesome](http://fontawesome.io/cheatsheet/){:target="_blank"}, [ionicons](http://ionicons.com/){:target="_blank"}, [Semantic-UI](http://react.semantic-ui.com/elements/icon){:target="_blank"} 등이 널리 쓰이고 있다.

그럼에도 불구하고 Custom Set을 만드는 이유는 이미지를 원하는대로 수정할 수 있고, 불필요한 아이콘은 프로젝트에 포함시키지 않음으로써 용량을 줄이는 등의 장점이 있기 때문이다.

#### 1) SVG 아이콘 파일 구하기

![svg-compound-path]({{ site.baseurl }}/assets/svg-icon-set.png)
<span></span>

[The Noun Project](https://thenounproject.com/){:target="_blank"}나 [Flaticon](http://www.flaticon.com/){:target="_blank"}과 같은 사이트에서 SVG 아이콘을 구할 수 있다. 두 사이트 모두 유사한 느낌의 아이콘들을 패키지로 제공하기 때문에 잘 활용하면 통일감 있는 디자인을 만들 수 있다.

#### 2) SVG 파일로 저장하기

![svg-compound-path]({{ site.baseurl }}/assets/svg-illust-size.png)
<span></span>

다운로드 받은 파일 중 실제 사용할 아이콘 영역을 복사한 뒤 64px * 64px의 새로운 문서에 붙여넣는다. 그리고 오브젝트의 가로세로 중 큰 쪽을 64px로 지정하여 오브젝트가 캔버스에 가득 차게 사이즈를 조정하고 정렬도구로 캔버스의 한가운데에 위치하게 만든다.

이렇게 하면 앞으로 만드는 다른 아이콘들도 동일한 비율로 사용할 수 있다. 벡터파일은 여러 곳에서 다양하게 활용할 수 있는 만큼 원본 소스를 일관된 형태로 가지고 있는 것이 중요하다.

또한 SVG파일로 저장하기 전 Compound Path를 만드는 과정도 진행한다.

![svg-compound-path]({{ site.baseurl }}/assets/svg-compound-path.png)
<span></span>

#### 3) React 컴포넌트 만들기

React에 SVG 컴포넌트를 만든다. 자세한 방법은 [이전 게시물](/notes/svg2)을 참고하자. 이번에는 정사각형 아이콘을 만들기 때문에 width, height 대신 size로 크기값을 받고, viewBox에 새로 만든 캔버스 사이즈인 0 0 64 64로 입력했다.


```jsx
import React, { Component } from 'react';

const svg = {}

class SVG extends Component {
  render() {
    return(
      <svg
      	x="0px" y="0px"
      	width={this.props.size}
      	height={this.props.size}
      	viewBox="0 0 64 64">
        <path
          fill={this.props.color}
          d={svg[this.props.name]}
        />
      />
    );
  }
}

export default SVG;
```

#### 4) 아이콘 패스 추가하기

SVG 파일을 열고 path 중 d로 시작하는 패스 부분의 값을 복사한다.
```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Generator: Adobe Illustrator 17.0.0, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
  <svg version="1.1" id="레이어_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="64px" height="64px" viewBox="0 0 64 64" enable-background="new 0 0 64 64" xml:space="preserve">
    <path fill="#040000" d="M58.68,8.737c-5.624-5.622-16.473-8.073-24.752-0.905l4.353,4.353c0.521,0.52,0.521,1.365,0,1.885 c-0.517,0.517-1.359,0.526-1.885,0l-5.335-5.333c-7.14-7.14-18.658-7.073-25.731,0c-7.087,7.085-7.127,18.608,0,25.732 l25.731,25.733c0.521,0.52,1.365,0.52,1.885,0L58.68,34.469C65.773,27.374,65.773,15.832,58.68,8.737z"/>
</svg>

```

그리고 아래와 같이 조금 전에 만든 React 컴포넌트의 SVG 객체 안에 JSON 형태의 배열로 추가한다. name에는 앞으로 사용할 아이콘 이름을 붙여주자.

```js
const svg = {
  heart: "M58.68,8.737c-5.624-5.622-16.473-8.073-24.752-0.905l4.353,4.353c0.521,0.52,0.521,1.365,0,1.885 c-0.517,0.517-1.359,0.526-1.885,0l-5.335-5.333c-7.14-7.14-18.658-7.073-25.731,0c-7.087,7.085-7.127,18.608,0,25.732 l25.731,25.733c0.521,0.52,1.365,0.52,1.885,0L58.68,34.469C65.773,27.374,65.773,15.832,58.68,8.737z"
}
```

#### 5) 아이콘 사용하기

이제 원하는 곳에 SVG 컴포넌트를 import한 뒤 아래와 같이 사용할 수 있다. 적절한 마크업과 함께 아이콘을 사용하자.

```jsx
import React, { Component } from 'react';
import SVG from '../../components/SVG';

export class Home extends Component {
  ....
  render() {
    return (
      <div className="like">
        <SVG name="heart" height="30px" color="#ff0000" />
        <span>{this.state.like}</span>
      </div>
    );
  }
}
```
<script>
    var i = 100;
    function buttonClick() {
        document.getElementById('inc').value = ++i;
    }
</script>
<div class="like-example">
	<div class="like-button" onclick="buttonClick()">
		<div class="inner-button">
			<img src="{{ site.baseurl }}/assets/heart.svg" />
			<input type="text" id="inc" value="100" disabled='disabled' />
		</div>
	</div>
</div>