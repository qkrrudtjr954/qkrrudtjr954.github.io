---
layout: post
title: "[ORACLE] DB의 집합"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - 집합
---


조인과 비슷한 개념으로 사용되는 집합에 대해 학습한다.
데이터 테이블 끼리 데이터에 대한 집합 연산을 사용할 수 있는데, 그 사용 결과는 JOIN 과 비슷하다.
그렇기 때문에 많이 사용되지는 않는다. (조인을 더 사용하기 때문)

<br>
<br>

## 집합의 종류
1. 합집합 (UNION)
2. 교집합 (INTERSECT)
3. 차집합 (MINUS)

<br>


## 합집합 (UNION)

![union](https://i.imgur.com/dsmD6hk.png)


EMPLOYEES 테이블의 JOB_ID (AD_VP, FI_ACCOUNT)와
JOBS 테이블의 JOB_ID (AD_VP, FI_ACCOUNT)가 모두 합해진 결과를 출력한다.


```sql
SELECT JOB_ID
FROM EMPLOYEES
WHERE JOB_ID IN('AD_VP', 'FI_ACCOUNT')
UNION ALL
SELECT JOB_ID
FROM JOBS
WHERE JOB_ID IN('AD_VP', 'FI_ACCOUNT');
```

<br>

## 교집합 (INTERSECT)

![intersect](https://i.imgur.com/IWVwTMu.png)

EMPLOYEE_ID와 MANAGER_ID의 교집합을 구한다.

중복은 사라지고 MANAGER_ID가 NULL인 PRESIDENT를 제외한 모든 MANAGER의 EMPLOYEE_ID가 출력된다.


```sql
SELECT EMPLOYEE_ID
FROM EMPLOYEES
INTERSECT
SELECT MANAGER_ID
FROM EMPLOYEES;
```

<br>

교집합은 JOIN을 사용해서 나타낼 수 있다.

```sql
SELECT DISTINCT E.EMPLOYEE_ID
FROM EMPLOYEES E INNER JOIN EMPLOYEES M
  ON E.EMPLOYEE_ID=M.MANAGER_ID;
```

<br>

## 차집합 (MINUS)

![minus](https://i.imgur.com/hMI7mFX.png)


EMPLOYEES 테이블에서 MANAGER를 전부 빼버린다.



```sql

SELECT EMPLOYEE_ID
FROM EMPLOYEES
MINUS
SELECT MANAGER_ID
FROM EMPLOYEES;
```

<br>

***차집합은 순서를 바꾸면 결과가 달라진다.***

<br>

MANGER에서 모든 직원을 제외한다. (사장만 남는다.)

```sql
SELECT MANAGER_ID
FROM EMPLOYEES
MINUS
SELECT EMPLOYEE_ID
FROM EMPLOYEES;
```
