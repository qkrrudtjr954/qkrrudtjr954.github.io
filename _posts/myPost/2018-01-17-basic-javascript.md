---
layout: post
title: "javascript의 Hello World"
categories:
  - javascript
tags:
  - javascript
---

모든 프로그래밍의 기초인 Hello World를 ***javascript*** 코드로 출력합니다.



### javascript with chrome

- 크롬 개발자 도구를 켜면 Console 탭에 들어간다.
- javascript console을 사용할 수 있다.
- ```console.log()``` 를 사용하면 콘솔에 출력을 할 수 있다.

```javascript
console.log('Hello World!');
```

```
Hello World!
```

<br>
<br>

### javascript with web(html)

- ```javascript```와 ```html``` 을 사용하여 웹에서 동작하는 스크립트 코드를 작성할 수 있다.
- 프로그램이 시작됨과 동시에 스크립트 코드가 로드된다.
- ```document.getElementById('demo')``` 코드로 ```p``` 태그에 대한 객체를 받아온다.
- ```p``` 태그 내부를 ```"Hello javascript World"```로 대체한다.


```html
<p id="demo"> This is P tag </p>

<script type="text/javascript">
	document.getElementById('demo').innerHTML = "Hello javascript World";
</script>
```


<br>
<br>

### DOM ( Document Object Model )

- document와 code를 이어주는 객체
- javascript 는 DOM을 기준으로 프로그래밍한다.


```javascript
document.getElementById("id") //DOM 객체를 받아온다.
```
