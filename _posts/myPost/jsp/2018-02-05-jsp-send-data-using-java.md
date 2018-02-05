---
layout: post
title: '[jsp] 페이지 전환의 방법'
categories:
  - jsp
tags:
  - jsp
  - java
  - 데이터 전송
  - forward()
  - sendRedirect()
---

java를 사용하여 데이터를 전송하기 위한 여러가지 방법이 존재한다.
그 중 데이터를 적절하게 보내지 못하는 방법도 있다. 이에 대해 학습합니다.

# java를 사용한 데이터 전송

- 자바를 사용하여 페이지를 전환할 때 ```pageContext.forward(), response.sendRedirect()```가 사용된다.
- 하지만 ```response.sendRedirect()```를 사용할 때 데이터를 가지고 갈 수 없는 상황이 생긴다.
  - 자바를 사용하여 데이터를 전송할 때 전송이 가능한 조합이 존재한다.

1. session을 사용하면 ```pageContext.forward(), response.sendRedirect()``` 두가지 페이지 전환을 사용해도 데이터를 모두 가져갈 수 있다.

#### index.jsp

```java
Human human = new Human(26, "Parker");

session.setAttribute("human", human);

// 사용가능
response.sendRedirect("hello.jsp");
// 사용가능
pageContext.forward("hello.jsp");
```

#### hello.jsp

```java
Human paramHuman = (Human)session.getAttribute("human");
out.println(paramHuman);
```

- session에 값을 저장하기 때문에 어떤 페이지 전환이어도 세션에만 접근하면 객체의 값을 가지고 올 수 있다.

1. 내장 객체 ```application```을 사용하면  ```pageContext.forward(), response.sendRedirect()``` 두가지 페이지 전환을 사용해도 데이터를 모두 가져갈 수 있다.

#### index.jsp

```java
Human human = new Human(26, "Parker");

application.setAttribute("human", human);

// 사용가능
response.sendRedirect("hello.jsp");
// 사용가능
pageContext.forward("hello.jsp");
```

#### hello.jsp

```java
Human paramHuman = (Human)application.getAttribute("human");
out.println(paramHuman);
```

- application 내장 객체는 session과 동일하게 사용된다.
- application 객체에 접근할 수 있다면 객체의 값을 가지고 올 수 있다.

<p>
Application object is used to store data which is visible across entire application and shared across multiple user sessions. Data which needs to be persisted for entire life of application should be stored in application object.

In classic ASP, application object is used to store connection strings. It's a great place to store data which changes infrequently. We should write to application variable only in application_Onstart event (global.asax) or application.lock event to avoid data conflicts. Below code sample gives idea
</p>

<p>
Session object:

Session object is used to store state specific information per client basis. It is specific to particular user. Session data persists for the duration of user session you can store session's data on web server in different ways. Session state can be configured using the <session State> section in the application's web.config file.
</p>

1. requset를 사용하면  ```pageContext.forward()``` 에서는 페이지 전환을 사용해도 데이터를 모두 가져갈 수 있지만, ```response.sendRedirect()```을 사용하면 데이터를 전송할 수 없다.



#### index.jsp

```java
Human human = new Human(26, "Parker");

request.setAttribute("human", human);

// 사용불가능
response.sendRedirect("hello.jsp");
// 사용가능
pageContext.forward("hello.jsp");
```

#### hello.jsp

```java
Human paramHuman = (Human)request.getAttribute("human");
out.println(paramHuman);
```

```java
//response.sendRedirect("hello.jsp");
null

// pageContext.forward("hello.jsp");
[age=26, name=Parker]
```

## 정리

- 자바 코드로 데이터를 넘겨줄 때, 넘기는 방식과 페이지 전환 방식에 따라 데이터를 못불러 오는 경우가 존재한다.



|             | pageContext.forward() | response.sendRedirect() |
| :---------- | :-------------------- | :---------------------- |
| session     | 전송 가능                 | 전송 가능                   |
| application | 전송 가능                 | 전송 가능                   |
| request     | 전송 가능                 | 전송 **불가능**              |
