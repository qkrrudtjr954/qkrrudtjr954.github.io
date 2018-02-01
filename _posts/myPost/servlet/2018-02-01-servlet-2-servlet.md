---
layout: post
title: '[Servlet] 화면 전환'
categories:
  - servlet
tags:
  - servlet
  - forward()
  - include()
---



특정 servlet에서 다른 servlet으로 페이지를 전환하는 방법을 배웁니다.




## 화면 전환 방법

1. ```include()```
   - include()는 다른 servlet을 현재 servlet에 추가하는 방법.
   - 현재 servlet코드와 다른 servlet코드가 공존한다.
2. ```forward()```
   - forward()는 다른 servlet으로 이동하는 방법.
   - 이동한 servlet의 코드만 존재한다.




## 예제



- ```includeTest.java```를 ```include()```와  ```forward()```로 각각 호출하는 예제.




#### includeTest.java

```java
public class IncludeTest extends HttpServlet {
  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    resp.setCharacterEncoding("utf-8");
    resp.setContentType("text/html; charset=utf-8");

    PrintWriter out = resp.getWriter();
    out.println("<p>This is include test</p>");
  }
}
```

- include test 코드
- include와 forward로 호출합니다.



#### DispatchTest.java ( include() 사용 )



```java
public class DispatchTest extends HttpServlet {
  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    resp.setCharacterEncoding("utf-8");
    resp.setContentType("text/html; charset=utf-8");

    PrintWriter out = resp.getWriter();

    out.println("<html>");

    out.println("<head>");
    out.println("<title>this is dispatch</title>");
    out.println("</head>");

    out.println("<body>");

    // include(가져오기) A형태를 유지하고 B를 가져온다
    // forward(이동) A에서 B로 무조건 이동해버린다.	-> 가볍다. ( 데이터를 가져가지 않는다. )
    out.println("<p>이 다음으로 include 처리를 시작합니다.</p>");

    String disp = "includeTest";
    RequestDispatcher dispatcher = req.getRequestDispatcher(disp);

    // dispatchTest 상태에서 includeTest를 불러온다.
    dispatcher.include(req, resp);

    out.println("<p>include 가 완료됐습니다.</p>");

    out.println("</body>");
    out.println("</html>");
    out.close();
  }
}
```




- 현재 servlet에서 includeTest를 include로 호출합니다.




#### 결과



```
이 다음으로 include 처리를 시작합니다.

This is include test

include가 완료됐습니다.
```



- 결과에서 확인할 수 있듯이 includeTest의 코드가 dispatchTest코드 사이에 include 되었다.



<br>



#### DispatchTest.java ( forward() 사용 )



```java
public class DispatchTest extends HttpServlet {
  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    resp.setCharacterEncoding("utf-8");
    resp.setContentType("text/html; charset=utf-8");

    PrintWriter out = resp.getWriter();

    out.println("<html>");

    out.println("<head>");
    out.println("<title>this is dispatch</title>");
    out.println("</head>");

    out.println("<body>");

    // include(가져오기) A형태를 유지하고 B를 가져온다
    // forward(이동) A에서 B로 무조건 이동해버린다.	-> 가볍다. ( 데이터를 가져가지 않는다. )
    out.println("<p>이 다음으로 include 처리를 시작합니다.</p>");

    String disp = "includeTest";
    RequestDispatcher dispatcher = req.getRequestDispatcher(disp);

    // dispatchTest 상태에서 includeTest로 이동한다.
    dispatcher.forward(req, resp);

    out.println("<p>include 가 완료됐습니다.</p>");

    out.println("</body>");
    out.println("</html>");
    out.close();
  }
}
```



- 현재 servlet에서 includeTest를 forward로 호출합니다.




#### 결과

```
This is include test
```



- 결과에서 확인할 수 있듯이 includeTest로 화면이 완전히 전환되었다.
