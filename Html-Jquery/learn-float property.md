


## #CSS Float과 Clear 사용하기

### **Why?**
 CSS레이아웃 잡기위하여 알아보는 중 대충 알고있던 CSS 에서 Float 기능 짚고 넘어간다.
 
----
### **Refer**

Float 알고가기 - http://www.nextree.co.kr/p8796/

----

### 내용
 링크사이트에 들어가서 글씨가 있더라도 귀찮게 생각하지말고  
 천천히 처음부터 끝까지 **한번만** 읽어볼것.

#### float이란?
> 
- float 속성은 **특정 요소**를 **떠 있게 하는 것**입니다. 
- 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽에 이동하는 것입니다.
- float 속성을 사용할 때 요소의 위치가 고정되면 안 되기 때문에 **position 속성의 absolute를 사용금지**
-  float 속성을 **사용하지 않으면** 요소들이 **수직으로** 출력됩니다.
-  float:left 속성 -> **왼쪽부터 정렬**되고, float:right 속성 -> **오른쪽부터 정렬**되어 출력됩니다.

예제를 따라서 하다보면 오타가 난 부분(예제3번 - 레이아웃 구성이 소스와 결과화면 값이 다름 )  존재.
  수정하여 아래에 예제소스 게시.
<br>
("H1" 태그에서 Clear 기능을 주석 해제 하고 안하고에 따라 **Clear기능을 확인** 할 수 있다.)
 
```javascript
 <!DOCTYPE html>
<html lang="en">
<head>
    <title> nextree </title>
    <style>
        div{
            width:85px;
            height:50px;
            margin:10px 5px;
            padding:5px;
            text-align: center;
        }
        img {
            float:left;
            width:95px;
            height:50px;
            margin:10px 5px;
            padding:5px;
        }
        #content1 {
            float: left;
            background:red;
        }
        #content2 {
            float: right; /* 첫 번째 예제에서는 float:left */
            background:orange;
        }

        h1 {
            float:left;
            /*clear:left;*/
            font-size: 10px;
            margin:10px 5px;
            padding:5px;
            color:blue;
        }
    </style>
</head>
<body>
<div id="content1"> RED </div>
<div id="content2"> ORANGE<br>(float='right') </div>
<img src="logo.JPEG">
<h1>TEST </h1>
</body>
</html>
```



 
 
 
	 
