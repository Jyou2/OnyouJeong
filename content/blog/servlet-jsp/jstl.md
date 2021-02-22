---
title: 'JSTL'
date: 2021-01-26
category: 'servlet'
draft: false
---




### JSTL
JSP에서 사용하는 스크립틀릿의 복잡함을 해결하기 위해 등장한 사용자정의 태그   
변수 생성, 출력, 조건문, 반복문, formatting 등을 지원해준다.   

(밑에 예제는 보기 편하기 위해 <span>태그를 넣었습니다.)   


#### c:set 변수 생성
var : 변수, value : 값
<br>
```jsp
<c:set var="num1" value="100"/>
<c:set var="num2" value="200"/>
<c:set var="html" value="<a href='https://www.naver.com'>naver로 이동</a>" />
<c:set var="js" value="<script>console.dir('el 표현식은 콘솔에 출력이된다.')</script>" />
```
<br>


### c:out 변수 출력
```jsp
<span>num1 : <c:out value="${num1}"/></span>
<span>num2 : ${num2}</span>
```


### jstl을 사용한 배열생성
```jsp
<c:set var="jstlArr">
	red,blue,yellow,pink,green
</c:set>
<span>jstlArr : <c:out value="${jstlArr}" /></span>
```
<br>


### jstl 조건문
c:if  
```jsp
<c:if test="${num1 < num2}">
	<span>조건문의 조건식 결과가 true 입니다.</span>
</c:if>
<c:if test="${true and false}">
	<span>조건문의 조건식 결과가 false 입니다.</span>
</c:if>
```
<br>


### c:choose when otherwise
<c:set var="" value=""/>  
```jsp
<c:choose>
	<c:when test="${score ge 90}">
		<span>당신의 학점은 A 입니다.</span>
	</c:when>
	<c:when test="${score ge 80}">
		<span>당신의 학점은 B 입니다.</span>
	</c:when>
	<c:otherwise>
		<span>당신의 학점은 C 입니다.</span>
	</c:otherwise>
</c:choose>
```


### jstl 반복문
c:forEach   
  **- for문처럼 사용하기**   
var : i  
begin : 시작값  
end : 끝값  
step : 증가하는 크기  


	<c:forEach var="i" begin="0" end="10" step="1">
		${i}
	</c:forEach>


  **- forEach문처럼 쓰기**
var : 배열 또는 리스트의 요소를 받을 변수  
items : forEach에서 탐색할 배열 또는 리스트  
varStatus : index, count 속성을 가진 객체  
index : 현재 탐색 중인 요소의 인덱스(시작이 0)  
count : 현재 탐색 중인 요소의 차례 (시작이 1)  

```jsp
<table border="1">
	<tr>
		<th>index</th>
		<th>count</th>
		<th>value</th>		
	</tr>
	<c:forEach var="color" items="${jstlArr}" varStatus="status">
		<tr>
			<td><span>인덱스 ${status.index }</span></td>
			<td><span>count : ${status.count}</span></td>
			<td><span>값 : ${color}</span></td>
		</tr>
	</c:forEach>
</table>
```



### c:forTokens
var : 잘라진 문자열을 받을 변수  
items : 자를 문자열  
delims : 구분자  

```jsp
<ul>
	<c:forTokens var="lang" items="java html css javascript aracle servlet" delims=" ">
		<li>
			${lang}
		</li>
	</c:forTokens>
</ul>
```



