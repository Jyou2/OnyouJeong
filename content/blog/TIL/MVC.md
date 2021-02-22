---
title: 'MVC2 패턴'
date: 2021-2-21
category: 'TIL'
draft: false
---


### MVC 패턴

MVC2는 디자인 패턴 중 하나이다.    
프로그램이나 어떤 특정한 것을 개발하는 중에 발생했던 문제점들을 정리해서   
상황에 따라 간편하게 적용해서 쓸 수 있는 것을 정리하여   
특정한 "규약"을 통해 쉽게 쓸 수 있는 형태로 만든 것이다.   
<br>


MVC2는 `Model`, `View`, `Controller`의 약자이다.   


### Model

Model은 dao, service 가 있다.
MODEL은 도메인 객체와 비즈니스 로직을 담당하는 `SERVICE` 객체와
DBMS에 접근해 데이터를 조회, 수정, 삽입, 삭제하는 `DAO` 객체로 이루어져있다.


### 도메인 객체

데이터베이스 테이블에서 조회 해온 한 행(ROW)의
값을 저장하는 용도로 사용되는 객체이다.
DOMAIN OBJECT, VALUE OBJECT(VO), DATA TRANSFER OBJECT(DTO), ENTITY, BEAN 등으로 불린다.

도메인객체 되기 위한 조건(JAVA BEAN 규약)
1. 모든 필드변수는 Private일 것 (캡슐화)
2. 반드시 기본생성자가 존재해야 한다.
3. 모든 필드변수는 Getter,Setter 메서드를 가져야 한다.

Oracle과 Java의 타입 매핑
char, varchar2 등 -> String
date -> java.util.date, java.sql.date
number -> int, double



model은 service와 dao로 나뉜다.
Service : 비지니스로직 작성
dao : daat access object db와 관련된 로직 작성

### controller
사용자의 요청을 받아, 해당 요청을 수행할 Service 의 메서드 호출
사용자가보낸 데이터를 Application에 내부에서 사용하기 적합하게 가공
따라서 사용자가 보내는 데이터의 형식이 바뀌더라도 Model의 코드가 변경될 일은 없어야 한다.
적합하지 않은 요청에 대해서는 허가/불가 처리를 하는 외벽 역할(권한관리)
Service에서 사용자의 요청을 처리해 결과를 반환하면,
Controller는 사용자에게 어떤 view를 보여줄 지를 선택




### model.dao
DAO: DBMS에 접근해 데이터의 조회, 수정, 삽입, 삭제 요청을 보내는 클래스
DAO의 메서드는 가능하다면 하나의 메서드에 하나의 쿼리만 처리하도록 작성


### model.service
웹어플리케이션의 비지니스 로직 작성
사용자가 전송한 데이터를 Controller에게 전달 받고
비지니스 로직을 위해 추가적으로 필요한 데이터를 Dao에게 요청해
핵심로직인 비지니스로직을 작성한다.
비지니스 로직을 Service가 담당하기 때문에 transaction관리도 Service가 담당한다.
transaction : 하나의 논리적인 작업 단위


### view
MVC2 모델이서 V는 view를 의미한다.
view는 사용자에게 데이터를 보여주는 형태와 양식을 의미한다.
view에 Index 클래스를 생성한다.


<!--
### JDBC
1. 오라클 jdbc driver를 jvm에 등록
forName메서드의 전달인자로 넣어준 문자열은 OracleDriver 클래스의fullName
Class.forName 메서드는 매개변수로 받은 클래스 명의 클래스객체를 반환
Class.forName메서드로 반환받은 Class객체를 통해 해당 Class의 메서드를 사용하거나
새로운 인스턴스를 반환받는 등으로 활용할 수 있다.


Class.forName("oracle.jdbc.driver.OracleDriver");

Connection

DBMS와의 연결을 관리
transaction(commit,rollback) 관리
Connection con = null;


Statement

쿼리 실행용 객체
Statement stmt = null;

ResultSet

Select쿼리의 결과로 반환된 데이터를 저장하는 객체
ResultSet rset = null;

-->









