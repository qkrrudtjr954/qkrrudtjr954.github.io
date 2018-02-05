---
layout: post
title: '[jsp] 페이지 include'
categories:
  - jsp
tags:
  - jsp
  - include
---

jsp에서 scriptlet을 사용하여 다른 페이지를 include하여 현재 페이지에서 다른 페이지를 보여줄 수 있다.


# include

- 다른 웹 페이지를 해당 웹페이지에 추가한다.

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
  pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Insert title here</title>
  </head>
  <body>
    <h1>jsp start</h1>

    <%@include file="include.jsp" %>

    <h1>jsp end</h1>
  </body>
</html>
```

- include.jsp를 index.jsp 파일에 임포트 합니다.
