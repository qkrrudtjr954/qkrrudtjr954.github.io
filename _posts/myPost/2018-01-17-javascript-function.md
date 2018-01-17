---
layout: post
title: "javascript의 함수"
categories:
  - javascript
tags:
  - javascript
  - function
  - 함수
---

자바 스크립트는 함수를 제공한다.

<br>

### javascript function (함수)

- javascript는 함수를 제공한다.


```html
<p id="demo"></p>

<button type="button" onclick="_func(22)">button</button>

<script type="text/javascript">
function myFunc(a, b) {
  return a+b;
}
document.getElementById("demo").innerHTML = myFunc(5, 4);
</script>
```

- 프로그램이 시작되면 ```myFunc(5,4)```를 실행시킨다.
- 함수의 리턴값으로 ```<p id="demo"></p>```의 값을 변경한다.



```html
<p id="demo"></p>

<button type="button" onclick="_func(22)">button</button>

<script type="text/javascript">
function _func(num) {
  document.getElementById("demo").innerHTML = num*2;
}
</script>
```

- 버튼을 클릭하면 ```onclick``` 속성에 의해 ```_func(22)``` 함수가 동작한다.
- 22를 인자로 받은 함수에서 ```<p id="demo"></p>```의 값을 변경한다.
