---
layout: post
title: '[jsp] 내장 객체'
categories:
  - jsp
tags:
  - jsp
  - 내장 객체
  - internal object
---


jsp는 내부적으로 포함하고 있는 내장 객체를 가지고 있다. 이렇게 정의된 내장 객체는 직접적인 선언없이 바로 접근이 가능하다.
내장 객체의 종류와 사용법을 학습합니다.



# jsp 내장 객체


- 할당할 필요없이 바로 사용이 가능하다.

| 기본 객체 | 설명 |
| :------------- | :------------- |
| request | 클라이언트의 요청 정보를 저장한다. |
| response | 응답 정보를 저장한다. |
| pageContext | JSP 페이지에 대한 정보를 저장한다. |
| session | HTTP 세션 정보를 저장한다. |
| application | 웹 어플리케이션에 대한 정보를 저장한다. |
| out | JSP 페이지에서 출력에 사용하는 출력스트림이다. |
| config | JSP의 설정 정보를 저장한다. |
| page | JSP의 페이지를 구현한 자바 클래스 인스턴스이다. |
| exception| 인셉션 객체, 여러 페이지에서만 사용된다.|



1. request  가장활용도가 좋다.

```java
request.setCharacterEncoding("utf-8");
```


```jsp
<%@page import="java.util.Arrays"%>
<%@page import="com.sun.xml.internal.bind.v2.runtime.unmarshaller.XsiNilLoader.Array"%>
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
// 내장 객체
request.setCharacterEncoding("utf-8");

String name = request.getParameter("name");
System.out.println(name);

String num = request.getParameter("num");
System.out.println(num);

String val[] = request.getParameterValues("hobby");
for(int i=0; i<val.length; i++){
  out.println(val[i]+"<br>");
}
%>

</body>
</html>
```

- parameter 넘겨주는법
