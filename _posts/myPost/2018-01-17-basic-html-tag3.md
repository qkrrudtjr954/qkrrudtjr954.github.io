---
layout: post
title: "HTML 기본 태그3"
categories:
  - HTML
tags:
  - HTML
  - HTML 기본 태그
  - checkbox
  - radio button
  - select
  - textarea
  - button
  - video
---


html 에서 가장 자주 사용되는 태그에 대해 공부합니다.

### check box

- 복수로 선택이 가능하다.
- name을 동일하게 사용하는 것이 가능하다.
- value 값은 문자열이다.
  - 숫자가 아니여도 된다.


<div class="example">
<form class="" action="#" method="post">
  <input type="checkbox" name="checkbox" value="1">Fashion
  <input type="checkbox" name="checkbox" value="2">Music
  <input type="checkbox" name="checkbox" value="3">Game
  <input type="checkbox" name="checkbox" value="4">Fishing
  <input type="submit" name="" value="submit">
</form>
</div>


  <br>

```html
<form class="" action="index.html" method="post">
  <input type="checkbox" name="checkbox" value="1">Fashion
  <input type="checkbox" name="checkbox" value="2">Music
  <input type="checkbox" name="checkbox" value="3">Game
  <input type="checkbox" name="checkbox" value="4">Fishing
  <input type="submit" name="" value="submit">
</form>
```


### radio button

- 복수로 선택이 불가능하다.
- ```checked``` 속성을 사용하면 기본값으로 체크되어 있다.


<div class="example">
<form action="#">
  <input type="radio" name="radio" value="apple" checked>  Apple
  <input type="radio" name="radio" value="peach">  Peach
  <input type="radio" name="radio" value="grape">  Grape
  <input type="submit" value="submit">
</form>
</div>


<br>

```html
<form action="#">
	<input type="radio" name="radio" value="apple" checked>  Apple
	<input type="radio" name="radio" value="peach">  Peach
	<input type="radio" name="radio" value="grape">  Grape
	<input type="submit" value="submit">
</form>
```


### select

- 특정 값을 선택할 수 있다.
- ```optgroup```을 설정하면 옵션을 그룹화할 수 있다.
  - 그룹이 없다면 ```option```만 사용하면 된다.


<div class="example">
<form action="#">
  <select name="car">
    <optgroup label="test1">
      <option value="1">hello1</option>
      <option value="2">hello2</option>
      <option value="3">hello3</option>
    </optgroup>
    <optgroup label="test2">
      <option value="1">hello1</option>
      <option value="2">hello2</option>
      <option value="3">hello3</option>
    </optgroup>
  </select>
</form>
</div>

<br>

```html
<form action="NewFile.jsp">
	<select name="car">
		<optgroup label="test1">
			<option value="1">hello1</option>
			<option value="2">hello2</option>
			<option value="3">hello3</option>
		</optgroup>
		<optgroup label="test2">
			<option value="1">hello1</option>
			<option value="2">hello2</option>
			<option value="3">hello3</option>
		</optgroup>
	</select>
</form>
```




### textarea

- 글을 작성할 수 있는 공간을 제공한다.

<div class="example">
  <form class="" action="#" method="post">
    <textarea name="textarea" rows="8" cols="50"></textarea>
    <br>
    <input type="submit" name="submit" value="submit">
  </form>
</div>


<br>



```html
<form class="" action="#" method="post">
  <textarea name="textarea" rows="8" cols="50"></textarea>
  <input type="submit" name="submit" value="submit">
</form>

```


### button

- submit 이 아닌 button 타입이 존재한다.

<br>

<div class="example">
  <button type="button" name="button" onclick="alert('Button!')">button</button>
</div>

<br>

```html
<button type="button" name="button" onclick="alert('Button!')">button</button>
```


### video

- html5에서는 video를 쉽게 삽입할 수 있는 태그를 제공한다.
- 동일한 디렉토리에 있는 파일을 삽입한다.

```html
<video width="400" controls="controls">
  <!-- mp4 movie file -->
  <source src="mov_bbb.mp4" type="video/mp4">
  <!-- ogg movie file -->
  <source src="mov_bbb.ogg" type="video/ogg">
</video>
```


<br>


#### 유튜브 동영상을 삽입하는 방법


- 유튜브 동영상 **우클릭** -> **소스코드 복사**
- html 파일에 붙여넣기
- iframe 으로 동영상이 삽입된다.



```html
<iframe width="854" height="480" src="https://www.youtube.com/embed/9gTw2EDkaDQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
```


<iframe width="854" height="480" src="https://www.youtube.com/embed/9gTw2EDkaDQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>



### html5 시간 관련

- html5에서는 시간 관련 태그를 제공한다.

<div class="example">
<form action="#">
  <fieldset>
    <legend><b>날짜 시간 관련</b></legend>
    datetime <br>
    <input type="datetime" name="datetime"><br>
    datetime-local <br>
    <input type="datetime-local" name="datetimelocal"><br>
    date <br>
    <input type="date" name="date" min="2012-02-01" max="2020-02-01"><br>
    month <br>
    <input type="month" name="month"><br>
    week<br>
    <input type="week" name="week"><br>
    time <br>
    <input type="time" name="time" min="07:00" max="24:00"><br>			
  </fieldset>
  <input type="submit">
</form>
</div>

<br>

```html
<form action="#">
  <fieldset>
    <legend><b>날짜 시간 관련</b></legend>
    datetime <br>
    <input type="datetime" name="datetime"><br>
    datetime-local <br>
    <input type="datetime-local" name="datetimelocal"><br>
    date <br>
    <input type="date" name="date" min="2012-02-01" max="2020-02-01"><br>
    month <br>
    <input type="month" name="month"><br>
    week<br>
    <input type="week" name="week"><br>
    time <br>
    <input type="time" name="time" min="07:00" max="24:00"><br>			
  </fieldset>
  <input type="submit">
</form>
```
