---
layout: post
title: '[jQuery] input 태그 foncus 액션'
categories:
  - jQuery
tags:
  - jQuery
  - .focus()
---

jQuery를 사용하여 input태그에 focus가 생겼을때 액션을 정의하는 방법을 알아봅니다.


<br>

## input태그 focus 옵션 주기

- jQuery를 사용하면 input 태그에 focus 됐을 때, 행동을 정의할 수 있습니다.


<div class="example">
<span>ID : </span>
<input type="text" name="id" value="">

<span>PWD : </span>
<input type="password" name="pwd" value="">

<script type="text/javascript">
  // focus 됐을 때 border와 배경화면 색을 변경합니다.
  $('input').focus(function () {
    $(this).css('border', '1px solid skyblue');
    $(this).css('background-color', 'yellow');
  });

  // focus가 out됐을 때 border와 배경화면 색을 변경합니다.
  $('input').focusout(function () {
    $(this).css('border', '1px solid red');
    $(this).css('background-color', 'white');
  });
</script>
</div>

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>input focus</title>
  </head>
  <body>
    <span>ID : </span>
    <input type="text" name="id" value="">

    <span>PWD : </span>
    <input type="password" name="pwd" value="">

    <script type="text/javascript">
      // focus 됐을 때 border와 배경화면 색을 변경합니다.
      $('input').focus(function () {
        $(this).css('border', '1px solid skyblue');
        $(this).css('background-color', 'yellow');
      });

      // focus가 out됐을 때 border와 배경화면 색을 변경합니다.
      $('input').focusout(function () {
        $(this).css('border', '1px solid red');
        $(this).css('background-color', 'white');
      });
    </script>
  </body>
</html>
```
