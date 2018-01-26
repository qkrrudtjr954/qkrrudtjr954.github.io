---
layout: post
title: "[ORACLE] DB의 sequence와 synonym"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - SEQUENCE
  - SYNONYM
---


sequence : 유일한 값을 생성해 주는 oracle object이다.

- 회원 번호, 게시판 글 번호 ( 1 -> 2 -> 3 ...) 에 사용되는 증가 연산이다.
- sequence 를 생성하면, 기본키와 같이 순차적으로 증가하는 컬럼을 자동적으로 생성해줄 수 있다.
- 독립적이다. ( 테이블과 관계가 없다. )
- sequence의 초기화는 불가능하다.

<br>

## SEQUENCE의 생성

```sql
CREATE SEQUENCE TEST_SEQ
INCREMENT BY 1      -- 1씩 증가된다.
START WITH 10;
```

<br>

## SEQUENCE의 삭제

```sql
-- SEQUENCE의 삭제
DROP SEQUENCE TEST_SEQ;
```

<br>

## SEQUENCE의 사용

```sql

-- CURRVAL 현재의 값을 뜻한다.
SELECT TEST_SEQ.CURRVAL -- 현재의 값
FROM DUAL;

-- NEXTVAL 다음의 값을 뜻한다.
SELECT TEST_SEQ.NEXTVAL -- 다음 값 ( 값이 하나 상승한다. )
FROM DUAL;
```

<br>

## SEQUENCE NUMBER의 수정

```sql
-- 숫자를 늘려주는 것이 가능
ALTER SEQUENCE TEST_SEQ
INCREMENT BY 3; -- 3씩 증가하도록 수정한다.
```

<br>

## 동의어(SYNONYM / 객체의 별명)

- 동의어 (객체의 별명) 를 생성하여 객체에 엑서스를 단순하게 한다.

```sql
CREATE SYNONYM "사원 테이블"
FOR EMPLOYEES;

SELECT * FROM "사원 테이블";

DROP SYNONYM "사원 테이블";
```

- ```EMPLOYEES``` 테이블을 ```사원 테이블```이란 별명으로 접근할 수 있다.
