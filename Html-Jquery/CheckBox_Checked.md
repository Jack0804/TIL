

## # CheckBox 체크된 영역의 속성 값 읽기


### Why ?

> *  팀 프로젝트 진행 중 테이블형 게시판List에서 체크박스가 체크되어진 값에 대해 속성 값을 얻어야 하는 기능 작업.

----
### Refer
> * [참고 1 - 스택오버 플로우](http://stackoverflow.com/questions/1287592/get-checkbox-list-values-with-jquery)
> * [참고 2 - 스택오버 플로우](http://stackoverflow.com/questions/2155622/get-a-list-of-checked-checkboxes-in-a-div-using-jquery)

----
### How ?

> * 로직 : 버튼 클릭 -> (여러개)체크박스 체크 된 Tr의 Id값 얻기.
> *  **.is(:checked)** 를 통하여 체크여부 확인.
> * **.each** 반복문을 사용하여 체크된(여러개 가능) 영역에 해당하는 곳에서 속성 값 얻기.
> * 반복문을 통하여 값을 얻어야하므로 **배열**에 값을 담는다.



```javascript
// 삭제버튼 클릭이벤트 발생.
$('#deledteCamera').on('click', function(){

// CheckBox 검사
if ($('input:checkbox[name="checkbox"]').is(":checked")){

	var names = [];
	
	$('#list input:checked').each(function() {
		names.push(this.id); //Check된 Check박스의 "Id"태그 얻기.
	});
	
console.log(names)
}
```





