---
title: 'Oracle 예제1'
excerpt: 학원에서 배운 것을 복습합니다.
date: 2020-11-21
category: 'SQL'
draft: false
---



1.EMPLOYEE 테이블에서 부서코드가 'D9'인 직원의 이름, 부서코드 조회  
```sql   
select emp_name, dept_code   
from employee   
where dept_code = 'D9';   
```   


2.EMPLOYEE 테이블에서 급여가 4000000이상인 직원들의 이름과 연봉을 조회  
```sql   
select emp_name, salary*12  
from employee   
where salary salary >= 4000000;  
```   

3.EMPLOYEE 테이블에서 부서코드가 D9가 아닌 사원의 사번, 이름, 부서코드를 조회  
```sql   
select emp_id, emp_name, dept_code  
from employee  
where dept_code != 'D9';   
```   
4.EMPLOYEE 테이블에서 퇴사여부가 N인 직원을 조회하고,   
근무여부를 '재직중'으로 표시하여 사번, 이름, 고용일, 근무여부를 조회하시오   
```sql   
select emp_id, emp_name, hire_date, '재직중' 근무여부   
from employee   
where ent_yn = 'N'   
```   

5.EMPLOYEE 테이블에서 월급이 3000000 이상인 사원의 이름, 월급, 고용일 조회   
```sql   
select emp_name, salary, hire_date  
from employee   
where salary >= 3000000;   
```   

6.EMPLOYEE 테이블에서 실제연봉(세후연봉, 세금 3%)이 4500만원 이상인   
사원의 이름, 월급, 실수령액, 고용일을 조회   
```sql   
select emp_name, salary, salary*0.97 as 실수령액, hire_date   
from employee   
where salary*0.97*12 >= 45000000;   
```   

<br>
<br>
AND, OR 문제  
<br>

1.부서코드가 'D6' 이고 급여를 200만원 보다 많이 받는 직원의 이름, 부서코드, 급여를 조회   
```SQL   
select emp_name, dept_code, salary  
from employee  
where dept_code = 'D6' and salary > 2000000;  
```   

2.EMPLOYEE 테이블에서 월급이 400만원 이상이고 JOB코드가 J2인 사원의 모든 컬럼을 조회   
```sql  
select * from employee  
where salary >= 4000000, job_code = 'J2';  
```  

3.EMPLOYEE 테이블에서 부서코드가 D9이거나  D5인 사원 중   
고용일이 02/01/01 보다 빠른 사원의 이름, 부서코드, 고용일 조회   
```sql
select emp_name, dept_code, hire_date  
from employee  
where (dept_code = 'D9' or dept_code = 'D5')  
and hire_date < '02/01/01';  
```


4.EMPLOYEE 테이블에서 월급이 350만원 이상이고 600만원 이하인   
직원의 사번, 이름, 급여, 직급코드를 조회   
```sql  
select emp_id, emp_name, salary, job_code  
from employee  
where salary >= 3500000 and salary <= 6000000
```  

```sql  
-- betweem 사용
select emp_id, emp_name, salary, job_code  
from employee   
where salary between 3500000 AND 6000000;  
```  





