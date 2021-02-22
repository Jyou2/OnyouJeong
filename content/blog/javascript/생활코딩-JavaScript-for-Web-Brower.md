---
title: '생활코딩 JavaScript for Web Brower'
excerpt: JavaScript for Web Browser(생활코딩)으로 공부합니다.
date: 2021-01-05
category: 'Javascript'
draft: false
---




### 전역객체 Window
<br>

![window 설명](https://github.com/Jyou2/onyouJeong/blob/main/content/blog/javascript/images/window.png)   
출처: 생활코딩   
<br>
Window 객체는 모든 객체가 소속된 객체이고, 전역객체이면서, 창이나 프레임을 의미한다.   
DOM(Document Object Model), BOM(Browser Object Model), JavaScript는 window에 소속돼있다.   
<br>


### 사용자와 커뮤니케이션

#### alert();

`alert()`은 경고창이다.   
밑에 두개는 결과가 같다.   
window가 생략되어있는 것이다.   

```javascript
window.alert('Hello World!');
arlert('Hellow World!');
```
<br>


#### confirm();

경고창이지만 확인과 취소 버튼이 있다.   
확인을 누르면 `true`를 리턴하고   
취소를 누르면 `false`를 리턴한다.   
<br>



#### prompt(); 
사용자로부터 어떤 입력값을 입력받아서 그것에 따라 자바스크립트가 입력한 값을 얻어낼 수 있는 기능이다.   
<br>


예시   

```javascript
<!DOCTYPE html>
<html>
    <body>
        <input type="button" value="prompt" onclick="func_prompt()" />
        <script>
            function func_prompt(){
                if(prompt('id?') === 'javascript'){
                    alert('welcome');
                } else {
                    alert('fail');
                }
            }
        </script>
    </body>
</html>

```
<br>



### Location 객체
Location 객체는 문서의 주소와 관련된 객체로 Window 객체의 property다.   
윈도우의 문서 URL을 변경할 수 있고, 문서의 위치와 관련해서 다양한 정보를 얻을 수 있다.   
<br>



```javascript
location.toString() : 현재 윈도우의 문서가 위치하는 URL을 알아내는 방법이다.
location.href : 위와 똑같지만 더 선호되는 방식이다.
```
<br>


#### URL Parsing   
Location 객체는 URL을 의미에 따라서 별도의 프로퍼티를 제공하고 있다.   
```javascript
console.log(location.protocol, location.host, location.port, location.pathname, location.search, location.hash)
```
<br>


#### URL 변경하기   
  
```javascript
아래 코드는 현재 문서를 http://egoing.net으로 이동한다.
location.href = 'http://egoing.net';

아래와 같은 방법도 같은 효과를 낸다.
location = 'http://egoing.net';

아래는 현재 문서를 리로드하는 간편한 방법을 제공한다.
location.reload();
```
<br>



### Navigator 객체
브라우저의 정보를 제공하는 객체다. 주로 호환성 문제등을 위해서 사용한다.   

`console.dir();`로 객체의 모든 프로퍼티를 열람할 수 있다.   

```javascript
appName: 웹브라우저의 이름
IE(Microsoft Internet Explorer), 파이어폭스,크롬등은 Netscape로 표시

appVersion: 브라우저의 버전

userAgent: 브라우저가 서버측으로 전송하는 USER-AGENT HTTP의 헤더의 내용이다.
appVersion과 비슷하다.

platform: 브라우저가 동작하고 있는 운영체제에 대한 정보
```
<br>


#### 기능테스트

navigator 객체는 브라우저 호환성을 위해서 주로 사용하지만, 모든 브라우저에 대응하는 것은 쉬운 일이 아니므로 아래와 같이 기능 테스트를 사용하는것이 선호된다.   
<br>


```javascript
// From https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys
if (!Object.keys) {
  Object.keys = (function () {
    'use strict';
    var hasOwnProperty = Object.prototype.hasOwnProperty,
        hasDontEnumBug = !({toString: null}).propertyIsEnumerable('toString'),
        dontEnums = [
          'toString',
          'toLocaleString',
          'valueOf',
          'hasOwnProperty',
          'isPrototypeOf',
          'propertyIsEnumerable',
          'constructor'
        ],
        dontEnumsLength = dontEnums.length;
 
    return function (obj) {
      if (typeof obj !== 'object' && (typeof obj !== 'function' || obj === null)) {
        throw new TypeError('Object.keys called on non-object');
      }
 
      var result = [], prop, i;
 
      for (prop in obj) {
        if (hasOwnProperty.call(obj, prop)) {
          result.push(prop);
        }
      }
 
      if (hasDontEnumBug) {
        for (i = 0; i < dontEnumsLength; i++) {
          if (hasOwnProperty.call(obj, dontEnums[i])) {
            result.push(dontEnums[i]);
          }
        }
      }
      return result;
    };
  }());
}
```
<br>



#### 창 제어

```javascript
window.open('문서.html'): 새창을 생성하여 이동한다. 새탭으로 생성된다.
window.open('문서.html','_self'): 새탭이 열리지 않고 현재창에서 지정한 문서가 열린다.
window.open('문서.html','_blank'): 새탭으로 지정한 문서가 열린다.
window.open('문서.html','ot'): 창에 이름을 붙일 수 있다.
open을 재실행 했을 때 동일한 창의 이름이 있다면 그곳으로 문서가 로드된다.

```


### DOM

Document Object Model로 웹페이지를 자바스크립트로 제어하기 위한 객체 모델을 의미한다.   
window 객체의 document 프로퍼티를 통해서 사용할 수 있다.   
Window 객체가 창을 의미한다면 Document 객체는 윈도우에 로드된 문서를 의미한다고 할 수 있다.   
<br>


문서를 자바스크립트로 제어하려면 제어의 대상에 해당되는 객체를 찾아야한다.   
문서 내에서 객체를 찾는 방법은 document 객체의 메소드를 이용한다.    
<br>


document.getElementsByTagName : tag이름을 기준으로 객체를 조회한다.   
document.getElementsByClassName : class 속성의 값을 기준으로 객체를 조회한다.   
document.getElementById : id 값을 기준으로 객체를 조회한다.   
document.querySelector : css선택자의 문법을 이용해서 객체를 조회한다.   
document.querySelectorAll : querySelector과 같지만 모든 객체를 조회한다는 점이 다르다.   
















