---
layout: post
title: "[ORACLE] DB의 무결성 제약 조건"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
---


***무결성 제약 조건*** 이란 잘못된 데이터의 입력을 방지하기 위해 테이블의 컬럼에 설정할 수 있는 규칙을 의미한다.

설계 단계에서 데이터의 정확성을 위해서 다양한 종류의 규칙을 ***무결성 제약 조건*** 을 통해 설정하고 계획할 수 있다.


<br><br>

## PRIMARY KEY

- 한글 명칭은 ***기본키*** 이다.
- ID값으로 사용되는 컬럼이다.
- 유일하게 식별할 수 있는 정의된 규칙이다. ***(유일한 값)***
- 주민등록번호와 같은 ***단 하나의 정보(ROW)*** 를 뜻한다.
- NULL을 허용하지 않는다.
- PRIMARY KEY = NOT NULL + UNIQUE
- 최대 32개 컬럼까지 지정이 가능하다.

<br>

#### PRIMARY KEY의 생성
```sql
CREATE TABLE TEST_01(
    KEY_01 VARCHAR2(10) CONSTRAINT PK_TEST_01 PRIMARY KEY,
    KEY_02 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10)
);
```
```sql
CREATE TABLE TEST_01(
    KEY_01 VARCHAR2(10 PRIMARY KEY,
    KEY_02 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10)
);
```



- KEY_01을 PRIMARY KEY로 하여 TEST_01 테이블을 만든다.
- 두가지 모두 같은 방법이다.

<br>


#### PRIMARY KEY가 두 개 이상일 경우

```sql
CREATE TABLE TEST_01(
    KEY_01 VARCHAR2(10),
    KEY_02 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10),
    CONSTRAINT PK_TEST_01 PRIMARY KEY (KEY_01, KEY_02)
        USING INDEX TABLESPACE USERS    -- 빼도됨
);
```

- 테이블을 생성하는 시점에서 **PRIMARY KEY** 를 지정한다.


<br>


```sql
CREATE TABLE TEST_01(
    KEY_01 VARCHAR2(10),
    KEY_02 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10)
);

ALTER TABLE TEST_01
ADD
CONSTRAINT PK_TEST_01
PRIMARY KEY(KEY_01, KEY_02);
```

- 테이블을 생성하고 특정 컬럼을 **PRIMARY KEY** 로 지정한다.


<br>

#### PRIMARY KEY의 성질

```sql
INSERT INTO TEST_01(KEY_01, KEY_02, COL_01, COL_02)
VALUES ('AAA', 'aaa', 'CCC', 'DDD');
```

- 생성된 테이블에 값을 삽입한다.
- 이때 ```AAA```는 기본키값이 된다.

<br>


```sql
INSERT INTO TEST_01(KEY_01, KEY_02, COL_01, COL_02)
VALUES ('', 'aaa', 'CCC', 'DDD');
```

- 첫번째 컬럼 ```KEY_01```은 **PRIMARY KEY** 이다. **PRIMARY KEY** 는 null이 될수 없기 때문에 ***에러*** 가 발생한다.


<br>


```sql
INSERT INTO TEST_01(KEY_01, KEY_02, COL_01, COL_02)
VALUES ('AAA', 'bbb', 'BBB', 'DDD');
```

- **PRIMARY KEY** 로 ```AAA```가 이미 존재한다.
- ```AAA```를 삽입하려 하면 ***에러*** 가 발생한다.
-  **PRIMARY KEY** 의 **중복은 불가능** 하다.


<br>

```sql
SELECT *
FROM USER_CONSTRAINTS
WHERE TABLE_NAME= 'TEST_01'
    AND CONSTRAINT_TYPE ='P'
```

- TEST_01 테이블의 **PRIMARY KEY** 를 모두 확인한다.


<br>
<br>


## UNIQUE KEY

- EMAIL과 같은 정보를 저장하는 컬럼에 해당된다.
- 반드시 필요하지는 않지만, 값이 들어가야 한다면 중복이 되면 안된다.
- 값이 UNIQUE 하지만 NULL은 들어갈 수 있다.

<br>

#### UNIQUE KEY의 생성

생성 방법은 **PRIMARY KEY** 와 같다.


```sql
CREATE TABLE UKEY_TEST1(
    UKEY_01 VARCHAR2(10) CONSTRAINT UK_TEST_01 UNIQUE,
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10)
);  
```


<br>

#### 두 개 이상의 UNIQUE KEY 생성
```sql
CREATE TABLE UKEY_TEST2(
    UKEY_01 VARCHAR2(10),
    UKEY_02 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 VARCHAR2(10),
    CONSTRAINT UK_TEST UNIQUE(UKEY_01, UKEY_02)
);   
```

<br>

#### UNIQUE KEY의 특성

```sql
INSERT INTO TEST_01(UKEY_01, COL_01, COL_02)
VALUES('A', 'column1', 'column1');
```

- ```A``` 는 고정키가 된다.
- 위 값은 정상적으로 삽입된다.

<br>

```sql
INSERT INTO TEST_01(UKEY_01, COL_01, COL_02)
VALUES('', 'column2', 'column2');
```

- 고정키는 NULL값을 허용한다.
- 위 값은 정상적으로 삽입된다.



<br>

```sql
INSERT INTO TEST_01(UKEY_01, COL_01, COL_02)
VALUES('A', 'column3', 'column3');
```

- 고정키는 ***중복을 허용하지 않는다.***
- ```A``` 가 이미 고정키로 존재한다.
- 위 질의문의 ***에러*** 를 발생시킨다.



<br>

|UKEY_01 | COL_01| COL_02|
|:------:|:-----:|:-----:|
| A      |column1|column1|
|(null)  |column2|column2|


<br>
<br>



## CHECK

- 값 중 다른값이 들어왔을 때, 체크해준다.
- 데이터의 값의 범위나 특정한 값의 지정이 가능하다.
- 예제) 성별의 입력이 남자인지 여자인지 등등
- NULL값을 허용한다.

<br>


#### CHECK 의 생성

```sql
CREATE TABLE TEST_01(
    KEY_01 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    COL_02 NUMBER,
    CONSTRAINT CHK_TEST_01 CHECK(COL_01 IN ('MAN', 'WOMAN', 'ETC')),
    CONSTRAINT CHK_TEST_02 CHECK(COL_02 >= 1 AND COL_02 <= 999)
);
```

- ```KEY_01``` 은 ```MAN, WOMAN, ETC``` 그리고 ```NULL```을 허용한다.
- ```KEY_02``` 는 1 ~ 999 사이의 수를 삽입한다.


<br>

#### CHECK의 특성

```sql
INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('AAA', '', '');
```

- NULL값의 삽입이 가능하다.

<br>

```sql
INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('AAA', '', '1000');
```

- 첫번째 값은 NULL이기 때문에 문제가 발생하지 않는다.
- 두번째 값은 1 ~ 999 의 범위를 벗어나기 때문에 에러를 발생한다.

<br>

```sql
INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('AAA', 'MOONG', '550');
```

- 문자열은 ```MAN, WOMAN, ETC```만 가능하다.
- 위 질의문은 에러를 발생한다.


<br>

```sql
INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('AAA', 'MAN', '550');

INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('BBB', '', '100');

INSERT INTO TEST_01(KEY_01, COL_01, COL_02)
VALUES('CCC', 'WOMAN', '');
```

- 정상적으로 값이 삽입된다.

<br>

#### 삽입 결과

|KEY_01  | COL_01| COL_02|
|:------:|:-----:|:-----:|
|   AAA  | (null)| (null)|
|   AAA  |	MAN  | 550   |
|   BBB  | (null)| 100   |
|   CCC  |	WOMAN| (null)|



<br>
<br>


## FOREIGN KEY

- 한국 명칭은 **외래키** 라고 한다.
- 다른 테이블의 **PRIMARY KEY** 를 자신 테이블에 하나의 컬럼으로 정한다.
- 현재 테이블의 **FOREIGN KEY** 를 사용하여 다른 테이블에 **PRIMARY KEY** 에 접근하여 정보를 찾아온다.
- 하지만 반드시 **PRIMARY KEY** 일 필요는 없다.   
  - 중복이라면 값을 찾는데 어려움이 있을 수 있기 때문에 **PRIMARY KEY** 를 많이 사용한다.

<br>


#### TABLE1 생성

```sql
CREATE TABLE TABLE1(
    KEY_01 VARCHAR2(10) CONSTRAINT PK_TABLE PRIMARY KEY,
    COL_01 VARCHAR2(10)
);
```

- ```KEY_01```을 **PRIMARY KEY** 로 하는 TABLE1 생성

<br>


#### TABLE2 생성

```sql
CREATE TABLE TABLE2(
    KEY_01 VARCHAR2(10) CONSTRAINT PK_TABLE2 PRIMARY KEY,
    FKEY_01 VARCHAR2(10),
    COL_01 VARCHAR2(10),
    CONSTRAINT FK_TEST FOREIGN KEY(FKEY_01)
        REFERENCES TABLE1(KEY_01)
);


```

- TABLE1의 기본키(KEY_01)를 TABLE2의 외래키(FKEY_01)와 연결한다.


<br>


#### FOREIGN KEY의 성질

```sql
INSERT INTO TABLE1(KEY_01, COL_01)
VALUES ('A', 'AAAA');
INSERT INTO TABLE1(KEY_01, COL_01)
VALUES ('B', 'BBBB');
INSERT INTO TABLE1(KEY_01, COL_01)
VALUES ('C', 'CCCC');
```

- TABLE1에 값을 삽입한다.

|KEY_01 | COL_01|
|:-----:|:-----:|
|A	    |  AAAA |
|B	    |  BBBB |
|C	    |  CCCC |

<br>

```sql
INSERT INTO TABLE2(KEY_01, FKEY_01, COL_01)
VALUES ('F_A', 'A', 'AAAA');
INSERT INTO TABLE2(KEY_01, FKEY_01, COL_01)
VALUES ('F_B', 'B', 'BBBB');
INSERT INTO TABLE2(KEY_01, FKEY_01, COL_01)
VALUES ('F_C', 'C', 'CCCC');

-- 아래 쿼리는 에러를 발생한다.
INSERT INTO TABLE2(KEY_01, FKEY_01, COL_01)
VALUES ('F_C', 'D', 'CCCC');
```

- TABLE2에 값을 삽입한다.
- 이때, **두번째 컬럼은 외래키** 이다.
- ***외래키의 값은 TABLE1의 PRIMARY KEY이다.***
- ***TABLE1에 존재하지 않는 값을 삽입하면 에러가 난다.***


![외래키 사용](https://i.imgur.com/yO9e7gs.png)



#### 삽입 결과

|KEY_01 | FKEY_01 | COL_01|
|:-----:|:-------:|:-----:|
|F_A    |A	      |  AAAA |
|F_B    |B	      |  BBBB |
|F_C    |C	      |  CCCC |

<br>
<br>
#### 조인을 통한 결과 확인


```sql
SELECT *
FROM TABLE1 A INNER JOIN TABLE2 B
  ON A.KEY_01 = B.FKEY_01;
  ```

- TABLE1의 기본키와 TABLE2의 외래키를 기준으로 조인한다.


|KEY_01 | COL_01|KEY_01 | FKEY_01 | COL_01|
|:-----:|:-----:|:-----:|:-------:|:-----:|
|A	    |  AAAA |F_A    |A	      |  AAAA |
|B	    |  BBBB |F_B    |B	      |  BBBB |
|C	    |  CCCC |F_C    |C	      |  CCCC |



<br>
<br>


## NOT NULL

- 컬럼에 설정하는 설정 플래그이다.
- NULL 값을 허용하지 않는다는 의미이다.
- 컬럼에 설정할 수 있다.
- NULL 값이 삽이 되려하면 에러가 발생한다.

```sql
CREATE TABLE TB_TEST(
    COL_1 VARCHAR2(10) NOT NULL,
    COL_2 VARCHAR2(10)
);

-- 값을 삽입합니다.
INSERT INTO TB_TEST(COL_1, COL_2) VALUES('HELLO', 'WORLD');

INSERT INTO TB_TEST(COL_1, COL_2) VALUES('HELLO', '');

-- 에러가 난다. NULL을 삽입할 수 없기 때문에
INSERT INTO TB_TEST(COL_1, COL_2) VALUES('', 'WORLD');
```
