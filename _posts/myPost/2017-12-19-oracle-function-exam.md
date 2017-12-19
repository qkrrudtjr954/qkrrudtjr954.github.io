---
layout: post
title: "[ORACLE] DB의 FUNCTION 문제 풀이"
categories:
  - Data Base
tags:
  - Data Base
  - DB
  - ORACLE
  - 함수
  - FUNCTION
  - 문제 풀이
  - PL/SQL
---





#### 두 숫자를 제공하면 덧셈을 해서 결과값을 반환하는 함수를 정의하시오.(함수명 add_num)A

```sql
CREATE OR REPLACE FUNCTION SUM_FUNC(num1 IN NUMBER, num2 IN NUMBER) RETURN NUMBER
IS
    result NUMBER;
BEGIN
    DBMS_OUTPUT.ENABLE;
    result := num1+num2;
    DBMS_OUTPUT.PUT_LINE(result);
    RETURN result;
END;
/
SELECT SUM_FUNC(10, 20) FROM DUAL;
```


#### 부서번호를 입력하면 해당 부서에서 근무하는 사원 수를 반환하는 함수를 정의하시오.

   (함수명 get_emp_count)
```sql
CREATE OR REPLACE FUNCTION get_emp_count(deptno EMPLOYEES.DEPARTMENT_ID%TYPE) RETURN NUMBER
IS
    emp_count NUMBER;
BEGIN
    SELECT COUNT(*)
    INTO emp_count
    FROM EMPLOYEES
    WHERE DEPARTMENT_ID=deptno;
    RETURN emp_count;
END;
/
SELECT get_emp_count(10) FROM DUAL;
```


#### emp테이블을 이용해서 입사일을 제공하면 근무연차를 구하는 함수를 정의하시오.

(소수점 자리 절삭, 함수명 get_info_hiredate)

```sql
CREATE OR REPLACE FUNCTION get_info_hiredate(empno EMPLOYEES.EMPLOYEE_ID%TYPE) RETURN NUMBER
IS
    year_count NUMBER;
BEGIN
    SELECT TRUNC((SYSDATE - HIRE_DATE)/365)
    INTO year_count
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=empno;

    RETURN year_count;
END;
/
SELECT get_info_hiredate(100) FROM DUAL;
select hire_date from employees where employee_id=100;
```





#### emp테이블을 이용해서 사원번호를 입력하면 해당 사원의 관리자 이름을 구하는 함수를 정의하시오.

(함수명 get_mgr_name)

```sql
CREATE OR REPLACE FUNCTION get_mgr_name(empno EMPLOYEES.EMPLOYEE_ID%TYPE) RETURN VARCHAR2
IS
    mgr_name VARCHAR2(10);
BEGIN
    SELECT LAST_NAME
    INTO mgr_name
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID = (   SELECT MANAGER_ID
                            FROM EMPLOYEES
                            WHERE EMPLOYEE_ID=empno);
    RETURN mgr_name;
END;
/
SELECT EMPLOYEE_ID, MANAGER_ID FROM EMPLOYEES;
SELECT get_mgr_name(101) FROM DUAL;
```


#### emp테이블을 이용해서 사원번호를 입력하면 급여 등급을 구하는 함수를 정의하시오.
4000~5000 A, 3000~4000미만 B, 2000~3000미만 C, 1000~200미만 D, 1000미만 F
  (함수명 get_sal_grade)
```sql
CREATE OR REPLACE FUNCTION get_sal_grade(empno EMPLOYEES.EMPLOYEE_ID%TYPE) RETURN VARCHAR2
IS
    temp_sal NUMBER;
    grade VARCHAR2(10);
BEGIN
    DBMS_OUTPUT.ENABLE;

    SELECT SALARY
    INTO temp_sal
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID=empno;

    CASE
        WHEN 4000 <= temp_sal THEN grade:='A';
        WHEN 3000 <= temp_sal AND temp_sal < 4000 THEN grade:='B';
        WHEN 2000 <= temp_sal AND temp_sal < 3000 THEN grade:='C';
        WHEN 1000 <= temp_sal AND  temp_sal <2000 THEN grade:='D';
        ELSE grade:='F';
    END CASE;

    RETURN grade;
END;
/
SELECT get_sal_grade(100) FROM DUAL;
SELECT SALARY FROM EMPLOYEES WHERE EMPLOYEE_ID=100;
```
