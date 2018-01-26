---
layout: post
title: '[jQuery] .attr()을 사용한 속성 변경'
categories:
  - jQuery
tags:
  - jQuery
---

jQuery의 ```.attr()``` 메소드를 사용하여 태그의 속성값을 수정할 수 있다.




<br>






## .attr()을 사용한 속성 변경

- img 태그의 src나 a 태그의 href와 같은 속성을 변경할 수 있는 함수이다.
- a태그의 href 속성을 변경하여 다른 홈페이지로 링크되도록 한다.
- img태그의 src 속성을 변경하여 다른 사진이 표시되도록 한다.


<div class="example">
  <a href="https://qkrrudtjr954.github.io" id="github">qkrrudtjr954</a>
  <button type="button" name="button" id="btn4">Change URL</button>

  <br>
  <br>

  <img id="img" src="https://i.imgur.com/YR2TfpH.jpg" alt="" width="400px" height="300px">

  <br>

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

  <br>
  <br>

  <img id="img" src="https://i.imgur.com/YR2TfpH.jpg" alt="" width="400px" height="300px">

  <br>

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

<br>

## .attr()을 사용하여 여러개의 속성을 변경

- 하나의 속성이 아닌 여러개의 속성을 한번에 바꿀때 ***json*** 을 이용한다.
- 버튼을 클릭하면 ```naver.com``` 의 링크와 타이틀을 변경한다.



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
