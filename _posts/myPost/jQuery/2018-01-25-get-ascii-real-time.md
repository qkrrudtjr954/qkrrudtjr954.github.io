---
layout: post
title: '[jQuery] 입력값 복사'
categories:
  - jQuery
tags:
  - jQuery
  - .keydown()
  - 입력값 복사
---

jQuery를 사용하여 입력한 값을 곧 바로 복사할 수 있다.


<br>




## 실시간으로 텍스트 복사하기


- jQuery를 사용하여 입력하는 즉시 값이 복사되도록 한다.
- ```.keydown()``` 함수는 event를 반환한다.
- ```event.keyCode``` 는 입력된 값의 ascii 코드 값을 가져온다.


<div class="example">
<input type="text" id="hoge"><br>
<input type="text" id="hogeKeyCode"><br>

<script type="text/javascript">
  $(document).ready(function () {

    // event 가 넘어온다.
    // keyCode는 ASCII CODE값
    $('#hoge').keydown(function ( event ) {
      var keyCode = event.keyCode;

      var res = String.fromCharCode(keyCode);
      var text = $('#hogeKeyCode').val();

      $('#hogeKeyCode').val(text+res);
    });
  })
</script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>값 복사하기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <input type="text" id="hoge"><br>
    <input type="text" id="hogeKeyCode"><br>

    <script type="text/javascript">
      $(document).ready(function () {

        // event 가 넘어온다.
        // keyCode는 ASCII CODE값
        $('#hoge').keydown(function ( event ) {
          var keyCode = event.keyCode;

          var res = String.fromCharCode(keyCode);
          var text = $('#hogeKeyCode').val();

          $('#hogeKeyCode').val(text+res);
        });
      })
    </script>
  </body>
</html>
```

- ```.keyCode()``` 함수는 입력된 텍스트의 아스키 코드를 리턴한다.
- 띄어쓰기, 화살표 역시 아스키 코드로 표현된다.
