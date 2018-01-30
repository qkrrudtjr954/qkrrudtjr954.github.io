---
layout: post
title: "[json] 파싱하기"
categories:
  - json
tags:
  - json
  - parsing
  - parse
---

데이터 뭉치에서 원하는 데이터만을 추출하는 것을 파싱이라고 한다.
웹 페이지 에서 javascript를 사용하여 json을 읽고 원하는 데이터만을 추출(파싱)할 수 있다.

<br>


## json 텍스트 파싱

- 웹페이지에서 response로 주어지는 json은 대부분 text형으로 전달이 되기 때문에 ***JSON으로 형변환이 필요하다.***

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>JSON parsing</title>
  </head>
  <body>
    <p id="demo"></p>

    <script type="text/javascript">
      // json이 문자열로 주어졌다.
      var text = '{"name" : "parker", "address" : "chung ju -si",	"phone" : "123-4567"}';

      // json 문자열을 json으로 형변환 한다.
      var obj = JSON.parse(text);

      document.getElementById('demo').innerHTML = obj.name+" <b>"+obj.address+"</b> "+obj.phone;
    </script>
  </body>
</html>
```

- JSON객체가 제공하는 ```.parse()``` 메소드로 텍스트를 json으로 변환한다.




## 외부 json파일 파싱


- javascript로 외부 json파일을 읽고 원하는 데이터를 파싱한다.
- 추합한 데이터를 html에 보여주는 간단한 예제를 제시한다..

#### data.json

```json
[
  {
    "firstname":"kyung seok",
    "lastname":"park"
  },
  {
    "firstname":"hun seok",
    "lastname":"kim"
  },
  {
    "firstname":"kyung chul",
    "lastname":"hong"
  }
]
```



#### index.html

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>

  </head>
  <body>
    <p id="demo"></p>

    <script type="text/javascript">
      var xmlhttp = new XMLHttpRequest();
      var url = "data.json";

      xmlhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
          myfunc(xmlhttp.responseText);
        }
      };
      xmlhttp.open("GET", url, true);
      xmlhttp.send();

      function myfunc(resp) {
        var arr = JSON.parse(resp);
        var out = "<table border='1'>";

        for (var i = 0; i < arr.length; i++) {
          out+=
            "<tr>"+
            "<td>"+ arr[i].firstname + "</td>" +
            "<td>"+ arr[i].lastname + "</td>" +
            "</tr>";
        }
        document.getElementById('demo').innerHTML = out;
      }
    </script>
  </body>
</html>
```


- json을 파싱하기 위해 ***xml*** 을 추출하는 ***XMLHttpRequest*** 객체를 사용한다.
- ```xmlhttp.responseText``` 는 json을 텍스트 형태로 반환한다.
- ```myfunc()```는 json 텍스트를 json으로 파싱한다.
