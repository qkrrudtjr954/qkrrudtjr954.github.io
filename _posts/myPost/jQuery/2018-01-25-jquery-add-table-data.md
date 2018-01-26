---
layout: post
title: '[jQuery] 활용하기2'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery를 사용하여 배열의 값을 동적으로 테이블에 추가하는 방법을 알아봅니다.

<br>



## 테이블 태그 추가하기


- 배열의 값으로 동적으로 테이블에 데이터를 추가한다.

<div class="example">
  <h1>수행사항</h1>
  <button id="woman">여자부</button>
  <button id="man">남자부</button>
  <br><br>
  <table id="result">
    <tr>
      <th></th>
      <th>이름</th>
      <th>타임</th>
    </tr>
    <tr>
      <td>우승</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>2위</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>3위</td>
      <td></td>
      <td></td>
    </tr>
  </table>

  <script type="text/javascript">
    var man = [
      ["", ""],
      ["남자1", "1:21:13"],
      ["남자2", "1:31:27"],
      ["남자3", "1:23:54"],
    ];

    var woman = [
      ["", ""],
      ["여자1", "1:41:37"],
      ["여자2", "1:43:53"],
      ["여자3", "1:38:31"],
    ];

    $(document).ready(function () {

      $('#woman').click(function () {
        for (var i = 0; i < 4; i++) {
          for (var j = 0; j < 2; j++) {
            $('#result tr:eq('+ i +') > td:eq('+ (j+1) +')').html(woman[i][j]);
          }
        }
      });

      $('#man').click(function () {
        for (var i = 0; i < 4; i++) {
          for (var j = 0; j < 2; j++) {
            $('#result tr:eq('+ i +') > td:eq('+ (j+1) +')').html(man[i][j]);
          }
        }
      });
    });
  </script>
</div>

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>Index1</title>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
</head>

<body>

  <!-- 테이블에 행 추가하는 방법 -->
  <h1>수행사항</h1>
  <button id="woman">여자부</button>
  <button id="man">남자부</button>
  <br><br>
  <table id="result">
    <tr>
      <th></th>
      <th>이름</th>
      <th>타임</th>
    </tr>
    <tr>
      <td>우승</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>2위</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>3위</td>
      <td></td>
      <td></td>
    </tr>
  </table>

  <script type="text/javascript">
    var man = [
      ["", ""],
      ["남자1", "1:21:13"],
      ["남자2", "1:31:27"],
      ["남자3", "1:23:54"],
    ];

    var woman = [
      ["", ""],
      ["여자1", "1:41:37"],
      ["여자2", "1:43:53"],
      ["여자3", "1:38:31"],
    ];

    $(document).ready(function () {

      $('#woman').click(function () {
        for (var i = 0; i < 4; i++) {
          for (var j = 0; j < 2; j++) {
            $('tr:eq('+ i +') > td:eq('+ (j+1) +')').html(woman[i][j]);
          }
        }
      });

      $('#man').click(function () {
        for (var i = 0; i < 4; i++) {
          for (var j = 0; j < 2; j++) {
            $('tr:eq('+ i +') > td:eq('+ (j+1) +')').html(man[i][j]);
          }
        }
      });
    });
  </script>

</body>

</html>
```
