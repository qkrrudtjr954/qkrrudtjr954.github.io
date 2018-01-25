---
layout: post
title: '[jQuery] 활용하기2'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery를 사용하여 할 수 있는 활용 방법 예시를 간단하게 소개한다.



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
  <link rel="stylesheet" href="style.css">
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




## 페이지를 전환하는 여러가지 방법

- 현재 페이지에서 다른 페이지로 이동하는 여러가지 방법을 소개한다.


#### 값을 넘기는 방법


1. input 만 사용하는 방법
2. button with javascript
3. button with jquery
4. input with jquery

html에서 다른 페이지로 이동할때 필요한 데이터를 추합해서 가지고 넘어가야한다. 그 행위는 from 만 가능하다.


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <form action="index.html" method="post">
      <input type="submit" name="" value="submit">

      <button type="button" name="button" onclick="btnClick()">submit</button>

      <button type="button" name="button" id="btn">submit</button>

      <input type="button" id="btn" value="submit">
    </form>

    <script type="text/javascript">
      function btnClick() {
        location.href="index.html";
      }

      $(document).ready(function () {
        $('#btn').click(function () {
          location.href="index.html";
        });
      });
    </script>
  </body>
</html>
```



## .text() vs .html()


- javascript의 ```innerHTML```, ```innerTEXT``` 와 같은 기능을 하는 함수가 jQuery에도 존재한다.

- ```.text()``` : html 태그는 제외하고 문자열만 가져온다.
- ```.html()``` : html 태그를 포함한 문자열을 가져온다.


<div class="example">
  <p id="loremtext">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. <b>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam.</b>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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

  <p id="test">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. <b>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam.</b>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
  </p>


  <button type="button" name="button" id="btn1">Show Text</button>
  <button type="button" name="button" id="btn2">Show HTML</button>


  <script type="text/javascript">
    $(function(){

      // .text()는 텍스트만 불러온다.
      $('#btn1').click(function () {
        alert($('#test').text());
      });

      // .html()은 html태그까지 전부 불러온다.
      $('#btn2').click(function () {
        alert($('#test').html());
      });
    });
  </script>
  </body>
</html>
```



## .attr()을 사용한 속성 변경

- img 태그의 src나 a 태그의 href와 같은 속성을 변경할 수 있는 함수이다.
- a태그의 href 속성을 변경하여 다른 홈페이지로 링크되도록 한다.
- img태그의 src 속성을 변경하여 다른 사진이 표시되도록 한다.


<div class="example">
  <a href="https://qkrrudtjr954.github.io" id="github">qkrrudtjr954</a>
  <button type="button" name="button" id="btn4">Change URL</button>

  <img id="img" src="https://i.imgur.com/YR2TfpH.jpg" alt="" width="400px" height="300px">
  <button type="button" name="button" id="btn5">Change Picture</button>

  <script type="text/javascript">
    $(function(){
      // .attr()은 속성값(property)을 설정할 수 있다.
      $('#btn4').click(function () {
        $('#github').attr("href", "https://www.naver.com");
      });

      $('#btn5').click(function () {
        $('#img').attr("src", "https://i.imgur.com/dquIqqe.jpg");
      });
    })
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

  <a href="https://qkrrudtjr954.github.io" id="github">qkrrudtjr954</a>
  <button type="button" name="button" id="btn4">Change URL</button>

  <img id="img" src="https://i.imgur.com/YR2TfpH.jpg" alt="" width="400px" height="300px">
  <button type="button" name="button" id="btn5">Change Picture</button>

  <script type="text/javascript">
    $(function(){
      // .attr()은 속성값(property)을 설정할 수 있다.
      $('#btn4').click(function () {
        $('#github').attr("href", "https://www.naver.com");
      });

      $('#btn5').click(function () {
        $('#img').attr("src", "https://i.imgur.com/dquIqqe.jpg");
      });
    })
  </script>
  </body>
</html>
```


## .attr()을 사용하여 여러개의 속성을 변경

- 하나의 속성이 아닌 여러개의 속성을 한번에 바꿀때 ***json*** 을 이용한다.

<div class="example">
  <p>
    <a href="https://www.naver.com" title="naver" id="id">naver.com</a>
  </p>

  <p>
    <a href="https://www.tutorialspoint.com" title="w3s" id="w3s">tutorialspoint.com</a>
  </p>

  <button type="button" id="attrBtn" name="button">href와 title변경</button>

  <script type="text/javascript">
    $(document).ready(function () {
      $('#attrBtn').click(function () {
        // json을 이용한다.
        $('#id').attr({
          'title' : '속았지?',
          'href' : 'https://www.daum.net'
        });

        $('#id').text('Daum');

        // 인자로 함수를 넘길 수 있다.
        $('#w3s').attr('href', function (i, originValue) {
          return originValue+'/jsp';
        })
      })
    })
  </script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>attr tag</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <p>
      <a href="https://www.naver.com" title="naver" id="id">naver.com</a>
    </p>

    <p>
      <a href="https://www.tutorialspoint.com" title="w3s" id="w3s">tutorialspoint.com</a>
    </p>

    <button type="button" name="button">href와 title변경</button>

    <script type="text/javascript">
      $(document).ready(function () {
        $('button').click(function () {
          // json을 이용한다.
          $('#id').attr({
            'title' : '속았지?',
            'href' : 'https://www.daum.net'
          });

          $('#id').text('Daum');

          // 인자로 함수를 넘길 수 있다.
          $('#w3s').attr('href', function (i, originValue) {
            return originValue+'/jsp';
          })
        })
      })
    </script>
  </body>
</html>
```


## 요소 추가하는 방법

- 요소를 생성해서 태그의 앞 또는 뒤에 추가한다.


<div class="example">
<ol id="olist">
  <li>item1</li>
  <li>item2</li>
  <li>item3</li>
</ol>

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
    $('#btn6').click(function() {
      // 문자열을 더한다.
      $('p#appendParagraph').append("<br>.append()<br>");
      // 리스트 요소를 더한다.
      $('#olist').append("<li>.append()</li>");
    });

    $('#btn7').click(function() {
      // 문자열을 제일 앞쪽에 더한다.
      $('p#appendParagraph').prepend("<br>.prepend()<br>");
      // 리스트 요소를 제일 앞쪽에 더한다.
      $('#olist').prepend("<li>.prepend()</li>");
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
      $('#btn6').click(function() {
        // 문자열을 더한다.
        $('p#appendParagraph').append("<br>.append()<br>");
        // 리스트 요소를 더한다.
        $('#olist').append("<li>.append()</li>");
      });

      $('#btn7').click(function() {
        // 문자열을 제일 앞쪽에 더한다.
        $('p#appendParagraph').prepend("<br>.prepend()<br>");
        // 리스트 요소를 제일 앞쪽에 더한다.
        $('#olist').prepend("<li>.prepend()</li>");
      });
    })
  </script>
</body>

</html>
```


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
