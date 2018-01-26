---
layout: post
title: "[javascript] 배열과 객체"
categories:
  - javascript
tags:
  - javascript
  - array
  - object
---

***javascript*** 에서 사용하는 배열에 대해 학습합니다.

<br>

### 배열

- ```javascript```의 배열 선언과 사용법은 Java와 아주 흡사하다.


```javascript
var arr = ['hello', 'javascript', 'world'];
console.log(arr[0]);
console.log(arr[1]);
console.log(arr[2]);
```

```
hello
javascript
world
```


<br>


### 객체

- ```javascript```  는 자바와 같은 객체지향 언어다.
- 객체는 자바의 객체처럼 완전한 객체의 개념은 아니다.

```javascript
var obj = {
  firstname: "kyung seok",
  lastname: "park",
  age: 26
};
console.log(obj.firstname);
console.log(obj.lastname);
console.log(obj.age);
```

```
kyung seok
park
26
```

- 객체의 내부에 **함수** 를 삽입하는 것도 가능하다.

```javascript
var person={
  firstname: 'park',
  lastname: 'kyung'
  id: 1216,
  fullName: function(){
  	return firstname+lastname;
  }
};

console.log(fullName);
```
```
parkkyung
```
