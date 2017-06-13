---
title: 맥에서 MySQL 초기암호 재설정
updated : 2017-06-09 19:20
---

### 맥에서 MySQL 설정하기

라라벨 개발환경을 세팅하기 위해 MySQL을 설치했는데, 1) 처음 발급해주는 관리자 비밀번호를 아무 생각없이 엔터치고 넘어가버렸다. 2) 무식하게 재설치해봤지만 비밀번호는 다시 알려주지 않더라 3) 비밀번호를 재설정하려고 검색하는데 옛날 버전의 내용들이 많아서 시키는게 잘 안 되더라 4) 거기다 아직 mysql에 익숙하지 않아서 버벅댔다. 다시 고생 안 하기 위해 (삽질한 내용은 괄호안에) 정리!

### 1. MySQL 맥버전 설치

가장 쉬운 방법은 [MySQL](https://dev.mysql.com/downloads/mysql/) 사이트에서 최신 버전의 .dmg 파일을 다운로드하는 것이다. 다운로드하기 위해서는 로그인을 해야 하는데 하단에 있는 No thanks ...를 누르면 로그인 없이도 다운로드할 수 있다. 설치하는 과정에서 초기 비밀번호를 랜덤하게 생성해서 제공하기 때문에 무의식적으로 엔터를 누르지 않도록 한다. (사실 그 이후로 다른 맥에 MySQL을 설치할 기회가 있어서 초기 비밀번호를 메모하고 정확하게 입력했지만 여전히 로그인이 안 되어서 매번 재설정 과정을 강제 복습함) 참고로 Homebrew로도 설치할 수 있는데, 관련 내용은 [여기](https://github.com/helloheesu/SecretlyGreatly/wiki/%EB%A7%A5%EC%97%90%EC%84%9C-mysql-%EC%84%A4%EC%B9%98-%ED%9B%84-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0)에 잘 정리되어 있다.

### 2. MySQL 서버 켜기
설치가 끝나고 맥의 시스템 환경설정에 가면 하단에 MySQL 메뉴가 생긴다. 여기 들어가면 클릭 한번으로 간단하게 서버를 켜고 끌 수 있다. MySQL에 접속하기 위해 서버를 켰다. 참고로 터미널 명령어로도 서버를 켜고 끌 수 있다.
```
sudo /usr/local/mysql/support-files/mysql.server start
sudo /usr/local/mysql/support-files/mysql.server stop
```
![step2]( {{ site.baseurl }}/assets/img/mysql-reset-password/setting.png)
![step2]( {{ site.baseurl }}/assets/img/mysql-reset-password/mysql-on.png)

### 3. 터미널에서 접속하기

MySQL 실행은 "/usr/local/mysql/bin/" 폴더에서 할 수 있다. (검색하다가 찾은 블로그에서 알려준대로 하다가 잘 안 되길래 뭐가 문제인가 봤더니 중간에 local을 빼먹어서 다른 폴더를 헤매고 있었던 것이었다!) 첫번째와 같이 경로로 이동해서 mysql을 실행하거나 또는 두번째처럼 붙여서 바로 실행할 수 있다. mysql을 실행하면 비밀번호를 물어보는데 분실한 상황이므로 새로 설정해야 한다.
```
cd /usr/local/mysql/bin/
sudo ./mysql
```
```
/usr/local/mysql/bin/mysql -uroot
```

### 4. 비밀번호 재설정

아래와 같이 입력하면 인증을 생략하고 안전모드로 데몬을 실행한다. 즉, 비밀번호 없이도 MySQL에 접속할 수 있게 된다. (여기서도 많이 헤맸다. 해당 경로로 이동해서 그대로 mysqld_safe --skip-grant-tables 명령어를 치면 실행할 수 없는 명령이라고 나오는데, 반드시 관리자 권한(sudo)로 실행하고 경로에도 ./를 붙여서 실행해야 한다) 그리고 이 단계에서 비밀번호를 물어보는 건 MySQL 비밀번호가 아닌 맥의 관리자 비밀번호다.
```
sudo /usr/local/mysql/bin/mysqld_safe --skip-grant-tables
```
위 명령어는 실행된 상태로 유지되므로 새로운 터미널 창을 열어서 MySQL에 접속한다. 이제 비밀번호를 묻지 않고 바로 접속이 된다. (예이!) 만약 접속이 잘 안 된다면 방금 전 실행한 명령어가 완전히 실행되었는지(=바람개비가 다 사라졌는지) 확인한다.
```
/usr/local/mysql/bin/mysql -uroot
```
접속한 뒤에는 아래와 같이 비밀번호를 root로 변경한다. password=('root')에 root 대신 원하는 비밀번호를 입력해도 된다. (참고로 5.7 버전 이전에는 set password=password('원하는 비밀번호')였는데 컬럼명이 바꼈다.[^1] 굳이 바뀐 컬럼명을 직접 보고자 한다면 use mysql;을 하고 show full columnes from user;를 치면 된다.)
```
mysql> use mysql; 
mysql> update user set authentication_string=password('root') where user='root';
```
마지막으로 변경사항을 적용하기 위해 flush privileges 명령어를 실행한다.
```
mysql> flush privileges;
```

### 5. MySQL 접속하기
다시 MySQL에 접속하면 잘 되는 것을 확인할 수 있다. 만약 접속이 거부되면 -uroot -proot와 같이 비밀번호까지 붙여서 한번에 실행하는 것을 시도한다.
```
/usr/local/mysql/bin/mysql -uroot
/usr/local/mysql/bin/mysql -uroot -proot
```
그런데 접속 후 명령을 실행하게 되면 다음과 같은 에러가 발생한다. ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement. 이 경우 아래 명령어를 실행하면 정상적으로 MySQL 명령을 실행할 수 있다.[^2]
```
mysql> use mysql; 
mysql> set password = password('원하는 비밀번호');
```
<div class="divider"></div>

[^1]:Junee01 - [MySQL - root 비밀번호 변경 오류 관련 포스팅(16.02.21 수정)](http://m.blog.naver.com/potter777777/220619477175)
[^2]:kogun82 - [MySQL 5.7.9 릴리즈 변화된 root 비밀번호 변경하기](http://kogun82.tistory.com/122)
