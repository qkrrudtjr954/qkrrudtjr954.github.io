---
layout: post
title: "[javascript] 간단한 애니메이션"
categories:
  - javascript
tags:
  - javascript
  - 문자열 함수
  - animation
---

javascript에서 문자열을 다루는 함수를 사용한 간단한 애니메이션을 구현합니다.

<br>



## 간단한 애니메이션

<form name="myForm">
   <input type="text" size="30" name="myFormMsg">
</form>

<script type="text/javascript">
var myMsg = "환영합니다 어서오십시오";
var myCnt = 0;

function myFunc() {
   document.myForm.myFormMsg.value = myMsg.substring(0, myCnt) + "_ ";
   myCnt = ( myCnt == myMsg.length ) ? 0 : myCnt+1;
}

setInterval("myFunc()", 500);
</script>

<br>

```html
<h1>여기는 index3입니다.</h1>

<form name="myForm">
   <input type="text" size="30" name="myFormMsg">
</form>

<script type="text/javascript">
var myMsg = "환영합니다 어서오십시오";
var myCnt = 0;

function myFunc() {
   document.myForm.myFormMsg.value = myMsg.substring(0, myCnt) + "_";

   myCnt = ( myCnt == myMsg.length ) ? 0 : myCnt+1;
}

setInterval("myFunc()", 500);

</script>
```
