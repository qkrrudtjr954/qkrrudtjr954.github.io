---
layout: post
title: '[ajax] .load()를 사용한 ajax의 기본 개념'
categories:
  - ajax
tags:
  - Ajax
  - .load()
---


jQuery에서 제공하는 기본 함수 ```.load```를 사용하여 ajax의 기본 개념과 동작 원리를 알아봅니다.



## ajax의 개념원리


- 아래의 예제는 진짜 ajax는 아니지만 ajax의 개념을 쉽게 이해하기 위해 준비했다.
- ```.load()``` 함수는 다른 파일을 현재 페이지로 로드하는 함수 입니다.


<br><br>


#### 1. page 내부 데이터 불러오기

```js
$(document).ready(function () {
    $('button#testBtn1').on('click', function () {
        $('#result').load('test.html #session01');
    })
})
```

- 다른 페이지인 ```test.html```에 있는 ```<p id="session01"></p>``` 태그에 접근해서 데이터를 로드한다.


<br><br>


#### 2. parameter 세팅해서 불러오기


###### test.jsp 내부

```
t1=<%=request.getParameter("t1")%>
t2=<%=request.getParameter("t2")%>
```



```js
$(document).ready(function () {
    $('button#testBtn1').on('click', function () {
        $('#result').load('test.jsp', "t1=Hello&t2=World");
    })
})
```

- t1과 t2를 파라미터로 설정하고 test.jsp를 load한다.


<br>


```js
$(document).ready(function () {
    $('button#testBtn1').on('click', function () {
        $('#result').load('test.jsp', {t1:"hello", t2:"world"} );
    })
})
```

- t1과 t2를 ***json*** 방식으로 사용하는 것도 가능하다.


<br><br>

#### 3. callback 함수를 통한 데이터 로드


```js
$(document).ready(function () {
    $('button#testBtn1').on('click', function () {
        $('#result').load('test.html', function (data, status, xhr) {
            $('#result').append('<p>data='+data+'</p><br>');
            $('#result').append('<p>status='+status+'</p><br>');
            $('#result').append('<p>xhr='+xhr+'</p><br>');
            $('#result').append('<p>xhr.status='+xhr.status+'</p><br>');
            $('#result').append('<p>xhr.statusText='+xhr.statusText+'</p><br>');
        });
    })
})
```

- callback 함수를 설정할 수 있다.
- ```test.html```을 로드하면서 ```data```, ```status```, ```xhr```의 정보를 함께 가져온다.
- ```data``` : 데이터를 저장하는 객체
- ```status``` : 상태를 갖고 있는 객체
  - 성공하면  ```"success"``` 문자열을 반환한다.
  - 에러가 발생하면  ```"error"``` 문자열을 반환한다.
- ```xhr``` : XMLHttpRequest 객체, 상태와 상태 코드를 갖고 있는 객체
