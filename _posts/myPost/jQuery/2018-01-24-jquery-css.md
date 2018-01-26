---
layout: post
title: '[jQuery] CSS 수정하기'
categories:
  - jQuery
tags:
  - jQuery
  - .css()
  - css 수정
---

jQuery로  CSS를 수정하는 방법을 살펴봅니다.

<br>


## jQuery로 CSS수정하기


- ```.css(attribute, value)``` 함수를 사용하면 해당 DOM의 CSS를 변경할 수 있다.


<div class="example">
  <h1 class="cls" style="background-color: pink">H1 tag 클릭해주세요</h1>
  <p id="ptag">hello world!!!</p>

  <button type="button" name="button" id="changeSize">Bigger!</button>
  <button type="button" name="button" id="changeBg">Background change!</button>
  <button type="button" name="button" id="changeHeight">Taller!</button>
  <button type="button" name="button" id="changeWidth">More Slim!</button>
</div>

<script type="text/javascript">
$(document).ready(function () {
  $('h1.cls').click(function(){
    $(this).css("background-color", "lightgreen");
    });

    $('#changeSize').click(function(){
      $('p#ptag').css("font-size", "30px");
      });

      $('#changeBg').click(function(){
        $('p#ptag').css("background-color", "lightgreen");
        });

        $('#changeHeight').click(function(){
          $('p#ptag').css("height", "50px");
          });

          $('#changeWidth').click(function(){
            $('p#ptag').css("width", "200px");
            });
            });
            </script>



```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  </head>
  <body>

    <h1 class="cls" style="background-color: pink">H1 tag</h1>
    <p id="ptag">hello world!!!</p>

    <button type="button" name="button" id="changeSize">Bigger!</button>
    <button type="button" name="button" id="changeBg">Background change!</button>
    <button type="button" name="button" id="changeHeight">Taller!</button>
    <button type="button" name="button" id="changeWidth">More Slim!</button>

    <script type="text/javascript">
      $(document).ready(function () {
        $('h1.cls').click(function(){
          $(this).css("background-color", "lightgreen");
        });

        $('#changeSize').click(function(){
          $('p#ptag').css("font-size", "30px");
        });

        $('#changeBg').click(function(){
          $('p#ptag').css("background-color", "lightgreen");
        });

        $('#changeHeight').click(function(){
          $('p#ptag').css("height", "50px");
        });

        $('#changeWidth').click(function(){
          $('p#ptag').css("width", "200px");
        });
      });
    </script>
  </body>
</html>
```

- ```h1``` 태그를 클릭하면 배경화면이 바뀐다.
- 각 버튼을 누르면 정해진 css가 변경된다.
