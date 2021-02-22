---
title: 'JSP 기초'
date: 2021-01-25
category: 'servlet&jsp'
draft: false
---



### JSP(Java Server Page)

JSP는 기존에 서버용 언어인 Servlet에서 화면 구현에 관련된 소스 부분을 별도로 분리하는 기술을 말한다.  

Comments tag : <%-- 주석 --%>  
Directive tag : <%@ 지시자 %>  
Declaration tag : <%! 선언문 %>  
Scriptlet tag : <% 코드 %>  
Expression tag : <%= 표현식 %>  


### 지시자 태그
지시자 태그란 페이지 전체에서 사용할 속성을 지정하는 JSP 태그이다.  
<br>

**page 지시자태그** : 해당 페이지에서 사용할 속성을 지정  
   -language : 사용할 프로그래밍언어  
   -import : 페이지에서 필요한 자바 클래스를 import 할 때 사용한다.  
<br>

**include 지시자태그** : 다른 위치의 html/jsp를 현재 페이징에 삽입할 때 사용한다.  
<br>

**taglib 지시자태그** : 다른 라이브러리에서 제공하는 커스텀태그를 사용할 때 사용한다.  
<br>



### 선언 태그
선언태그는 메서드, 필드변수를 선언할 때 사용한다.  
필드에 변수나 메서드가 선언되기 때문에 조심해서 사용할 필요가 있다.  
<br>


### 스크립틀릿 태그
페이지 내부에서 JAVA 소스코드를 작성하는 영역을 나타내는 코드이다.  
스클립틀릿 태그에 작성하는 코드는 \_jspService() 메서드 내부에 작성된다.  
\_jspService 메소드의 로컬 변수와 코드를 작성할 때 사용된다.  
<br>



### 표현식 태그
표현식 태그란 특정 객체나 변수의 값을 출력하는 용도로 사용한다.  
out.print 메서드를 쉽게 사용할 수 있다.  
표현 태그에서는 ‘;’ 을 붙이지 않는다.  



### JSP 내장 객체
JSP에서 기본적으로 제공하는 객체들로 request, response, out 등  
Scriptlet tag와 Expression tag에서 사용할 수 있도록 암시적으로 선언된 객체를 뜻한다.  
<br>


**JSP 내장 객체의 영역**   
page : 하나의 JSP페이지를 처리할 때 사용되는 영역  
request : 하나의 요청을 처리할 때 사용되는 영역  
session : 하나의 브라우저와 관련된 영역  
application : 하나의 웹 어플리케이션과 관련된 영역  
<br>
application > session > request > page  






