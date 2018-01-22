---
layout: post
title: "[javascript] DOM (Document Object Model)"
categories:
  - javascript
tags:
  - javascript
  - DOM
  - Document Object Model
---

javascript는 DOM을 다루는 프로그래밍 언어이다.


<br>



## What is DOM?

- DOM 은 Document Object Model의 약자로 도큐먼트 객체 모델이다.


- 페이지를 수정할때, 기존에는 html 을 전부 리로딩하는 방식을 사용했다. 하지만, javascript는 ***DOM*** 을 활용하여 html 전체 코드가 아닌 ***특정 document 객체만을 수정하고 삭제하고 추가할 수 있다.***


- Document를 하나의 웹페이지 코드 즉, 전체 html 코드라고 생각할 때 ***head, body, div, p*** 태그 등으로 묶여있는 하나의 코드 뭉치를 DOM 이라고 생각할 수 있다.

- javascript는 html 코드 전체를 다루는 것이 아니라 ***특정 DOM 코드 뭉치*** 에 접근하여 제어를 할 수 있다. ( ***html코드 전체도 하나의 DOM이 될 수 있다.*** )




<br>
<br>




### Sample.html



```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hi! I'm Sample HTML!</title>
  </head>
  <body>
    <div id="hello">
      <p id="world">This is p tag!</p>
    </div>
    <script src="Sample.js" charset="utf-8"></script>
  </body>
</html>
```



### Sample.js



```javascript
var divDOM = document.getElementById('hello');  // div 코드 뭉치 (DOM)
var pDOM = document.getElementById('world'); // p 코드 뭉치 (DOM)
var htmlDOM = document.getElementsByTagName('html')[0]; // html 코드 뭉치 (DOM)
```


<br>
<br>


- ```divDOM``` 은 ```<div id="hello">...</div>``` 를 가르키는 하나의 ***DOM*** 이다.
- ```pDOM``` 은 ```<p id="world">...</p>``` 를 가르키는 하나의 ***DOM*** 이다.
- ```htmlDOM``` 은 ```<html>...</html>``` 를 가르키는 하나의 ***DOM*** 이다.
- 이처럼 DOM은 html의 모든 태그를 상대로 지정할 수 있다.
