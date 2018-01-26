---
layout: post
title: '[jQuery] fade 액션'
categories:
  - jQuery
tags:
  - jQuery
  - .fadeIn()
  - .fadeOut()
  - .fadeToggle()
---

jQuery를 사용하여 요소에 간단한 fade 액션을 줄수 있습니다.




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
