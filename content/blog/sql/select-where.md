---
title: 'SELECT, WHERE'
date: 2020-11-21
category: 'SQL'
draft: false
---




### SELECT
-테이블에서 원하는 데이터를 조회하는 구문   
-SELECT문의 결과물 -> RESULT SET(반환된 행들의 집합)   
-작성법 : SELECT 컬럼 명 FROM 테이블 명 WHERE 조건식;   
-테이블에서 조건식에 부합하는 ROW들의 컬럼 값들을 조회   
<br>



EMPLOYEE 테이블의 사번과 이름, 급여를 조회   

```sql   
SELECT EMP_ID, EMP_NAME, SALARY FROM EMPLOYEE;   
```   
<br>

EMPLOYEE 테이블의 고용일, 사원이름, 이메일 조회  
```sql
SELECT HIRE_DATE, EMP_NAME, EMAIL FROM EMPLOYEE;   
```
<br>


### SELECT *

EMPLOYEE 테이블의 모든 정보를 조회   
```sql   
SELECT * FROM EMPLOYEE;   
```
<br>




### DISTINCT

컬럼에 포함된 중복된 ROW를 제거하고 표시하고자 할 때 사용 
중복을 제거해서 조회하고 싶은 컬럼 앞에 `DISTINCT`를 붙이면 된다.   
<br>

EMPLOYEE 테이블에서 직원 직급코드를 조회   
```sql
SELECT JOB_CODE FROM EMPLOYEE;
```
<br>

**실행결과**   

|JOB_CODE|
|--------|
|J2|
|J2|
|J3|
|J5|
|J5|
|J1|
|J3|
|J4|
|J1|

<br>


```sql
SELECT DISTINCT JOB_CODE FROM EMPLOYEE;
```
<br>

**실행결과**   

|JOB_CODE|
|--------|
|J2|
|J3|
|J5|
|J1|
|J4|

<br>



### WHERE절
조회할 테이블에서 원하는 ROW를 조회하기 위해 작성하는 **조건문**  
SELECT 컬럼명 FROM 테이블명 WHERE 조건절  
<br>

### 비교연산자,논리연산자
비교연산자: <, >, <=, >=, =  
같지 않다 : !=, ^=, <>  
논리연산자: AND, OR, NOT  
<br>

### WHERE - BETWEEN AND
`WHERE`절에서 사용한다.   
~부터 ~까지 등의 범위를 지정할 때 사용된다.   

컬럼명 BETWEEN 하한값 AND 상한값   
<br>

월급이 350만 이상 600만 이하 이지 않은 사원의 정보를 조회   

```sql
SELECT EMP_ID, EMP_NAME, SALARY, JOB_CODE
FROM EMPLOYEE
WHERE SALARY NOT BETWEEN 3500000 AND 6000000;
```
<br>


### WHERE - IN

`WHERE` 조건절에서 여러 조건을 검색할 때 `IN`을 사용해 쉽게 조회할 수 있다.   
OR를 편하게 사용할 수 있다.   
컬럼명 IN(값,값,값, ...)   
<br>

D6부서와 D8부서의 사원들의 이름, 부서코드, 급여를 조회   

IN을 사용하지 않을 때   
```sql
SELECT DEPT_CODE, EMP_NAME, SALARY
FROM EMPLOYEE
WHERE DEPT_CODE = 'D8' OR DEPT_CODE = 'D6';
```
<br>

IN을 사용했을 때   
```sql
SELECT DEPT_CODE, EMP_NAME, SALARY
FROM EMPLOYEE
WHERE DEPT_CODE IN('D8','D9');
```
<br>

두 결과는 같지만 `IN` 사용하는 것이 훨씬 간편하다.   


