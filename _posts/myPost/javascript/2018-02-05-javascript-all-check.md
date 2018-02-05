---
layout: post
title: '[javascript] 여러개 체크 박스 한번에 체크하기'
categories:
  - javascript
tags:
  - javascript
  - function
  - checkbox
---


테이블에서 제일 상단의 체크 박스를 체크하면 아래 모든 요소의 체크박스가 체크되는 예제입니다.


```javascript
function deletechecks(e){
	var x = document.getElementsByName('delcheck');
	var len = x.length;

	for(var i=0; i<len; i++){
		x[i].checked = e;
	}
}
```


<script type="text/javascript">
function deletechecks(e){
	var x = document.getElementsByName('delcheck');
	var len = x.length;

	for(var i=0; i<len; i++){
		x[i].checked = e;
	}
}
</script>
<div class="exmaple">
<table>
<tr bgcolor="skyblue">
  <td>
    <input type="checkbox" name="alldel" onclick="deletechecks(this.checked)">
  </td>
  <td>id</td>
  <td>name</td>
</tr>

<tr>
  <td>
    <input type="checkbox" name="delcheck">
  </td>
  <td>1</td>
  <td>hello</td>
</tr>
<tr>
  <td>
    <input type="checkbox" name="delcheck">
  </td>
  <td>2</td>
  <td>javascript</td>
</tr>
<tr>
  <td>
    <input type="checkbox" name="delcheck">
  </td>
  <td>3</td>
  <td>world</td>
</tr>
</table>
</div>


- header 에 있는 체크박스를 클릭하면 아래 요소가 전부 체크된다.
