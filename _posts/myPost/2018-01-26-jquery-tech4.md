---
layout: post
title: '[jQuery] 활용하기3'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery를 사용하여 할 수 있는 활용 방법 예시를 간단하게 소개한다.



## input range로 이미지 투명도 조절

- input 타입중 range를 통해서 이미지의 투명도를 조절할 수 있다.
- jquery-ui를 html 페이지에 추가해주어야한다.

```html
<!-- jQuery UI css -->
<link rel="stylesheet" href="http://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css" type="text/css" />

<!-- jQuery 최신버젼 -->
<script  src="http://code.jquery.com/jquery-latest.min.js"></script>
<!-- jQuery UI js -->
<script src="http://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
```



<div class="example">
  <h1>JQuery UI</h1>
  <h2>Slider</h2>

  <img alt="" src="https://cnet2.cbsistatic.com/img/HFJgghjpo8khVJJRRTjO6dBo1ys=/fit-in/570x0/2011/01/18/2a55ad4f-f0f4-11e2-8c7c-d4ae52e62bcc/HTML5_Logo_550px.png" class="opaimg">
  <img alt="" src="http://www.desartlab.com/wp-content/uploads/2015/10/css3-search-box.png" class="opaimg">
  <img alt="" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Badge_js-strict.svg/2000px-Badge_js-strict.svg.png" class="opaimg">

  <p>
    Slider의 키를 좌우로 이동시키면, 이미지의 투명도를 조정할 수 있습니다.
  </p>

  <div id="slider1" style="width: 250px"></div>

  <br>

  <p id="opa"></p>

  <script type="text/javascript">
  $(function() {
     $("#slider1").slider({
        animate : true,
        range : "min",
        value : 100,
        slide : function(event,ui){
           //console.log("move");
           $(".opaimg").css("opacity", ui.value/100);
           $("#opa").text(ui.value);
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
    <title>range opacity</title>
    <link rel="stylesheet" href="http://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css" type="text/css" />

    <script  src="http://code.jquery.com/jquery-latest.min.js"></script>
    <script src="http://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
  </head>
  <body>
    <h1>JQuery UI</h1>
    <h2>Slider</h2>

    <img alt="" src="https://cnet2.cbsistatic.com/img/HFJgghjpo8khVJJRRTjO6dBo1ys=/fit-in/570x0/2011/01/18/2a55ad4f-f0f4-11e2-8c7c-d4ae52e62bcc/HTML5_Logo_550px.png" class="opaimg">
    <img alt="" src="http://www.desartlab.com/wp-content/uploads/2015/10/css3-search-box.png" class="opaimg">
    <img alt="" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Badge_js-strict.svg/2000px-Badge_js-strict.svg.png" class="opaimg">

    <p>
      Slider의 키를 좌우로 이동시키면, 이미지의 투명도를 조정할 수 있습니다.
    </p>

    <div id="slider1" style="width: 250px"></div>

    <br>

    <p id="opa"></p>

    <script type="text/javascript">
    $(function() {
       $("#slider1").slider({
          animate : true,
          range : "min",
          value : 100,
          slide : function(event,ui){
             //console.log("move");
             $(".opaimg").css("opacity", ui.value/100);
             $("#opa").text(ui.value);
          }
       });
    });
    </script>

  </body>
</html>

```
