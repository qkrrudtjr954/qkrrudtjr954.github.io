---
layout: post
title: "[ORACLE] 데이터 베이스의 기본 함수"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
---

오라클에서 자주 사용되는 함수에 대한 사용법을 학습한다.



- 문자 함수
- 숫자 함수
- 날짜 함수

## 문자 함수
```sql

-- 더미 테이블을 만들어준다.
-- 값만 확인하는 테이블
SELECT 1 FROM DUAL;

-- CHR(N) : ASKII CODE 값을 문자로 변환.
SELECT CHR(65) FROM DUAL; -- A 출력

-- || 문자를 하나로 붙여서 표현한다.
SELECT 'AA' || CHR(97) || 'BB' FROM DUAL; -- AAaBB

-- LPAD 왼쪽 나머지를 특정 문자로 채움
-- 빈문자를 채우지 않음
--"       BBB" 출력
SELECT LPAD('BBB', 10) FROM DUAL;
-- 빈문자를 -로 채움
-- "-------BBB" 출력
SELECT LPAD('BBB', 10, '-') FROM DUAL;

--RPAD 오른쪽 나머지를 특정 문자로 채움
--"BBB       " 출력
SELECT RPAD('BBB', 10) FROM DUAL;
--"BBB-------" 출력
SELECT RPAD('BBB', 10, '-') FROM DUAL;

-- INSTR : java indexOf 와 비슷한 함수
-- 해당 문자의 위치를 반환한다. (DB index 는 항상 1부터 시작)
SELECT INSTR('A1234B567A1234B', 'A') FROM DUAL; -- 1출력
--2번째 수 부터 끝까지 중에 A의 위치를 찾아낸다.
SELECT INSTR('A1234B567A1234B', 'A', 2) FROM DUAL; -- 10출력
--2번째 이후로 첫번째에 나오는 A를 찾는다
SELECT INSTR('A1234B567A1234B', 'A', 2, 1) FROM DUAL;

--REPLACE : 문자열 치환
-- W를 빈문자로 치환 : HEELO ORLD 출력
SELECT REPLACE('HEELO WORLD', 'W') FROM DUAL;
-- EE를 ㄱ으로 치환 : HㄱLO WORLD
SELECT REPLACE('HEELO WORLD', 'EE', 'ㄱ') FROM DUAL;

--문자를 숫자로 변환
SELECT TO_NUMBER('125') FROM DUAL;
-- 숫자로 변경되어 연산이 가능하다
-- 130 출력
SELECT TO_NUMBER('125')+5 FROM DUAL;

--문자를 자르는 함수
-- 2번째 부터 3개
SELECT SUBSTR('ABCDEFG', 2, 3) FROM DUAL;
-- 2번째 부터 쭉
SELECT SUBSTR('ABCDEFG', 2) FROM DUAL;
```

## 숫자 함수
```sql
-- 올림
SELECT CEIL(14.1) FROM DUAL;
-- 내림
SELECT FLOOR(15.6) FROM DUAL;
--반올림
SELECT ROUND(15.5) FROM DUAL;
SELECT ROUND(15.3) FROM DUAL;

--나머지를 구하는 함수
SELECT MOD(5, 3) FROM DUAL;
SELECT MOD(5, 7) FROM DUAL;

--제곱수를 구하는 함수( 2의 3승 )
SELECT POWER(2, 3) FROM DUAL;
--제곱근을 구하는 방법(루트)
SELECT POWER(4, 0.5) FROM DUAL;

--부호
SELECT SIGN(13) FROM DUAL;  --양수면 1
SELECT SIGN(0) FROM DUAL;   --0이면 0
SELECT SIGN(-13) FROM DUAL; --음수면 -1

--버림
SELECT TRUNC(13.1231230) FROM DUAL;
--소수 3번째까지는 남김
SELECT TRUNC(13.1231230, 3) FROM DUAL;
--1의 자리수 아래로 전부 버림
SELECT TRUNC(13.1231230, -1) FROM DUAL;

--아스키 코드 값을 숫자로 출력해주는 함수
SELECT ASCII('A') FROM DUAL;

--변환 함수
--TO_CHAR : DATA를 STRING으로 변환할 때 많이 사용된다.( 스트링으로 변환 )
SELECT TO_CHAR(SYSDATE) FROM DUAL;
-- 현재 시간을 두번째 인자(포맷) 모양의 문자열로 바꾼다.
-- 2017-12-08 15:35:28 출력
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD HH24:MI:SS') FROM DUAL;
-- 첫번째 인자의 수를 두번째 인자(포맷) 모양의 문자열로 바꾼다.
-- 10,000,000 출력
SELECT TO_CHAR(10000000, '999,999,999') FROM DUAL;
```

## 날짜 함수

```sql
-- 문자를 숫자로 변환하는 함수 ( 포맷을 명시해주어야 한다. )
SELECT TO_DATE('20180424', 'YYYYMMDD') FROM DUAL;
-- 달을 더하는 함수( 현재 날짜에 6개월을 더한다. )
SELECT SYSDATE, ADD_MONTHS(SYSDATE, 6) FROM DUAL;

--해당하는 월의 마지막 날짜.
SELECT LAST_DAY(SYSDATE) FROM DUAL;
SELECT LAST_DAY(TO_DATE('2018-04-24', 'YYYY-MM-DD')) FROM DUAL;
SELECT LAST_DAY(TO_DATE('2018-04', 'YYYY-MM')) FROM DUAL;
```


## 자주 사용되는 함수
```sql
/*
 NVL 함수
 NVL( 대상이 되는 컬럼, 숫자)
 대상이 되는 컬럼이 NULL이 아니면, 컬럼을 집어넣고
 아니면, 뒤의 숫자를 집어넣는다.

 NVL2 함수
 NVL2( 대상이 되는 컬럼, 숫자, 숫자)
 대상이 되는 컬럼이 NULL이 아니면, 첫번째 숫자를 집어넣고
 아니면, 두번째 숫자를 집어넣는다.
*/
SELECT EMPNO, NVL(MGR, 0) MGR
FROM EMP
WHERE DEPTNO = 10;
```
