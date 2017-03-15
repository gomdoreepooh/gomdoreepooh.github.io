---
title: 레퍼런스 로고 이미지
updated: 2017-01-04 23:37
---

## 아임포트 레퍼런스

[아임포트 홈페이지](http://iamport.kr/pricing){:target="_blank"}에 게재한 아임포트를 사용하는 가맹점들의 로고들이다. 구글 이미지검색에서 비트맵 로고를 찾은 뒤 벡터로 변환하여 svg 파일로 만들고, 배열로 불러와 사용한다. 전체 파일을 다운로드하거나 신규 가맹점을 추가하는 등 일련의 작업은 아임포트 홈페이지 [프로젝트](https://bitbucket.org/siotiamport/iamport-www-new){:target="_blank"}에서 진행할 수 있다.

<script>
var referenceList = [
  {name:"셀잇", logo:"sellit", url:"https://www.withsellit.com/"},
  {name:"번개장터", logo:"bunjang", url:"http://bunjang.co.kr/"},
  {name:"눔코리아", logo:"noom", url:"http://noom.co.kr/"},
  {name:"스마트스터디", logo:"smartstudy", url:"http://www.smartstudy.co.kr/"},
  {name:"스트라입스", logo:"stripes", url:"http://stripes.co.kr/"},
  {name:"프렌트립", logo:"frientrip", url:"http://www.frientrip.co.kr/"},
  {name:"샤넬코리아", logo:"chanel", url:"https://chaneln5leaushop.co.kr/"},
  {name:"PMO", logo:"pmo", url:"http://peaceminusone.com/"},
  {name:"위즈돔", logo:"wisdome", url:"http://www.wisdo.me/"},
  {name:"스포카", logo:"spoqa", url:"https://www.spoqa.com/"},
  {name:"카닥", logo:"cardoc", url:"http://www.cardoc.co.kr/m/"},
  {name:"Yellostory", logo:"yellostory", url:"http://yellostory.co.kr/company"},
  {name:"바로풀기", logo:"bapul", url:"https://www.bapul.net/"},
  {name:"웨이웨어러블", logo:"helloway", url:"http://helloway.co/"},
  {name:"파이콘코리아", logo:"pycon", url:"http://www.pycon.kr/2016apac/"},
  {name:"와이퍼", logo:"yper", url:"http://yper.co.kr/"},
  {name:"스페이스클라우드", logo:"spacecloud", url:"http://www.spacecloud.kr/"},
  {name:"원모먼트", logo:"onemoment", url:"http://www.1moment.co.kr/ko/?gclid=CKiNyITzycsCFYGavAodWMAG1g"},
  {name:"아그레아블", logo:"shoplink", url:"https://www.shoplink.cc/"},
  {name:"링글잉글리쉬", logo:"ringle", url:"https://www.ringleplus.com/"},
  {name:"마인드스케일", logo:"mindscale", url:"http://mindscale.kr/"},
  {name:"컷앤컬", logo:"cutandcurl", url:"http://cutandcurl.co.kr/"},
  {name:"에이팀벤처스", logo:"ateamventures", url:"http://ateamventures.com/"},
  {name:"올스테이", logo:"allstay", url:"http://www.allstay.kr/"},
  {name:"콩콩", logo:"congkong", url:"https://www.congkong.net/"},
  {name:"맵씨닷컴", logo:"mapssi", url:"http://www.mapssi.com/"},
  {name:"원투웨어", logo:"wanttowear", url:"http://wanttowear.kr/"},
  {name:"퍼블리", logo:"publy", url:"http://publy.co/"},
  {name:"리얼씨리얼", logo:"realseereal", url:"http://realseereal.com/"},
  {name:"에스크에이드", logo:"askdjango", url:"https://ask.festi.kr/"},
  {name:"닥스웨이브", logo:"docswave", url:"https://www.docswave.com/ko"},
  {name:"플러닝", logo:"flearning", url:"http://www.flearning.net/"},
  {name:"로아컨설팅", logo:"roaconsulting", url:"http://www.roaconsulting.co.kr/kor/main/"},
  {name:"페달링", logo:"pedaling", url:"http://www.pedaling.is/"},
  {name:"SCALLOP", logo:"scallop", url:"http://www.scallop.co.kr/"},
  {name:"백준온라인저지", logo:"baekjoon", url:"https://www.acmicpc.net/"},
  {name:"히빈드라이", logo:"heebeandry", url:"https://heebeandry.com/"},
  {name:"숨고", logo:"soomgo", url:"https://soomgo.com/"},
  {name:"잉큼잉큼", logo:"inkminkm", url:"http://www.inkminkm.co.kr/"},
  {name:"올버스", logo:"allbus", url:"https://allbus.kr/"},
  {name:"코스모스팜", logo:"cosmosfarm", url:"http://www.cosmosfarm.com/"},
]  
</script>

<style>
.logo-list {
  list-style-type: none;
  margin: 0;
  padding: 0;
  *zoom: 1;
  margin: 0 -10px;
}
.logo-list li {
  width: 25%;
  float: left;
}
.logo-list li .item {
  border: 1px solid #ddd;
  height: 50px;
  margin: 10px;
  text-align: center;
  border-radius: 2px;
  background-size: 60%;
  background-position: 50% 50%;
  background-repeat: no-repeat;
}
.logo-list:after {
  clear: both;
  display: block;
  content: '';
}
</style>

<ul class="logo-list">
<script>
for(var i=0; i<referenceList.length; i++){
  document.write("<li><a href="+referenceList[i].url+" target='_blank' title='"+referenceList[i].name+"'><div class='item' style='background-image:url({{ site.baseurl }}/assets/logo/references/"+referenceList[i].logo+".svg')></div></a></li>")
}
</script>
</ul>


```js
referenceList = [
  {name:"셀잇", logo:"sellit", url:"https://www.withsellit.com/"},
  {name:"번개장터", logo:"bunjang", url:"http://bunjang.co.kr/"},
  {name:"눔코리아", logo:"noom", url:"http://noom.co.kr/"},
  {name:"스마트스터디", logo:"smartstudy", url:"http://www.smartstudy.co.kr/"},
  {name:"스트라입스", logo:"stripes", url:"http://stripes.co.kr/"},
  {name:"프렌트립", logo:"frientrip", url:"http://www.frientrip.co.kr/"},
  {name:"샤넬코리아", logo:"chanel", url:"https://chaneln5leaushop.co.kr/"},
  {name:"PMO", logo:"pmo", url:"http://peaceminusone.com/"},
  {name:"위즈돔", logo:"wisdome", url:"http://www.wisdo.me/"},
  {name:"스포카", logo:"spoqa", url:"https://www.spoqa.com/"},
  {name:"카닥", logo:"cardoc", url:"http://www.cardoc.co.kr/m/"},
  {name:"Yellostory", logo:"yellostory", url:"http://yellostory.co.kr/company"},
  {name:"바로풀기", logo:"bapul", url:"https://www.bapul.net/"},
  {name:"웨이웨어러블", logo:"helloway", url:"http://helloway.co/"},
  {name:"파이콘코리아", logo:"pycon", url:"http://www.pycon.kr/2016apac/"},
  {name:"와이퍼", logo:"yper", url:"http://yper.co.kr/"},
  {name:"스페이스클라우드", logo:"spacecloud", url:"http://www.spacecloud.kr/"},
  {name:"원모먼트", logo:"onemoment", url:"http://www.1moment.co.kr/ko/?gclid=CKiNyITzycsCFYGavAodWMAG1g"},
  {name:"아그레아블", logo:"shoplink", url:"https://www.shoplink.cc/"},
  {name:"링글잉글리쉬", logo:"ringle", url:"https://www.ringleplus.com/"},
  {name:"마인드스케일", logo:"mindscale", url:"http://mindscale.kr/"},
  {name:"컷앤컬", logo:"cutandcurl", url:"http://cutandcurl.co.kr/"},
  {name:"에이팀벤처스", logo:"ateamventures", url:"http://ateamventures.com/"},
  {name:"올스테이", logo:"allstay", url:"http://www.allstay.kr/"},
  {name:"콩콩", logo:"congkong", url:"https://www.congkong.net/"},
  {name:"맵씨닷컴", logo:"mapssi", url:"http://www.mapssi.com/"},
  {name:"원투웨어", logo:"wanttowear", url:"http://wanttowear.kr/"},
  {name:"퍼블리", logo:"publy", url:"http://publy.co/"},
  {name:"리얼씨리얼", logo:"realseereal", url:"http://realseereal.com/"},
  {name:"에스크에이드", logo:"askdjango", url:"https://ask.festi.kr/"},
  {name:"닥스웨이브", logo:"docswave", url:"https://www.docswave.com/ko"},
  {name:"플러닝", logo:"flearning", url:"http://www.flearning.net/"},
  {name:"로아컨설팅", logo:"roaconsulting", url:"http://www.roaconsulting.co.kr/kor/main/"},
  {name:"페달링", logo:"pedaling", url:"http://www.pedaling.is/"},
  {name:"SCALLOP", logo:"scallop", url:"http://www.scallop.co.kr/"},
  {name:"백준온라인저지", logo:"baekjoon", url:"https://www.acmicpc.net/"},
  {name:"히빈드라이", logo:"heebeandry", url:"https://heebeandry.com/"},
  {name:"숨고", logo:"soomgo", url:"https://soomgo.com/"},
  {name:"잉큼잉큼", logo:"inkminkm", url:"http://www.inkminkm.co.kr/"},
  {name:"올버스", logo:"allbus", url:"https://allbus.kr/"},
  {name:"코스모스팜", logo:"cosmosfarm", url:"http://www.cosmosfarm.com/"},
]
```