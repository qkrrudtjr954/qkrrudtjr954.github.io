---
layout: post
title: "[ORACLE] DB의 TRIGGER(트리거)"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - TRIGGER
  - 트리거
---


FUNCTION과 PROCEDURE은 사용자가 정의한 후에 필요할때 사용자의 의해 수동적으로 호출되지만 ***TRIGGER*** 는 쿼리가 실행될 때 자동적으로 실행된다.


## TRIGGER의 생성


```sql
CREATE OR REPLACE TRIGGER T
BEFORE
    INSERT OR
    UPDATE OF SALARY, DEPARTMENT_ID OR
    DELETE
    ON EMPLOYEES FOR EACH ROW
BEGIN
    DBMS_OUTPUT.ENABLE;
    CASE
        WHEN INSERTING THEN
            DBMS_OUTPUT.PUT_LINE('INSERT');
        WHEN UPDATING('SALARY') THEN
            DBMS_OUTPUT.PUT_LINE('UPDATE SALARY');
        WHEN UPDATING('DEPARTMENT_ID') THEN
            DBMS_OUTPUT.PUT_LINE('UPDATE DEPARTMENT_ID');
        WHEN DELETING THEN
            DBMS_OUTPUT.PUT_LINE('DELETING');
    END CASE;
END;
/
```

- INSERT 가 이루어질 때 INSERT를 출력한다.
- SALARY 값이 변경될 때 UPDATE SALARY 를 출력한다.
- DEPARTMENT_ID 값이 변경될 때 UPDATE DEPARTMENT_ID 를 출력한다.
- DELETE 가 이루어질 때 DELETING 을 출력한다.


<br>

```sql
INSERT INTO EMPLOYEES(EMPLOYEE_ID, LAST_NAME, DEPARTMENT_ID, JOB_ID, HIRE_DATE, EMAIL)
VALUES(302, 'PAKCKK', 10, 'IT_PROG', SYSDATE, 'EMAADA');
```
```
INSERT
```
- 값의 삽입이 이루어졌기 때문에 INSERT 가 출력된다.

<br>

## TRIGGER 예제

```sql
CREATE OR REPLACE TRIGGER TRIGGER_TEST
BEFORE
    UPDATE ON DEPARTMENTS
    FOR EACH ROW
BEGIN
    DBMS_OUTPUT.ENABLE;

    DBMS_OUTPUT.PUT_LINE('변경전 컬럼값' || :old.department_name);
    DBMS_OUTPUT.PUT_LINE('변경후 컬럼값' || :new.department_name);
END;
/
```
```sql
UPDATE DEPARTMENTS                        
SET DEPARTMENT_NAME = 'DE'
WHERE DEPARTMENT_ID=60;
```
- 값을 변경하면 ```TRIGGER```가 동작한다.
- 변경전 컬럼값과 변경후 출력값을 출력한다.


<br>

```
변경전 컬럼값 department
변경후 컬럼값 DE
```
