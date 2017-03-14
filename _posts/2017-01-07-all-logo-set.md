---
title: 관계사 로고 이미지
updated: 2017-01-04 23:37
---

## 규칙

아임포트 관계사(카드/은행/통신사)들의 아이콘 세트이다. [아임포트 통계분석](https://analytics.iamport.kr/){:target="_blank"}의 차트 목록을 그리는데 사용하며, React에서 constant.js 파일로 만들어 관리한다. 레퍼런스와 마찬가지로 다양하게 쓸 수 있도록 svg 파일로 만들었는데, 이 과정에서 내가 정한 로고 이미지를 만드는 기본적인 규칙은 다음과 같다.

* 패스파인더로 공백영역을 제거한다.
* 개발에서 바로 사용할 수 있도록 아이템명으로 폴더를 만든다.
* 2x1 비율로 맞추되, 필요한 경우 1x1도 추가한다.
* 색상정보가 보존된 경우 color_를 붙인다.
* 향후 컬러테마를 추가한다면 white_나 black_도 확장할 수 있다.

![reference-logo-dir]({{ site.baseurl }}/assets/reference-logo-dir.png)

<div class="divider"></div>

## PG사

<script>
var pg_list = [
    {name:"KG이니시스", logo:"inicis"},
    {name:"나이스정보통신", logo:"nice"},
    {name:"JTNET", logo:"jtnet"},
    {name:"LG유플러스", logo:"lgu"},
    {name:"다날", logo:"danal"},
    {name:"KG모빌리언스", logo:"mobilians"},
    {name:"카카오페이", logo:"kakao"},
    {name:"Paypal Express",logo:"paypal"},
    {name:"페이코", logo:"payco"},
    {name:"시럽페이", logo:"syrup"},
    {name:"세틀뱅크", logo:"settlebank"},
    {name:"KICC", logo:"kicc"},
]
</script>

<ul class="logo-list">
<script>
for(var i=0; i<pg_list.length; i++){
  document.write("<li><div class='item' style='background-image:url({{ site.baseurl }}/assets/logo/pg/"+pg_list[i].logo+"/color_2x1.svg') /></div></li>")
}
</script>
</ul>

```js
export const PG_LIST = {
    "INC": {name:"KG이니시스", logo:"inicis"},
    "NIC": {name:"나이스정보통신", logo:"nice"},
    "JTN": {name:"JTNET", logo:"jtnet"},
    "LGU": {name:"LG유플러스", logo:"lgu"},
    "DNL": {name:"다날", logo:"danal"},
    "MOB": {name:"KG모빌리언스", logo:"mobilians"},
    "KKO": {name:"카카오페이", logo:"kakao"},
    "PPL": {name:"Paypal Express",logo:"paypal"},
    "PYC": {name:"페이코", logo:"payco"},
    "SYR": {name:"시럽페이", logo:"syrup"},
    "STB": {name:"세틀뱅크", logo:"settlebank"},
    "KIC": {name:"KICC", logo:"kicc"},
}
```

<div class="divider"></div>

## 신용카드

<script>
var card_list = [
    {name:"BC카드", logo:"bc"},
    {name:"광주카드", logo:"kwangjoo"},
    {name:"삼성카드", logo:"samsung"},
    {name:"신한카드", logo:"shinhan"},
    {name:"현대카드", logo:"hyundai"},
    {name:"롯데카드", logo:"lotte"},
    {name:"수협카드", logo:"soohyup"},
    {name:"씨티카드", logo:"citi"},
    {name:"NH카드", logo:"nh"},
    {name:"전북카드", logo:"jeonbook"},
    {name:"제주카드", logo:"jeju"},
    {name:"하나SK카드", logo:"hanask"},
    {name:"KB국민카드", logo:"kb"},
    {name:"우리카드", logo:"woori"},
    {name:"외환카드", logo:"keb"},
    {name:"우체국", logo:"post"},
    {name:"해외", logo:"etc"},
    {name:"기타", logo:"etc"},
]
</script>

<ul class="logo-list">
<script>
for(var i=0; i<card_list.length; i++){
  document.write("<li><div class='item' style='background-image:url({{ site.baseurl }}/assets/logo/card/"+card_list[i].logo+"/color_2x1.svg') /></div></li>")

}
</script>
</ul>

```js
export const CARD_LIST = {
    "361":{name:"BC카드", logo:"bc"},
    "364":{name:"광주카드", logo:"kwangjoo"},
    "365":{name:"삼성카드", logo:"samsung"},
    "366":{name:"신한카드", logo:"shinhan"},
    "367":{name:"현대카드", logo:"hyundai"},
    "368":{name:"롯데카드", logo:"lotte"},
    "369":{name:"수협카드", logo:"soohyup"},
    "370":{name:"씨티카드", logo:"citi"},
    "371":{name:"NH카드", logo:"nh"},
    "372":{name:"전북카드", logo:"jeonbook"},
    "373":{name:"제주카드", logo:"jeju"},
    "374":{name:"하나SK카드", logo:"hanask"},
    "381":{name:"KB국민카드", logo:"kb"},
    "041":{name:"우리카드", logo:"etc"},
    "044":{name:"외환카드", logo:"etc"},
    "071":{name:"우체국", logo:"etc"},
    "071":{name:"해외", logo:"etc"},
    "null":{name:"기타", logo:"etc"},
}
```

<div class="divider"></div>

## 은행

<script>
var bank_list = [
    {name:"기업은행", logo:"ibk"},
    {name:"국민은행", logo:"kb"},
    {name:"수협중앙회", logo:"soohyup"},
    {name:"농협은행", logo:"nh"},
    {name:"우리은행", logo:"woori"},
    {name:"SC은행", logo:"sc"},
    {name:"한국씨티은행", logo:"citi"},
    {name:"대구은행", logo:"dgb"},
    {name:"부산은행", logo:"bnk"},
    {name:"광주은행", logo:"kwangjoo"},
    {name:"경남은행", logo:"kyungnam"},
    {name:"우체국", logo:"post"},
    {name:"KEB하나은행", logo:"keb"},
    {name:"신한은행", logo:"shinhan"},
    {name:"지역농축협", logo:"local"},
    {name:"전북은행", logo:"jeonbook"},
    {name:"새마을금고 중앙회" ,logo:"mg"},
    {name:"제주은행", logo:"jeju"},
    {name:"신협중앙회", logo:"shinhyup"},
    {name:"기타", logo:"etc"},
]
</script>

<ul class="logo-list">
<script>
for(var i=0; i<bank_list.length; i++){
  document.write("<li><div class='item' style='background-image:url({{ site.baseurl }}/assets/logo/bank/"+bank_list[i].logo+"/color_2x1.svg') /></div></li>")

}
</script>
</ul>

```js
export const BANK_LIST = {
    "003":{name:"기업은행", logo:"ibk"},
    "004":{name:"국민은행", logo:"kb"},
    "007":{name:"수협중앙회", logo:"soohyup"},
    "011":{name:"농협은행", logo:"nh"},
    "020":{name:"우리은행", logo:"woori"},
    "023":{name:"SC은행", logo:"sc"},
    "027":{name:"한국씨티은행", logo:"citi"},
    "031":{name:"대구은행", logo:"dgb"},
    "032":{name:"부산은행", logo:"bnk"},
    "034":{name:"광주은행", logo:"kwangjoo"},
    "039":{name:"경남은행", logo:"kyungnam"},
    "071":{name:"우체국", logo:"post"},
    "081":{name:"KEB하나은행", logo:"keb"},
    "088":{name:"신한은행", logo:"shinhan"},
    "012":{name:"지역농축협", logo:"local"},
    "037":{name:"전북은행", logo:"jeonbook"},
    "045":{name:"새마을금고중앙회" ,logo:"mg"},
    "035":{name:"제주은행", logo:"jeju"},
    "048":{name:"신협중앙회", logo:"shinhyup"},
    "null":{name:"기타", logo:"etc"},
}
```

<div class="divider"></div>

## 통신사

<script>
var mobile_list = [
    {name:"KT",logo:"kt"},
    {name:"SKT",logo:"skt"},
    {name:"LGT",logo:"lguplus"},
    {name:"CJH",logo:"cjh"},
    {name:"ETC",logo:"etc"},
]
</script>

<ul class="logo-list">
<script>
for(var i=0; i<mobile_list.length; i++){
  document.write("<li><div class='item' style='background-image:url({{ site.baseurl }}/assets/logo/mobile/"+mobile_list[i].logo+"/color_2x1.svg') /></div></li>")

}
</script>
</ul>

```js
export const MOBILE_LIST = {
    "KT":{name:"KT", logo:"kt"},
    "SKT":{name:"SKT", logo:"skt"},
    "LGT":{name:"LGT", logo:"lguplus"},
    "CJH":{name:"CJH", logo:"cjh"},
    "etc":{name:"ETC", logo:"etc"},
}
```

