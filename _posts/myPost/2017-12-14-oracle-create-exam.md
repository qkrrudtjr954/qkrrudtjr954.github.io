---
layout: post
title: "[ORACLE] DB의 생성 문제 풀이"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
---

데이터 베이스에서 테이블을 생성하고 삭제, 수정하는 예제

예제의 테이블은 오라클에서 기본으로 제공되는 테이블을 사용합니다.


### EMPLOYEES 테이블
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

<br>
<br>

##### 문제1) EMPLOYEES 테이블에서 부서별로 인원수, 평균 급여, 급여의 합, 최소 급여, 최대 급여를 포함하는 EMP_DEPTNO 테이블을 생성하라.
```sql
CREATE TABLE EMP_DEPTNO( DEPNO, E_COUNT, E_AVG, E_SUM, E_MIN, E_MAX )
AS (
    SELECT DEPARTMENT_ID DEPTNO, COUNT(DEPARTMENT_ID), TRUNC(AVG(SALARY), 3), SUM(SALARY), MIN(SALARY), MAX(SALARY)
    FROM EMPLOYEES
    GROUP BY DEPARTMENT_ID
);
```


<br>


##### 문제2) EMP_DEPTNO 테이블에 ETC COLUMN을 추가하라.
(단 자료형은 VARCHAR2(50) 사용하라.)

```sql
ALTER TABLE EMP_DEPTNO ADD ETC VARCHAR2(50);
DESC EMP_DEPTNO;
```


<br>


##### 문제3) EMP_DEPTNO 테이블에 ETC COLUMN을 수정하라.
(자료 형은 VARCHAR2(15)로 하라.)

```sql
ALTER TABLE EMP_DEPTNO MODIFY ETC VARCHAR(15);
DESC EMP_DEPTNO;
```


<br>


##### 문제4) EMP_DEPTNO 테이블에 있는 ETC 을 삭제하고 확인하라.

```sql
ALTER TABLE EMP_DEPTNO DROP COLUMN ETC;
DESC EMP_DEPTNO;
```


<br>


##### 문제5) 이전에 생성한 EMP_DEPTNO 테이블의 이름을 EMP_DEPT로 변경하라.

```sql
ALTER TABLE EMP_DEPTNO RENAME TO EMP_DEPT;
```


<br>


##### 문제6) EMP_DEPT 테이블을 삭제하라.

```sql
DROP TABLE EMP_DEPT;
```


<br>


##### 문제7) EMPLOYEES 테이블을 EMP 테이블을 생성하고 복제하도록 하라.
(데이터 포함)

```sql
CREATE TABLE EMP AS (SELECT * FROM EMPLOYEES);
```
