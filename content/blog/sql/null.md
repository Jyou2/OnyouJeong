---
title: 'NULL'
date: 2020-11-30
category: 'SQL'
draft: false
---




### IS NULL
컬럼값이 NULL인 경우를 조회할 경우   

보너스를 받지 않는 사원의 사번, 이름, 급여, 보너스 조회   

```sql
SELECT EMP_ID, EMP_NAME, SALARY, BONUS
FROM EMPLOYEE
WHERE BONUS IS NULL;
```
<br>

### IS NOT NULL
컬럼값이 NULL인 아닌 경우 TRUE 반환   

보너스를 받은 사원의 사번, 이름, 급여, 보너스 조회  

```sql
SELECT EMP_ID, EMP_NAME, SALARY, BONUS
FROM EMPLOYEE
WHERE BONUS IS NOT NULL;
```



