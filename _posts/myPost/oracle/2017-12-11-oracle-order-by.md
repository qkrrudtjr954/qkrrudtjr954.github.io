---
layout: post
title: "[ORACLE] 데이터 베이스의 정렬"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - ORDER BY
---

우리는 데이터를 내림차순, 오름차순으로 정렬해서 사용할 필요가 있다.
데이터 베이스에서는 order by 명령어를 사용해서 컬럼을 정렬할 수 있다.
정렬 가능한 항목은 숫자 뿐만 아니라 알파벳, 한글까지 포함한다.

```
SELECT 출력할 컬럼
FROM 테이블 명
WHERE 조건
ORDER BY 정렬할 컬럼
```
위의 쿼리문은 테이블에서 정렬할 컬럼을 ***오름차순*** 으로 정렬하고 결과를 보여준다.

<BR>
<BR>

#### EMPLOYEES 테이블
```
EMPLOYEE_ID    NOT NULL NUMBER(6)    
FIRST_NAME              VARCHAR2(20)
LAST_NAME      NOT NULL VARCHAR2(25)
EMAIL          NOT NULL VARCHAR2(25)
PHONE_NUMBER            VARCHAR2(20)
HIRE_DATE      NOT NULL DATE         
JOB_ID         NOT NULL VARCHAR2(10)
SALARY                  NUMBER(8,2)  
COMMISSION_PCT          NUMBER(2,2)  
MANAGER_ID              NUMBER(6)    
DEPARTMENT_ID           NUMBER(4)  
```

```sql
-- 급여에 따라 오름차순으로 정렬한다.
SELECT FIRST_NAME, LAST_NAME, SALARY
FROM EMPLOYEES
ORDER BY SALARY ASC;

-- 급여에 따라 내림차순으로 정렬한다.
SELECT FIRST_NAME, LAST_NAME, SALARY
FROM EMPLOYEES
ORDER BY SALARY DESC;

-- JOB_ID가 'IT_PROG' 인 사람에 대해
-- 급여를 기준으로 내림차순 정렬한다.
SELECT FIRST_NAME, LAST_NAME, SALARY
FROM EMPLOYEES
WHERE JOB_ID = 'IT_PROG'
ORDER BY SALARY DESC;

-- MANAGER_ID 가 NULL 이면 제일 앞으로 오고,
-- 오름차순 정렬한다.
SELECT EMPLOYEE_ID, FIRST_NAME, LAST_NAME, SALARY, MANAGER_ID
FROM EMPLOYEES
ORDER BY MANAGER_ID NULLS FIRST;

-- MANAGER_ID 가 NULL 이면 제일 뒤에 오고,
-- 내림차순 정렬한다.
SELECT EMPLOYEE_ID, FIRST_NAME, LAST_NAME, SALARY, MANAGER_ID
FROM EMPLOYEES
ORDER BY MANAGER_ID DESC NULLS LAST;

-- 직원 번호를 기준으로 내림차순 정렬한다.
SELECT *
FROM EMPLOYEES
ORDER BY EMPLOYEE_ID DESC;

-- 매니져 아이디로 정렬하고,
-- 그 안에서 SALARY를 정렬한다.
SELECT FIRST_NAME, LAST_NAME, SALARY, MANAGER_ID
FROM EMPLOYEES
ORDER BY MANAGER_ID NULLS FIRST, SALARY ASC;

-- ALIAS(별명)로도 정렬이 가능하다.
SELECT FIRST_NAME, LAST_NAME, SALARY*12 AS ANNUAL
FROM EMPLOYEES
ORDER BY ANNUAL DESC;

-- 부서 번호로 내림차순 정렬하고,
-- 그 안에서 직업 번호로 오름차순 정렬한다.
-- 그리고 연봉을 기준으로 내림차순 정렬한다.
SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, HIRE_DATE, JOB_ID, DEPARTMENT_ID
FROM EMPLOYEES
ORDER BY DEPARTMENT_ID DESC, JOB_ID ASC, SALARY DESC;
```
