---
layout: post
title: '[jQuery] 라디오 버튼, 체크박스 값 가져오기'
categories:
  - jQuery
tags:
  - jQuery
  - 라디오 버튼 값 가져오기
  - 체크박스 값 가져오기
---

jQuery를 사용하여 라디오 버튼의 값을 가져올 수 있고, 체크박스의 값도 가져올 수 있다.


<br>


## radio 버튼 값 가져오기


- jQuery를 사용하여 radio 버튼의 값을 가져옵니다.


<div class="example">
<ul>
  <li>
    <input type="radio" name="radioTxt" value="Apple" checked>Apple
  </li>
  <li>
    <input type="radio" name="radioTxt" value="Grape">Grape
  </li>
  <li>
    <input type="radio" name="radioTxt" value="Banana">Banana
  </li>
</ul>
<button type="button" name="button" id="radioButton">get radio Value</button>
<button type="button" name="button" id="radioButton2">set radio Value</button>

<script type="text/javascript">
  $(document).ready(function () {
    $('#radioButton').click(function () {
      // getter
      var radioVal = $('input[name="radioTxt"]:checked').val();
      alert(radioVal);
    });

    $('#radioButton2').click(function () {
      // setter
      // 선택한 부분을 세팅할 수 있다.
      $('input[name="radioTxt"]').val(['Banana']);
    });
  });
</script>
</div>

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>radio 값 가져오기</title>
  </head>
  <body>
    <ul>
      <li>
        <input type="radio" name="radioTxt" value="Apple" checked>Apple
      </li>
      <li>
        <input type="radio" name="radioTxt" value="Grape">Grape
      </li>
      <li>
        <input type="radio" name="radioTxt" value="Banana">Banana
      </li>
    </ul>
    <button type="button" name="button" id="radioButton">get radio Value</button>
    <button type="button" name="button" id="radioButton2">set radio Value</button>

    <script type="text/javascript">
      $(document).ready(function () {
        $('#radioButton').click(function () {
          // getter
          var radioVal = $('input[name="radioTxt"]:checked').val();
          alert(radioVal);
        });

        $('#radioButton2').click(function () {
          // setter
          // 선택한 부분을 세팅할 수 있다.
          $('input[name="radioTxt"]').val(['Banana']);
        });
      });
    </script>
  </body>
</html>
```

- 선택된 라디오 버튼의 값을 가져올 수 있다.
- 라이오 버튼의 선택값을 설정할 수 있다.

<br>


## checkbox 값 가져오기

- jQuery를 사용하여 checkbox의 값을 가져옵니다.


<div class="example">
  <input type="checkbox" name="check" value="" id="rd2">Drawing
  <button type="button" name="button" id="checkBtn">get Value</button>

  <script type="text/javascript">
    $(document).ready(function () {
      $('#checkBtn').click(function () {
        // checkbox

        // var check = $('#rd2').is(":checked");
        // alert(check);

        // var check = $('input[id="rd2"]').is(':checked');
        // alert(check);

        var check = $('input:checkbox[id="rd2"]').is(':checked');
        alert(check);
      });
    });
  </script>
</div>

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>checkbox 값 가져오기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <input type="checkbox" name="check" value="" id="rd2">Drawing
    <button type="button" name="button" id="checkBtn">get Value</button>

    <script type="text/javascript">
      $(document).ready(function () {
        $('#checkBtn').click(function () {
          // checkbox

          // var check = $('#rd2').is(":checked");
          // alert(check);

          // var check = $('input[id="rd2"]').is(':checked');
          // alert(check);

          var check = $('input:checkbox[id="rd2"]').is(':checked');
          alert(check);
        });
      });
    </script>
  </body>
</html>
```

- 주석 처리된 2가지 방법으로도 값을 가져올 수 있다
