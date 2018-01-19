---
layout: post
title: "[javascript] 진수 변환"
categories:
  - javascript
tags:
  - javascript
  - 진수 변환
---


javascript에서 숫자를 변화하는 방법을 학습합니다.

### 진수 변환

- javascript에서 10진수를 **2진수, 8진수, 16진수** 로 변환합니다.

```html
<p id="demo"> </p>

<button type="button" onclick="myFunc()">hello</button>

<script type="text/javascript">
	function myFunc() {
		var number = 23;
		document.getElementById("demo").innerHTML =
			"128 = " +number+ " Decimal <br>" +
			"0x" + number.toString(16) + " Hexadecimal <br> " +
			"0" + number.toString(8) + " Octal <br> " +
			number.toString(2) + " Binary <br>";
	}
</script>
```
