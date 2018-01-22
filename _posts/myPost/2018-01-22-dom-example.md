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
    <script src="Exam1.js" charset="utf-8"></script>
  </body>
</html>
```



<br>



#### Exam1.js

```javascript
var innerDiv = document.getElementById('exam').innerHTML;
console.log(innerDiv);

var innerP = document.getElementById('exam2').innerHTML;
console.log(innerP);
```


<br>



#### 콘솔 결과


```
<p id="exam2">Hello World!!</p>
Hello World!!
```


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
  </body>
  <script src="Exam2.js" charset="utf-8"></script>
</html>
```


<br>




#### Exam2.js


```javascript
var myPtags = document.getElementById('intro').childNodes;
// div 내부에 있는 4개의 p태그와 \n 문자를 배열로 저장한다.

document.getElementById('demo').innerHTML = myPtags[1].innerHTML;
// div 내부에 있는 2번째 태크의 text 값을 demo에 삽입한다.
```

- 웹페이지가 로드 되면서 ```<p id="demo"></p>``` 내부를 ```myPtags[1].innerHTML```로 채운다.

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
    <div id="exam">
      <p>first</p>
      <p>second</p>
      <p id="exam2">third</p>
      <p>fourth</p>
    </div>
  </body>
  <script src="Exam3.js" charset="utf-8"></script>
</html>
```



<br>



#### Exam3.js (.appendChild)


```javascript
var divDOM = document.getElementById('exam'); // div DOM
var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
newPtag.innerHTML = 'fifth'; // 내부를 채운다.

divDOM.appendChild(newPtag);  // div DOM에 더한다.
```

```
first
second
third
fourth
fifth
```


<br>



#### Exam3.js (.insertBefore)


- 태그를 삽입하는 위치를 지정할 수도 있다.



```javascript
var divDOM = document.getElementById('exam'); // div DOM
var ptag = document.getElementById('exam2');

var newPtag = document.createElement('p');  // 새로운 p DOM 객체를 생성
newPtag.innerHTML = 'fifth'; // 내부를 채운다.

divDOM.insertBefore(newPtag, ptag);  // div DOM에 더하는데 ptag 앞에 더한다.
```


```
first
second
fifth
third
fourth
```


<br>



---

<br>



## .remove, .removeChild

- 특정 DOM 객체를 지울 수 있다.
- 특정 DOM 객체의 자식 노드를 지울 수 있다.


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
    <div id="exam">
      <p>first</p>
      <p>second</p>
      <p id="exam2">third</p>
      <p>fourth</p>
    </div>

    <p id="exam3">I want to disappear</p>
  </body>
  <script src="Exam4.js" charset="utf-8"></script>
</html>
```


<br>



#### Exam4.js

```javascript
var divDOM = document.getElementById('exam');
var ptag = document.getElementById('exam2');

divDOM.removeChild(ptag);

var ptag2 = document.getElementById('exam3');
ptag2.remove();

```

```
first
second
fourth
```

- ```.remove()``` 는 특정 DOM 객체를 삭제한다.
- ```.removeChild()``` 는 특정 DOM 객체의 자식 노드를 삭제한다.


<br>



---

## .getElementsByTagName

- 특정 태그를 갖는 DOM을 배열 형태로 가져온다.


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
    <div id="exam">
      <p>hello</p>
      <p>world</p>
    </div>

    <div id="exam2">
      <span>javascript is good!</span>
      <div id="exam3">
        <span>I'm inner div!</span>
      </div>
    </div>
  </body>
  <script src="Exam5.js" charset="utf-8"></script>
</html>
```


<br>



#### Exam5.js

```javascript
// getElementsByTagName(tagname)
// 해당 태그 이름을 갖는 모든 태그를 가져온다.
var divDOMs = document.getElementsByTagName('div');
console.log(divDOMs[0]);
console.log(divDOMs[1]);
console.log(divDOMs[2]);
```

```
<div id="exam">...</div>
<div id="exam2">...</div>
<div id="exam3">...</div>
```

- 코드내 모든 ```div``` 태그를 불러온다.
