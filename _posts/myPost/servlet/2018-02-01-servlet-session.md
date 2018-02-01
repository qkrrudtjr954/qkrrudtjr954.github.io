---
layout: post
title: '[Servlet] Session 세션'
categories:
  - servlet
tags:
  - servlet
  - session
---


session은 웹서버에 일정량의 데이터를 저장할 수 있는 기술이다.
서블렛의 java코드를 사용하여 session을 저장하는 방법을 살펴본다.



## 세션

- 저장매개체, 저장공간이다.
- 웹서버에 위치하고 데이터가 웹서버에 저장된다.
- 로그인한 정보가 세션에 저장할 때 많이 사용된다.
- 저장을 하는 기간을 지정할 수 있다.
- 한글은 동작을 하지 않는다.
- 내부는 파일로 관리 된다.
- object로 저장이 가능하다 (String, Integer, 여러가지 DTO 등)


## 세션 생성하기


- 서블렛에서 자바코드를 사용해 세션을 생성하고 값을 저장한다.


```java
HttpSession session = req.getSession();
HttpSession session = req.getSession(true);
```

- ```HttpSession``` ***이 존재하면 session을 반환하고 없으면 새로운 session을 생성한다.***
- 두 가지 모두 같은 뜻으로 사용된다.


<br>


```java
HttpSession session = req.getSession(false);
```

- ```HttpSession``` ***이 존재하면 session을 반환하고 없으면 null을 반환한다.***



<br>


## 세션에 저장하기

- ***세션에는 일반 문자열 뿐 아니라 Object 타입의 객체를 저장하는 것도 가능하다.***


#### 일반 자료형


```java
// 세션을 가져온다.
HttpSession session = req.getSession(true);
session.setAttribute("hello", "world");
session.setAttribute("intValue", 123);
```

- session에 world를 속성값으로 갖는 hello를 추가했다.
- 문자열 뿐 아니라 int형으로도 추가가 가능하다.


#### Object 저장하기


```java
// human 객체 생성
Human human = new Human("parker", 26, 178);

// 세션을 가져온다.
HttpSession session = req.getSession(true);
session.setAttribute("parker", human);
```


- Human 객체를 parker라는 이름으로 세션에 저장했다.





## 세션에서 값 가져오기




- 세션에 저장되어 있는 값을 가져올 수 있다.
- 세션에 저장된 값은 ```.getAttribute()``` 함수를 사용하여 가져올 수 있다.
- 세션의 속성의 이름으로 접근이 가능하다.
- session에는 ```Object```가 저장될 수 있다.


#### 일반 자료형 값 가져오기


```java
HttpSession session = req.getSession(true);

session.setAttribute("hello", "world");
session.setAttribute("intValue", 123);

String hello = session.getAttribute("hello");
int intValue = session.getAttribute("intValue");

System.out.println(hello + intValue);
```


```
world123
```

- 속성 이름으로 세션에서 값을 가져올 수 있다.



#### Object 객체 가져오기


```java
Human human = new Human("parker", 26, 178);

// 세션을 가져온다.
HttpSession session = req.getSession(true);
session.setAttribute("parker", human);

Human parker = (Human)session.getAttribute("parker");

System.out.println(parker.getName());
System.out.println(parker.getAge());
System.out.println(parker.getHeight());
```


```
parker
26
178
```


- 일반 자료형 뿐 아니라 ***객체*** 도 가져올 수 있다.


#### 값 뿌려주기


```java
Enumeration<String> enum_session = session.getAttributeNames();

while(enum_session.hasMoreElements()) {
  String key = enum_session.nextElement();
  String val = (String)session.getAttribute(key);

  sb.append(key + " : " + val + "<br>");
}
```

- ```Enumeration<E>```을 사용하여 속성의 이름의 집합을 만들 수 있다.
- 집합을 반복문을 통해 값을 꺼내와 뿌려줄 수 있다.





## 세션 객체 삭제하기


- 세션을 저장할 수 있다면, 당연히 삭제하는 것도 가능하다.
- 세션에는 객체를 저장할 수 있는데 객체를 삭제하는 방법이 ```.removeAttribute()```를 사용하는 것이다.
- 현재 세션에 ```name : Parker```와 ```age : 25```가 저장되어 있을 때.


#### Session

```
name : Parker
age : 25
```


#### Servlet

```java
HttpSession session = req.getSession(false);

if(session != null) {
  // 세션 속성 삭제하기
  session.removeAttribute("age");
}else {
  sb.append("<p>session is not exist</p>");
}
```

- ```session.removeAttribute("age")``` 메소드를 통해 세션에 저장되어 있는 age를 삭제할 수 있다.



## 세션 자체를 삭제하기


- 이 외에 세션 자체를 삭제하는 방법이 있다.

```java
// session 이 존재하면 session을 가져오고
// 존재하지 않으면 새로운 session을 가져온다.
HttpSession session = req.getSession(true);

//session 자체를 날려버린다.
session.invalidate();
```


- 세션 자체가 삭제된다.
