
## Why?
> 프로젝트 진행 중, 쇼핑몰(Web)은 Node서버를 연동하여서 진행해보라는 PM(강사)님의 말씀으로 Node서버 구현을 맡게되었다.
 시작하면서 느끼는것은 Spring-Tomcat 서버 적용할 때와 느낌이 비슷하여 이해하는부분에서는 수월하게 이해가 진행되었다.

## Refer
> [생활코딩 - Nodejs](https://opentutorials.org/course/2136/11850)
> [Nodejs 강좌 Blog](https://velopert.com/133)
> 
>  현재까지 두개의 사이트를 번갈아 가며 배우고 있다.
>   생활코딩은 이론 위주로 , Blog는 Express의 사용 및 실습 위주로 진행 중.

#간단한 웹 에플리케이션 만들기

##인터넷 동작방법

 * 컴퓨터<->컴퓨터 연결되는것(인터넷)
 * **서버**는 클라이언트에서 요청한 내용을 응답(제공)
 * 웹브라우저가 설치되어진 컴퓨터 -> 클라이언트
 * 서버컴퓨터에서 서버가 여러가지 있을경우 도메인(주소값) 입력 시, 어떤 서버가 응답해야하는가?
 * 포트(PORT) -> 0~65535개의 포트가 있으며, 이중에 하나(예:80번)에 웹 서버를 연결(80번 포트 Listen)
 * 사용자가 http://a.com:80 으로 입력 시, 80포트로 접속 -> 80번포트로 연결된 웹 서버 연결.

##소스코드
###Nodejs에서 제공하는 기본 코드(웹 서버)
>Refer
>https://nodejs.org/ko/about/

```javascript
const http = require('http');
const hostname = '127.0.0.1';
const port = 1337; // 포트번호=1337

//CreateServer를 통하여 서버생성 
http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello World\n');
}).listen(port, hostname, () => { //listen동작 실시(1337포트번호로 접속했을 때) 
  console.log(`Server running at http://${hostname}:${port}/`);
}); 
```


# Express 도입

## Express들어가기전 웹 서버(위)소스설명
 
 * IP -> 컴퓨터 식별자, Port -> 서버 식별자
 
> listen(port, hostname, () => {       });

* server.listen(port, hostname) -> server가 hostname:port URL로 요청값이 들어오는것을 대기중
* listen동작은 동작시간이 걸릴수있으므로 비동기 방식 -> Callback방식으로처리.
 
> var server = http.createServer(function(req, res){ });
  
* 서버 생성, 요청 -> REQ 응답 -> RES

# Express-간단한 웹에플리케이션 만들기
  
##소스코드
>Refer
http://expressjs.com/ko/starter/hello-world.html


```javascript
var express = require('express');
var app = express();

app.get('/', function (req, res) {
  res.send('Hello World!');
});

// 추가
app.get('/login', function (req, res) {
	res.send('Login Please');
});

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});

```

> **설명**
> 
- 'express'를 import.
- import한 express함수의 객체 app변수 생성. 
- 3000번 포트를 Listen, 성공시 function내용 실행.
- app.get() -> "Get"방식으로 URL(/) 접속 시, 응답으로 **"Hello World"**
- URL(/login) 접속 시, 응답으로 **"Login Please"**
-  위에 2개의 app.get처럼 각각의 주소 값 입력 시,  주소 값에 정해진 내용으로 가는 Get메소드를 **Router**라고 부르며 그 URL을 입력된 주소값에 따라 나뉘어주는 행위를 **Routing**



 

 
   	
