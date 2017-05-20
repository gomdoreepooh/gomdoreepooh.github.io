---
title: 통계분석 서비스 기획
category: 기획
page : 1/4
---

## 아임포트

우선 아임포트에 대해 그동안 쓰여진 글들을 읽어보자. 날짜를 파악할 수 있는 선에서 최신 순으로 정렬했다. 이 글들을 읽어보면 아임포트가 어떻게 만들어졌으며, 누구에게 어떻게 쓰이는 서비스인지 이해할 수 있다.
* 더팀스의 [시옷 페이지](https://www.theteams.kr/teams/detail/7)
* 샵미디어의 [온라인 결제는 왜 어렵고 해결책은 무엇일까](https://www.shopmag.kr/article.html?ma_uid=122)
* 플래텀의 [인터뷰 (장지윤)](http://platum.kr/archives/62935)
* 더팀스의 [인터뷰 (안현석)](https://brunch.co.kr/@vinnie/10)
* 플래텀의 [카카오페이 연동지원 기사](http://platum.kr/archives/53679)
* 디캠프의 [시옷 페이지](http://dcamp.kr/startup/59)
* [아임포트 서비스 소개서](https://www.slideshare.net/jangbora/ss-45572363)

위 글들에 따르면 아래 3가지 상황을 확인할 수 있다. 비즈니스의 차원에서 보자면 아임포트는 시장참여자의 다양한 이해관계로 시장에서 해결되지 않고 있는 문제를 정확히 진단하고 해결하는 서비스다.
1. 결제를 연결하는 기술은 매우 뒤쳐져 있지만 PG사는 개선하지 않는다.
2. 다양한 결제 방식이 출현하면서 시장과 기술은 더욱 복잡해졌다.
3. 쇼핑몰이 아닌 새로운 형태의 결제를 원하는 비즈니스들이 많아졌다.

이를 뒤집어 다시 보면 아임포트의 문제해결 방법을 알 수 있다. 특히 3번의 경우 이러한 이유로 PG사 입장에서 시옷을 호스팅사로 볼 것인지에 대한 논란도 있는데, 그만큼 기존에는 생각하지 못했던 새로운 시도로 평가할 수 있다.
1. PG사의 구형 기술을 개선한 최신 기술로 고객에게 제공한다.
2. 여러 결제 방식을 표준화하여 지원함으로써 다양한 니즈에 대응한다.
3. 올인원 솔루션 대신 결제를 제외한 파트에 자율성을 준다.

## 통계분석

통계분석은 위에서 언급한 것 이상으로 "이용자에게 어떤 가치를 더 제공할 수 있을지"라는 고민에 대한 답이다. 결제 과정에서 생성된 RAW 데이터를 유의미한 지표로 보기 쉽게 만들어주며, 이를 통해 이용자가 데이터에 기반한 합리적인 의사결정을 할 수 있게 돕는다. 아래는 아임포트 통계분석의 지향점을 알 수 있는 인터뷰 기사이며, 보다 자세한 통계분석의 효용은 [서비스 소개서 키노트](/notes/iamport-analytics-kenotes)에서 볼 수 있다.

> 지금 기술은 사람들이 어떤 사이트에서 배너 광고를 눌러 쇼핑몰에 진입했는지, 상품을 클릭은 했는지, 장바구니에 담았는지, 어떤 페이지까지 들어왔다가 이탈했는지 정보를 모두 트래킹할 수 있는 수준이다. 그런데 결제 중 어떤 단계에서 실패했는지는 알 수 없다. 결제 창과 보안 프로그램에서 일어난 일은 쇼핑몰에서 수집할 수 없는 데이터기 때문이다. 우리는 결제 과정에서 일어난 모든 일을 최대한까지 수집해 데이터로 제공하면 충분한 인사이트가 될 거라고 본다. 만약, 데이터를 분석해보니 크롬 최신 버전에서는 결제 실패율이 10% 미만인데 IE 10 이하 버전에서는 30% 이상으로 나온다면 결제 테스트를 IE 중심으로 진행하는 등 의사결정을 내릴 수 있고, 결제 오류 문제를 겪는 고객 대응도 더욱 신속해지니까. 

## 기획문서

통계분석에 들어갈 각종 지표를 설계하는 과정은 아래 기획문서들에서 볼 수 있다. 시옷 구성원이면 열람 및 수정이 가능하도록 모든 파일의 권한을 변경했다.

* [가맹점관리자 페이지 2.1](https://docs.google.com/presentation/d/1HKQHSLCBth3z4LbIdUNq5QzcLbpY0BvqxyEpefvBHPw/edit#slide=id.p)
* [관리자 페이지 통계분석 지표 v0.2](https://docs.google.com/spreadsheets/d/1GY7zXdPP0cYSdLUOe3wfc8pJGxdBexThUe1WKTQsFvE/edit#gid=0)
* [관리자 페이지 통계분석 지표 v0.2 (추가)](https://docs.google.com/spreadsheets/d/1w-r814JAJOR1uqvFI96wU4-7pQMt08RQgV0bFfSBiPk/edit#gid=0)
* [아임포트 통계차트](https://docs.google.com/presentation/d/13tTZgBNXSTihiKCmD3C2HhzFfvqsxjxQ2NTyfjrwZUY/edit#slide=id.g18bcdf7e49_0_0)
* [통계분석 수정요청 사항 (1~10차)](https://docs.google.com/presentation/d/1GxGlLyMjd3gAck12fwWuYLyM-s8sduRcpjgs6j0OpAA/edit#slide=id.g19bbdee121_0_27) 
* [통계분석 서버구조](https://docs.google.com/presentation/d/1EK2tFEA_5Tj6csG3yRAuAr-qam_upZEHSfFwZ9nVnV8/edit#slide=id.p)