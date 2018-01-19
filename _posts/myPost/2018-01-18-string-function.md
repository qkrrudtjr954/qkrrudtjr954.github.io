---
layout: post
title: "[javascript] 문자열 함수"
categories:
  - javascript
tags:
  - javascript
  - 문자열 함수
  - function
  - string
---

javascript에서 문자열을 다루는 여러가지 함수를 제공합니다.



### 문자열 함수



```html
<p id="demo"></p>
<p id="p1">
  ntrary to popular belief, Lorem Ipsum is not simply
  random text. It has roots in a piece of classical Latin literature
  from 45 BC, making it over 2000 years old. Richard McClintock, a Latin
  professor at Hampden-Sydney College in Virginia, looked up one of the
  more obscure Latin words, consectetur, from a Lorem Ipsum passage, and
  going through the cites of the word in classical literature,
  discovered the undoubtable source. Lorem Ipsum comes from sections
  1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes
  of Good and Evil) by Cicero, written in 45 BC. This book is a treatise
  on the theory of ethics, very popular during the Renaissance. The
  first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from
  a line in section 1.10.32.
</p>
<p id="demo"></p>

<script type="text/javascript">
  var str = document.getElementById('p1').innerHTML;

  var indexOf = str.indexOf('popular');
  var lastIndexOf = str.lastIndexOf("Lorem");
  var search = str.search('belief');
  var slice = str.slice(4,10); //4~9 까지의 글자 출력
  var substring = str.substring(4, 10);
  var charAt = str.charAt(10); //1번지의 글자를 출력

  console.log(indexOf);
  console.log(lastIndexOf);
  console.log(search);
  console.log(slice);
  console.log(substring);
  console.log(charAt);
</script>
```


```
13
716
21
trary
trary
t
```



- ```.indexOf()``` : 해당 문자열이 있는 위치를 반환합니다.
- ```.lastIndexOf()``` : 해당 문자열이 있는 위치를 뒤에서 부터 찾아 반환합니다.
- ```.search()``` : 해당 문자열이 있는 위치를 반환합니다.
- ```.slice()``` : 앞 index부터 뒤 index까지의 문자열을 반환합니다.
- ```.substring()``` : 앞 index부터 뒤 index까지의 문자열을 반환합니다.
- ```.charAt()``` : 해당 인덱스의 문자를 반환합니다.
