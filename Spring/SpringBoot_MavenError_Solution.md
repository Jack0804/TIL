
## Spring Boot 프로젝트 생성 시 Maven(Library) 오류 해결하기

####Spring Boot 프로젝트 생성 시, 아래의 오류 발생에 대한 해결 포스팅

> 
 - 프로젝트 생성 시 Pom.xml에서 Maven에 빨간 밑줄 발생.
 - 에러 문구
	- ``failure to transfer org.springframework ...``
    -  Missing artifact org.springframework.boot:spring-boot-starter-parent:jar:1.3.2.RELEASE

	
### Why?

 > 
 - 스프링부트 프로젝트 생성하였는데 오류가 발생(위에 오류메시지)
 -  기존에 존재하던 Library 오류가 원인 가능성 높다.
 
 
###Solution
 > 
 - 기존의 라이브러리를 삭제 -> 다시 다운로드 진행
 - " C:\\사용자폴더\\사용자계정폴더\\m2 " 로 진입.
 -  m2폴더 안에 repository 폴더를 삭제(Spring을 종료 한 상태에서).
 -  스프링 재 시작.
 -  스프링부트 프로젝트 다시 생성하기. (**library를 다시 다운받으므로 시간이 평소보다 더 소요된다**)

###Refer
>  
-  http://stackoverflow.com/questions/31901320/pom-error-failure-to-find-org-springframework-boot
	- 위의 링크에서 마지막 답변대로 실시.



	 나는 라이브러리 폴더를 삭제하고 다시 스프링을 시작해주고 프로젝트를 시작하여
	 위의 문제를 해결할 수 있었다.
	 다만 삭제하고 다시 받는다해도 그 전에 오류가 났던 프로젝트는 복구가 불가능 한걸로 판단.

 


