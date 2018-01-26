---
layout: post
title: "[javaScript] 자바스크립트의 콜백 함수"
categories:
  - javascript
tags:
  - javaScript
  - 자바 스크립트
  - 자바 스크립트 콜백 함수
  - callback function
---


자바스크립트에서는 함수가 데이터로도 쓰이고 특별히 이름을 지어주지 않아도 사용할 수 있다는 점에서 발생하는 특징이 바로 ***콜백 함수*** 이다.

## 콜백 함수

- 특정 이벤트가 발생하면 호출되는 함수
- 버튼 클릭, 네트워크를 통해 어떤 데이터가 도착 등의 이벤트가 발생했을 때 동작하는 특정 함수를 정의할 수 있다.

<br>
<br>

#### 함수 인자로서 함수를 넘겨주기

<br>

```javascript
function one(){
  return 1;
}

var two = function () {
  return 2;
}

function invoke_add_add(a, b) {
  return a()+b();
}

invoke_add_add(one, two);   // 3
```

- ```one()```과 ```two()``` 함수 그 자체가 ```invoke_add_add()``` 라는 함수의 인수로 전달된다.
- ```invoke_add_add()``` 함수는 해당 함수를 실행하고 그 결과를 받아 최종 연산을 수행한다.
- 콜백 함수는 명시적인 함수(```one(), two()```)만 넘겨줄 수 있는 것은 아니다.

<br>
<br>



#### 함수 인자로서 무기명 함수를 넘겨주기

<br>

```javascript
function one(){
  return 1;
}

function invoke_add_add(a, b) {
  return a()+b();
}

invoke_add_add(one, function() { return 2; });  // 3
```

- 함수의 첫번째 인자는 기존 함수 ```one()``` 을 넘겨주었다.
- 두번째 인자는 **무기명 함수를 생성함과 동시에** 인자로 넘겨주었다.
- ***이벤트 기반의 구조를 가지는 자바스크립트에서는 콜백 함수의 개념이 아주 중요하게 사용된다.***
