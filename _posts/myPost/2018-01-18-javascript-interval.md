---
layout: post
title: "[javascript] Interval"
categories:
  - javascript
tags:
  - javascript
  - Interval
---


javascript에서는 일정한 시간동안 주기적으로 함수를 호출할 수 있다.



### 현재 시간을 보여주는 웹

<div class="example">
  <div class="title">
    <h1>현재시간은</h1>
  </div>

  <div class="containers">
    <p id="current"></p>
  </div>

  <script type="text/javascript">
    function currentTime() {
      document.getElementById('current').innerHTML = new Date();
    }

    setInterval("currentTime()", 1000);
  </script>

</div>


```html
<div class="title">
  <h1>현재시간은</h1>
</div>
<div class="containers">
  <p id="current"></p>
</div>
<script type="text/javascript">
  function currentTime() {
    document.getElementById('current').innerHTML = new Date();
  }

  setInterval("currentTime()", 1000);
</script>
```

- ```setInterval("currentTime()", 1000);``` 은 ```currentTime()``` 함수를 1초에 한번씩 실행시킨다.

<br><br>




### 타이머를 설정한 앱

- 통화 시간 체크
- 통화 요금 체크

<br>

<div class="example">
  <form name="form1">
    전화하는 시간은
    <input type="text" size="10" name="formSec"> 입니다. <br>
    전화 요금은
    <input type="text" size="10" name="formWon"> 입니다.
  </form>

</div>
<script type="text/javascript">
var myCount = 1;

function func() {
  document.form1.formSec.value = myCount + "초";
  document.form1.formWon.value = ((Math.floor(myCount/5) * 10) + 10) + "원";
  myCount = myCount + 1;
}

setInterval("func()", 1000);
</script>

<br>


```html
<form name="form1">
전화하는 시간은
<input type="text" size="10" name="formSec"> 입니다.

<br>
전화 요금은
<input type="text" size="10" name="formWon"> 입니다.
</form>

<script type="text/javascript">
  var myCount = 1;

  function func() {
  	document.form1.formSec.value = myCount + "초";
  	document.form1.formWon.value = ((Math.floor(myCount/5) * 10) + 10) + "원";
  	myCount = myCount + 1;
  }

  setInterval("func()", 1000);
</script>
```


- ```setInterval("func()", 1000);``` 은 ```func()``` 함수를 1초에 한번씩 실행시킨다.
