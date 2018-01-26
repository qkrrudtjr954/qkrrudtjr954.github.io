---
layout: post
title: '[jQuery] jQuery vs javascript'
categories:
  - jQuery
tags:
  - jQuery
  - Selector
  - 선택자
---


실제 코드를 통해 javascript와 jQuery의 차이를 확인해보자.

## javascript와 jQuery

- 실제 코드를 통해 javascript와 jQuery의 차이를 확인해보자.


<div class="example">
  <p id="demo">
    This is p tag.
    and id is 'demo'
  </p>

  <p id="demo2">
    This is p tag.
    and id is 'demo2'
  </p>

  <p class="cls">
    This is P tag.
    and class is 'cls'
  </p>

  <h1 class="cls">This is h1 tag and class is 'cls'</h1>

  <button type="button" onclick="myFunc()">Javascript Button</button>
  <button type="button" id="jqueryBtn">jQuery Button</button>


  <script type="text/javascript">
    function myFunc() {
      // demo2 글을 demo 글로 바꿈.
      var text = document.getElementById('demo').innerHTML;
      document.getElementById('demo2').innerHTML = text+' with javascript';

      // cls 클래스 글을 Hello world 로 바꿈.
      var num = document.getElementsByClassName('cls').length;
      for (var i = 0; i < num; i++) {
        document.getElementsByClassName('cls')[i].innerHTML='Hello javascript world';
      }
    }

    $(document).ready(function () {
      $('#jqueryBtn').click(function () {
        // demo2 글을 demo 글로 바꿈.
        var text = $('#demo').text();
        $('#demo2').text(text+' with jQuery');

        // cls 클래스 글을 Hello world 로 바꿈.
        $('.cls').text('Hello jQuery world');
      })
    });
  </script>
</div>



```html
<p id="demo">
  This is p tag.
  and id is 'demo'
</p>

<p id="demo2"></p>

<p class="cls">
  This is P tag.
  and class is 'cls'
</p>

<h1 class="cls">
  This is h1 tag
  and class is 'cls'
</h1>


<pre>
  <button type="button" onclick="myFunc()">Javascript Button</button>
  <button type="button" id="jqueryBtn">jQuery Button</button>
</pre>
```

#### javascript

```html
<script type="text/javascript">
  function myFunc() {
    // demo2 글을 demo 글로 바꿈.
    var text = document.getElementById('demo').innerHTML;
    document.getElementById('demo2').innerHTML = text + ' with javascript';

    // cls 클래스 글을 Hello world 로 바꿈.
    var num = document.getElementsByClassName('cls').length;
    for (var i = 0; i < num; i++) {
      document.getElementsByClassName('cls')[i].innerHTML='Hello javascript world';
    }
  }
</script>
```


#### jQuery

```html
<script type="text/javascript">
  $(document).ready(function () {
    $('#jqueryBtn').click(function () {
      // demo2 글을 demo 글로 바꿈.
      var text = $('#demo').text();
      $('#demo2').text(text+' with jQuery');

      // cls 클래스 글을 Hello world 로 바꿈.
      $('.cls').text('Hello jQuery world');
    })
  });
</script>
```

- **jQuery** 코드가 훨씬 간결하고 직관적이다.
