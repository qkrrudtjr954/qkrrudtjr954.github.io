---
layout: post
title: "[javascript] DOM 예제"
categories:
  - javascript
tags:
  - javascript
  - DOM
  - Document Object Model
  - innerHTML
  - childNodes
  - appendChild
  - insertBefore
  - remove
  - removeChild
  - getElementsByTagName
---

DOM을 활용하는 방법에 대해 몇가지 함수(기능)에 대해 학습합니다.

<br>

---

<br>


## .innerHTML

- 말 그대로 DOM객체 안에 있는 html 코드를 가져온다.

<br>

<div class="example">
  <div id="exam">
    <p id="exam2">Hello World!!</p>
  </div>

  <p id="exam3"></p>
  <p id="exam4"></p>

  <button type="button" name="button" onclick="func()">Btn</button>

  <script type="text/javascript">
  function func() {
    var innerDiv = document.getElementById('exam').innerHTML;
    document.getElementById('exam3').innerHTML=innerDiv;

    var innerP = document.getElementById('exam2').innerHTML;
    document.getElementById('exam4').innerHTML=innerP;
  }
  </script>
</div>



#### Exam1.html

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exam1</title>
  </head>
  <body>
    <div id="exam">
      <p id="exam2">Hello World!!</p>
    </div>

    <p id="exam3"></p>
    <p id="exam4"></p>

    <button type="button" name="button" onclick="func()">Btn</button>
    <script src="Exam1.js" charset="utf-8"></script>
  </body>
</html>
```



<br>



#### Exam1.js

```javascript
function func() {
  // innerDiv = <p id="exam2">Hello World!!</p>
  var innerDiv = document.getElementById('exam').innerHTML;
  document.getElementById('exam3').innerHTML=innerDiv;

  // innerP = Hello World!!
  var innerP = document.getElementById('exam2').innerHTML;
  document.getElementById('exam4').innerHTML=innerP;
}
```


<br>


- ```innerDiv```는 ```div``` 태그 안에 있는 html 코드를 가져온다.
- ```innerP```는 ```p``` 태그 안에 있는 html 코드를 가져온다.
  - ```p```태그 안에 텍스트만 있기 때문에 텍스트를 가져온 것 처럼 보인다.
  - 사실은 텍스트가 아닌 html Element를 가져온다.


<br>



---


<br>


## .childNodes


- 태그 안에 있는 자식 태그와 모든 노드를 전부 배열 형태로 가져온다.
- 노드는 html 태그 뿐만 아니라 일반 텍스트도 나타낼 수 있다.

<div id="intro">
<p> Hello </p>
<p> javascript </p>
<p> World </p>
<p> !!! </p>
</div>

<p id="demo"></p>

<button type="button" name="button" onclick="func2()">.childNodes()</button>

<script type="text/javascript">
function func2() {
  var myPtags = document.getElementById('intro').childNodes;
  // div 내부에 있는 4개의 p태그와 \n 문자를 배열로 저장한다.

  document.getElementById('demo').innerHTML = myPtags[1].innerHTML;
  // div 내부에 있는 2번째 태크의 text 값을 demo에 삽입한다.
}
</script>

<br>



#### Exam2.html


```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exam2</title>
  </head>
  <body>
    <div id="intro">
      <p> Hello </p>
      <p> javascript </p>
      <p> World </p>
      <p> !!! </p>
    </div>

    <p id="demo"></p>

    <button type="button" name="button" onclick="func()"></button>
  </body>
  <script src="Exam2.js" charset="utf-8"></script>
</html>
```


<br>




#### Exam2.js


```javascript
function func() {
  var myPtags = document.getElementById('intro').childNodes;
  // div 내부에 있는 4개의 p태그와 \n 문자를 배열로 저장한다.

  document.getElementById('demo').innerHTML = myPtags[1].innerHTML;
  // div 내부에 있는 2번째 태크의 text 값을 demo에 삽입한다.
}

```

- 함수를 호출하면 ```<p id="demo"></p>``` 내부를 ```myPtags[1].innerHTML```로 채운다.

<br>

#### myPtags 에 포함된 요소들

```
myPtags[0] = "\n";
myPtags[1] = "<p> Hello </p>";
myPtags[2] = "\n";
myPtags[3] = "<p> javascript </p>";
myPtags[4] = "\n";
myPtags[5] = "<p> World </p>";
myPtags[6] = "\n";
myPtags[7] = "<p> !!! </p>";
myPtags[8] = "\n";
```


- 노드는 html 태그를 제외하고 일반 텍스트도 객체로 잡는다.
- 따라서, 개행 문자도 배열에 포함된다.
- [Node와 Element의 차이](https://stackoverflow.com/questions/9979172/difference-between-node-object-and-element-object)



<br>


---



<br>



## .appendChild, .insertBefore


- 특정 DOM 객체에 태그를 추가할 수 있다.  (.appendChild)
- 특정 DOM 객체 내부 원하는 위치에 태그를 추가할 수 있다.  (.insertBefore)


<div class="example">
  <div id="exam5">
    <p>first</p>
    <p>second</p>
    <p id="exam6">third</p>
    <p>fourth</p>
  </div>

  <button type="button" name="button" onclick="append()">.appendChild()</button>
  <button type="button" name="button" onclick="before()">.insertBefore()</button>
</div>

<script type="text/javascript">
function append() {
  var divDOM = document.getElementById('exam5'); // div DOM
  var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
  newPtag.innerHTML = 'fifth'; // 내부를 채운다.

  divDOM.appendChild(newPtag);  // div DOM에 더한다.
}

function before() {
  var divDOM = document.getElementById('exam5'); // div DOM
  var ptag = document.getElementById('exam6');

  var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
  newPtag.innerHTML = 'fifth'; // 내부를 채운다.

  divDOM.insertBefore(newPtag, ptag);  // div DOM에 더하는데 ptag 앞에 더한다.
}
</script>




<br>




#### Exam3.html



```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Exam3</title>
  </head>
  <body>
    <div id="exam5">
      <p>first</p>
      <p>second</p>
      <p id="exam6">third</p>
      <p>fourth</p>
    </div>

    <button type="button" name="button" onclick="append()">.appendChild()</button>
    <button type="button" name="button" onclick="before()">.insertBefore()</button>

    <script src="Exam3.js" charset="utf-8"></script>
  </body>
</html>
```



<br>



#### Exam3.js (.appendChild)


```javascript
function append() {
  var divDOM = document.getElementById('exam5'); // div DOM
  var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
  newPtag.innerHTML = 'fifth'; // 내부를 채운다.

  divDOM.appendChild(newPtag);  // div DOM에 더한다.
}
```


<br>



#### Exam3.js (.insertBefore)


- 태그를 삽입하는 위치를 지정할 수도 있다.



```javascript
function before() {
  var divDOM = document.getElementById('exam5'); // div DOM
  var ptag = document.getElementById('exam6');

  var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
  newPtag.innerHTML = 'fifth'; // 내부를 채운다.

  divDOM.insertBefore(newPtag, ptag);  // div DOM에 더하는데 ptag 앞에 더한다.
}
```




<br>



---

<br>



## .remove, .removeChild

- 특정 DOM 객체를 지울 수 있다.
- 특정 DOM 객체의 자식 노드를 지울 수 있다.

<div class="example">
  <div id="exam7">
    <p>first</p>
    <p>second</p>
    <p id="exam8">third</p>
    <p>fourth</p>
  </div>

  <p id="exam9">I want to disappear</p>

  <button type="button" name="button" onclick="removeChild()">.removeCh()</button>
  <button type="button" name="button" onclick="remove()">.remove()</button>
</div>

<script type="text/javascript">
function removeCh() {
  var divDOM = document.getElementById('exam7');
  var ptag = document.getElementById('exam8');

  divDOM.removeChild(ptag);
}

function remove() {
  var ptag2 = document.getElementById('exam9');
  ptag2.remove();    
}
</script>


<br>



#### Exam4.html

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Exam4</title>
  </head>
  <body>
    <div id="exam7">
      <p>first</p>
      <p>second</p>
      <p id="exam8">third</p>
      <p>fourth</p>
    </div>

    <p id="exam9">I want to disappear</p>

    <button type="button" name="button" onclick="removeChild()">.removeChild()</button>
    <button type="button" name="button" onclick="remove()">.remove()</button>
  </body>
  <script src="Exam4.js" charset="utf-8"></script>
</html>
```


<br>



#### Exam4.js

```javascript
function removeChild() {
  var divDOM = document.getElementById('exam7');
  var ptag = document.getElementById('exam8');

  divDOM.removeChild(ptag);
}

function remove() {
  var ptag2 = document.getElementById('exam9');
  ptag2.remove();    
}
```


- ```.remove()``` 는 특정 DOM 객체를 삭제한다.
- ```.removeChild()``` 는 특정 DOM 객체의 자식 노드를 삭제한다.


<br>



---

## .getElementsByTagName

- 특정 태그를 갖는 DOM을 배열 형태로 가져온다.

<div class="example">
  <div id="exam10">
    <p>hello</p>
    <p>world</p>
  </div>

  <div id="exam11">
    <span>javascript is good!</span>
    <div id="exam12">
      <span>I'm inner div!</span>
    </div>
  </div>

  <p id="demo2"></p>

  <button type="button" name="button" onclick="func5()">.getElementsByTagName()</button>
</div>

<script type="text/javascript">
function func5() {
  // getElementsByTagName(tagname)
  // 해당 태그 이름을 갖는 모든 태그를 가져온다.
  var divDOMs = document.getElementsByTagName('div');
  var obj = document.getElementById('demo2');

  for (var i = 0; i < divDOMs.length; i++) {
    obj.innerHTML = obj.innerHTML + "\n" + divDOMs[i];
  }
}
</script>

<br>




#### Exam5.html

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Exam5</title>
  </head>
  <body>
    <div id="exam10">
      <p>hello</p>
      <p>world</p>
    </div>

    <div id="exam11">
      <span>javascript is good!</span>
      <div id="exam12">
        <span>I'm inner div!</span>
      </div>
    </div>

    <p id="demo2"></p>

    <button type="button" name="button" onclick="func5()">.getElementsByTagName()</button>
    <script src="Exam5.js" charset="utf-8"></script>
  </body>
</html>
```


<br>



#### Exam5.js

```javascript
function func5() {
  // getElementsByTagName(tagname)
  // 해당 태그 이름을 갖는 모든 태그를 가져온다.
  var divDOMs = document.getElementsByTagName('div');
  var obj = document.getElementById('demo2');

  for (var i = 0; i < divDOMs.length; i++) {
    obj.innerHTML = obj.innerHTML + "<br>" + divDOMs[i];
  }
}
```


- 코드내 모든 ```div``` 태그를 불러온다.
