---
layout: post
title: '[jQuery] 활용하기3'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery를 사용하여 할 수 있는 활용 방법 예시를 간단하게 소개한다.



## 텍스트를 추가하는 여러가지 방법

- jQuery를 사용하여 text 또는 html 태그를 추가하는 방법을 알아봅니다.
- 문자열에 html코드를 직접 넣어 더하는 방법
- jQuery를 사용하여 html코드를 만들어 주는 방법
- javascript를 사용하여 html 코드를 만들어 주는 방법


<div class="example">
  <div id="appendDiv">기본 div!</div>

  <button type="button" name="button" onclick="appendText()">append</button>

  <script type="text/javascript">
    function appendText() {
      var text1 = "<p>추가 텍스트!!</p>";  // html로 코드를 생성한다.
      // $('div#appendDiv').append(text1); // 텍스트를 추가한다. html

      var text2 = $('<p></p>').text('다른 방식의 추가 텍스트!!!');  // jquery로 코드를 생성한다.
      // $('div#appendDiv').append(text1, text2);

      var text3 = document.createElement('p');
      text3.innerHTML = "또 다른 방식의 추가 텍스트!!!";
      $('div#appendDiv').append(text1, text2, text3);
    }
  </script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>

    <div id="appendDiv">기본 div!</div>

    <button type="button" name="button" onclick="appendText()">append</button>

    <script type="text/javascript">
      function appendText() {
        var text1 = "<p>추가 텍스트!!</p>";  // html로 코드를 생성한다.
        // $('div#appendDiv').append(text1); // 텍스트를 추가한다. html

        var text2 = $('<p></p>').text('다른 방식의 추가 텍스트!!!');  // jquery로 코드를 생성한다.
        // $('div#appendDiv').append(text1, text2);

        var text3 = document.createElement('p');
        text3.innerHTML = "또 다른 방식의 추가 텍스트!!!";
        $('div#appendDiv').append(text1, text2, text3);
      }
    </script>
  </body>
</html>
```


## 문자열 또는 태그를 삽입하는 위치를 지정

- 문자열 또는 태그를 삽입하는데 앞에 삽입할지 뒤에 삽입할지 위치를 지정할 수 있다.

<div class="example">
  <p id="originP">-original p tag-</p>

  <button type="button" name="button" id="btn1">insert before</button>
  <button type="button" name="button" id="btn2">insert after</button>

  <script type="text/javascript">
  $(function () {
    $('#btn1').click(function () {
      $('#originP').before('<b>before</b><br>');
    });

    $('#btn2').click(function () {
      $('#originP').after('<b>after</b><br>');
    });
  })
  </script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>insert before & after</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <p id="originP">-original p tag-</p>

    <button type="button" name="button" id="btn1">insert before</button>
    <button type="button" name="button" id="btn2">insert after</button>

    <script type="text/javascript">
    $(function () {
      $('#btn1').click(function () {
        $('#originP').before('<b>before</b><br>');
      });

      $('#btn2').click(function () {
        $('#originP').after('<b>after</b><br>');
      });
    })
    </script>
  </body>
</html>
```


## 요소 및 태그 삭제

- jQuery를 사용하여 요소를 삭제하거나 요소의 내부를 삭제할 수 있다.


<div class="example">
  <div id="div1" style="width:500px; height:200px; border:1px solid red; background-color:skyblue; margin-top:50px;">
    This is <b>div1</b>

    <br>

    <p id="pid">This is p tag id="id"</p>

    <p class="pcls">This is p tag class="class"</p>
  </div>

  <div id="div2" style="width:500px; height:200px; border:1px solid red; background-color:skyblue; margin-top:50px;">
    This is <b>div2</b>

    <br>

    <p id="pid">This is p tag id="id"</p>

    <p class="pcls">This is p tag class="class"</p>
  </div>

  <button type="button" name="button" id="btn3">div1 태그를 지운다.</button>
  <button type="button" name="button" id="btn4">div2 태그 내부를 지운다.</button>
  <button type="button" name="button" id="btn5">특정 p 태그를 지운다.</button>

  <script type="text/javascript">
    $(document).ready(function () {
      $('#btn3').click(function () {
        $('#div1').remove(); // div 전체 삭제
      });
      $('#btn4').click(function () {
        $('#div2').empty(); // div 안에 태그를 전부 삭제
      });
      $('#btn5').click(function () {
        $('.pcls').remove(); // 특정 태그를 삭제
      });
    })
  </script>
</div>




```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>delete tag</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <div id="div1" style="width:500px; height:200px; border:1px solid red; background-color:skyblue; margin-top:50px;">
      This is div1 tag

      <p id="pid">This is p tag id="id"</p>

      <p class="pcls">This is p tag class="class"</p>
    </div>

    <div id="div2" style="width:500px; height:200px; border:1px solid red; background-color:skyblue; margin-top:50px;">
      This is div1 tag

      <p id="pid">This is p tag id="id"</p>

      <p class="pcls">This is p tag class="class"</p>
    </div>

    <button type="button" name="button" id="btn3">div1 태그를 지운다.</button>
    <button type="button" name="button" id="btn4">div2 태그 내부를 지운다.</button>
    <button type="button" name="button" id="btn5">특정 p 태그를 지운다.</button>

    <script type="text/javascript">
      $(document).ready(function () {
        $('#btn3').click(function () {
          $('#div1').remove(); // div 전체 삭제
        });
        $('#btn4').click(function () {
          $('#div2').empty(); // div 안에 태그를 전부 삭제
        });
        $('#btn5').click(function () {
          $('.pcls').remove(); // 특정 태그를 삭제
        });
      })
    </script>
  </body>
</html>
```



## 외부 파일 불러오기


- jQuery를 사용해서 외부 텍스트 파일을 불러온다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>외부 파일 불러오기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  </head>
  <body>
    <div id="news">
      loading....
    </div>

    <script type="text/javascript">
      $(function () {
        // 파일의 url을 적어준다.
        $('#news').load('news.txt', function (text, status) {
          // status는 로딩의 상태값을 가져온다.
          if(status == 'success'){
            alert('Success');
          }else if(status=='error'){
            alert('Error');
          }
        });
      });
    </script>
  </body>
</html>
```


## 배경색 속성, 값 가져오기

- jQuery를 사용하여 배경화면의 속성과 값을 가져옵니다.


<div class="example">
  <p style="background-color:red" id="bgP1">this is p tag</p>
  <p style="background-color:blue" id="bgP2">this is p tag</p>
  <p style="background-color:black" id="bgP3">this is p tag</p>

  <button type="button" name="button" id="bgBtn">background</button>

  <script type="text/javascript">
    $(function () {
      $('button#bgBtn').click(function () {
        // color 값을 반환한다.
        var color = $('p#bgP1').css("background-color");
        alert('첫번째 p 태그의 배경색 : ' + color);

        // 배경색을 바꾼다.
        $('p#bgP2').css("background-color", "yellow");

        // 배경색을 바꾸고 글자 크기를 조정한다.
        $('p#bgP3').css({
          "background-color" : "pink",
          "font-size" : "30px"
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
    <title>외부 파일 불러오기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  </head>
  <body>

    <p style="background-color:red" id="bgP1">this is p tag</p>
    <p style="background-color:blue" id="bgP2">this is p tag</p>
    <p style="background-color:black" id="bgP3">this is p tag</p>

    <button type="button" name="button" id="bgBtn">background</button>

    <script type="text/javascript">
      $(function () {
        $('button#bgBtn').click(function () {
          // color 값을 반환한다.
          var color = $('p#bgP1').css("background-color");
          alert('첫번째 p 태그의 배경색 : ' + color);

          // 배경색을 바꾼다.
          $('p#bgP2').css("background-color", "yellow");

          // 배경색을 바꾸고 글자 크기를 조정한다.
          $('p#bgP3').css({
            "background-color" : "pink",
            "font-size" : "30px"
          })
        })
      })
    </script>
  </body>
</html>
```



## 요소(element)에 class를 넣고 뺀다.


- jQuery를 사용하여 요소에 class를 부여할 수 있다.
- jQuery를 사용하여 요소에 class를 제거할 수 있다.


<div class="example">
  <div id="noClassDivTag">
    Hi, i'm div tag. i don't have class.
    <br>
    <p id="noClassPtag">Hi, i'm p tag! but, i don't have class.</p>
    <p id="noClassPtag2">Hi, i'm p2 tag! but, i don't have class.</p>
  </div>

  <button type="button" name="button" id="insert">element에 class를 더한다.</button>
  <button type="button" name="button" id="remove">element에서 class를 삭제한다.</button>

  <script type="text/javascript">
    $(function () {
      // class를 더합니다.
      $('button#insert').click(function () {
        $('div#noClassDivTag').addClass('important');
        $('p#noClassPtag').addClass('blue');
        $('p#noClassPtag2').addClass('blue important');
      });

      // class를 뺍니다.
      $('button#remove').click(function () {
        $('div#noClassDivTag').removeClass('important');
        $('p#noClassPtag').removeClass('blue');
        $('p#noClassPtag2').removeClass('blue important');
      });
    });
  </script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>add and remove class</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

    <style media="screen">
      .important {
        background-color: red;
        text-align: center;
      }

      .blue {
        font-size: 15px;
        color : blue;
      }
    </style>
  </head>
  <body>
    <div id="noClassDivTag">
      Hi, i'm div tag. i don't have class.
      <br>
      <p id="noClassPtag">Hi, i'm p tag! but, i don't have class.</p>
      <p id="noClassPtag2">Hi, i'm p2 tag! but, i don't have class.</p>
    </div>

    <button type="button" name="button" id="insert">element에 class를 더한다.</button>
    <button type="button" name="button" id="remove">element에서 class를 삭제한다.</button>

    <script type="text/javascript">
      $(function () {
        // class를 더합니다.
        $('button#insert').click(function () {
          $('div#noClassDivTag').addClass('important');
          $('p#noClassPtag').addClass('blue');
          $('p#noClassPtag2').addClass('blue important');
        });

        // class를 뺍니다.
        $('button#remove').click(function () {
          $('div#noClassDivTag').removeClass('important');
          $('p#noClassPtag').removeClass('blue');
          $('p#noClassPtag2').removeClass('blue important');
        });
      });
    </script>
  </body>
</html>
```


## 리스트 선택시 값 가져오기


- 리스트를 선택했을때 선택한 요소의 값을 가져옵니다.


<div class="example">
  <p>리스트를 클릭하세요</p>
  <ul class="ulist">
    <li>coffee</li>
    <li>red tea</li>
    <li>milk</li>
    <li>juice</li>
    <li>green tea</li>
  </ul>

  <p id="q02"></p>
  <p id="q03"></p>

  <script type="text/javascript">
    $(function () {
      var len = $('ul.ulist').children().length;
      $('#q02').text('리스의 갯수: '+len);

      $('ul.ulist').children().click(function () {
        var choice = $('ul.ulist').children().index(this);
        $('#q03').text('선택한 index: '+choice);
      })
    })
  </script>
</div>


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>list 값 가져오기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  </head>
  <body>
    <ul class="ulist">
      <li>coffee</li>
      <li>red tea</li>
      <li>milk</li>
      <li>juice</li>
      <li>green tea</li>
    </ul>

    <p id="q02"></p>
    <p id="q03"></p>

    <script type="text/javascript">
      $(function () {
        var len = $('ul.ulist').children().length;
        $('#q02').text('리스의 갯수: '+len);

        $('ul.ulist').children().click(function () {
          var choice = $('ul.ulist').children().index(this);
          $('#q03').text('선택한 index: '+choice);
        })
      })
    </script>

  </body>
</html>
```
