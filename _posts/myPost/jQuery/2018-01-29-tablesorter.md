---
layout: post
title: '[jQuery] 정렬 테이블'
categories:
  - jQuery
tags:
  - jQuery
  - tablesorter
  - 정렬 테이블
---

javascript ```tablesorter.js``` 를 추가하여 자동으로 정렬을 할 수 있는 테이블을 생성합니다.


## Get Started

- CDN을 통해서 jquery와 tablesorter파일을 추가합니다.


```html
<script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
<script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/jquery.tablesorter/2.9.1/jquery.tablesorter.min.js"></script>
```



## 예제


- 테이블 헤드를 클릭하면 값을 정렬합니다.


<div class="example">
<h1>Table sorter</h1>

<table id="sampleTable" class="tablesorter">
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>Address</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>park</td>
      <td>23</td>
      <td>chung ju si</td>
    </tr>
    <tr>
      <td>kyung</td>
      <td>34</td>
      <td>chun cheon si</td>
    </tr>
    <tr>
      <td>seok</td>
      <td>26</td>
      <td>seoul city</td>
    </tr>
  </tbody>
</table>

<script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/jquery.tablesorter/2.9.1/jquery.tablesorter.min.js"></script>
<script type="text/javascript">
  $(document).ready(function () {
    $('#sampleTable').tablesorter();
  });
</script>
</div>


```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

<!-- file import -->
  <script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/jquery.tablesorter/2.9.1/jquery.tablesorter.min.js"></script>

<style type="text/css">
	#sampleTable td:nth-of-type(3){
		text-align: right;
		padding-right: 0.7em;
	}
	#sampleTable td:nth-of-type(4){
		text-align: right;
		padding-right: 0.7em;
	}
	#sampleTable td:nth-of-type(5){
		text-align: right;
		padding-right: 0.7em;
	}
</style>
</head>
<body>
	<h1>Table sorter</h1>

	<table id="sampleTable" class="tablesorter">
		<thead>
			<tr>
				<th>Name</th>
				<th>Age</th>
				<th>Address</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>park</td>
				<td>23</td>
				<td>chung ju si</td>
			</tr>
			<tr>
				<td>kyung</td>
				<td>34</td>
				<td>chun cheon si</td>
			</tr>
			<tr>
				<td>seok</td>
				<td>26</td>
				<td>seoul city</td>
			</tr>
		</tbody>
	</table>

	<script type="text/javascript">
		$(document).ready(function () {
			$('#sampleTable').tablesorter();
		});
	</script>
</body>
</html>
```
