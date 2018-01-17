---
layout: post
title: "[javaScript] 자바스크립트의 기본 문법과 연산자"
categories:
  - javascript
tags:
  - javaScript
  - 자바 스크립트
  - 자바 스크립트 기본 문법
  - 자바 스크립트 연산자
  - 논리 연산
  - 조건 연산
  - 산술 연산
  - 문자 연산
---

자바스크립트에서 기본적으로 사용하는 ***문법*** 과 변수들을 연산하는 ***연산자*** 에 대해 학습합니다.

## 기본 문법

> 자바스크립트 문법은 기본적으로 C / C++이나 Java와 비슷하다.

- 세미콜론(;)으로 문장이 종료되어야 한다.
  - 필수는 아니지만 붙여주는 것이 좋다.
- 변수 이름은 항상 알파벳이나 밑줄(_ )로 시작되어야한다.
- 대, 소문자는 구별한다.
- **예약어** 는 변수이름으로 사용할 수 없다.
- 중괄호를({ }) 이용하여 구역을 나눈다.
- C / C++ 과 같은 구조의 조건문과 반복문을 가지고 있다.


#### 실습

```javascript
var a = 1;  // 기본 변수의 선언
b = 2;  // 그냥 선언하는 것도 가능하다
var c = 1, d = 10; // 여러개를 한번에 선언하는 것도 가능하다.
var str = "hello";
var str2 = "world";
var str3 = null;
```

## 연산자

자바스크립트의 연산자 역시 C / C++과 비슷하다. 하지만 **문자열 연산자는 조금 다르니 주의해야한다.**

#### 산술 연산자

```javascript
a = b + 1;
a = b - 1;
a = b * c;
a = a / 10;

// 후위 연산자
d = 1;
d++;  //1
d;    //2
d--;  //2
d;    //1
```

- 후위 연산자는 C / C++과 동작방법이 같다.


#### 문자열 연산자

- 문자열 연산자에는 +가 있는데, 두 문자열을 결합시켜주는 역할을 한다.
  - Java와 같다.

```javascript
var str1 = "hello";
var str2 = " ";
var str3 = "world!";
var str4 = str1+str2+str3;
str4; // hello world!
```


#### 할당 연산자

```javascript
a+=1; // a = a + 1;
a-=1; // a = a - 1;
a*=2; // a = a * 2;
a/=2; // a = a / 2;
```


#### 비교 연산자

```javascript
var a=10, b=20, c=30;

a>b;  //false
b>=c; //false
c >= 10; //true
a<c;  // true
```


#### 논리 연산자

```javascript
var a=10, b=20, c=30;
a==1; //false
b!=c; //true
true && false;  //false
false || true;  //true
!false; //true
```

#### 조건 연산자

- 삼항연산자

```javascript
(a > b) ? (console.log("a is bigger than b")) : (console.log("a is smaller than b"));
```
