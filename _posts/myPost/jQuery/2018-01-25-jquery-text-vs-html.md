---
layout: post
title: '[jQuery] .text() vs .html()'
categories:
  - jQuery
tags:
  - jQuery
  - .text()
  - .html()
---

jQuery를 사용하여 값을 가져오는 방법에는 2가지 있다. ```.text()```와 ```.html()``` 의 사용법과 차이를 비교해본다.





<br>


## .text() vs .html()


- javascript의 ```innerHTML```, ```innerTEXT``` 와 같은 기능을 하는 함수가 jQuery에도 존재한다.

- ```.text()``` : html 태그는 제외하고 문자열만 가져온다.
- ```.html()``` : html 태그를 포함한 문자열을 가져온다.


<div class="example">
  <p id="loremtext">
    <b>Lorem ipsum dolor sit amet, consectetur adipisicing elit,</b> sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. <br><br><br>Ut enim ad minim veniam, quis nostrud exercitation.
  </p>


  <button type="button" name="button" id="btn1">Show Text</button>
  <button type="button" name="button" id="btn2">Show HTML</button>


  <script type="text/javascript">
    $(function(){

      // .text()는 텍스트만 불러온다.
      $('#btn1').click(function () {
        alert($('#loremtext').text());
      });

      // .html()은 html태그까지 전부 불러온다.
      $('#btn2').click(function () {
        alert($('#loremtext').html());
      });
    });
  </script>
</div>



```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>jquery DOM</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
  <!--
  DOM (Document Object Model)

  javascript : .innerHTML, .value
  jQuery : .val(), .text(), .html(), .attr()
  -->

  <p id="loremtext">
    <b>Lorem ipsum dolor sit amet, consectetur adipisicing elit,</b> sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. <br><br><br>Ut enim ad minim veniam, quis nostrud exercitation.
  </p>


  <button type="button" name="button" id="btn1">Show Text</button>
  <button type="button" name="button" id="btn2">Show HTML</button>


  <script type="text/javascript">
    $(function(){

      // .text()는 텍스트만 불러온다.
      $('#btn1').click(function () {
        alert($('#loremtext').text());
      });

      // .html()은 html태그까지 전부 불러온다.
      $('#btn2').click(function () {
        alert($('#loremtext').html());
      });
    });
  </script>
  </body>
</html>
```



- ```.text()``` 는 내부에 있는 문자열만 가져온다. (html태그 제외)
- ```.html()``` 은 내부에 있는 모든 태그까지 가져온다.
