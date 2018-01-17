---
layout: post
title: "[javascript] Hello World"
categories:
  - javascript
tags:
  - javascript
---

***javascript*** 에서 사용하는 변수의 선언과 사용에 대해 학습합니다.

<br>

### javascript의 변수


- ```var```로 변수를 선언한다.
- ```var```은 모든 자료형을 내포하고 있다.
  - ```int, double, string, Object, boolean```등
- 대소문자를 구별한다.

<br>

### 변수의 선언과 연산

- 선언과 연산은 Java와 흡사하다.

- 숫자 선언과 연산

```javascript
var a=5;
var b=6;
console.log(a+b);
```

```
11
```

<br>


- 문자 선언과 연산

```javascript
var str1 = 'Hello';
var str2 = 'World';
console.log(str1+' '+str2);
```

```
Hello World
```

<br>


- 숫자+숫자, 문자+숫자 연산

```javascript
var person="Parker";
var answer="Yes or No";
var num=123;
var num2=321;
var updown=true;

console.log(person+num);
console.log(num+num2);
```

```
Parker123
444
```

<br>


### 변수의 다중 선언

- 모든 변수는 ```var```로 선언하기 때문에, 숫자와 문자 다중 선언도 가능하다.

```javascript
var per="Parker", number=3+4;
console.log(per);
console.log(number);
```

```
Parker
7
```

<br>

### typeof

- 변수의 타입을 확인하는 연산자.
- 현재 변수의 타입을 리턴한다.

```javascript
var str = "Parker";
console.log(typeof str);
```

```
string
```


```javascript
document.getElementById("type").innerHTML =
  typeof "Parker" + "<br>" +
  typeof 123 + "<br>" +
  typeof {num:1, str:"hello"} + "<br>" +
  typeof 123.456 + "<br>" +
  typeof [1,2,3] + "<br>"
```
```
string
number
object
number
object
```
