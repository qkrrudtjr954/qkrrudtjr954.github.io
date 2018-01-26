---
layout: post
title: '[jQuery] Selector'
categories:
  - jQuery
tags:
  - jQuery
  - Selector
  - 선택자
---


javascript의 ```document.getElementById()```와 같은 객체를 선택하는 방법에 대해 알아보자.

## jQuery Selector

- 자바스크립트에서 DOM을 얻어오기 위해 사용한 함수

```javascript
var obj = document.getElementById('id');
```
- 하지만 jQuery 에서는 훤씬 더 간편한 방법을 사용하여 DOM에 접근할 수 있다.
- class 에 접근하기

```javascript
var classObj = $('.classname');
```
- id 로 접근하기

```javascript
var idObj = $('#id');
```
- 특정 태그에 접근하기

```javascript
var tagObj = $('div'); // 모든 div 태그에 접근
var tagObj2 = $('p'); // 모든 p 태그에 접근
```
- id또는 class를 갖는 html 태그에 접근하기

```javascript
var tagObj = $('div#id'); // <div id="id"></div> 에 접근
var tagObj2 = $('p.hello'); // <p class="hello"></p> 에 접근
```

<br>
