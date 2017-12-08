---
layout: post
title: "[ORACLE] 데이터 베이스의 기본"
categories:
  - Data Base
tags:
  - Java
  - Data Base
  - DB
  - ORACLE
---

본 포스트는 ORACLE 데이터 베이스를 사용합니다. <br>

#### 테이블
테이블이란 데이터 베이스에서 데이터를 저장하는 하나의 공간을 의미한다.
그 의미는 우리가 보편적으로 사용하는 ***표*** 와 같다.
테이블은 컬럼(column)과 로우(row)를 갖는다.
- 컬럼(column) : 하나의 속성을 나타내며 표의 세로 줄을 의미한다.
- 로우(row) : 하나의 객체를 나타내며 표의 가로 한 줄을 의미한다.

<table>
  <tr>
    <th>컬럼</th>
    <th>컬럼</th>
    <th>컬럼</th>
    <th>컬럼</th>
  </tr>
  <tr>
    <td colspan=4>로우( 컬럼의 속성을 갖는다 )</td>
  </tr>
  <tr>
    <td colspan=4>로우( 컬럼의 속성을 갖는다 )</td>
  </tr>
</table>

<br>

#### 자료형
- 문자열
  - CHAR( SIZE )
  - VARCHAR( SIZE )
  - VARCHAR2( SIZE )
- 숫자
  - NUMBER
- 날짜
  - DATE

***문자열과 숫자 자료형에는 많은 서브 타입이 존재하지만,*** 통상적으로 하나의 ```VARCHAR2```***와*** ```NUMBER```***로 사용한다.***

<br>

#### 테이블 생성
```
CREATE TABLE 데이블명 (
  변수명 자료형(크기 [단위])     
);
```
테이블의 이름을 정의하고 테이블에 들어갈 변수의 이름을 지정할 수 있다.
```sql
CREATE TABLE TB_SAMPLE(
    COL_VARCHAR2 VARCHAR2(10 BYTE), --10BYTE 크기의 문자열을 저장하는 컬럼
    COL_NUMBER1 NUMBER(5),    --정수 5자리
    COL_NUMBER2 NUMBER(5, 2), --정수 5자리, 소수점 2자리
    COL_DATE DATE --날짜를 저장하는 컬럼
);
```

<br>

#### 테이블에 삽입
```
INSERT INTO 테이블명 (변수명)
VALUES (값);
```
테이블에 값을 삽입할 수 있다.

```
INSERT INTO 테이블명 (변수명 , 변수명...)
VALUES (값 , 값...);
```
테이블에 여러개의 값을 한번에 넣을 수 있다.

```sql
INSERT INTO ( COL_VARCHAR2, COL_NUMBER1, COL_NUMBER2, COL_DATE )
VALUES ( 'HELLO', 100, 200.444, SYSDATE );
```
**삽입 결과**
| COL_VARCHAR2 | COL_NUMBER1     | COL_NUMBER2     | COL_DATE     |
| :----------- | :-------------- | :------------- | :------------- |
| HELLO       | 100       | 200.44 | 17/12/08 |

- SYSDATE 는 현재의 날짜를 삽입한다.
- 200.444 는 소수점 2자리까지 들어가기 때문에 200.44 만 저장된다.

<br>

#### 자료 조회
```
SELECT 변수명 [, 변수명...]
FROM 테이블명;
```
테이블에 저장된 값을 조회할 수 있다.

```sql
SELECT * FROM TB_SAMPLE;
```

 * <span> * </span> 은 테이블 내에 모든 컬럼을 의미하며 출력해준다. <br>
 * <span> * </span> 대신 원하는 컬럼 이름을 넣으면 해당 컬럼만 출력된다.

**TB_SAMPLE**
| COL_VARCHAR2 | COL_NUMBER1     | COL_NUMBER2     | COL_DATE     |
| :------------- | :------------- | :------------- | :------------- |
| HELLO       | 100       | 200.44 | 17/12/08 |

<br>

## 예제

직원에 대한 정보를 담는 ***EMP*** 테이블을 활용해서 데이터를 출력하고, 삽입하는 데이터 베이스 사용 예제를 연습해본다.

<BR>

#### EMP 테이블 구조
```
EMPNO    NOT NULL NUMBER(4)    
ENAME             VARCHAR2(10)
JOB               VARCHAR2(9)  
MGR               NUMBER(4)    
HIREDATE          DATE         
SAL               NUMBER(7,2)  
COMM              NUMBER(7,2)  
DEPTNO            NUMBER(2)  
```
- EMPNO : 사원 번호
- ENAME : 사원 이름
- JOB : 업무
- MGR : 매니져
- HIREDATE : 고용일
- SAL : 월급
- COMM : 보너스
- DEPTNO : 부서 번호

<BR>

#### EMP 테이블 생성
```sql
CREATE TABLE EMP (
  EMPNO    NOT NULL NUMBER(4),
  ENAME             VARCHAR2(10),
  JOB               VARCHAR2(9),  
  MGR               NUMBER(4),    
  HIREDATE          DATE,         
  SAL               NUMBER(7,2),
  COMM              NUMBER(7,2),  
  DEPTNO            NUMBER(2)
);
```
- EMP 테이블을 생성한다.

<BR>

#### QUERY

```SQL
-- * : 테이블의 모든 컬럼을 표시한다.
-- EMP 테이블의 모든 DATA 출력
SELECT * FROM EMP;  

-- 테이블에서 원하는 컬럼만을 출력할 때
SELECT ENAME FROM EMP;
SELECT ENAME, EMPNO FROM EMP;

SELECT ENAME, SAL, SAL+300 FROM EMP;
SELECT ENAME, SAL, SAL*12 FROM EMP;
```
- 데이터를 출력하는 QUERY

<BR>

```SQL
-- 주석
/* 범위 주석 */

/* ALIAS : 별명 (대소문자 구분이 없다) */
SELECT SAL*12 연봉 FROM EMP;
```
- 별명을 설정할 수 있다.
- 컬럼의 이름이 ***연봉*** 으로 출력된다.

<BR>

```SQL
-- 연결 연산자 : 열이나 문자열을 다른 열에 연결
SELECT ENAME || ' HAS $ ' || SAL FROM EMP;
-- ENAME HAS $SAL 의 형태로 데이터를 출력한다.

SELECT ENAME || COMM FROM EMP;
-- ENAME COMM 의 형대로 데이터를 출력한다.
-- COMM이 NULL이면 아무것도 표현되지 않고 ENAME만 출력된다.
```

- 한개 이상의 데이터를 붙여서 한번에 출력할 수 있다.
- 데이터 + 데이터, 데이터 + 문자열 모두 가능하다.

<BR>

```SQL
-- DISTINCT : 중복행을 삭제해준다.
SELECT DISTINCT DEPTNO FROM EMP;
```

- 중복되는 행을 제거하고 출력해준다.

<BR>

```SQL
-- 테이블 구조 표시
DESCRIBE EMP;
DESC EMP;
```
- 현재 테이블의 구조를 표시해준다.
- 데이터의 타입과 크기를 명시해준다.

<BR><BR>

#### 연습 문제
```SQL
-- 1 BUN
-- EMP 테이블에서 사원번호, 사원 이름, 월급을 출력하세요
SELECT EMPNO, ENAME, SAL FROM EMP;

-- 2 BUN
-- EMP 테이블에서 사원 이름과 월급을 출력하는데
-- 컬럼명은 이름, 월급으로 바꿔서 출력하세요
SELECT ENAME 이름, SAL 월급 FROM EMP;

-- 3 BUN
-- EMP 테이블에서 사원번호, 사원이름, 월급, 연봉을 구하고
-- 각각 컬럼명은 사원번호, 사원이름, 월급, 연봉으로 출력하세요.
SELECT EMPNO 사원번호, ENAME 사원이름, SAL 월급, SAL*12 연봉 FROM EMP;

-- 4 BUN
-- EMP 테이블의 업무를 중복되지 않게 표시하세요
SELECT DISTINCT JOB FROM EMP;

-- 5 BUN
-- EMP 테이블의 사원명과 업무로 연결 (SMITH, CLERK)해서 표시하고
-- 컬럼명은 EMPLOYEE AND JOB으로 표시하세요.
SELECT (ENAME || ', ' || JOB) AS "EMPLOYEE AND JOB" FROM EMP;
```
