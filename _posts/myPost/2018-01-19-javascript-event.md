---
layout: post
title: "[javascript] Event처리"
categories:
  - javascript
tags:
  - javascript
  - 이벤트
  - event
---

javascript는 event를 기반으로 동작한다.
특정 태그에 특정 이벤트를 적용하고 활용할 수 있다.


<br><br>

### onchange

- select and option 태그를 사용하여 원하는 경로로 이동하는 코드

<div class="example">
<form action="" name="form1">
<select name="links" onchange="goLink()">
  	<option selected disabled hidden>Choose here</option>
	<optgroup label="portal">
		<option value="www.google.co.kr">google</option>
		<option value="www.naver.com">naver</option>
		<option value="www.daum.net">Daum</option>
	</optgroup>

	<optgroup label="music">
		<option value="www.genie.com">Genie</option>
		<option value="www.melon.com">Melon</option>
		<option value="www.mnet.com">Mnet</option>
	</optgroup>
</select>

<script type="text/javascript">
function goLink() {
	var n = document.form1.links.selectedIndex;

	if(n!=0){
		location.href=document.form1.links.options[n].value;
	}
}
</script>
</div>


```html
<form action="" name="form1">
<select name="links" onchange="goLink()">
  	<option selected disabled hidden>Choose here</option>
	<optgroup label="portal">
		<option value="www.google.co.kr">google</option>
		<option value="www.naver.com">naver</option>
		<option value="www.daum.net">Daum</option>
	</optgroup>

	<optgroup label="music">
		<option value="www.genie.com">Genie</option>
		<option value="www.melon.com">Melon</option>
		<option value="www.mnet.com">Mnet</option>
	</optgroup>
</select>

<script type="text/javascript">
function goLink() {
	var n = document.form1.links.selectedIndex;

	if(n!=0){
		location.href=document.form1.links.options[n].value;
	}
}
</script>
```


### onload

- 특정 태그가 로드가 될때 지정된 함수 또는 javascript 코드를 실행한다.


```html
<body onload="checkCookies()">

<!-- onclick, onload, onchange -->

<p id="demo"></p>

<script type="text/javascript">
function checkCookies() {
 var test = "onload 실행";

 document.getElementById('demo').innerHTML = test;
}
</script>

</body>
```

- body가 로드가 될 때, ```checkCookies``` 함수를 실행한다.


### onblur

- 포커스가 다른 곳으로 이동이 되었을때 실행된다

<div class="example">
<form action="#">
age: <input type="text" onblur="isRegNum(this)" size="3" maxlength="3"> years old. <br>
	write only number.

</form>
<script type="text/javascript">
/* object 가 넘어온다. * /
function isRegNum(obj) {
	var str = obj.value;

	// 숫자가 아닌 문자가 포함된 경우를 나타내는 정규식
	if(str.match(/[^0-9]/g)){
		alert("문자열이 포함되어 있습니다.");
		obj.value="";
		return false;
	}
}
</script>
</div>


```html
<form action="#">
age: <input type="text" onblur="isRegNum(this)" size="3" maxlength="3"> years old. <br>
	write only number.

</form>
<script type="text/javascript">
/* object 가 넘어온다. */
function isRegNum(obj) {
	var str = obj.value;

	// 숫자가 아닌 문자가 포함된 경우를 나타내는 정규식
	if(str.match(/[^0-9]/g)){
		alert("문자열이 포함되어 있습니다.");
		obj.value="";
		return false;
	}
}
</script>
```


### onchange

- 태그가 변경됐을때 스크립트 함수, javascript 코드가 실행된다.
- 굉장히 많이 사용되는 속성이다.


<div class="example">
<form action="#">
	Post number
	T:
	<input type="text" size="5" maxlength="3" onchange="isPostNum(this)">
	<input type="text" size="4" maxlength="3" onchange="isPostNum(this)">
</form>

<script type="text/javascript">
function isPostNum(obj) {
	var str = obj.value;

	if(str.match(/[^0-9]/g)){
		alert("문자열이 포함되어 있습니다.");
		obj.value="";
		return false;
	}

}
</script>
</div>


```html
<form action="#">
	Post number
	T:
	<input type="text" size="5" maxlength="3" onchange="isPostNum(this)">
	<input type="text" size="4" maxlength="3" onchange="isPostNum(this)">
</form>

<script type="text/javascript">
function isPostNum(obj) {
	var str = obj.value;

	if(str.match(/[^0-9]/g)){
		alert("문자열이 포함되어 있습니다.");
		obj.value="";
		return false;
	}

}
</script>
```


### onkeydown, onkeyup

- keyboard 에 대한 함수


<div class="example">
<form action="#">
<p>입력:
	<input type="text" onkeydown="fCopy(this.form)" onkeyup="fCopy(this.form)" name="txt" size="40">
</p>
<p>확인:
	<input type="text" name="copy" size="40" readonly >
</form>

<script type="text/javascript">
function fCopy(frameObj) {
	frameObj.elements["copy"].value = frameObj.elements["txt"].value;
}
</script>
</div>



```html
<form action="#">
<p>입력:
	<input type="text" onkeydown="fCopy(this.form)" onkeyup="fCopy(this.form)" name="txt" size="40">
</p>
<p>확인:
	<input type="text" name="copy" size="40" readonly >
</form>

<script type="text/javascript">
function fCopy(frameObj) {
	frameObj.elements["copy"].value = frameObj.elements["txt"].value;
}
</script>
```



### onmousedown, onmouseup

- 마우스를 눌렀을 때와 마우스를 땠을 때 동작을 정의할 수 있습니다.



<div class="example">
<form action="#">
	<p>
		when you click the image, mousedown will activate.
		And When you attach the mouse from image, mouseup will activate.
	</p>
	<p>
		<input type="image" src="https://i.imgur.com/A8eQsll.jpg" onmousedown="this.style='border: 5px solid red;'" onmouseup="this.style='border: 5px solid blue;'" width="300">  
	</p>
</form>
</div>


```html
<form action="#">
	<p>
		when you click the image, mousedown will activate.
		And When you attach the mouse from image, mouseup will activate.
	</p>

	<p>
		<input type="image" src="https://i.imgur.com/A8eQsll.jpg" onmousedown="this.style='border: 5px solid red;'" onmouseup="this.style='border: 5px solid blue;'" width="300">   
	</p>
</form>
```


### onmouseover, onmouseout

- 마우스가 특정 태그 영역 위에 있을 때의 동작을 정의합니다.
- 마우스가 특정 태그 영역에서 벗어났을 때 동작을 정의합니다.

<div class="example">
<form action="#">
	<p>
		<input type="image" src="https://i.imgur.com/A8eQsll.jpg" onmouseover="mouseOver(this)" onmouseout="mouseOut(this)" onmousedown="mouseDown(this)" width="300">  
	</p>
</form>

<script type="text/javascript">
function mouseOver(obj) {
  obj.style="border:5px solid black;";
}
function mouseOut(obj) {
  obj.style="border:5px dot red;";
}
function mouseDown(obj) {
  obj.style="border:5px solid blue;";
}

</script>
</div>


```html
<form action="#">
	<p>
		<input type="image" src="https://i.imgur.com/A8eQsll.jpg" onmouseover="mouseOver(this)" onmouseout="mouseOut(this)" onmousedown="mouseDown(this)">  
	</p>
</form>

<script type="text/javascript">
	function mouseOver(obj) {
		obj.style="border:5px solid black;";
	}
	function mouseOut(obj) {
		obj.style="border:5px dot red;";
	}
	function mouseDown(obj) {
		obj.style="border:5px solid blue;";
	}

</script>
```
