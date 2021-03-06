---
title: Node.js에서 Ajax로 데이터 통신
updated : 2017-05-12 19:20
---

## URL ROUTING 처리하기

angularJS와 react에서 JSON 형식의 데이터를 다루는 방법을 익히고 나니 이제 서버와의 데이터 통신 방법이 궁금해졌다. 그래서 Node.js에서 Ajax 방식으로 데이터를 주고받는 방법을 [Inflearn 강좌](https://www.inflearn.com/course/node-js-%EC%9B%B9%EA%B0%9C%EB%B0%9C/)로 공부했다.

### 1. 새 프로젝트를 만들고 express를 설치한다.

```
mkdir node && cd node
npm init
npm install express —save
```

### 2. app.js 파일을 작성한다.
```js
var express = require('express')
var app = express()
app.listen(3000, function(){
  console.log("start! express server is running on port 3000")
})
```

### 3. 참고로 node는 비동기로 동작한다.
```js
var express = require('express')
var app = express()
app.listen(3000, function(){
  console.log("this line will be at the end")
})
for(var i=0; i<20; i++){
  console.log("this is line number " + i)
}
```

### 4. 서버는 nodemon으로 실행한다.
```
npm install nodemon -g
nodemon app.js
```

### 5. GET 방식의 요청을 처리한다.
```js
app.get('/', function(req,res){
  res.send("<h1>안녕하세요</h1>")
  res.sendFile( __dirname + "/public/main.html")
})
```

### 6. Static 디렉토리를 express에 등록한다.
```js
app.use(express.static('public'))
```

### 7. form.html에 폼 양식을 만든다.
```html
<form action="/email_post"  method="post">
  email : <input type="text" name="email">
  <input type="submit">
</form>
```

### 8. bodyParser를 이용해 POST 요청을 처리한다.
```
npm install body-parser -save
```
```js
var bodyParser = require('body-parser')
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended:true}))

app.post('/email_post', function(req,res){
  console.log(req.body)
  res.send("welcome! " + req.body.email)
})
```

## Ajax 통신 추가하기

위에서 한 FORM 방식이 URL이 바뀐다면, Ajax는 한 페이지 안에서 새로고침 없이 비동기 형태로 데이터를 주고받을 수 있는 방식이다. 폼 화면은 동일하게 활용하고, 아래와 같이 통신부분만 추가한다.

### 1. ajax 요청을 보낼 버튼을 그린다.
```html
<button class="ajaxsend">ajaxsend</button>
```

### 2. 이벤트리스너에 등록한다.
```html
<script>
  document.querySelector('.ajaxsend').addEventListener('click', function(){
    // 입력값 위치를 찾아 변수에 담고
    var inputdata = document.forms[0].elements[0].value;
    // sendAjax 함수를 만들고 URL과 data를 전달
    sendAjax('http://127.0.0.1:3000/ajax_send_email', inputdata)
  })
</script>
```

### 3. XMLHttpRequest로 데이터를 보내고 받는다.
```html
<script>
function sendAjax(url, data){
  
  // 입력값을 변수에 담고 문자열 형태로 변환
  var data = {'email' : data};
  data = JSON.stringify(data);

  // content-type을 설정하고 데이터 송신
  var xhr = new XMLHttpRequest();
  xhr.open('POST', url);
  xhr.setRequestHeader('Content-type', "application/json");
  xhr.send(data);
  
  // 데이터 수신이 완료되면 표시
  xhr.addEventListener('load', function(){
    console.log(xhr.responseText);
  });
}
</script>
```

### 4. app.js에서 Ajax 요청을 처리한다.
```js
app.post('/ajax_send_email', function(req, res){
  console.log(req.body.email);
  var responseData = {'result' : 'ok', 'email' : req.body.email}
  res.json(responseData);
  // 서버에서는 JSON.stringify 필요없음
})
```

### 5. 데이터 수신 부분을 수정해 결과를 표시한다.
```html
<div class="result"></div>
<script>
  xhr.addEventListener('load', function(){
    // 문자열 형식으로 변환
    var result = JSON.parse(xhr.responseText);
    // 데이터가 없으면 return 반환
    if(result.result !== 'ok') return;
    // 데이터가 있으면 결과값 표시
    document.querySelector(".serult").innerHTML = result.email;
  });
</script>
```

