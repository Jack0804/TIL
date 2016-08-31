


## # Json에 대해 알아보자.

### Why?
> 
 * Client(Javascript) <-> Spring(Server) 사이에서 데이터를 주고받기위해 Json방식으로 사용하는데 정확히 무엇인지 개념을 짚고넘어가자.
 
----

### Refer
> 
* [Json의 개념알고가기 (난이도 : 쉬움)](http://www.json.org/json-ko.html)
*  [생활코딩 - Json ~ Ajax](https://opentutorials.org/course/1375/6844)

----

###  So
 >   
   * json은 JavaScript Object Notation 의 약자로서, 의미그대로 해석하면 JavaScript에서 객체를 만들 때 사용하는 표현식을 의미한다.
   *  json은 클라이언트와 서버간의 데이터를 주고받을 때 사용할 수 있는 표현의 하나이다.
   * 자바 스크립트는 객체를 **{ }** 대괄호 로 표현한다. 그래서 Json데이터의 구조의 첫 시작은 **{** 로 시작하며(객체이다)  **"Key값(name)"**  과 **"Data(value)"** 로 구성 되어 있으며 **:** 으로 구분한다. 
   * 또한 Json데이터의 자료형은 Hashmap, array ~ value(String, int , double ...)까지  다양하게 표현이 가능하다.(Refer에서 Json의 개념알고가기 링크 참조)

**Json데이터 구조(객체 구조) **

![enter image description here](http://www.json.org/object.gif)


**Json데이터 구조(배열 구조)**

![enter image description here](http://www.json.org/array.gif)


**Json데이터 구조(Value 구조)**

![enter image description here](http://www.json.org/value.gif)

----

### How
 > 
  * 글로는 와닿지가 않으므로 실제 예제를 만들어보자.
 

#### Case 1
  
**Type : hashmap**

![Hashmap(source)](https://github.com/Jack0804/TIL/blob/master/img/json/hashmap_02.JPEG?raw=true)

```java
@ResponseBody	
@RequestMapping(value = "/hash", method = RequestMethod.GET)
public Map<String, Object> hash(Model model) {
	
	Map<String, Object> map = new HashMap<String, Object>(); 
	
	List<CameraVO> list = service.listRead();
	List<CameraVO> list2 = service.listRead();
	
	map.put("list", list);
	map.put("list2", list2);
	
	return map;
}
```
> 예제를 위해 hashmap 선언 후, Object로 List 2개를 삽입하며,
 URL 경로 입력 시, map을 반환(Json데이터 전송)




![Hashmap](https://github.com/Jack0804/TIL/blob/master/img/json/hashmap_01.JPEG?raw=true)

> hashmap에 해당하는 경로 입력 하면 list2와 list의 자료형이 보여진다.
 아래는 데이터를 추려서 가져와보았다.

 결과 값(화면)
 
```text
{"list2":[{"cameraNo":1,"cameraId":"abc123456789",
"regdate":"2016-08-31","modidate":"2016-08-31","deleted":false,"memberVo":0},
{"cameraNo":5,"cameraId":"abc123456784","regdate":"2016-08-31",
"modidate":"2016-08-31","deleted":false,"memberVo":0}],
"list":[{"cameraNo":1,"cameraId":"abc123456789","regdate":"2016-08-31",
"modidate":"2016-08-31","deleted":false,"memberVo":0},
{"cameraNo":5,"cameraId":"abc123456784","regdate":"2016-08-31",
"modidate":"2016-08-31","deleted":false,"memberVo":0}]}
```

> 
 * Json은 {로 시작하여 "Key(name)" : Data(value)로 구성된다 -> **{"cameraNo":1**
 * **,** 를사용하여 Key를 분류  **{"cameraNo":1,"cameraId":"abc123456789"}**
 * 직접 데이터를 보고 위에 사진에 나와있는 json 데이터 구조 사진을 보면서 분석해보니 훨씬 쉽게 이해가 다가왔다.
 * 또한 Hash에서 List를 담은 것 또한 Json이다.
  **{ "list2" : [data] , "list1":[data]}** 으로 구성되어있는 Json(Object) HashMap안에 json(Object)List데이터(camera 데이터)값이 각각 존재한다.
 
 
 ----
 
#### Case2
 
   
**Type :  list**

> Json구조 Object타입 사진과 똑같은 구조이다.

```java
@ResponseBody	
@RequestMapping(value = "/list", method = RequestMethod.GET)
public List<CameraVO> list(Model model) {
	
	List<CameraVO> list = service.listRead();
	
	return list;
}
```

  결과 값(화면)
```text
[{"cameraNo":1,"cameraId":"abc123456789","regdate":"2016-08-31",
"modidate":"2016-08-31","deleted":false,"memberVo":0},
{"cameraNo":5,"cameraId":"abc123456784","regdate":"2016-08-31",
"modidate":"2016-08-31","deleted":false,"memberVo":0}]
```

> 구조는 위에 설명한것과 똑같다, 대괄호 시작으로 "Key명" : 데이터 , 로 구분.


---

#### Case3
**Type : array**

```java
@ResponseBody	
@RequestMapping(value = "/array", method = RequestMethod.GET)
public String[] array(Model model) {
	
	String array[] = new String[10]; 
	
	for(int i =0; i<10; i++){
		
		array[i] = "test"+i;
	}
	
	return array;
}
```

 결과 값(화면)
```text
["test0","test1","test2","test3","test4","test5",
"test6","test7","test8","test9"]
```



#### Case4
**Type : Value**

```java
@ResponseBody	
@RequestMapping(value = "/string", method = RequestMethod.GET)
public String string(Model model) {
	
	String test ="Test String";
	
	return test;
}
```

 결과 값(화면)
```text
Test String
```
