---
layout: post
title: "[javascript] 날짜 함수"
categories:
  - javascript
tags:
  - javascript
  - Date()
  - 날짜
---

javascript에서 사용하는 날짜 관련 객체와 함수에 대해 학습합니다.


<br>


### 날짜

```javascript
var date = new Date();
var date2 = new Date(99, 5,24,11,33,20,0);
var date3 = new Date("October 12, 2018 12:11:22");
```

```
Thu Jan 18 2018 10:32:29 GMT+0900 (대한민국 표준시)

Thu Jun 24 1999 11:33:20 GMT+0900 (대한민국 표준시)

Fri Oct 12 2018 12:11:22 GMT+0900 (대한민국 표준시)
```
- 현재 날짜를 가져올 수 있다.
- 원하는대로 날짜를 커스텀할 수 있다.

<br>


```javascript
date3.getDay(); // 요일을 숫자로 받아온다.
date3.getMonth()+1; // 월을 받아온다.(0부터 시작)
date3.getFullYear(); // 년도를 받아온다.
date3.getDate(); // 일을 받아온다.
date3.getHours(); // 시간을 받아온다.
date3.getMinutes(); // 분을 받아온다.
date3.getSeconds(); // 초를 받아온다.
```

```
5
10
2018
12
12
11
22
```

- 날짜의 정보를 받아올 수 있다.
