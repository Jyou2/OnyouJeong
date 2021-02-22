---
title: 'EL 표기법'
date: 2021-01-25
category: 'servlet&jsp'
draft: false
---




### EL 표기법
자바 bean 객체의 값들을 편하게 사용하기 위해 제공되는 표기법  

**자바 bean 규약**  
기본 생성자, 캡슐화, getter/setter  
자바 bean 규약을 따르는 객체 자바 bean객체라고 한다.  

**${}** : 객체 프로퍼티에서 값을 꺼낼 때 주로 사용한다.  


### EL에서 접근 가능한 데이터들

**${requestScope.name}** : request 객체의 Attribute에 저장된 값에 접근  
**${sessionScope.name}** : session 객체의 Attribute에 저장된 값에 접근  
**${applicatopnScope.name}** : servletContext 객체의 Attribute에 저장된 값에 접근  
<br>


scope를 명시하지 않고 속성명만 작성할 경우 :  
현재 page scope로 부터 가까운 scope를 탐색하며 해당 속성의 값을 찾는다.  
(자바스크립트의 scope chain과 같다.)  
<br>


${param.name} : request객체에 저장된 parameter 접근  
${paramValues.name} : 같은 파라미터명으로 저장된 데이터가 여러 개일 경우 배열로 받아온다.  
${cookie.name} : 쿠키값 조회   



예제
`${param.name}` 과 `request.getParameter("name")`은 같다.  
`${requestScope.sum}` 과 `request.getAttribute("sum")`은 같다.  
scope 없이 속성명만 작성하면 가까운 스코프부터 해당 속성명을 가진 값을 탐색한다.  
<br>

cookie.name   
JSESSION : ${cookie.JSESSIONID.value}   
<br>


${null} : null이 담길 경우 공백으로 출력한다.  



### EL 연산자
산술연산자, 논리연산자, 비교연산자, 삼항연산자, empty 연산자   

```jsp
<h2>산술연산자 (+ - * / %)</h2>
<span> 1 + 1 : ${1 + 1}</span>
<span> 1 - 1 : ${1 - 1}</span>
<span> 2 * 3 : ${2 * 3}</span>
<span> 2 / 3 : ${2 / 3}</span>
<span> 2 % 3 : ${2 mod 3}</span>

<h2>논리연산자</h2>
<span> true && false : ${true && false}</span>
<span> true || false : ${true || false}</span>
<span> !false : ${!false}</span>
<span> true and false : ${true and false}</span>
<span> true or false : ${true or false}</span>
<span> not false : ${not false}</span>

<h2>비교연산자</h2>
<pre>
  크다 : > gt
  작다 : &lt  lt
  크거나 같다 : >= ge
  작거나 같다 : &lt= le
</pre>
<span> 1 == 2 : ${1 == 2}</span>
<span> 1 != 2 : ${1 != 2}</span>
<span> 1 > 2 : ${1 gt 2}</span>
<span> 1 lt 2 : ${1 < 2}</span>
<span> 1 >= 2 : ${1 ge 2}</span>
<span> 1 le 2 : ${1 <= 2}</span>


<h2>삼항연산자</h2>
<span>1>2? "크다" : "작다"  >>>  결과:  ${1>2?"크다":"작다"}</span>


<h2>empty 연산자</h2>
<pre>
  값이 null 이면 true
  문자, 배열, collection의 length가 0이면 true
  이외에는 false
</pre>
<span>
  empty null : ${empty null}
</span>
<span>
  empty sessionScope.name : ${empty sessionScope.name}
</span>

```



