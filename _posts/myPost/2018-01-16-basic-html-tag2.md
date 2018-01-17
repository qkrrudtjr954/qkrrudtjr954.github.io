---
layout: post
title: "[HTML] 기본 태그2"
categories:
  - HTML
tags:
  - HTML
  - HTML 기본 태그
  - ul
  - ol
  - iFrame
  - form
---


html 에서 가장 자주 사용되는 태그에 대해 공부합니다.

<br>


## List

### ul

- 순서가 없는 목록
- Unordered List

<div class="example">
  <ul>
    <li>홍길동</li>
    <li>김똥개</li>
    <li>이기영</li>
  </ul>
<div>

```html
<ul>
  <li>홍길동</li>
  <li>김똥개</li>
  <li>이기영</li>
</ul>
```

- 리스트의 type 을 지정할 수 있다.

<div class="example">
  <ul style="list-style-type: square">
    <li>홍길동</li>
    <li>김똥개</li>
    <li>이기영</li>
  </ul>
</div

```html
<ul style="list-style-type: square">
  <li>홍길동</li>
  <li>김똥개</li>
  <li>이기영</li>
</ul>
```

- 리스트 스타일 타입의 종류
  - disc : 기본 타입
  - circle : 중간이 비어있는 원
  - square : 사각형
  - none : 스타일을 적용하지 않음


### ol

- 순서가 있는 목록
- Ordered List

<br>

<div class="example">
  <ol type="1">
    <li>홍길동</li>
    <li>김똥개</li>
    <li>이기영</li>
  </ol>
</div>

```html
<ol type="1">
  <li>홍길동</li>
  <li>김똥개</li>
  <li>이기영</li>
</ol>
```

- ol type 의 종류
  - 1 : 숫자
  - I : 이태릭체
  - a, A : 알파벳



```html
<ol start="2"> <!-- html5 코드 -->
  <li>홍길동</li>
  <li>김똥개</li>
  <li>이기영</li>
</ol>
```

<div class="example">
  <ol start="2"> <!-- html5 코드 -->
    <li>홍길동</li>
    <li>김똥개</li>
    <li>이기영</li>
  </ol>
</div>

- 순서가 시작하는 번호를 지정할 수 있다.
- html5에서 사용가능하다.



### dl, dd, dt

- html5에서 등장한 리스트
- 리스트를 설명할 수 있는 태그가 존재한다.

<br>

<div class="example">
  <dl class="">
    <dt>커피</dt>
      <dd>아메리카노오~</dd>
    <dt>홍차</dt>
      <dd>빨간색 차</dd>
    <dt>우유</dt>
      <dd>하얀색 음료</dd>
  </dl>
</div>

<br>


```html
<dl class="">
  <dt>커피</dt>
    <dd>아메리카노오~</dd>
  <dt>홍차</dt>
    <dd>빨간색 차</dd>
  <dt>우유</dt>
    <dd>하얀색 음료</dd>
</dl>
```


<br>

---

<br>



### iFrame

- 웹페이지 안에 웹페이지

```html
<iframe src="NewFile.html" width="500" height="500">iframe</iframe>
<iframe src="https://www.google.co.kr" width="500" height="500">
  iframe
</iframe>
```


<br>

---

<br>


### form

- 사용자 입력을 수집해서 Server(Web) 에 전달하는데 사용되는 태그

<br>

<div class="example">
  <form class="" action="index.html" method="post">
    firstname <br>
    <input type="text" name="firstname">
  </form>
</div>

<br>

```html
<form class="" action="index.html" method="post">
  firstname <br>
  <input type="text" name="firstname">
</form>
```

- html5 에서 더많은 input의 타입을 제공한다.

<br>
<div class="example">
  <form action="#none">
    <!-- 숫자를 입력할 수 있는 input -->
    숫자 <input type="number" name="num" min="1" max="5"><br>
    <!-- 날짜를 선택할 수 있는 input -->
    날짜 <input type="date" name="date"><br>
    <!-- 색을 선택할 수 있는 input -->
    색깔 <input type="color" name="color"><br>
    <!-- 범위를 입력할 수 있는 input -->
    범위 <input type="range" name="range"><br>
  </form>
</div>

<br>

```html
<form action="#none">
  <!-- 숫자를 입력할 수 있는 input -->
  <input type="number" name="num" min="1" max="5">
  <!-- 날짜를 선택할 수 있는 input -->
  <input type="date" name="date">
  <!-- 색을 선택할 수 있는 input -->
  <input type="color" name="color">
  <!-- 범위를 입력할 수 있는 input -->
  <input type="range" name="range">
</form>
```
