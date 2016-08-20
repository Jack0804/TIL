
# #게시판 페이징 처리(Spring)
----

### 개발환경
Server - Java(Spring)사용
Web - Jsp사용
게시판에서 페이징 리스트를 사용하기위하여

----
### 순서
	1. 현재 페이지번호를 Web으로부터 받아올것 ,
	2. 게시판 게시글 갯수(Count) 값을 가져올것,
	3. 갯수와 현재 페이지 번호를 가지고 페이징 알고리즘을 활용하여 End페이지 계산 및 Prev,Next버튼 생성

----
### 소스코드
#### Controller(server)
```java
	@RequestMapping(value = "/list", method = RequestMethod.GET)
	public String list(PageMaker pagemaker, Model model) {

		logger.info("START LIST");

		int count = 0;

		pagemaker.setPage(pagemaker.getPage());

		count = service.count();   // 레코드 총 갯수 구함
		pagemaker.setCount(count); // 페이지 계산

		List<BoardVO> list = service.getRead(pagemaker.getPage());

		System.out.println("list = " + list.toString());

		model.addAttribute("result", list);
		model.addAttribute("pageMaker", pagemaker);

		return "/board/list";
	}	
```
 Web(jsp)에서 현재 페이지 번호를 Controller(list)에 전달,
 Controller는 Pagemaker클래스에 접근하여 페이지 계산.
 ----

####pagemaker.java
```java
	public Integer getPage() {
		return page;
	}

	public void setPage(Integer page) {

		if (page < 1) {
			this.page = 1;
			return;
		}

		this.page = page;
	}

public void setCount(Integer count) {

		if (count < 1) {
			return;
		}

		this.count = count;
		
		System.out.println("총 컬럼 갯수 = "+count);
		
		calcPage();
	}

	private void calcPage() {

		// page변수는 현재 페이지번호
		int tempEnd = (int)(Math.ceil(page / 10.0) * 10);
		// 현재 페이지번호를 기준으로 끝 페이지를 계산한다.
		
		System.out.println("page = " +page);
		System.out.println("tempEnd = "+tempEnd);
		System.out.println("this.count =" +this.count);
		
		// 시작 페이지 계산
		this.start = tempEnd - 9;
		

		if (tempEnd * 10 > this.count) { // 가상으로 계산한 tempEnd크기가 실제 count보다 많을경우
			this.end = (int) Math.ceil(this.count / 10.0);
		} else {						
			this.end = tempEnd;			 // 실제 count가 tempEnd보다 많을경우
		}

		System.out.println("this.end = "+this.end);
		
		this.prev = this.start != 1; 
		this.next = this.end * 10 < this.count;	
	}

```
 페이지 알고리즘 및 현재 페이지를 기준으로 마지막 페이지 , Prev, Next 계산.

----

#### list.jsp (일부)
```jsp
<ul class="pageUL">
	<c:if test="${pageMaker.prev }">
		<li><a href='list?page=${pageMaker.start -1}'>이전</a></li>
	</c:if>

	<c:forEach begin="${pageMaker.start }" end="${pageMaker.end}" var="idx">
		<li
			class='<c:out value="${idx == pageMaker.page?'current':''}"/>'>
			<a href='list?page=${idx}'>${idx}</a>
		</li>

	</c:forEach>

	<c:if test="${pageMaker.next }">

		<li><a href='list?page=${pageMaker.end +1}'>다음</a></li>
	</c:if>
</ul>
```
서버에서 계산된 페이지값을 받아서 화면(Web)에 출력 부분입니다.
