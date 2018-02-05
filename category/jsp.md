---
layout: category
title: jsp
---

자바코드를 웹에서 사용하기 위해 고안된 ***java server page ( jsp )*** 에 대해 학습합니다.



```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>JSP</title>
</head>
<body>

  <h1>This is JSP!</h1>

  <%
  String str = "You can use java code in your Web!!";
  %>

  <p>
    <%= str %>
  <p>

</body>
</html>
```



### -- Post List --
