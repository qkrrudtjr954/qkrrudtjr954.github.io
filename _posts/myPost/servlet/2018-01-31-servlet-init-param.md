---
layout: post
title: '[Servlet] Init-param'
categories:
  - servlet
tags:
  - servlet
  - init-param
---


servlet에서는 ```web.xml``` 에 파라미터를 미리 설정해놓고 원할때 꺼내어 세팅할 수 있다.


#### web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" version="3.1">
  <display-name>sample</display-name>
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.htm</welcome-file>
    <welcome-file>index.jsp</welcome-file>
    <welcome-file>default.html</welcome-file>
    <welcome-file>default.htm</welcome-file>
    <welcome-file>default.jsp</welcome-file>
  </welcome-file-list>


  <servlet>
  	<servlet-name>hello</servlet-name>
  	<servlet-class>hello.HelloServlet</servlet-class>

  	<init-param>
  		<param-name>wallet</param-name>
  		<param-value>500</param-value>
  	</init-param>
  </servlet>

  <servlet-mapping>
  	<servlet-name>hello</servlet-name>
  	<url-pattern>/hello</url-pattern>
  </servlet-mapping>
</web-app>
```

- servlet 부분에 ```<init-param></init-param>```을 세팅한다.
- ```wallet```을 변수의 이름처럼 사용할 수 있다. ( ```<param-name></param-name>``` )
- 500을 변수의 값으로 사용할 수 있다. ( ```<param-value></param-value>``` )





#### HelloServlet.java


```java
package hello;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class HelloServlet extends HttpServlet{
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		// web.xml에 세팅한 parameter를 꺼내는 방법
		String wallet = getInitParameter("wallet");
		System.out.println(wallet);
	}
}
```


- servlet 에서 ```getInitParameter()``` 메소드를 통해 정의한 파라미터를 꺼내올 수 있다.
- 꺼내온 파라미터의 값은 모두 스트링 형이다. 필요한 경우 형변환을 해주어야 한다.


```
500
```
