---
layout: post
title: "HTML 기본 태그"
categories:
  - HTML
tags:
  - HTML
  - HTML 기본 태그
---

html 에서 가장 자주 사용되는 태그에 대해 공부합니다.

<br>


### HTML이란?

- 웹 브라우져가 읽을 수 있는 언어이다.
- 각각의 태그(tag)로 구성되어 있다.
- Standard Tag는 기본 HTML 태그이다.
- 웹이 표시하는 표시용이다.
- 사용자 지정 tag(XML)이 있다.
- 데이터를 사용할 때 사용하는 태그이다.


### 주석문

```html
<!-- 이것은 주석문 입니다. -->
<!-- 실제 코드에는 표시가 되지 않습니다. -->
```

### 기본 규칙

- ```<태그명>  </태그명>```
- 태그의 시작과 끝이 있다.
- standard tag 와 xml tag 모두 동일한 규칙을 갖는다.

---

### head Tag


- ```<head> </head>```
- ```<html> </html>``` 태그 바로 뒤에 온다.
- 파일에 대한 기본적인 설정을 포함한다.
- 선언이나 초기화하는 코드가 들어간다.
- CSS, javascript 코드를 넣거나 임포트하는 코드를 넣는다.

### h1 Tag


- h는 heading 의 약자로 **머릿말** 을 나타낸다.


```html
<h1>h1 입니다.</h1>
<h2>h2 입니다.</h2>
<h3>h3 입니다.</h3>
<h4>h4 입니다.</h4>
<h5>h5 입니다.</h5>
<h6>h6 입니다.</h6>
```

### p Tag

- paragraph의 약자이다.
- 하나의 단락을 나타낸다.



```html
<p>
  안녕하세요.
  저는 Parker입니다.
  나이는 25살 입니다.
</p>
```

### br Tag

- break 의 약자이다.
- 태그가 있는 위치에서 띄어쓰기를 할 수 있다.



```html
안녕하세요. <br> Parker입니다.
```
```
안녕하세요.
Parker입니다.
```

### pre Tag

- 소스코드에서 보이는 데로 띄워준다.


```html
<pre>
  안
  녕하세
  요오?
  .
</pre>
```


```
안
녕하세
요오?
.
```

### hr Tag

- 라인을 삽입하는 코드
- ```<hr/>``` 코드 위치에 줄을 삽입한다.
- 닫는 코드가 존재하지 않는다.

---

### bold Tag

- 특정 글자에 bold 처리를 한다.



```html
이것은 <b>bold 글씨체 입니다.!!!</b>
이것은 <strong> strong 글씨체 입니다!!! </strong>
```


### i Tag

- 특정 글자를 italic 체로 만든다.

```html
이것은 <i>italic 글씨체 입니다.!!!</i>
```


### em Tag

- 특정 글자를 강조합니다.

```html
이것은 <em>강조</em> 글씨체 입니다!!!
```

### mark Tag

- 특정 글자를 마킹합니다. (형광펜 처리)

```html
mark 태그는 글자를 <mark>마킹 처리할 수 있습니다!!!!</mark>
```


### del Tag

- 특정 글자에 삭제 처리를 할 수 있습니다.

```html
이 글자는 <del>삭제 되었습니다.</del>
```

### sub Tag

- 아래 첨자를 나타낼 수 있습니다.

```html
이 글자는 <sub>아래첨자를</sub> 나타냅니다.
```

### sup Tag

- 위 첨자를 나타낼 수 있습니다.

```html
이 글자는 <sup>아래첨자를</sup> 나타냅니다.
```

<br>

---

<br>

### font Tag

- 폰트에 대한 설정을 할 수 있습니다.
- ***html5에서는 더이상 지원하지 않는다.***

```html
<font size="4" color="red">4사이즈의 빨간색 폰트로 글씨를 표시합니다. </font>
<font size="3">default 크기</font>
```

<br>

---

<br>

### div Tag

- 특정 코드를 하나의 묶음 처리를 할 수 있다.
- 범위를 묶어 특정 설정을 적용할 수 있다.
- div 안에 있는 모든 태그를 오른쪽 정렬한다.

```html
<p>저는 div 태그 밖에 있는 p태그 입니다.</p>

<div align="right">
  <p>저는 div 태그 안에 있는 p태그 입니다.</p>
  <font size="3">저는 div 태그 안에 있는 font 태그 입니다.</font>
</div>
```


<br>

---

<br>

### a Tag (anchor Tag)

- url로 이동이 가능하게 연결해주는 코드

```html
<a href="https://www.google.co.kr">구글로 이동!</a>

<a href="index2.html">index2로 이동!</a> <!-- index2.html 파일로 이동할 수 있다. -->
```

- 현재창에서 id값을 통해 이동이 가능하다.

```html
<p>
  <!-- chap4 라는 id값을 갖는 태그로 이동한다. -->
  <a href="#chap4">Chatper4로 이동</a>
</p>

<div class="chat" id="chap1">
  <p>this is chap1</p>
</div>
<div class="chat" id="chap2">
  <p>this is chap2</p>
</div>
<div class="chat" id="chap3">
  <p>this is chap3</p>
</div>

<!-- 이곳으로 이동한다. -->
<div class="chat" id="chap4">
  <p>this is chap4</p>
</div>

<div class="chat" id="chap5">
  <p>this is chap5</p>
</div>
<div class="chat" id="chap6">
  <p>this is chap6</p>
</div>
```



<br>

---

<br>


### img Tag

- 이미지를 삽입할 수 있는 코드
- src (source) 이미지가 있는 **상대 경로** 를 설정한다.
  - 동일한 폴더 내부에 사진이 존재해야 한다.
- alt (alternative) 이미지가 없을 경우 "이미지 없음" 이 출력된다.


```html
<!-- img tag -->
<img src="picture.png" alt="이미지 없음">
<!-- img 에 사이즈를 지정할 수 있습니다. -->
<img src="picture.png" alt="이미지 없음" width="200" height="200">
<!-- img 에 테두리를 지정할 수 있습니다. -->
<img src="picture.png" alt="이미지 없음" border="1px solid black">
<!-- img 를 정렬할 수 있다. -->
<img src="picture.png" alt="이미지 없음" align="left">
<br clear="left">
<img src="picture.png" alt="이미지 없음" align="right">
<br clear="right">
```

- img Tag는 a 태그와 함께 사용할 수 있다.

```html
<a href="http://www.google.co.kr" target="_blank">
  <img src="picture.png" alt="이미지 없음" width="200" height="200">
</a>
```



<br>

---

<br>


## table Tag

- table을 생성할 수 있다.
- table은 행(Table Row)과 열(Table Data)를 갖는다.
  - th : 열의 이름 (table header)
  - tr : 행
  - td : 열

```html
<table style="width: 100%;" border="2">
  <tr>
    <th>hello head</th>
    <th>world head</th>
    <th>!!!! head</th>
  </tr>
  <tr>
    <td>hello</td>
    <td>world</td>
    <td>!!!!</td>
  </tr>
  <tr>
    <td>hello</td>
    <td>world</td>
    <td>!!!!</td>
  </tr>
  <tr>
    <td>hello</td>
    <td>world</td>
    <td>!!!!</td>
  </tr>
</table>
```

- style Tag 로 table을 꾸밀 수 있다.

```html
<head>
<style type="text/css">
	table, tr{
		border:1px solid blue;
		/*border-collapse: collapse; /* 단선으로 */
		background-color: #ff0000;
	}
</style>

</head>
<body>
  <table border="1" style="width: 100%">
  	<tr>
  		<td>홍</td>
  		<td>길동</td>
  		<td>24</td>
  	</tr>
  	<tr>
  		<td>일</td>
  		<td>지매</td>
  		<td>22</td>
  	</tr>
  	<tr>
  		<td>임</td>
  		<td>꺽정</td>
  		<td>28</td>
  	</tr>
  </table>
</body>
```


<br>

---

<br>


### style Tag ( attribute로 속성값을 의미한다. )

- css 코드가 들어간다.
- 각 태그에 style을 지정할 수 있다.

```html
<body style="background:gray;">
  <h1 style="background:yellow;">This is colorful h1 tag!!!</h1>
  <h2 style="font-family:verdana;">Style tag can change font style!!!</h2>
  <h3 style="color:white;">Change font color</h3>
  <h4 style="text-align:center;">가운데 정렬</h4>
</body>
```

```html
<pre style="font-weight:200%;">
  pre 태크 안에 있는 모든 글의 크기를 2배로 키운다.
  style 속성은 다른 태그의 속성을 지정할 수 있다.
</pre>

<p style="color:red; font-family:verdana; font-weight:15px;">
  여러개의 style 속성을 한번에 지정하는 것도 가능하다.
</p>
```

- style tag를 사용할 수 있다.
- 위치는 **head Tag** 내부에 들어간다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style media="screen">
      .hello {
        font-family: verdana;
        size: 15px;
      }
    </style>
  </head>
  <body>
    <p class="hello">
      안녕하세요.
      verdana 15px font 를 사용하는 p 태그입니다.
    </p>
  </body>
</html>
```
