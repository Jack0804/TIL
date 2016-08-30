
## # Express를 사용한 HTML 라우팅(Routing)
----

### Why?
> 
 * 프로젝트 방향이 Node는 웹 화면을 띄우기위한 웹 서버 역활로 확정.
 * 데이터는 Spring서버를 이용하기로 결정.
 * 따라서 Node에서의 역할은 라우터를 이용하여 주소별로 웹을 나뉘어주는 역할.


----

### How ?
> 
* Server / Route / View로 구성하여 역할을 구분.
* Server - 'Express' 사용, EJS사용 , 라우터 경로 설정
* Router - 접속경로( 회사 / 고객페이지) 에 따라 경로구분.
* View  -  Html기반의 화면소스 (+부트스트랩)
 
----

### Problem
> 
 생활 코딩 및 블로그에서는 화면부분에 HTML이 아닌 EJS를 사용하여 출력을 하는데,
 그렇게되면 현재 html로 제작된 페이지를 모두 ejs로 변환해야한다.
`` 라우터(Router)에서 EJS가 아닌 HTML을 사용하는 방법을 찾자.``

----

### 소스코드

### Server.js
```javascript
/**
 * Created by JK on 2016-08-30.
 */

// Express 서버생성
var express = require('express');
var app = express();

// 10-1 내용 추가
var bodyParser = require('body-parser');

// express-session이 error발생 -> Cmd -> "npm install express-session" 으로 설치완료.
var session = require('express-session');
var fs = require("fs")

// 서버가 읽을 수 있도록 HTML 의 위치를 정의해줍니다.
app.set('views', __dirname + '/views');

// 서버가 HTML 렌더링을 할 때, EJS엔진을 사용하도록 설정합니다.
app.set('view engine', 'ejs');
app.engine('html', require('ejs').renderFile);

var server = app.listen(3000, function(){
    console.log("Express server has started on port 3000")
});

// 스타일(CSS) 적용하기
app.use(express.static('public'));

// "localhost:3000/dudukri"으로 접속 -> 농부페이지
var routes = require('./routes/dudukri_server_html');
app.use('/dudukri', routes);

var users = require('./routes/users');
app.use('/users', users);
```

----


### Routes(라우터)

```javascripit
/**
 * Created by JK on 2016-08-30.
 */

module.exports = function(app)
{
    console.log("START Dudukri")

    app.get('/', function(req, res){

        console.log("START /")
        res.render('index.html');
    })

    app.get('/company', function(req, res){

        console.log("start dudukri/company");

        res.render('dudukri_company/main.html');
    })

    app.get('/farmer', function(req, res){

        res.render('dudukri_farmer/main.html');
    })
}
```

----
#### View(Html소스)
(로그인 부분 일부 예시)
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootsrtap Free Admin Template - SIMINTA | Admin Dashboad Template</title>
    <!-- Core CSS - Include with every page -->
    <link href="assets/plugins/bootstrap/bootstrap.css" rel="stylesheet" />
    <link href="assets/font-awesome/css/font-awesome.css" rel="stylesheet" />
    <link href="assets/plugins/pace/pace-theme-big-counter.css" rel="stylesheet" />
    <link href="assets/css/style.css" rel="stylesheet" />
    <link href="assets/css/main-style.css" rel="stylesheet" />
    <link href="assets/css/custom.css" rel="stylesheet" />

</head>

<body class="body-Login-back">

<nav class="navbar navbar-default navbar-fixed-top" role="navigation" id="navbar">
    <!-- navbar-header -->
    <div class="navbar-header">
        <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".sidebar-collapse">
            <span class="sr-only">열기</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
        </button>
        <a class="navbar-brand" href="main.html">
            <img src="assets/img/logo.png" alt="" />
        </a>
    </div>
</nav>
<!-- end navbar top -->

    <div class="container">
       
        <div class="row">
            <div class="col-md-4 col-md-offset-4 text-center logo-margin ">
              <img src="assets/img/logo.png" style="margin-left: -10px"; height=100px alt=""/>
                </div>
            <div class="col-md-4 col-md-offset-4">
                <div class="login-panel panel panel-default">                  
                    <div class="panel-heading">
                        <h3 class="panel-title">로그인</h3>
                    </div>
                    <div class="panel-body">
                        <form role="form">
                            <fieldset>
                                <div class="form-group">
                                    <input class="form-control" placeholder="ID" name="acountID" type="text" autofocus>
                                </div>
                                <div class="form-group">
                                    <input class="form-control" placeholder="Password" name="password" type="password" value="">
                                </div>
                                <div class="checkbox save-login">
                                    <label>
                                        <input name="remember" type="checkbox" value="Remember Me">저장하기
                                    </label>
                                    <a class="register" href="resister.html">회원가입</a>
                                </div>
                                <!-- Change this to a button or input when using this as a form -->
                                <a href="main.html" class="btn btn-lg btn-primary btn-block">로그인</a>
                            </fieldset>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>

     <!-- Core Scripts - Include with every page -->
    <script src="assets/plugins/jquery-1.10.2.js"></script>
    <script src="assets/plugins/bootstrap/bootstrap.min.js"></script>
    <script src="assets/plugins/metisMenu/jquery.metisMenu.js"></script>

</body>

</html>

```


### End
> 
  무엇보다 라우터 사용부분에서 기존소스 및 공부한 사이트(생활코딩 , 블로그 (이전 글을 보면 URL존재)) 를  보면 Html화면을 사용하지않고 .EJS  확장자로 사용한다. 
 이것을 어떻게 HTML로 해야하나 하면서 **fs.readfile()**을 사용하여 응답하고자할 html파일을 써서 보내는 삽질을 좀 하긴했지만 간단하게 Html로 보낼 수 있는 결과를 얻었다.
 
