---
title: 비트맵 이미지를 벡터로 변환하기
updated : 2017-01-20 19:20
---

## 비트맵 이미지 준비

웹사이트에 SVG 형태로 이미지를 넣기 위해서는 벡터 형태의 이미지 파일이 있어야 한다. 하지만 로고파일의 경우 벡터 파일을 구하기가 쉽지 않다. 그래서 상대적으로 구하기 쉬운 비트맵 이미지를 찾은 뒤 변환한다.

비트맵 이미지를 벡터로 변환하는 방법은 여러가지가 있다. 일러스트에서 비슷한 기능을 제공하는 사실을 알기 전까지는 [Vectormagic](https://vectormagic.com/)이라는 사이트를 이용했다. 매월 7달러 정도의 비용으로 벡터변환을 무제한으로 할 수 있다.

변환작업을 진행하기 위해 [구글 이미지 검색](http://images.google.com/)에서 외환카드 로고를 검색하고 다운로드받았다.

![step1]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step1.png)

<div class="divider"></div>

## 이미지추적

Illustrator에서 다운받은 비트맵 이미지파일을 연 뒤, 이미지파일을 선택하고 이미지 추적 > 충실도가 낮은 사진을 선택한다.
이미지에 따라 [적절한 옵션](https://helpx.adobe.com/kr/illustrator/using/image-trace.html)을 선택해서 최적화된 추적 결과를 만들 수 있다. 이미지추적을 한 뒤에는 그 옆에 있는 확장 버튼을 눌러 추적결과를 패스로 만들고 그룹풀기를 한다.

![step2]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step2.png)

<div class="divider"></div>

## 패스파인더

배경을 제거하고 아래 Before & After 예시처럼 패스파인더로 공백을 뚫어준다.
영어 알파벳이나 한글자음 중에는 빈 공간이 포함되는 경우가 많은데,
Illustrator에서는 기존의 패스 위에 흰색의 패스를 추가로 만들기 때문에 패스파인더로 이 부분을 공백으로 변환해주는 것이 좋다.

물론 대개 흰색의 바탕 위에 로고를 올리므로 굳이 이렇게까지 해주지 않아도 된다.
다만, 만약 회색이나 또는 다른 배경색에 로고를 올릴 상황이 생긴다면 흰색이 도드라져 보이게 된다. 다소 귀찮은 작업이지만 해놓는 것을 추천하고 싶다.

![step3]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step3.png)
![step4]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step4.png)

<div class="divider"></div>

## 위치정렬

기존의 로고파일과 동일한 400px * 200px의 캔바스를 만들고, 지금까지 작업한 개체를 복사해서 붙여넣는다. 그리고 가로 사이즈를 400px로 변경한 뒤, 정렬도구로 캔바스의 한가운데에 위치하게 만든다. 크기변경과 정렬을 하기 전 반드시 개체 전체를 그룹으로 만들어야 한다.

![step5]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step5.png)

<div class="divider"></div>

## 저장하기

개발 프로젝트에서 이미지 폴더를 그대로 사용할 수 있도록 몇가지 규칙을 도입했다. 아래 방식으로 저장하면 명단을 JSON으로 만든 뒤 쉽게 프로젝트에서 불러올 수 있다. 아임포트 홈페이지와 통계분석을 만들 때 사용했다.
* 아이템명으로 폴더를 만든다.
* 파일이름은 색상_비율.svg로 통일한다. (예:color_2x1.svg)
* 2x1 비율을 기본으로 하되, 필요한 경우 1x1도 추가한다.
* 색상정보가 보존된 경우 color_를 붙인다.
* 향후 컬러테마를 추가한다면 white_나 black_으로 종류를 늘린다.

![step6]( {{ site.baseurl }}/assets/img/bitmap-to-vector/step6.png)

작업의 결과는 [아임포트 레퍼런스 로고 이미지](/notes/ref-logo-set)와 [아임포트 관계사 로고 이미지](/notes/all-logo-set)에서 볼 수 있다.