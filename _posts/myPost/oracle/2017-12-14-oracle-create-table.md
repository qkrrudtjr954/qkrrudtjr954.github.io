---
layout: post
title: "[ORACLE] DB의 테이블 생성 및 수정"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
---

데이터 베이스 내부에 테이블을 데이터를 저장하는 가장 기본적인 저장 구조로 ***행과 열*** 로 구분지어 데이터를 저장한다.

테이블의 가로를 행(row)이라고 하고 세로를 열(column)이라고 한다.
이제 테이블을 추가하고 수정하는 방법과 행과 열을 수정하는 방법을 학습한다.

<br>
<br>

## 테이블의 생성

기본적으로 테이터 테이블을 생성할 때는 ```CREATE TABLE ```명령어를 사용한다.

#### 테이블을 생성하는 방법

```sql
CREATE TABLE TB_TEST01(
    컬럼1 VARCHAR2(20),
    컬럼2 VARCHAR2(20),
    컬럼3 VARCHAR2(20),
    컬럼4 VARCHAR2(20),
    컬럼5 VARCHAR2(20)
);
```

<br>


#### 테이블을 생성함과 동시에 TABLESPACE를 설정하는 방법

```sql
CREATE TABLE TB_TEST02(
    컬럼1 VARCHAR2(20),
    컬럼2 VARCHAR2(20),
    컬럼3 VARCHAR2(20),
    컬럼4 VARCHAR2(20),
    컬럼5 VARCHAR2(20)
)TABLESPACE TABLESPACE1;
```

<br>


#### 기존에 존재하는 테이블을 복제해서 테이블을 생성하는 방법

```sql  
CREATE TABLE TB_TEST03
AS
SELECT * FROM JOBS;
```

- JOBS 테이블의 정보를 모두 가져와 TB_TEST03 를 만든다.
- JOBS 테이블의 모든 값을 가져와야하기 때문에 ```SELECT``` 문이 사용되었다.


<br>


#### 기존의 존재하는 테이블의 컬럼만을 복제해서 테이블을 생성하는 방법

```sql
CREATE TABLE TB_TEST04
AS
SELECT * FROM JOBS WHERE 1 = 2;
```

- 데이터까지 전부 복사를 하는 것이 아니라 컬럼만 복사하는 방법이다.
- ```WHERE``` 절에 거짓된 조건을 넣어 값을 추출하지 않도록 했다.

<br>


#### 기존에 존재하는 테이블에서 원하는 데이터만 가져와 테이블을 생성하는 방법

```sql
CREATE TABLE TB_TEST05(ID, NAME, SALARY, HIRE)
AS (  
  SELECT EMPLOYEE_ID, LAST_NAME, SALARY, HIRE_DATE
  FROM EMPLOYEES
);
```

- 기존에 존재하는 EMPLOYEES 테이블에서 원하는 컬럼만 ```SELECT``` 한다.


<br>


#### 기존에 존재하는 테이블에서 원하는 컬럼만 가져와 테이블을 생성하는 방법


```sql
CREATE TABLE TB_TEST06(ID, NAME, SALARY, HIRE)
AS
  SELECT EMPLOYEE_ID, LAST_NAME, SALARY, HIRE_DATE FROM EMPLOYEES WHERE 1 = 2;
```

- 데이터 없이 원하는 컬럼 만을 가져오는 방법이다.
- ```WHERE``` 절에 거짓된 조건을 넣어 값을 추출하지 않도록 했다.



<br>



#### 한개 이상의 테이블에서 값을 가져와 테이블을 생성하는 방법


```sql
CREATE TABLE TB_TEST07(번호, 이름, 월급, 입사일, 부서)
AS
SELECT EMPLOYEE_ID, LAST_NAME, SALARY, HIRE_DATE, DEPARTMENTS.DEPARTMENT_NAME
FROM EMPLOYEES, DEPARTMENTS
```

- 조인을 사용하여 두개 이상의 테이블에서 원하는 데이터만을 가져올 수 있다.
- 위의 방법들과 마찬가지로 ```WHERE``` 절을 추가해서 컬럼만 가져올 수도 있다.


<br>
<br>
<br>
<br>



## 테이블의 수정

테이블을 생성하고 테이블의 이름이나 컬럼, 값등을 수정해야할 때, ```ALTER``` 명령어를 사용한다.
.```ALTER```는 테이블 내 값이 아닌 테이블 자체를 수정할 때 사용된다.

<br>


#### 테이블의 이름을 수정하는 방법

```sql
ALTER TABLE TB_TEST04
RENAME TO TB_TEST99;
```

- 이미 정의된 TB_TEST04 테이블의 이름을 TB_TEST99 로 수정한다.

<br>



#### 테이블에 하나의 컬럼(열)을 추가하는 방법



```sql
ALTER TABLE TB_TEST99
ADD COL_01 VARCHAR2(30);
```

- TB_TEST99 에 하나의 COL_01 컬럼 추가한다.
- 데이터의 자료형은 ```VARCHAR2```이고 사이즈는 30이다.




<br>


#### 테이블에 두개 이상의 컬럼(열)을 추가하는 방법


```sql
ALTER TABLE TB_TEST99
ADD (   COL_02 VARCHAR2(20),
        COL_03 VARCHAR2(30) );        
```


- TB_TEST99 에 COL_02 컬럼과 COL_02 컬럼을 추가한다.
- 두 데이터의 자료형은 ```VARCHAR2```이고 사이즈는 각각 20과 30이다.



<br>



#### 하나의 컬럼을 수정하는 방법



```sql
ALTER TABLE TB_TEST99
MODIFY COL_01 VARCHAR2(10);
```

- 기존 COL_01의 크기를 30에서 10으로 변경한다.
- 테이블에서 하나의 컬럼을 수정하는 방법이다.
- 데이터를 수정하는 것이 아니고 컬럼의 속성을 수정하는 것이다.


<br>


#### 두개 이상의 컬럼을 수정하는 방법



```sql
ALTER TABLE TB_TEST99
MODIFY (    COL_01 VARCHAR2(20),
            COL_02 VARCHAR2(20),
            COL_03 VARCHAR2(20) );
```


- 테이블의 컬럼( COL_01, COL_02, COL_03 )를 ```VARCHAR2``` 로 수정한다.
- 테이블에서 두개 이상의 컬럼을 수정하는 방법이다.
- 데이터를 수정하는 것이 아니고 컬럼의 속성을 수정하는 것이다.


<br>



#### 하나의 컬럼을 삭제하는 방법



```sql
ALTER TABLE TB_TEST99
DROP COLUMN COL_03;
```
- TB_TEST99 테이블의 COL_03 컬럼을 삭제한다.


<br>


#### 두개 이상의 컬럼을 삭제하는 방법

```sql
ALTER TABLE TB_TEST99
DROP ( COL_01, COL_02 );
```

- TB_TEST99 테이블의 COL_01, COL_02 컬럼을 삭제한다.


<br>



#### 컬럼의 이름을 수정하는 방법


```sql
ALTER TABLE TB_TEST99
RENAME COLUMN COL_01 TO 컬럼1;
```

- ```COL_01``` 의 이름을 ```컬럼1```으로 변경한다.
- 컬럼 이름을 수정하는 방법


<br>



#### 테이블을 삭제하는 방법


```sql
DROP TABLE TB_TEST99;
```
- 테이블을 삭제하는 방법
- 실무에서 사용하면 잡혀간다.
