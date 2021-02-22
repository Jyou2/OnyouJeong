---
title: 'Session'
date: 2021-1-24
category: 'servlet&jsp'
draft: false
---

**학원에서 배운 것을 기록합니다.**
<br>

### HttpSession

Session Scope를 가지는 객체이다.  
Session Scope : 요청이 온 시점 부터 브라우저가 종료되는 시점까지 존재하는 수명주기    
HttpSession은 JVM의 Heap영역에 저장되는 일반적인 객체이다.  
원하는 데이터를 저장하고 꺼내쓰기 위한 메서드가 제공된다.  
HttpSession을 생성하기 위해 사용하는 request.getSession() 메서드는  
해당 요청에 의해 생성된 Session객체를 반환한다.  
<br>


생성된 session객체는 해당 session 객체를 접근할 수 있는 고유의 id를 가지고 있다.  
session이 생성되면 해당 응답 때 응답헤더에  
session 객체를 식별할 수 있는 아이디(JSESSIONID)를 쿠키에 담아 보낸다.  
서버는 응답을 하고 나면 모든 걸 잊기 때문에, session 객체를 식별하기 위한 아이디도 잊는다.  
<br>


하지만 해당 JSESSION 아이디가 쿠키에 담겨저 보내졌기 때문에,
클라이언트가 다시 요청할 때 JSESSION ID도 함께 서버에 전달된다.  
그럼 서버는 요청 header에 담겨온 JSESSION ID를 사용해 다시 session 객체를 식별할 수 있게 된다.  
<br.


쿠키의 기본 수명주기가 session이기 때문에, 별 다른 쿠키정책이 없다면  
JSESSION ID를 가지고 있는 쿠키는 브라우저가 종료될 때 브라우저에서 삭제된다.  
Session 객체를 식별하기 위한 JSESSION ID가 더이상 요청헤더에 담겨오지 않음으로  
해당 Session객체는 더이상 사용이 불가능 해진다.  
<br>


Session객체는 마지막으로 호출된지 30분이 지나면 JVM에서 삭제된다.  
Session.setMaxInActiveInterval() 메서드를 사용해 조절할 수 있다.  
<br>

`setAttribute()` 속성에 정보를 저장 및 수정한다.  
`getAttribute()` 해당 속성을 가져온다.  
`removeAttribute()` 해당 속성을 삭제한다.  
<br>


```java
String nick = request.getParameter("nick");

//Session 객체 생성
HttpSession session = request.getSession();

//session에 정보를 저장
session.setAttribute("nick", nick);

//브라우저를 종료해도 session을 유지하기  
//JSESSIONID 쿠키의 max-age를 session이 아니라 시간으로 잡아
//브라우저가 종료되더라도 쿠키가 삭제되지 않게 처리
//JSESSIONID 쿠키에 담기게 되는 Session ID를
//HttpSession.getID() 메서드로 반환받을 수 있다.
response.setHeader("set-cookie", "JSESSIONID=" + session.getId() + "; max-age=3600; path=/");

```











