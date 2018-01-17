---
layout: post
title: "[javaScript] 자바스크립트의 특징"
categories:
  - JavaScript
tags:
  - javaScript
  - 자바 스크립트
---

자바 스크립트가 가지는 특징을 간단하게 살펴보고 예제를 확인한다.

<br>


## 자바 스크립트의 특징

<br>

### 1. 동적 형변환

- 다른 스크립트 언어들이 그렇듯 자바 스크립트 역시 값에 따라 변수의 형변환이 자동으로 이루어진다.



```javascript
var i = 1;
var ch = "a";
console.console.log(i+ch);    // 1a

ch = 1;
console.console.log(i+ch);    // 2
```


<br>
<br>

### 2. 프로토 타입 기반 객체 지향

- 자바스크립트는 프로토타입 기반 객체지향 언어이다.
- 객체를 생성할 때 클래스로부터 그 내용을 상속받아서 객체를 만드는 것이 아니라 객체로부터 그 ***특성을 복제하여 새로운 객체를 생성한다.***
- 그렇게 때문에 런타임 중에도 객체의 송성과 값을 추가하거나 변경하고 삭제까지 가능하다.

#### 예제
```javascript
var person = { name: "Parker", age: 24};
```

#### 결과
```javascript
person
Object
  age : 24
  name : "Parker"
  _proto_ : Object
```

#### 예제
```javascript
person.height = 187;
```

#### 결과
```javascript
person
Object
  age : 24
  name : "Parker"
  height : 187
  _proto_ : Object
```


<br>
<br>




### 3. 실행 시 평가 (Run-Time Evaluation)

- 프로그램 실행 시에 코드블록을 실행할 수 있는 ```eval()``` 함수와 같은 요소를 가지고 있기 때문에 프로그램 실행 도중에도 동적으로 코드를 실행할 수 있다.


#### 예제
```javascript
eval("var a = 1, b = 2;");
console.log(a,b);   // 1 2
```


<br>
<br>



### 4. 고차 함수

- 고차 함수는 인자로 함수를 취하거나 함수를 반환할 수 있는 함수를 말한다.
- 자바 스크립트에서는 다른 언어에서는 불가능한 방식으로 함수들을 쉽게 조작할 수 있다.


#### 예제
```javascript
// 인자로 받은 함수를 실행시킨다.
var ho_func = function (param_func) {
  param_func();
};

// 함수를 인자로 ho_func() 를 호출한다.
ho_func(function() {
  console.log("hello!");
});
```

#### 결과
```
hello!
```
