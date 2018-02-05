---
layout: post
title: '[jsp] 페이지 전환의 방법'
categories:
  - jsp
tags:
  - jsp
  - jdbc
  - jsp&database
  - html
  - action
  - 액션
  - 페이지 전환
  - 페이지 전환 방법
---


웹에서는 페이지를 전환하기 위한 여러가지 방법을 제공합니다. 쓰임새에 따라 맞는 방법을 택해야하므로 전환의 방법이 무엇이 있고 어떻게 사용하는지 학습합니다.


# 페이지 전환의 방법

## 1. \<form action=""\> 과 \<a href=""\>

```html
<a href="localhost:8090/sampleXX/action.jsp?age=23&name=parker">
```

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

	<%
	String address = "Seoul";
	%>
	<form action="NewFile.jsp" method="post">
		<input type="text" name="age" value="10">
		<input type="text" name="address" value=<%=address%>>
		<input type="submit">
	</form>



</body>
</html>
```

## 2. javascript의 location.href=""



```javascript
location.href = "/action.jsp?age="+age+"&name="+name;
```

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
	<%
	String address = "Chung ju";
	%>

	<input type="text" name="age" value="15" id="age">
	<input type="text" name="address" value=<%=address%> id="address">
	<input type="button" id="hello" value="hello" onclick="hello()">


	<script type="text/javascript">
	function hello() {
		var age = document.getElementById('age').value;
		var address = document.getElementById('address').value;

		// javascript 에서 sciptlet을 불러올 수 있다.
		var str="<%=address%>";


		location.href="NewFile.jsp?age="+age+"&address="+address;
	}

	</script>
</body>
</html>
```



## 3. java

#### 3-1. forward

```html
<%@page import="java.net.URLEncoder"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

	<%
	String address = "Mars";
	%>

	<!-- pageContext : internal object -->
	<%
	pageContext.forward("NewFile.jsp?age=15&address=" + URLEncoder.encode(address, "utf-8"));

	// 한글이 깨질때 URLEncoder.encode(address, "utf-8") 를 address 대신 사용한다.
	%>
	<form action="NewFile.jsp" method="post">
		<input type="text" name="age" value="10">
		<input type="text" name="address" value=<%=address%>>
		<input type="submit">
	</form>
</body>
</html>
```



#### 3-2. sendRedirect

```jsp
<%@page import="java.net.URLEncoder"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

	<%
	String address = "Moon";
	%>

	<%
	response.sendRedirect("NewFile.jsp?age=15&address=" + URLEncoder.encode(address, "utf-8"));
	%>

</body>
</html>
```
