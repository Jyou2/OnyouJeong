---
title: 'Servlet'
date: 2021-01-24
category: 'servlet&jsp'
draft: false
---



### Servlet Container

컨테이너는 Servlet의 생성부터 소멸까지의 일련의 과정(Lifer Cycle)을 관리한다.   
Servlet Container는 요청이 들어올 때마다 새로운 자바 thread를 만든다.   
톰캣같은 WAS가 Java파일을 컴파일해서 Class로 만들고 메모리에 올려 Servlet객체를 만든다.  
<br>


### 생명주기
Servlet Container가 서블릿 인스턴스의 init() 메소드를 호출하여 초기화한다.  
최초 요청을 받았을 때 한번 초기화 하고 그 다음 요청부터는 이 과정을 생략한다.  
서블릿이 초기화 된 다음부터 클라이언트의 요청을 처리할 수 있다.  
각 요청은 별도의 thread로 처리하고 이때 서블릿 인스턴스의 service() 메소드를 호출한다.  
  이 안에서 HTTP 요청을 받고 클라이언트로 보낼 HTTP 응답을 만든다.  
  이 안에서 HTTP 요청을 받고 클라이언트로 보낼 HTTP 응답을 만든다.  
  보통 doGet() 또는 doPost()를 구현한다.  
<br>



### ServletContext

Servlet과 ServletContainer가 상호작용하기 위해 필요한 메서드를 제공해주는 객체  
즉, 하나의 Servlet이 ServletContainer와 통신하기 위해서 사용되어지는  
메서드를 가지고 있는 클래스가 바로 ServletContext다.  
(쉽게말하면 web application의 모든 thread와 Servlet이 공유하는 객체)  
<br>


하나의 웹 어플리케이션당 하나의 ServletContext만 존재한다.  
application scope를 가지는 객체  
application scope : 서버가 실행될 때 메모리에 올라가서, 서버가 종료될 때 파괴  
따라서 ServletContext에 저장한 정보는 서버가 종료될 때 까지 삭제되지 않는다.  
<br>


ServletContext를 얻기위해 getServletContext() 메소드를 사용한다.  
Servlet(서블릿)은 HttpServlet을 상속한다.  
HttpServlet은 ServletConfig를 구현하고 있기 때문에 getServletContext() 메서드를 바로 이용할 수 있다.  
<br>



### Servlet의 Scope

page scope : 해당 페이지에서만 유효한 scope  
request scope : 요청에 의해 생성되고 응답이 완료되면 종료되는 scope  
session scope : 요청에 의해 생성되고, 클라이언트의 브라우저가 종료되면 파괴  
application scope : 서버가 실행될 때 생성되고, 서버가 종료될 때 파괴  
<br>


### form Tag
웹페이지의 정보를 서버로 전송하는 역할   
action : url  
action태그에 url을 작성할 때 상대/절대경로 모두 사용 가능하다.  
but 절대경로를 사용하는 것이 낫다. 상대경로는 리소스위치가 변경될 경우 경로가 꼬일 위험이 있다.   
method : method / 기본값 : get  
HTTP Request는 여러 종류가 있지만, HTML5에서는 post와 get만 지원한다.  
enctype : mime타입 지정 / 기본값 : application/x-www-form-urlencoded  
<br>
 


name 속성에 담긴 값 : HTTP 요청의 parameter name 값  
value 속성에 담긴 값 : parameter value 값  
<br>

**html 작성**  

```html
<form action="/servlet/first" method="post">
  <h1>사용하실 닉네임을 입력하세요</h1>
  <input type="text" name="nick">
  <button>입장하기</button>
</form>
```
<br>


인코딩을 UTF-8로 지정해 인코딩 문제를 해결한다.  
request.setCharacterEncoding("UTF-8");  
response.setHeader("content-type", "text/html; charset=utf-8");  


파라미터 이름이 nick인 파라미터값을 반환  
String nick = request.getParameter("nick");  

response.getWriter() 메서드를 사용해   
response body를 작성할 수 있는 PrintWriter 객체를 반환받는다.  
PrintWriter writer = response.getWriter();  
<br>


**Servlet 작성**  

```java
@WebServlet("/first")
public class A_First extends HttpServlet {
	private static final long serialVersionUID = 1L;
  
  public A_First() {
        super();
        // TODO Auto-generated constructor stub
    }
  
  protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
      request.setCharacterEncoding("UTF-8");
      response.setHeader("content-type", "text/html; charset=utf-8");

      String nick = request.getParameter("nick");
      System.out.println("넘어온 데이터 : " + nick);

      PrintWriter writer = response.getWriter();
      writer.println("<h2>어서오세요 "+ nick +"님!</h2>");
    }
}
```
<br>


response 응답코드 지정. 404에러 코드를 담아서 보낸다.   
response.setStatus(404); 
<br>



### GET

GET메서드는 서버로부터 정보를 조회하기 위해 설계된 메서드이다.  
요청 파라미터는 쿼리스트링을 통해 전달한다.  
query String : 이름과 값이 쌍으로 이루어져 있고, 여러 값을 전달할 경우 `&` 사용해 구분한다.  
ex)url?=name=value&name=value&...   
`query String`의 경우 파라미터가 브라우저창을 통해 노출되어 보안에 취약하다.   
전송하는 길이에 제한이 있어 많은 정보를 전달할 수 없다.  
<br>



### POST

POST메서드는 리소스를 생성 변경하기 위해 설계되었다.  
파라미터를 body에 담아서 전달한다.  
전송하는 길이에 제한이 없다.  
POST로 요청하는 경우, body에 정보가 담기기 때문에 `Content-type` 헤더를 작성해야한다.   
form태그의 경우 `enctype` 속성을 사용해 `mime-type` 을 지정할 수 있다.   
만약 enctype을 지정하지 않을 경우 `application/x-www-form-urlencoded` 방식이 기본값으로 잡힌다.  



### multipart
content-type이 multipart인 경우 request.getParameter() 메서드 사용불가  
직접 request body에 있는 값을 읽어와야 한다.   
<br>


```java
InputStream is = null;
		OutputStream os = null;
		String root = getServletContext().getRealPath("/");
		
		try {
			is = request.getInputStream();
			os = new FileOutputStream(new File(root + "multipart.txt"));
			int check = 0;
			while((check=is.read()) != -1) {
				os.write(check);
			}
		}finally {
			os.close();
			is.close();
		}

```
<br>





### HttpServletResponse
클라이언트에게 응답을 보내기 위한 기능들을 제공한 객체  
<br>


### Content-type
서버와 브라우저간 통신이 발생할 때 본문으로 전달되는 데이터가 
어떤 타입의 데이터인지 알려주기 위해 지정하는 헤더
mime-type 또는 charset 등을 작성한다.
<br>


### MIME TYPE
text(문자) : text/plain, text/html, text/css, text/javascript  
image : image/gif, image/png, image/jpeg...  
application (바이트) : application/octet-stream(이진데이터)  
multpart(복합) : 바운더리(boundary)를 사용해서 데이터들을 구분  
<br>



### URI와 URL

URI : 인터넷상의 자원을 식별하기 위한 문자열  
URL : 인터넷상의 자원의 위치를 나타내는 문자열  
<br>


http://localhost:9090/servlet/book.html?title=자바의정석  
호스트가 localhost:9090인 웹 어플리케이션 root폴더 아래의 있는 제목이 자바의 정석인 book.html  
=> 정확하게 자원을 식별하는 문자열이기 때문에 URI  
<br>


http://localhost:9090/servlet/book.html  
자원의 위치는 있지만, 정확하게 자원을 식별하기 위한 파라미터는 없음.  
=> 자원의 위치만 나타내므로 URL  
<br>


http://localhost:9090/servlet/book.html?title=자바의정석  
http://localhost:9090/servlet/book.html?title=자바스크립트의 정석  
=>같은 URL  
=>다른 URI  
<br>




### Content-Disposition 헤더

응답이 브라우저 화면에 출력되어야 하는지 사용자의 컴퓨터에 다운로드 되어야 하는지 지정  

Content-Disposition=inline  
기본 값. 화면에 출력이 가능한 데이터라면 브라우저의 화면에 응답바디의 데이터를 출력  
attachment; [filename=파일명]: 응답바디의 데이터를 다운로드 받는다.  




### Request Scope

요청이 발생한 시점에 객체가 생성되어 응답이 마무리되는 시점에 객체가 소멸하는 스코프(범위)  
ex) HttpServletRequest, HttpServletResponse 객체가 Request Scope를 가지고 있다.  



### RequestDispatcher.forward() 와 Response.sendRedirect()

**RequestDispatcher.forward()**
요청을 재지정해주는 메서드  
/servlet/page/forward/name 넘어온 요청을 /servlet/page/impl 로 내부에서 재지정  
받은 요청객체와 응답객체를 함께 넘겨준다.   

RequestDispatcher view = request.getRequestDispatcher("/page/impl");
view.forward(request, response);
<br>

**Response.sendRedirect()**  
요청을 재요청하는 메서드   
응답코드 302는 브라우저에게 재요청할 것을 요청하는 응답코드이다.  
response.sendRedirect() 메서드는 브라우저에게 302상태코드와 location헤더로  재요청할 url을 응답한다.  
따라서 응답이 발생하게 되고 응답이 발생하는 시점에  
우리가 header를 설정한 응답객체와 요청객체는 응답이 끝나고 소멸한다.  
(Request Scope를 가지고 있는 객체이기 때문!)  
응답을 받은 브라우저는 302상태코드이기 때문에 우리가 location 헤더에 담아준  
(== response.setRedirect() 메서드의 매개변수로 넣어준) 경로로 새로운 요청을 하게된다.  
새로운 요청이기 때문에 새로운 request 객체와 response 객체가 생성된다.  
<br>

```java
response.setHeader("content-disposition", "attachment; filename=cat.jpg");
response.sendRedirect("/servlet/resources/image/image01.jpg");
```
<br>


즉, sendRedirect(url) 클라이언트에게 302 상태코드와 함께 매개변수로 넘겨준 url을 응답해준다.    
302 상태코드를 받은 브라우저는 응답헤더에 함께 넘어온 url로 다시 요청하게 된다.  
브라우저가 재요청할 url을 매개변수로 넘겨주기 때문에 context path가 반드시 필요하다.  
브라우저는 우리의 웹어플리케이션으로 접근하기 위해 context path가 필요하기 때문이다.  
<br>








