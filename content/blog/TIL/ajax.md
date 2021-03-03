---
title: '동기식 데이터 통신과 비동기식 데이터 통신(Ajax)'
date: 2021-03-03
category: 'TIL'
draft: false
---

작성중입니다.  

### 동기식 데이터 통신
클라이언트가 서버로 데이터를 요청하면 응답이 올 때까지 다른 작업은 **대기**  


클라이언트가 작업을 진행하다가 서버로 요청을 보내게 되면은  
서버는 클라이언트에게 요청 받은 데이터를 처리한다.  
그리고 나서 요청 처리된 결과를 응답이라는 형태로 다시 클라이언트에게 전송 한다.  
<br>


이 때 서버가 요청처리하는 시간동안 클라이언트는 다른 작업을 진행하지 못하고  
응답을 대기하고 있는 상태 즉, 아무것도 하지 못하고 기다리고 있다.  
이런 데이터 통신 방식을 동기식 데이터 통신 이라고 한다.  
<br>


### Ajax
Asynchronous JavaScript And XML 의 약자이다.  
JavaScript를 이용하여 비동기식으로 클라이언트와 서버가 데이터(XML)를 주고 받는(통신)이다.  
데이터 형식은 XML 뿐만 아니라 Text, HTML, JSON, CSV등 다양한 형식 사용 가능하다.  


클라이언트가 서버로 데이터 요청 후 **응답을 기다리지 않고 다른 작업 수행** 가능하다.  
추후 요청에 대한 응답이 오면 응답에 관련된 작업을 진행한다.  
응답 대기 없다.  



### Ajax 특징
전체 페이지를 갱신하지 않고 일부분만 업데이트 가능  
사용자에게 즉각적인 반응과 풍부한 UI 경험을 제공 가능  
ActiveX나 플러그인 프로그램 설치 없이 이용가능  
JavaScript 방식, jQuery 방식으로 구현 가능  


### Ajax 단점
Ajax는 JavaScript이므로 브라우저에 따른 크로스 브라우저 처리가 필요함  
오픈 소스로 차별화가 어려움  
연속적인 데이터 요청 시 서버 부하 증가하여 페이지가 느려짐  
페이지 내 복잡도가 증가하여 헤어 발생 시 디버깅이 어려움  

```javascript
function getXMLHttpRequset(){
	//IE 7버전 이상 또는 그 외 브라우저들
	if(window.XMLHttpRequest){
		return new XMLHttpRequest();
	}else if(window.ActiveXObject){
		try{
			return new ActiveXObject("Microsoft.XMLHTTP");
		}catch(e){
			return null;
		}
	//ajax를 지원하지 않는 브라우저
	}else{	
		return null;
	}

}

```

1. XMLHttpRequest 객체 생성  
2. onreadystateChange  
3. open() 메서드 : 서버와 데이터 교환시 필요한 정보를 입력  
4. send() : 전송(서버로 데이터 교환 요청)  




출처 :  
https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest  
https://www.w3schools.com/js/js_ajax_http.asp
https://www.iei.or.kr/login/mediaBoardView.kh


