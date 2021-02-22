---
title: 'JDBC'
date: 2021-02-20
category: 'TIL'
draft: false
---


### JDBC (Java Database Connectivity)
Java 언어에서 Database에 접근할 수 있게 해주는 Programming API   
Oracle DBMS, My SQL DBMS, Sybase DBMS 등 어떤 DBMS가 돼도 
JDBC를 통해 별다른 조건 없이 가능하다.   
즉, 유연하다.
<br>


<!--
MVC2패턴대로 패키지를 controller, model, view로 나눈 후
model.vo에 Member라는 class를 생성한다.
Member라는 클래스는 도메인 객체이다.

도메인 객체
:데이터베이스 테이블에서 조회 해온 한 행(ROW)의
값을 저장하는 용도로 사용되는 객체

모든 필드변수는 private으로 선언하고
기본 생성자와 getter/setter메서드를 선언한다.

그리고 나서 
View는 사용자에게 데이터를 보여주는 형태와 양식을 의미한다.
view패키지에 사용자에게 보여줄 MemberMenu라는 클래스와 Index클래스를 생성한다.

-->



### JDBC 절차

1.Driver 등록   
2.DBMS와 연결   
3.Statement 생성   
4.SQL전송   
5.결과 받기   
6.닫기  
<br>


```java
1. Class.forName("oracle.jdbc.driver.OracleDriver");
2. Connection con = DriverManager.getConnection("url","id","password");
3. Statement stmt = con.createStatement();
4. ResultSet rset = stmt.executeQuery(sql);
5. rs.next();
```
<br>



### Dao에 작성한다.

```java
//model.vo에 있는 도메인 객체 
Member member = null;


//Connection
//DBMS와의 연결을 관리
//transaction(commit,rollback) 관리
Connection con = null;

//Statement
//쿼리 실행용 객체
Statement stmt = null;

//ResultSet
//Select쿼리의 결과로 반환된 데이터를 저장하는 객체
ResultSet rset = null;

```


### 1.오라클 JDBC Driver를 JVM에 등록

Java Build Path Libraries에 jar파일 추가해준다.   
<br>



forName메서드의 전달인자로 넣어준 문자열은 OracleDriver 클래스의fullName   
Class.forName 메서드는 매개변수로 받은 클래스 명의 클래스객체를 반환   
Class.forName메서드로 반환받은 Class객체를 통해 해당 Class의 메서드를 사용하거나   
새로운 인스턴스를 반환받는 등으로 활용할 수 있다.   
<br>


```java
Class.forName("oracle.jdbc.driver.OracleDriver");
```
<br>


### 2. 데이터베이스와 연결처리

```java
conn = DriverManager.getConnection("url", "user", "password");
```
<br>



**Data Source Explorer**
Window - Show View - Data Source Explorer 클릭   
Database Connections -  마우스 우클릭 - New 클릭   
DBMS랑 이클립스랑 연결하는 설정 창이다.   
<br>


**JAR 위치**
oraclexe - app - oracle - product - 폴더 클릭 - server - jdbc - lib - jar파일 선택   
<br>


연결 후  
Connection URL 이라고 적힌 것이 URL이다.   
jdbc:oracle:thin:@localhost:1521:xe   
<br>



### 3. 쿼리 실행용 객체 생성

```java
stmt = conn.createStatement();
```
<br>


### 4. 쿼리작성

```java
//oracle에서 문자열 다룰 때 ''있어야 하므로 똑같이 작성해준다.
String query = "select * from member where user_id = '" + userId + "' and password = '" + password + "'";
```
<br>


### 5. 쿼리를 실행하고 결과(ResultSet)를 받는다.

```java
rset = stmt.executeQuery(query);
```
<br>


### 6. ResultSet에 저장된 데이터를 VO객체로 옮겨담기

next() :   
현재 위치에서 다음 Row의 데이터가 있는지 확인하고   
있으면 true, 없으면 false를 반환한다.   
<br>


```java
if(rset.next()){
  //쿼리 실행결과가 존재하면 member에 데이터 반환
  member = new Member();
  //현재 Row의 user_id 컬럼값을 java의 String타입으로 가져온다.
  member.setUserId(rset.getString("user_id"));
  member.setPassword(rset.getString("password"));
  //등등 가져온다.
}

```
<br>


**SQLException**   
DB와 통신 중에 발생하는 모든 예외를 담당하는 Exception   
<br>


### 7. finally 블럭에 DBMS의 연결을 끊어준다.   

```java
} finally {
			try {
				rset.close();
				stmt.close();
				conn.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

```












