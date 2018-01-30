---
layout: post
title: '[Servlet] 서블릿이란?'
categories:
  - servlet
tags:
  - servlet
---

servlet의 개념과 servlet의 간단한 예제를 설명합니다.



# Servlet 이란?

- java코드와 web을 연결해주는 중간 다리 역할을 하는 기술
- java로 구현되 CGI ( Common Gateway Interface )
- javax.servlet.http.HttpServlet 클래스를 상속하여 구현한다.
  - GenericServlet은 service 메서드를 제외한 나머지 Servlet 인터페이스의 메서드를 구현해 놓은 abstract 클래스이다.
  - GenericServlet 클래스를 상속받아 실제 Http request 처리에 필요한 service 메서드를 구현해 놓은 것이 바로 HttpServlet이다.
- Servlet은 Container에 의해서 실행되고, 관리된다.

# Servlet Container

- 서블릿을 관리하며 네크워크 통신, 서블릿의 생명주기 관리, 스레드 기반의 병렬처리를 대행합니다.
- 웹 클라이언트로 부터 HTTP 요청이 전달되면 해당 HTTP 요청을 해석하여 적정한 서블릿의 service 메서드를 ServletRequet, ServletResponse 매개변수와 함께 호출합니다.


![servlet](https://i.imgur.com/o58pFQ0.png)


# 예제

#### index.html


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
  </head>
  <body>
    <h1>sevelet</h1>

    <form action="helloworld" method="get">
      <input type ="submit" value="get">
    </form>

    <form action="helloworld" method="post">
      <input type ="submit" value="post">
    </form>
  </body>
</html>
```
- ```form```태그는 ```/helloworld``` 으로 action 한다.
- get과 post 두가지 방식으로 동작한다. (***request***)


#### web.xml

- web.xml파일은 ```/WebContent/WEB-INF/``` 하위에 위치한다.


```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="http://java.sun.com/xml/ns/j2ee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"
         version="2.4">

  <display-name>HelloWorld Application</display-name>
  <description>
    This is a simple web application with a source code organization
    based on the recommendations of the Application Developer's Guide.
  </description>

  <servlet>
    <servlet-name>helloworld</servlet-name>
    <servlet-class>servlet01.HelloWorldServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>helloworld</servlet-name>
    <url-pattern>/helloworld</url-pattern>
  </servlet-mapping>
</web-app>
```

- ```<servlet></servlet>```과 ```<servlet-mapping></servlet-mapping>``` 은 하나의 쌍이라고 생각하면 된다.
- ```/helloworld``` 의 경로로 가는 모든 요청은 helloworld servlet을 지난다.
- ```servlet-mapping```을 통해 동작될 servlet을 결정한다.
- helloworld 이름을 가진 서블렛이 동작될 class를 정한다.
- 해당 클래스가 실행된다.


#### HelloWorldServlet.java


- servlet java 파일은 ```Java Resource``` 하위에 위치한다.

```java
package servlet01;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class HelloWorldServlet extends HttpServlet{

  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    // TODO Auto-generated method stub
    System.out.println("doGet()!");

    PrintWriter out = resp.getWriter();

    out.println("<html>");
    out.println("<head>");
    out.println("<title>This is Servlet.</title>");
    out.println("</head>");
    out.println("<body>");
    out.println("<p>this is servlet response ( get )</p>");
    out.println("</body>");
    out.println("</html>");
  }

  @Override
  protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    // TODO Auto-generated method stub
    System.out.println("doPost()!");

    PrintWriter out = resp.getWriter();

    out.println("<html>");
    out.println("<head>");
    out.println("<title>This is Servlet.</title>");
    out.println("</head>");
    out.println("<body>");
    out.println("<p>this is servlet response ( post )</p>");
    out.println("</body>");
    out.println("</html>");
  }

}
```

- get 또는 post 요청 방식에 따라 ```doGet()```, ```doPost()```가 실행된다.
- ```PrintWriter```를 사용하여 html 코드를 직접 작성해서 요청에 응답할 수 있다.(***response***)
  - 하지만 이 방식은 잘 사용하지 않는다.
