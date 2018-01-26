---
layout: post
title: '[jQuery] 활용하기'
categories:
  - jQuery
tags:
  - jQuery
  - jquery & list
---


jQuery로 list 태그에 접근하고 값을 숨기는 방법을 알아봅니다.


## jQuery로 list 태그 접근하기

- jQuery 로 ```<ul></ul>```등 html 리스트 태그에 접근하는 방법을 제시한다.

<div class="example">
  <ul id="myList">
    <li>coffee
      <ul>
        <li>black</li>
        <li>milk</li>
      </ul>
    </li>
    <li>red tea</li>
    <li id="greentea">green tea</li>
  </ul>

  <button type="button" name="button" id="deleteGreenBtn">green tea 숨기기</button>
  <button type="button" name="button" id="delChildBtn">black 숨기기</button>

  <script type="text/javascript">
    $(document).ready(function () {

      // 리스트 요소를 숨기는 첫번째 방법
      $('#deleteGreenBtn').click(function () {
        $('li#greentea').hide();
      });

      // 리스트 자식 요소를 숨기는 두번째 방법
      $('#delChildBtn').click(function () {
        // myList 속 첫번째 li 안에 ul 안에 첫번째 li를 숨긴다.
        $('#myList li:first ul li:first').hide();
      });
    });
  </script>
</div>

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
    <script
            src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  </head>
  <body>
    <ul id="list">
      <li>coffee
        <ul>
          <li>black</li>
          <li>milk</li>
        </ul>
      </li>
      <li>red tea</li>
      <li id="greentea">green tea</li>
    </ul>

    <button type="button" name="button" id="deleteGreenBtn">green tea 숨기기</button>
    <button type="button" name="button" id="delChildBtn">black 숨기기</button>

    <script type="text/javascript">
      $(document).ready(function () {

        // 리스트 요소를 숨기는 첫번째 방법
        $('#deleteGreenBtn').click(function () {
          $('li#greentea').hide();
        });

        // 리스트 자식 요소를 숨기는 두번째 방법
        $('#delChildBtn').click(function () {
          // ul 속 첫번째 li 안에 ul 안에 첫번째 li를 숨긴다.
          $('#myList li:first ul li:first').hide();
        });
      });
    </script>

  </body>
</html>
```
