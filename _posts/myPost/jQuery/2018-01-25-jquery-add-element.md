---
layout: post
title: '[jQuery] .append() 요소 추가하기'
categories:
  - jQuery
tags:
  - jQuery
  - .append()
  - 요소 추가하기
---

jQuery를 사용하여 특정 태그 요소를 동적으로 추가할 수 있다.




<br>



## 요소 추가하는 방법

- 요소를 생성해서 태그의 앞 또는 뒤에 추가한다.


<div class="example">
<ol id="olist">
  <li>item1</li>
  <li>item2</li>
  <li>item3</li>
</ol>


<button type="button" name="button" id="btn4">append()</button>
<button type="button" name="button" id="btn5">prepend()</button>

<br>

<p id="appendParagraph">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor
  in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>


<button type="button" name="button" id="btn6">append()</button>
<button type="button" name="button" id="btn7">prepend()</button>


<script type="text/javascript">
  $(function() {
    $('#btn4').click(function() {
      // 리스트 요소를 더한다.
      $('#olist').append("<li>.append()</li>");
    });

    $('#btn5').click(function() {
      // 리스트 요소를 제일 앞쪽에 더한다.
      $('#olist').prepend("<li>.prepend()</li>");
    });

    $('#btn6').click(function() {
      // 문자열을 더한다.
      $('p#appendParagraph').append("<br>.append()<br>");
    });

    $('#btn7').click(function() {
      // 문자열을 제일 앞쪽에 더한다.
      $('p#appendParagraph').prepend("<br>.prepend()<br>");
    });
  })
</script>
</div>

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>요소의 추가, 삭제</title>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
</head>

<body>
  <ol id="olist">
    <li>item1</li>
    <li>item2</li>
    <li>item3</li>
  </ol>


  <button type="button" name="button" id="btn4">append()</button>
  <button type="button" name="button" id="btn5">prepend()</button>

  <p id="appendParagraph">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor
    in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
  </p>
  <br>
  <p id="appendParagraph">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor
    in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
  </p>

  <button type="button" name="button" id="btn6">append()</button>
  <button type="button" name="button" id="btn7">prepend()</button>


  <script type="text/javascript">
    $(function() {
      $('#btn4').click(function() {
        // 리스트 요소를 더한다.
        $('#olist').append("<li>.append()</li>");
      });

      $('#btn5').click(function() {
        // 리스트 요소를 제일 앞쪽에 더한다.
        $('#olist').prepend("<li>.prepend()</li>");
      });

      $('#btn6').click(function() {
        // 문자열을 더한다.
        $('p#appendParagraph').append("<br>.append()<br>");
      });

      $('#btn7').click(function() {
        // 문자열을 제일 앞쪽에 더한다.
        $('p#appendParagraph').prepend("<br>.prepend()<br>");
      });
    })
  </script>
</body>

</html>
```
