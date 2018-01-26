---
layout: post
title: '[jQuery] 마우스 액션 다루기'
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
---


jQuery를 사용하여 mouse action을 다루는 방법을 알아봅니다.


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
