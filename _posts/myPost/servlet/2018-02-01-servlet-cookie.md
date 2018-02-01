---
layout: post
title: '[Servlet] Cookie 쿠키'
categories:
  - servlet
tags:
  - servlet
  - cookie
  - 쿠키
---



cookie는 웹클라이언트에 일정량의 데이터를 저장할 수 있는 기술이다.
서블렛의 java코드를 사용하여 cookie를 저장하는 방법을 살펴본다.


## 쿠키

- 저장매개체, 저장공간이다.
- 클라이언트에서 제공하는 저장공간이다.
- 우리가 사용하는 하드웨어 특정 공간에 저장된다.
- 요즘은 쿠키에 많이 저장한다.
- 한글은 동작을 하지 않는다.
- 세션은 객체도 저장이 가능하지만, 쿠키는 문자열만 저장이 가능하다.




## 쿠키 생성하기


- 쿠키는 하나의 자바 객체이다.
- key : value 한쌍으로 제공된다.
- servlet 코드에서 쿠키 객체를 생성하여 resp(리스폰)에 추가할 수 있다.
- ```addCookie()``` 메소드를 통해 생성된 쿠키를 저장할 수 있다.



```java
Cookie cookie1 = new Cookie("visited", "1");
resp.addCookie(cookie);

Cookie cookie2 = new Cookie("cookie1", "123");
resp.addCookie(cookie);
```

<br>



## 쿠키 가져오기

- 저장된 쿠키를 전부 가져올 수 있다.
- 저장된 모든 쿠키는 **배열** 로 가져올 수 있기 때문에 반복문을 통해 출력이 가능하다.


#### DispCookie.java

```java
Cookie[] cookies = req.getCookies();

if(cookies!=null) {
  Arrays.stream(cookies).forEach(cookie -> {
    sb.append("<p>");
    sb.append(cookie.getName());
    sb.append(" : ");
    sb.append(cookie.getValue());
    sb.append("</p>");
  });
}else {
  sb.append("<p>Can't find Cookie</p>");
}
```


- ```request```객체에 ```.getCookies()```메소드는 존재하는 모든 쿠키를 배열로 가져온다.
- ```.getName()```, ```.getValue()``` 각각의 메소드로 쿠키의 이름과 값을 가져올 수 있다.





## 쿠키 삭제하기


- ```.setMaxAge()``` 메소드는 활성 상태 시간을 나타낸다.
- 쿠키의 활성시간을 0으로 만들면 추가하는 순간 날아간다.
- 삭제할때 ```.setMaxAge()``` 메소드를 활용한다.


#### 현존하는 모든 쿠키 삭제

```java
// cookie 삭제
Cookie[] cookiees = req.getCookies();
if(cookies!=null) {
  Arrays.stream(cookiees).forEach(cok -> {
    cok.setMaxAge(0);
    resp.addCookie(cok);
  });
}
```

- 모든 쿠키의 활성 시간을 0으로 맞춘다.(==삭제)


#### 특정 쿠키 삭제


```java
// 특정 cookie삭제
Cookie cokies = new Cookie("cookiename", null);
cokies.setMaxAge(0);
resp.addCookie(cokies);
```

- 이름이 ```cookiename```인 쿠키의 활성 시간을 0으로 맞춘다.(==삭제)
