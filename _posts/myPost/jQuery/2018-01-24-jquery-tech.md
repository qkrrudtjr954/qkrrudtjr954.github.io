---
layout: post
title: '[jQuery] 활용하기'
categories:
  - jQuery
tags:
  - jQuery
  - mouseover
  - mouseout
  - mouseenter
  - mouseleave
  - mouseup
  - mousedown
  - mousehover
  - .css()
  -
---

jQuery를 사용하여 할 수 있는 활용 방법 예시를 간단하게 소개한다.


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


<br>


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

<br>

## jQuery mouse action


- jQuery 를 사용하여 mouse action을 정의할 수 있다.

- ```.mouseenter()``` : 마우스 커서가 특정 영역에 들어오면 함수를 동작시킨다.
- ```.mouseleave()``` : 마우스 커서가 특정 영역을 벗어나면 함수를 동작시킨다.
- ```.mouseup()``` : 마우스로 클릭하는 도중 마우스가 올라갈때 함수가 동작한다.
- ```.mousedown()``` : 마우스로 클릭하는 도중 마우스가 내려갈때 함수가 동작한다.
- ```.mouseover()``` : 마우스가 영역 위에 올라오면 함수를 동작시킨다.
- ```.mouseout()``` : 마우스가 영역을 벗어나면 함수를 동작시킨다.

<div class="example">
  <div id="mouseenter" class="mouseAction">
    <p>MouseEnter : Mouse를 여기로 가져와주세요.</p>
  </div>
  <div id="mouseleave" class="mouseAction">
    <p>MouseLeave : Mouse를 이 영역 밖으로 가져가주세요.</p>
  </div>

  <div id="upNdown" class="mouseAction">
    <p>MouseUp & MouseDown : 이 영역을 클릭해주세요.</p>
  </div>

  <div id="mouseover" class="mouseAction">
    <p>MouseOver : Mouse를 여기로 가져와주세요.</p>
  </div>
  <div id="mouseout" class="mouseAction">
    <p>MouseOut : Mouse를 이 영역 밖으로 가져가주세요.</p>
  </div>


  <div id="mousehover" class="mouseAction">
    <p>MouseHover : mouseover + mouseout 의 동작을 한번에 수행합니다.</p>
  </div>

  <script type="text/javascript">

    $(document).ready(function () {
      // 마우스가 영역에 들어오면 실행 (mouseover와 비슷)
      $('#mouseenter').mouseenter(function () {
        alert('마우스가 영역에 들어왔습니다!');
      });
      // 마우스가 영역에 들어오면 실행 (mouseover와 비슷)
      $('#mouseleave').mouseleave(function () {
        alert('마우스가 떠났습니다.');
      });

      // 마우스를 누를때 실행
      $('#upNdown').mouseup(function () {
        $('#upNdown p').append('Up! ');
      });
      // 마우스를 땔 때 실행
      $('#upNdown').mousedown(function () {
        $('#upNdown p').append('Down! ');
      });


      // 마우스가 영역에 들어오면 실행
      $('#mouseover').mouseover(function () {
        alert('마우스가 영역에 들어왔습니다!');
      });
      // 마우스가 영역에 들어오면 실행
      $('#mouseout').mouseout(function () {
        alert('마우스가 떠났습니다.');
      });


      // mouseover + mouseout
      $('#mousehover').hover(function() {
        alert('마우스가 들어왔을 때도 실행되고 나갈 때도 실행됩니다.');
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

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  </head>
  <body>
    <div id="mouseenter">
      <p>MouseEnter : Mouse를 여기로 가져와주세요.</p>
    </div>
    <div id="mouseleave">
      <p>MouseLeave : Mouse를 이 영역 밖으로 가져가주세요.</p>
    </div>

    <div id="upNdown">
      <p>MouseUp & MouseDown : 이 영역을 클릭해주세요.</p>
    </div>

    <div id="mouseover">
      <p>MouseOver : Mouse를 여기로 가져와주세요.</p>
    </div>
    <div id="mouseout">
      <p>MouseOut : Mouse를 이 영역 밖으로 가져가주세요.</p>
    </div>


    <div id="mousehover">
      <p>MouseHover : mouseover + mouseout 의 동작을 한번에 수행합니다.</p>
    </div>

    <script type="text/javascript">

      $(document).ready(function () {
        // 마우스가 영역에 들어오면 실행 (mouseover와 비슷)
        $('#mouseenter').mouseenter(function () {
          alert('마우스가 영역에 들어왔습니다!');
        });
        // 마우스가 영역에 들어오면 실행 (mouseover와 비슷)
        $('#mouseleave').mouseleave(function () {
          alert('마우스가 떠났습니다.');
        });

        // 마우스를 누를때 실행
        $('#upNdown').mouseup(function () {
          $('#upNdown p').append('Up! ');
        });
        // 마우스를 땔 때 실행
        $('#upNdown').mousedown(function () {
          $('#upNdown p').append('Down! ');
        });


        // 마우스가 영역에 들어오면 실행
        $('#mouseover').mouseover(function () {
          alert('마우스가 영역에 들어왔습니다!');
        });
        // 마우스가 영역에 들어오면 실행
        $('#mouseout').mouseout(function () {
          alert('마우스가 떠났습니다.');
        });


        // mouseover + mouseout
        $('#mousehover').hover(function() {
          alert('마우스가 들어왔을 때도 실행되고 나갈 때도 실행됩니다.');
        });
      });
    </script>
  </body>
</html>
```

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

<br>

## jQuery fadeIn, fadeOut, fadeToggle


- fade in, fade out 같은 애니메이션을 적용할 수 있습니다.

<div class="example">
  <!-- fade in, fade out, toggle -->
  <div id="div1" style="width: 50%; height: 80px; background-color: skyblue;"></div>
  <div id="div2" style="width: 50%; height: 80px; background-color: lightgreen;"></div>
  <div id="div3" style="width: 50%; height: 80px; background-color: pink;"></div>

  <br>
  <button type="button" id="fadein">fade in</button>
  <button type="button" id="fadeout">fade out</button>
  <button type="button" id="fadetoggle">fade toggle</button>

  <script type="text/javascript">
    $(document).ready(function() {

      // fade in, fade out, toggle
      $('#fadein').click(function() {
        $('#div1').fadeIn(1000);  // 1초
        $('#div2').fadeIn(2000);  // 2초
        $('#div3').fadeIn(3000);  // 3초
      });

      $('#fadeout').click(function() {
        $('#div1').fadeOut(1000);
        $('#div2').fadeOut(2000);
        $('#div3').fadeOut(3000);
      });

      $('#fadetoggle').click(function() {
        $('#div1').fadeToggle(1000);
        $('#div2').fadeToggle(2000);
        $('#div3').fadeToggle(3000);
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

    <!-- fade in, fade out, toggle -->
    <div id="div1" style="width: 50%; height: 80px; background-color: skyblue;"></div>
    <div id="div2" style="width: 50%; height: 80px; background-color: lightgreen;"></div>
    <div id="div3" style="width: 50%; height: 80px; background-color: pink;"></div>

    <br>
    <button type="button" id="fadein">fade in</button>
    <button type="button" id="fadeout">fade out</button>
    <button type="button" id="fadetoggle">fade toggle</button>

    <script type="text/javascript">
      $(document).ready(function() {

        // fade in, fade out, toggle
        $('#fadein').click(function() {
          $('#div1').fadeIn(1000);  // 1초
          $('#div2').fadeIn(2000);  // 2초
          $('#div3').fadeIn(3000);  // 3초
        });

        $('#fadeout').click(function() {
          $('#div1').fadeOut(1000);
          $('#div2').fadeOut(2000);
          $('#div3').fadeOut(3000);
        });

        $('#fadetoggle').click(function() {
          $('#div1').fadeToggle(1000);
          $('#div2').fadeToggle(2000);
          $('#div3').fadeToggle(3000);
        });
      });
    </script>
  </body>
</html>
```
