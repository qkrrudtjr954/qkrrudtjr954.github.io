---
layout: post
title: "[ORACLE] DB의 테이블 생성 문제 풀이"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
---


#### EMPLOYEES 테이블에서 부서별로 인원수,평균 급여,급여의 합,최소 급여,최대 급여를 포함하는 EMP_DEPTNO 테이블을 생성하라.

```sql
CREATE TABLE EMP_DEPTNO( DEPNO, E_COUNT, E_AVG, E_SUM, E_MIN, E_MAX )
AS (
    SELECT DEPARTMENT_ID DEPTNO, COUNT(DEPARTMENT_ID), TRUNC(AVG(SALARY), 3), SUM(SALARY), MIN(SALARY), MAX(SALARY)
    FROM EMPLOYEES
    GROUP BY DEPARTMENT_ID
);
```

<br>

#### EMP_DEPTNO 테이블에 ETC COLUMN을 추가하라.

(단 자료형은 VARCHAR2(50) 사용하라.)

```sql
ALTER TABLE EMP_DEPTNO ADD ETC VARCHAR2(50);
DESC EMP_DEPTNO;
```

<br>

#### EMP_DEPTNO 테이블에 ETC COLUMN을 수정하라.

(자료 형은 VARCHAR2(15)로 하라.)

```sql
ALTER TABLE EMP_DEPTNO MODIFY ETC VARCHAR(15);
DESC EMP_DEPTNO;
```

<br>

#### EMP_DEPTNO 테이블에 있는 ETC 을 삭제하고 확인하라.

```sql
ALTER TABLE EMP_DEPTNO DROP COLUMN ETC;
DESC EMP_DEPTNO;
```

<br>

#### 이전에 생성한 EMP_DEPTNO 테이블의 이름을 EMP_DEPT로 변경하라.

```sql
ALTER TABLE EMP_DEPTNO RENAME TO EMP_DEPT;
```

<br>

#### EMP_DEPT 테이블을 삭제하라.

```sql
DROP TABLE EMP_DEPT;
```

<br>

#### EMPLOYEES 테이블을 EMP 테이블을 생성하고 복제하도록 하라.

(데이터 포함)

```sql
CREATE TABLE EMP AS (SELECT * FROM EMPLOYEES);
```

<br>

#### EMP 테이블에 row를 추가해 봅니다.

(다만, 반드시 데이터를 기입을 안해도 되면, NULL로 설정하도록 한다.)

```sql
INSERT INTO EMP
VALUES (1222, 'HEELO', 'WORLD', 'EMAIN', NULL, SYSDATE, 'SA_PKS', NULL, NULL, NULL, NULL);

SELECT * FROM EMP WHERE EMPLOYEE_ID = 1222;
```

<br>

#### EMPLOYEES 테이블에서 EMPNO,ENAME,SAL,HIREDATE의 COLUMN만 선택하여 EMP_10 테이블을 생성(데이터 미포함)한 후, 10번 부서만 선택하여 이에 대응하는 값을 EMP_10테이블에 입력하라.

```sql
DROP TABLE EMP_10;
CREATE TABLE EMP_10 AS (
    SELECT EMPLOYEE_ID, LAST_NAME, SALARY, HIRE_DATE
    FROM EMPLOYEES
    WHERE DEPARTMENT_ID = 10
);
```

<br>

#### EMPLOYEES 테이블에서 사원 번호가 107인 사원의 부서를 10번으로 변경하여라.

```sql
UPDATE EMPLOYEES SET DEPARTMENT_ID=10 WHERE EMPLOYEE_ID=107;
SELECT DEPARTMENT_ID FROM EMPLOYEES WHERE EMPLOYEE_ID=107;
```

<br>

#### EMPLOYEES 테이블에서 사원 번호가 180인 사원의 부서를 20,

급여를 3500으로 변경하여라.

```sql
UPDATE EMPLOYEES
SET DEPARTMENT_ID =20, SALARY=3500
WHERE EMPLOYEE_ID = 180;
```

<br>

#### EMPLOYEES 테이블에서 Smith의 업무와 급여가 Hall의 업무와 급여와 일치하도록 수정하라.

```sql
UPDATE EMPLOYEES
SET (JOB_ID, SALARY) = (SELECT JOB_ID, SALARY FROM EMPLOYEES WHERE LAST_NAME='Hall')
WHERE LAST_NAME='Smith';
```
