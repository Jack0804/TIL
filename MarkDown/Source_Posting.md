
## #Intro
 지난 포스팅은 MD문서를 HTML로 변환하여 블로그와 Github에 둘다 빠르게 포스팅하는 방법을 게시하였습니다.
 이번 포스팅은 prettyprint를 사용하여 소스코드 하이라이팅 시키는 방법을 이어가겠습니다.
 
 ----
 
### Why?
  소스코드 하이라이팅 툴은 여러가지가 있는데  **왜 prettyprint를 사용하는지?**<br>
[(링크)하이라이팅 툴 종류 및 장 단점](http://blog.joostory.net/398)

1 - StackEdit는 마크다운 소스코드 첨삭 시 아래와 같이 pre태그 Class prettyprint사용
```javascript
<pre class='prettyprint'>
 /*소스코드 입력*/
</pre>
```
(참조 : [링크](http://hashcode.co.kr/questions/1772/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-%EC%9E%91%EC%84%B1-%ED%8C%81)).


2 - 티스토리 html편집 -> **Prettyprint를 적용**  -> 소스코드를 MD로 작성 및 업로드 -> Prettyprint를 사용하는 모든 소스코드에 **하이라이팅 효과적용**

----
### 티스토리 Html 편집하기
 
 * [(링크)티스토리 HTML편집하기](http://javahwan.tistory.com/92)
 * **(주의!)**저는 위에 링크대로 HTML 수정까진 들어갔으나 CDN 링크를 사용하여 적용하였습니다.
 *  제가 적용한 CDN으로 적용방법 http://blog.gaerae.com/2015/09/google-code-prettify.html
 * 위에 링크따라서 실행하면 소스코드가 Prettyprint 스킨(sunburst) 적용 완료.

#### 소스코드 배경 수정하기
![사진](http://cfile28.uf.tistory.com/image/2659B54257B8706F309B4A)

* 위에 사진처럼 CSS항목 선택 ->  "Pre" 검색 -> Background 지움
* "저장" 누르고 다시 글 확인하면 소스코드가 회색배경에서 Pretty스킨에 맞는 배경 적용완료.

----
###Refer
[여러개의  Highlighting 사용비교 글](http://blog.joostory.net/398)


PrettyPrint 적용하기

 * http://blog.gaerae.com/2015/09/google-code-prettify.html
 * http://www.bloggertipandtrick.net/prettify-syntax-highlighter-for-blogger-blogspot
 * http://winteriscoming2u.tistory.com/6

PrettyPrint 테마

- https://rawgit.com/google/code-prettify/master/styles/index.html
- https://jmblog.github.io/color-themes-for-google-code-prettify
* 총 5개의 테마사용가능

 
### 마치며
``prettyprint`` 클래스를 적용하여 소스코드 하이라이팅은 잘 되었으나 
배경은 계속해서 회색화면으로 고정되어있어서 꽤나 고생을했다...
 해결책으로 Skin.html 에 적용되어있는 CSS - pre태그 - background 를 지워서 잘 해결...
 
 CodeScriper , SyntaxHighlighter, Prettyprint 총 세개를 사용하였는데, 
 그 중 Prettyprint가 가장 심플하면서도 잘 적용될 수 있는 장점을 가지고있다.

---
 
