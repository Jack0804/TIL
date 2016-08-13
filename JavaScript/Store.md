# Javascript을 사용한 편의점 POS기기 구현.

화면은 HTML를 이용하여 틀을 잡았고 안에 내용 및 기능은 Jquery 사용.


## myStore.html (화면)
## 메뉴 출력
```javascript
  var $menuDiv = $(".menuDiv");
  var $billDiv = $(".billDiv");
  var $list = ("#list");

  var allMenu = orderManager.getAllMenus();//6.Js에서 받아온 menus 참조 값을 allMenu변수에 넣어줌
  var addOrder= "";
  var str = "";

  //6.문자열로 html로 화면에 출력
  for(var i=0; i<allMenu.length; i++){
    str += "<div data-mno='" + allMenu[i].mno + "'><p class='name'>"+allMenu[i].title+
      "</p><img src = '"+ allMenu[i].mno +".jpg'><p class='money'>" +
      allMenu[i].price + "원</p></div>";
    }
  
    $menuDiv.html(str);
```

## 메뉴 클릭 시, 구매 List추가

```javascript
$(".menuDiv").on("click","div",function (event) {

  var $this = $(this);
  var mno = $this.data("mno");

  orderManager.addOrder(mno);

  // console.log(mno);

  addOrder = orderManager.getAllOrders();

  var getTotalPrice = orderManager.getTotalPrice();
  var str="<colgroup><col><col style='width:100px;'><col style='width:70px;'></colgroup><tr style='text-align: center'><th>상품</th><th>수량</th><th>가격</th></tr>";

  for(var i=0; i<addOrder.length; i++){
      str += "<tr data-mno='" + addOrder[i].mno + "'>"
              + "<td>" + addOrder[i].menu.title + "</td><td>"+ addOrder[i].amount + "</td><td>"
              + addOrder[i].getTotal()+"</td></tr>";
  }

  $("#list").html(str);
  $("#total").html(getTotalPrice+"원");

});
```

##clear 버튼으로 List 초기화
```javascript
 $("#clear").on("click",function (event) {
      var allClear = orderManager.allClear();
      $("#list, #total").html(allClear);
  });
```


## 구매 List 클릭 시, 수량감소
```javascript
  $("#list").on("click", "tr", function (event) {
  
      var $this = $(this);
      var mno = $this.data("mno");
  
      orderManager.cancleOrder(mno);
  
      addOrder = orderManager.getAllOrders();
  
      var getTotalPrice = orderManager.getTotalPrice();
  
      //console.log(mno);
  
      var str="<colgroup><col><col style='width:100px;'><col style='width:70px;'></colgroup><tr style='text-align: center'><th>상품</th><th>수량</th><th>가격</th></tr>";
  
      for(var i=0; i<addOrder.length; i++){
          str += "<tr data-mno='" + addOrder[i].mno + "'>"
                  + "<td>" + addOrder[i].menu.title + "</td><td>"+ addOrder[i].amount + "</td><td>"
                  + addOrder[i].getTotal()+"</td></tr>";
      }
  
      $("#list").html(str);
      $("#total").html(getTotalPrice+"원");
  });
```


## store.js (기능)
- func으로 구성되어있으며 이벤트 발생 시, 외부가 아닌 내부적인 작업 처리진행.

```javascript
  var $menuDiv = $(".menuDiv");
  var $billDiv = $(".billDiv");
  var $list = ("#list");
  
  var allMenu = orderManager.getAllMenus();//6.Js에서 받아온 menus 참조 값을 allMenu변수에 넣어줌
  var addOrder= "";
  var str = "";
  
  //6.문자열로 html로 화면에 출력
  for(var i=0; i<allMenu.length; i++){
      str += "<div data-mno='" + allMenu[i].mno + "'><p class='name'>"+allMenu[i].title+
              "</p><img src = '"+ allMenu[i].mno +".jpg'><p class='money'>" +
              allMenu[i].price + "원</p></div>";
  }
  
  $menuDiv.html(str);
  
  //
  $(".menuDiv").on("click","div",function (event) {
  
      var $this = $(this);
      var mno = $this.data("mno");
  
      orderManager.addOrder(mno);
  
      // console.log(mno);
  
      addOrder = orderManager.getAllOrders();
  
      var getTotalPrice = orderManager.getTotalPrice();
      var str="<colgroup><col><col style='width:100px;'><col style='width:70px;'></colgroup><tr style='text-align: center'><th>상품</th><th>수량</th><th>가격</th></tr>";
  
      for(var i=0; i<addOrder.length; i++){
          str += "<tr data-mno='" + addOrder[i].mno + "'>"
                  + "<td>" + addOrder[i].menu.title + "</td><td>"+ addOrder[i].amount + "</td><td>"
                  + addOrder[i].getTotal()+"</td></tr>";
      }
  
      $("#list").html(str);
      $("#total").html(getTotalPrice+"원");
  
  });
  
  
  $("#clear").on("click",function (event) {
      var allClear = orderManager.allClear();
      $("#list, #total").html(allClear);
  });
  
  
  $("#list").on("click", "tr", function (event) {
  
      var $this = $(this);
      var mno = $this.data("mno");
  
      orderManager.cancleOrder(mno);
  
      addOrder = orderManager.getAllOrders();
  
      var getTotalPrice = orderManager.getTotalPrice();
  
      //console.log(mno);
  
      var str="<colgroup><col><col style='width:100px;'><col style='width:70px;'></colgroup><tr style='text-align: center'><th>상품</th><th>수량</th><th>가격</th></tr>";
  
      for(var i=0; i<addOrder.length; i++){
          str += "<tr data-mno='" + addOrder[i].mno + "'>"
                  + "<td>" + addOrder[i].menu.title + "</td><td>"+ addOrder[i].amount + "</td><td>"
                  + addOrder[i].getTotal()+"</td></tr>";
      }
  
      $("#list").html(str);
      $("#total").html(getTotalPrice+"원");
  });
```
