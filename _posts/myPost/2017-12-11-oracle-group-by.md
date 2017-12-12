---
layout: post
title: "[ORACLE] 데이터 베이스의 그룹화"
categories:
  - Data Base
tags:
  - Java
  - Data Base
  - DB
  - ORACLE
  - GROUP BY
---




데이터 베이스를 이용하면서 각 항목이나 그룹별로 데이터를 묶어야 할 필요가 있다.
이때 사용하는 데이터 베이스 명령어는 ```GROUP BY``` 명령어이다.
이는 ORACLE을 비롯한 다른 데이터 베이스에서 공통적으로 사용된다.





## GROUP BY
![group by example](https://i.imgur.com/nZN0a1d.png)

 group by 를 하게 되면 해당 컬럼에 대해 그룹이 생성된다.
 이해하기 쉽게 여러개의 컬럼이 하나의 컬럼이 된다고 생각하면 된다. 위 그림에서 두개의 Korea, 두 개의 Austria, 하나의 Taiwan, 두 개의 Japan을 가지는 7개의 row가 있다.
 여기서 Nation 을 기준으로 그룹을 지으면 각 나라별로 그룹이 생성된다.
 ***그렇기 때문에*** ```COUNT(*)``` ***를 해주면 7이 아닌 그룹별 원소의 개수가 출력된다.***

 <br>
 <br>

## 예제 코드

#### EMPLOYEES 테이블
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

#### group by 기본 문법

```sql
SELECT *
FROM EMPLOYEES
GROUP BY JOB_ID;
```
JOB_ID를 기준으로 묶이기 때문에 **JOB_ID 의 개수만큼의 row가 생성된다.**

```sql
SELECT SUM(SALARY), COUNT(*), JOB_ID
FROM EMPLOYEES
GROUP BY JOB_ID
ORDER BY JOB_ID;
```

JOB_ID 별 월급 합계와 인원수를 JOB_ID를 기준으로 그룹화하고 정렬한다.


<br>

#### group by 사용 시기

아래의 쿼리문(질의문)은 ```IT_PROG``` 직업에 대한 직원의 수와, 직원 월급의 총합, 평균을 구한다.

```sql
SELECT JOB_ID, COUNT(*), SUM(SALARY), AVG(SALARY)
FROM EMPLOYEES
WHERE JOB_ID = 'IT_PROG';
```


| JOB_ID | COUNT( * ) | SUM(SALARY) | AVG(SALARY) |
|:------:|:----------:|:-----------:|:-----------:|
| IT_PROG|           5|        28800|         5760|



하지만 다른 직업에 대한 정보를 모두 비교하고 싶을 때, 위 코드는 효율이 높은 편이 아니다.
이때, 각 직업별로 정보를 묶어야하기 때문에 ```group by```를 사용한다.

<br>

. ```JOB_ID``` 를 그룹화하여 결과를 구한다.
```sql
SELECT COUNT(*), SUM(SALARY), AVG(SALARY)
FROM EMPLOYEES
GROUP BY JOB_ID;
```


|JOB_ID| COUNT( * ) | SUM(SALARY)| AVG(SALARY)|
|:----:|:----:|:----:|:----:|
|IT_PROG| 5| 28800|5760|
|AC_MGR| 1| 12008|12008|
|AC_ACCOUNT| 1| 8300|8300|
|ST_MAN| 6| 36400|7280|
|PU_MAN| 1| 11000|11000|
|AD_ASST| 2| 34000|17000|



<br>


#### group by 와 조건식 having

.```group by``` 를 사용하면서 조건을 사용해야 할 때가 있다.
예를 들어, ```JOB_ID``` 를 기준으로 묶는데 ST_MAN 은 제외하라고 한다면 조건을 사용해서 그룹의 기준을 정해줘야한다.
이때 조건을 걸기 위해 ```having``` 을 사용한다.

```sql
SELECT JOB_ID, SUM(SALARY)
FROM EMPLOYEES
GROUP BY JOB_ID;
```

JOB_ID 별(직업별) 월급 합계를 나타낸다.




만약 JOB_ID 별(직업별) 월급 합계가 30000 이상일 경우만 표시하시오. 라고 한다면 ```having```을 사용해서 조건을 걸어주어야한다.

```sql
SELECT JOB_ID, SUM(SALARY)
FROM EMPLOYEES
GROUP BY JOB_ID
HAVING SUM(SALARY) >30000;
```

JOB_ID별 월급 합계가 30000 이상인 경우.

```sql
SELECT JOB_ID, COUNT(SALARY), SUM(SALARY), AVG(SALARY)
FROM EMPLOYEES
WHERE SALARY > 2000
GROUP BY JOB_ID
HAVING SUM(SALARY)>20000;
```
WHERE절과 함께 사용할 수도 있다.
그룹화하기 전에 월급이 2000이상인 직원들을 추리고 그룹화한 후 월급의 합이 20000이상인 그룹에 대해 연산을 한다.

<br>

## 이중 group by

데이터 베이스에서는 그룹화를 한 그룹내에서 다시 그룹화를 하는 것이 가능하다.


**모든 직원을 부서별로 분류한 후, 직업별로 분류해라 라고 한다면 그룹화가 2번 이루어져야한다.**

![double group by](https://i.imgur.com/6rk6isw.png)
```sql

SELECT DEPARTMENT_ID, JOB_ID, COUNT(SALARY), SUM(SALARY), AVG(SALARY)
FROM EMPLOYEES
GROUP BY DEPARTMENT_ID, JOB_ID;
```
모든 직원을 부서(DEPARTMENT)별로 분류하고, 다시 직업(JOB)별로 분류한 결과를 반환한다.

이중으로 그룹화가 이루어지면 그룹화가 된 row를 대상으로 다시 그룹화가 이루어진다.

<br>

## PARTITION BY

데이터 베이스에서 결과를 출력하기 위해 데이터들을 그룹화하는 방법을 배웠다.
만약, 뽑아야 하는 데이터가 하나의 그룹화로 해결이 되지 않을 경우 ```OVER(PARTITION BY column)```을 사용한다.
이름 그대로 파티션을 나누어 부분적인 그룹화를 가능하게 해준다.

```sql
SELECT FIRST_NAME, JOB_ID, SALARY,
    COUNT(JOB_ID) OVER(PARTITION BY JOB_ID),
    SUM (SALARY) OVER(PARTITION BY JOB_ID),
    SUM (SALARY) OVER(PARTITION BY DEPARTMENT_ID),
    DEPARTMENT_ID
FROM EMPLOYEES
ORDER BY JOB_ID;
```
- COUNT(JOB_ID) OVER(PARTITION BY JOB_ID)
  - JOB_ID로 그룹화된 개수를 출력한다.
- SUM (SALARY) OVER(PARTITION BY JOB_ID)
  - JOB_ID로 그룹화된 월급(SALARY)의 합을 표시한다.
- SUM (SALARY) OVER(PARTITION BY DEPARTMENT_ID)
  - DEPARTMENT_ID로 그룹화된 월급(SALARY)의 합을 표시한다.

**파티션을 사용하면 하나의 결과에서 여러번의 그룹화를 할 수 있다.**
