---
layout: post
title: '[jQuery] 활용하기2'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery를 사용하여 할 수 있는 활용 방법 예시를 간단하게 소개한다.



<br>


## 페이지를 전환하는 여러가지 방법

- 현재 페이지에서 다른 페이지로 이동하는 여러가지 방법을 소개한다.
- 값을 가지고 가는 방법
- 단순한 페이지 전환을 하는 방법


1. input 만 사용하는 방법

```html
<form action="index.html" method="post">
  <input type="submit" value="submit">
</form>
```

<br>


2. button with javascript

```html
<button type="button" name="button" onclick="btnClick()">submit</button>

<script type="text/javascript">
  function btnClick() {
    location.href = "index.html";
  }
</script>
```

<br>


3. button with jquery

```html
<button type="button" name="button" id="jqueryBtn">submit</button>

<script type="text/javascript">
  $(document).ready(function () {
    $('jqueryBtn').click(function () {
      location.href = "index.html";
    });
  });
</script>
```

<br>


4. input with jquery

```html
<input type="button" id="inputBtn" value="submit">

<script type="text/javascript">
  $(document).ready(function () {
    $('inputBtn').click(function () {
      location.href = "index.html";
    });
  });
</script>
```


<br>

- html에서 다른 페이지로 이동할 때 데이터를 가져가야 한다면 ```form``` 태그를 사용해야한다.
- javascript와 jquery를 사용하면 ```form```태그 없이 값을 넘기는 것이 가능하다.
  - (추후에 포스팅할 예정)
