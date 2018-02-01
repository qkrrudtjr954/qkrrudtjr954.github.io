---
layout: post
title: '[Servlet] Session을 사용한 방문 횟수 카운트'
categories:
  - servlet
tags:
  - servlet
  - session
  - visitcount
---


카운트를 세션에 저장하고 sevlet을 탈때 값을 꺼내 증가시켜 페이지에 방문한 카운트를 체크할 수 있는 간단한 예제를 제시합니다.




#### HelloServlet.java

```java
public class HelloServlet extends HttpServlet {

  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    resp.setCharacterEncoding("utf-8");
    resp.setContentType("text/html; charset=utf-8");

    PrintWriter out = resp.getWriter();
    StringBuffer sb = new StringBuffer();


    sb.append("<html>");

    sb.append("<head>");
    sb.append("<title>welcome</title>");
    sb.append("</head>");

    sb.append("<body>");

    HttpSession session = req.getSession(false);

    if(session==null) {
      sb.append("<p>First Visited!</p>");

      // session을 받아온다.
      session = req.getSession(true);

      // session object 생성
      session.setAttribute("visited", "1");
    }else {
      String visitedStr = session.getAttribute("visited").toString();
      int visited = Integer.parseInt(visitedStr);
      visited++;


      sb.append("<p>");
      sb.append(visited);
      sb.append("번째 방문입니다.");
      sb.append("</p>");
      session = req.getSession(true);	// session을 받아온다.

      // session object 생성
      session.setAttribute("visited", (visited)+"");
    }
    sb.append("<a href=\"hello\">refresh</a>");
    sb.append("</body>");

    sb.append("</html>");
    out.println(sb.toString());
    out.close();
  }
}
```

#### web.xml



```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" version="3.1">
  <display-name>0201session2</display-name>
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
  </servlet>
  <servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/hello</url-pattern>
  </servlet-mapping>
</web-app>
```
