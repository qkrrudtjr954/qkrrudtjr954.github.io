---
layout: post
title: '[xml] 속성값 설정'
categories:
  - xml
tags:
  - xml
  - attribute
---

xml도 html처럼 attribute를 설정할 수 있다.
그리고 이 attribute로 값을 가져올 수 있다.



## attribute 설정

- xml코드에 attribute를 설정할 수 있다.
- 성별에 대한 정보를 attribute로 설정했다.


```xml
<friends>
  <friend sex="man">
    <name>park</name>
    <age>23</age>
    <phone>123-4567</phone>
  </friend>
  <friend sex="woman">
    <name>kyung</name>
    <age>34</age>
    <phone>123-4567</phone>
  </friend>
  <friend sex="man">
    <name>seok</name>
    <age>25</age>
    <phone>123-4567</phone>
  </friend>
</friends>
```




## 예제

- attribute의 설정으로 값을 가져올 수 있다.


#### sample2.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<clients>
  <client job="요리사">
    <number>1</number>
    <name>홍길동</name>
    <address>서울시</address>
    <visit>2012/12/01</visit>    
  </client>
  <client job="운전사">
    <number>2</number>
    <name>일지매</name>
    <address>부산시</address>
    <visit>2013/12/02</visit>    
  </client>
  <client job="프로그래머">
    <number>3</number>
    <name>임꺽정</name>
    <address>대구시</address>
    <visit>2014/12/01</visit>    
  </client>
</clients>
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
    <p id="demo">

      <script type="text/javascript">
        var xhttp = new XMLHttpRequest();
        xhttp.onreadystatechange = function() {
          if (this.readyState == 4 && this.status == 200) {
            myFunc(this);
          }
        };
        xhttp.open("GET", "sample2.xml", true);
        xhttp.send();

        // 값 전부 가져오기
        function myFunc(xml) {
          var x, i, txt, xmlDoc;

          xmlDoc = xml.responseXML;
          txt = "";

          x = xmlDoc.getElementsByTagName('client');

          // attributes 를 가져올수 있다.
          for(i=0; i<x.length; i++){
            txt += x[i].attributes.getNamedItem("job").nodeValue + "<br>";			
          }

          document.getElementById('demo').innerHTML = txt;
        }
      </script>
  </body>
</html>
```

- ```.attributes``` 를 사용하면 현재 태그에 설정된 **attribute** 들의 값을 가져올 수 있다.
- ```.getNamedItem(name)``` 을 사용하면 **name** 과 일치하는 **attribute** 값을 가져올 수 있다.
