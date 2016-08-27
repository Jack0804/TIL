
## Why?
> 프로젝트 진행 중, 쇼핑몰(Web)은 Node서버를 연동하여서 진행해보라는 PM(강사)님의 말씀으로 Node서버 구현을 맡게되었다.
 시작하면서 느끼는것은 Spring-Tomcat 서버 적용할 때와 느낌이 비슷하여 이해하는부분에서는 수월하게 이해가 진행되었다.

## Refer
> [생활코딩 - Nodejs](https://opentutorials.org/course/2136/11850)
> [Nodejs 강좌 Blog](https://velopert.com/133)
> 
>  현재까지 두개의 사이트를 번갈아 가며 배우고 있다.
>   생활코딩은 이론 위주로 , Blog는 Express의 사용 및 실습 위주로 진행 중.

## #Node.js란?
> * 자바스크립트가 등장 -> 동적인 Web으로 변화
* 자바스크립트 -> WEB의 울타리안에서 활동범위로 한정되어있었다.
* 구글에서 자바스크립트 기반의 V8엔진 오픈소스 공개.
   Web이 아닌곳에서도 사용이 가능해짐(탈Web화)
(V8엔진 -> 브라우저의 성능을 높이기위한 자바스크립 엔진)
* NodeJS -> V8엔진사용 + Event-driven(자바스크립의 개발방식) + non-blockingIO
* V8엔진 이전 -> javascript는 web에서만 동작 / V8엔진 이후 -> Node가 등장하여 서버로 사용가능해짐.
* RunTime 이란? Javascript가 운영되어지는 환경 -> WebBrowser 와 Nodejs(Server)
* JavaScript를 통하여 WebBrowser 와 Nodejs 두군데에서 사용가능.

##Nodejs 장점
* 속도가 빠르다.
* 웹브라우저에서도 JS사용 / 서버에서도 JS 사용하기 때문에 통일성을 가지고 어플리케이션을 만들수있다.

# #간단한 웹 에플리케이션 만들기

##인터넷 동작방법

 * 컴퓨터<->컴퓨터 연결되는것(인터넷)
 * **서버**는 클라이언트에서 요청한 내용을 응답(제공)
 * 웹브라우저가 설치되어진 컴퓨터 -> 클라이언트
 * 서버컴퓨터에서 서버가 여러가지 있을경우 도메인(주소값) 입력 시, 어떤 서버가 응답해야하는가?
 * 포트(PORT) -> 0~65535개의 포트가 있으며, 이중에 하나(예:80번)에 웹 서버를 연결(80번 포트 Listen)
 * 사용자가 http://a.com:80 으로 입력 시, 80포트로 접속 -> 80번포트로 연결된 웹 서버 연결.





## #소스코드
###Nodejs에서 제공하는 기본 코드(웹 서버)
>Refer
>https://nodejs.org/ko/about/
```javascript
//Server.js
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
*첨부파일에서 Server.js 실행.
