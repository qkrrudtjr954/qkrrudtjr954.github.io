---
layout: post
title: "[ORACLE] DB의 PROCEDURE(프로시져)"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - PROCEDURE
  - 프로시져
---


- 특별한 작업을 수행하는 이름이 있는 PL/SQL Block이다
- 매개변수를 받고 반복적으로 수행 할 수 있는 Block이다.
- 이클립스에서는 수행되지 않는다!!

## Procedure의 생성

UPDATE SAL PROCEDURE의 생성

- 사원번호를 입력받아 급여를 수정하는 프로시져

```sql
CREATE OR REPLACE PROCEDURE update_sal(v_empno IN NUMBER)
IS
BEGIN
    UPDATE EMPLOYEES
    SET SALARY = SALARY*1.1
    WHERE EMPLOYEE_ID=v_empno;
    COMMIT;
END update_sal;
/
```

- ```v_empno``` : NUMBER의 타입을 갖는 인자값을 나타낸다.

## Procedure의 실행

```sql
EXECUTE update_sal(100);
```

- ```EXECUTE``` 실행 명령을 통해 프로시져를 실행할 수 있다.

## 변수를 사용한 Procedure

EMP_INFO의 생성

- 사원의 정보를 출력해주는 프로시져

```sql
CREATE OR REPLACE PROCEDURE EMP_INFO(p_empno IN EMPLOYEES.EMPLOYEE_ID%TYPE)
IS
    v_empno EMPLOYEES.EMPLOYEE_ID%TYPE;
    v_sal EMPLOYEES.SALARY%TYPE;
    v_name EMPLOYEES.FIRST_NAME%TYPE;
BEGIN
    DBMS_OUTPUT.ENABLE; -- PRINTLN을 사용하겠다고 명시해줌.

    --%TYPE 데이터 변수를 사용
    SELECT EMPLOYEE_ID, FIRST_NAME, SALARY
    INTO v_empno, v_name, v_sal
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID = p_empno;

    DBMS_OUTPUT.PUT_LINE('사원 번호: '||v_empno);
    DBMS_OUTPUT.PUT_LINE('사원 이름: '||v_name);
    DBMS_OUTPUT.PUT_LINE('사원 급여: '||v_sal);
END;
/
```

#### 프로시져의 실행

```sql
SET SERVEROUTPUT ON;
EXECUTE EMP_INFO(100);
```

- ```IS``` 와 ```BEGIN``` 사이에 변수를 선언 및 초기화해준다.
  - ```EMPLOYEES.EMPLOYEE_ID%TYPE;``` EMPLOYEE_ID 타입을 사용한다고 명시해주는 코드
  - ```EMPLOYEES.SALARY%TYPE;``` SALARY 타입을 사용한다고 명시해주는 코드
  - ```EMPLOYEES.FIRST_NAME%TYPE;``` FIRST_NAME 타입을 사용한다고 명시해주는 코드
- ```DBMS_OUTPUT.PUT_LINE();``` 을 사용한 출력

## ROWTYPE을 사용한 프로시져

ROWTYPE_TEST의 생성

- 사원의 번호를 인자로 사원의 정보를 출력해주는 프로시져
- 행의 정보를 담는 ROWTYPE 변수를 사용한다..

```sql
CREATE OR REPLACE PROCEDURE ROWTYPE_TEST(p_empno IN EMPLOYEES.EMPLOYEE_ID%TYPE)
IS
    v_emp EMPLOYEES%ROWTYPE;
BEGIN
    DBMS_OUTPUT.ENABLE;

    --% ROWTYPE 변수 사용
    SELECT EMPLOYEE_ID, FIRST_NAME, HIRE_DATE
    INTO v_emp.EMPLOYEE_ID, v_emp.FIRST_NAME, v_emp.HIRE_DATE
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=p_empno;

    DBMS_OUTPUT.PUT_LINE(v_emp.EMPLOYEE_ID);
    DBMS_OUTPUT.PUT_LINE(v_emp.FIRST_NAME);
    DBMS_OUTPUT.PUT_LINE(v_emp.HIRE_DATE);
END;
/
```

```sql
SET SERVEROUTPUT ON;
EXECUTE ROWTYPE_TEST(100);
```

- 행의 정보를 담는 ROWTYPE 변수를 통해 한번에 변수들을 저장하고 출력할 수 있다.
- ```v_emp EMPLOYEES%ROWTYPE;``` EMPLOYEES의 행의 정보를 변수로 사용한다.
- ```v_emp``` 는 EMPLOYEES의 행의 정보를 갖고 있기 때문에 ```v_emp.EMPLOYEE_ID, v_emp.FIRST_NAME, v_emp.HIRE_DATE``` 와 같은 접근이 가능하다.

## 예제

#### EMPLOYEE_ID, LAST_NAME, DEPARTMENT_ID, JOB_ID, EMAIL을 인자로 받아 사원의 정보를 추가(INSERT)하는 PROCEDURE를 만들어 보세요.

```sql
CREATE OR REPLACE PROCEDURE INSERT_TEST(
    v_id EMPLOYEES.EMPLOYEE_ID%TYPE,
    v_name EMPLOYEES.LAST_NAME%TYPE,
    v_did EMPLOYEES.DEPARTMENT_ID%TYPE,
    v_jid EMPLOYEES.JOB_ID%TYPE,
    v_email EMPLOYEES.EMAIL%TYPE
)
IS

BEGIN
    INSERT INTO EMPLOYEES(EMPLOYEE_ID, LAST_NAME, DEPARTMENT_ID, JOB_ID, EMAIL, HIRE_DATE)    
    VALUES(v_id, v_name, v_did, v_jid, v_email, SYSDATE);
END;
/

EXECUTE INSERT_TEST(500, 'PARK', 10,  'IT_PROG', 'HELLO');


SELECT EMPLOYEE_ID, LAST_NAME, DEPARTMENT_ID, JOB_ID, EMAIL FROM EMPLOYEES WHERE EMPLOYEE_ID=500;
```

- 입력받은 인자로 값을 추가한다.

#### 실행결과

| EMPLOYEE_ID | LAST_NAME | DEPARTMENT_ID | JOB_ID  | EMAIL |
| :---------: | :-------: | :-----------: | :-----: | :---: |
|     500     |   PARK    |      10       | IT_PROG | HELLO |



#### 사원 번호와 급여 인상율을 입력받아 인상된 사원의 급여를 출력하는 PROCEDURE을 만들어 보세요.

- 급여 인상률 : 급여 + ( 급여 * (인상률/100) )

```sql
CREATE OR REPLACE PROCEDURE UPDATE_TEST(empno EMPLOYEES.EMPLOYEE_ID%TYPE, inc NUMBER)
IS
    p_sal NUMBER;
BEGIN
    DBMS_OUTPUT.ENABLE;

    SELECT SALARY+(SALARY*(inc/100)) INTO p_sal
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=empno;

    DBMS_OUTPUT.PUT_LINE('인상 급여: '||p_sal);
END;
/
```

```sql
EXECUTE UPDATE_TEST(100, 150);
```

- inc 가 200이면 급여가 2배 증가하고 150이면 1.5배 증가한다.
- 100번인 사원의 기존 급여가 24000이고 인상률이 150이라면 상승된 급여는 24000+(24000 * ( 150 / 100 )) = 60000이 출력된다.

#### 실행 결과

```
인상 급여 : 60000
```
