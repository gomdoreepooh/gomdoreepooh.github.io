---
title: www 개발환경 설정 (Laravel)
category: 개발
page : 2/3
---

### 프로젝트 복사
```
git clone https://namusiot@bitbucket.org/siotiamport/iamport-www-new.git
```

### MAMP 설치
![MAMP](https://www.mamp.info/en/images/screenshots/en_mamp-start.jpg)

### 프로젝트 폴더에 .env 파일 추가

	APP_ENV=local
	APP_KEY=base64:xWE3pYrTlmoEE8fqzLr8OZR8CElZQozgdNlYhSUnF84=
	APP_DEBUG=true
	APP_LOG_LEVEL=debug
	APP_URL=http://localhost
	
	DB_CONNECTION=mysql
	DB_HOST=127.0.0.1
	DB_PORT=3306
	DB_DATABASE=iamport
	DB_USERNAME=root
	DB_PASSWORD=root
	
	CACHE_DRIVER=file
	SESSION_DRIVER=file
	QUEUE_DRIVER=sync
	
	REDIS_HOST=127.0.0.1
	REDIS_PASSWORD=null
	REDIS_PORT=6379
	
	MAIL_DRIVER=smtp
	MAIL_HOST=mailtrap.io
	MAIL_PORT=2525
	MAIL_USERNAME=null
	MAIL_PASSWORD=null
	MAIL_ENCRYPTION=null

DB 연동 시 [구글문서](https://docs.google.com/document/d/1LdF2NSJrOlW7-JgBXQF4Hi-dzcTjHa8EwFRUy0Z8iiM/edit) 참조