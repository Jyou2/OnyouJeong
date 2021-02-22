---
title: '기본적인 html문법'
date: 2020-12-10
category: 'TIL'
draft: false
---


### HTML이란?

HTML은 **Hyper Text Markup Language**의 약자이다.     
다른 페이지와 연결된 (Hyper Text)   
정보를 전달하기 위해 구조화된 언어(Markup Language)   



### 주석

HTML은 JAVA와는 주석 작성 방법이 다르다.   
`<!-- 주석 -->` 이렇게 작성한다.   




### DOCTYPE


DOCTYPE은 HTML 문서에서 <html> 태그를 정의하기 전에 가장 먼저 선언되어야 한다.   
DOCTYPE은 문서의 유형을 정의하기 위해 사용하는 선언문(Document Type Definition/DTD)이다.   
선언된 페이지의 HTML 버전이 무엇인지를 웹브라우저에게 알려준다.   
doctype은 대소문자를 구분하지 않는다.   
<br>


선언방법 : ``<!DOCTYPE HTML>``   
<br>


### <html>

html태그는 페이지 전체를 감싸는 태그이다.   
작성하는 모든 html 코드는 html 태그 안에서 작성되어야 한다.   
ROOT 요소라고 부른다.   
<br>

```
<!DOCTYPE HTML>   
<html>   
<html>   
<br>
```

### <head>

페이지 제목, 설명, CSS, 문자집합(인코딩)과 같은 html 페이지에 대한 정보를 작성한다.   
브라우저에게 해당 html 파일에 대해 알려줘야하는 정보들을 작성한다.   

```
<!doctype html>
<html>
  <head>   
    <meta charset="utf-8">   
    <title>페이지 제목</title>
  </head>
</html>
```
<br>

### <body>

이 페이지를 방문한 사용자에게 보여주고자 하는 모든 컨텐츠를 body 안에 넣는다.   


```
<!doctype html>
<html>
  <head>   
    <meta charset="utf-8">   
    <title>페이지 제목</title>
  </head>
  <body>
  <h1>Hello world!</h1>
  <h1></h1> : 태그(tag)
  Hello world! : content
  <h1>Hello world!</h1> : element
  
  </body>
</html>
```






### 제목 태그

```
<h1>h1 태그입니다.</h1>
<h2>h2 태그입니다.</h2>
<h3>h3 태그입니다.</h3>
<h4>h4 태그입니다.</h4>
<h5>h5 태그입니다.</h5>
<h6>h6 태그입니다.</h6>
```
<br>


**결과**   

<h1>h1 태그입니다.</h1>
<h2>h2 태그입니다.</h2>
<h3>h3 태그입니다.</h3>
<h4>h4 태그입니다.</h4>
<h5>h5 태그입니다.</h5>
<h6>h6 태그입니다.</h6>

<br>



### 문단을 나누는 태그   


`<p></p>` 와 `<pre></pre>` 태그가 있다.   

`p태그` 는 문단 영역을 나누는 태그이지만, 줄바꿈 처리는 별도로 지정해줘야 한다.   
`pre태그` 는 여러 칸 띄우기 또는 줄바꿈등을 포함해서 입력한 내용 그대로 표현하는 태그이다.   

<br>



### 글자 관련 태그

```   
1.일반 글꼴   
<strong>2.굵게</strong>   
<b>3.굵게(볼드체)</b/>   
<em>4.기울이기(이텔릭체)</em>   
<mark>5.형광팬 효과</mark>   
<u>6.글자에 밑줄 긋기</u>   
<small>7.글자를 작게</small>   
<sub>8.아래첨자</sub>   
<sup>9.윗첨자</sup>   
<s>10.취소선</s>   
기본 글자에 <sub>아래첨자</sub>나 <sup>윗첨자</sup>를 나타낼 수 있다.   

```   

<br>


**결과**   

1.일반 글꼴   
<strong>2.굵게</strong>   
<b>3.굵게(볼드체)</b/>   
<em>4.기울이기(이텔릭체)</em>   
<mark>5.형광팬 효과</mark>   
<u>6.글자에 밑줄 긋기</u>   
<small>7.글자를 작게</small>   
<sub>8.아래첨자</sub>   
<sup>9.윗첨자</sup>   
<s>10.취소선</s>   
기본 글자에 <sub>아래첨자</sub>나 <sup>윗첨자</sup>를 나타낼 수 있다.   

<br>


### 수평선

`<hr>`를 입력하면 수평선을 넣을 수 있다.   

<br>


**결과**     
<hr>

<br>



### Code

`<code></code>` 를 사용합니다.   

<br>


```
<code>
  public static void main(String args){
    System.out.println("Hello HTML!");
  }
</code>
```

<br>

**결과**   

<code>
  public static void main(String args){   
    System.out.println("Hello HTML!");   
  }   
</code>


---
title: HTML 표,block,inline
excerpt: 표와 block, inline에 대해 알아보자.
categories: TIL
tog: true
tags: [ HTML ]
toc : false
---



### 표(table)

`<table>` : 기본적인 표를 생성하는 태그   
`<th>` : 표의 제목 셀을 나타내는 태그   
`<tr>` : 표의 행을 나타내는 태그   
`<td>` : 표의 일반 셀을 나타내는 태그   

`<caption>` : 테이블에 제목을 달 때 사용하는 태그   

<table border="1">
		<caption><b>웹 브라우저의 종류</b></caption>
		<tr>
			<th>브라우저명</th><th>제조사</th><th>홈페이지</th>
		</tr>
		<tr>
			<td>explore</td><td>MS</td><td>https://www.microsoft.com</td>
		</tr>
		<tr>
			<td>edge</td><td>MS</td><td>https://www.microsoft.com</td>
		</tr>
		<tr>
			<td>chrome</td><td>google</td><td>https://www.google.com</td>
		</tr>
		<tr>
			<td>firefox</td><td>mozila</td><td>https://www.mozila.org</td>
		</tr>
</table>

<br>
<br>

### 셀 병합

`colspan`: 열을 합칠 때 사용   
`rowspan`: 행을 합칠 때 사용   
<br>
<br>

<table border="1">
	<tr>
		<td colspan="2" rowspan="2" width="100px" height="150px">사진</td>
		<td width="50px">이름</td>
		<td width="150px"></td>
	</tr>
	<tr>
		<td>연락처</td>
		<td></td>
	</tr>
	<tr>
		<td>주소</td>
		<td colspan="3"></td>
	</tr>
	<tr>
		<td>자기소개</td>
		<td colspan="3"></td>
	</tr>
</table>



### 테이블 태그의 구조

thead: 제목 컬럼을 작성하는 구역   
tbody: 일반 컬럼을 작성하는 구역   
tfoot: footer contents를 작성하는 구역   
<br>
<br>



### block과 lnline

HTML의 요소들은 block과 inline으로 구분할 수 있다.   

block: 한 줄에 오직 하나의 엘리먼트만 위치할 수 있다.   
inline 한 줄에 여러 엘리먼트가 있을 수 있다.   
<br>


**div태그(block element)**   
<br>
<div style="background-color:red; color:white; width:20%">첫번째 영역</div>
<div style="background-color:yellow; color:blue; width:20%">두번째 영역</div>
<div style="background-color:blue; color:white; width:20%">세번째 영역</div>	    
<br>
<br>


**span태그(inline element)**   
<br>
<span style="background-color:red; color:white;">첫번째 영역</span>
<span style="background-color:yellow; color:blue;">두번째 영역</span>
<span style="background-color:blue; color:white;">세번째 영역</span>















