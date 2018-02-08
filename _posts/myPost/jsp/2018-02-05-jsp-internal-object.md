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


http://gangzzang.tistory.com/entry/JSP-%EA%B8%B0%EB%B3%B8-%EA%B0%9D%EC%B2%B4-out-pageContext-application-page

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



## request


- request 내장 객체를 페이지에서 요청되는 정보를 포함하고 있다.
- HTTP 헤더와 HTTP 바디로 구성되어 있다.
- 웹 컨테이너는 요청된 HTTP 요청을 HttpServletRequest 객체로 받아 요청 정보에 접근할 수 있다.

###### 요청에 관한 메소드

|메소드|설명 |
|:------:|:------:|
|String getParameter(name) | 파라미터 변수 name에 저장된 변수를 얻어내는 메소드로, 이때 변수의 값은 String으로 리턴된다. |
| String[] getParameterValues(name) | 파라미터 변수 name에 저장된 |모든 변수값을 얻어내는 메소드로, 이때 변수의 값은 String 배열로 리턴된다. checkbox에서 주로 사용된다.|
Enumeration getParameterNames() | 요청에 의해 넘어오는 모든 파라미터 변수를 java.util.Enumeration 타입으로 리턴한다. |



###### request 내장 객체의 웹 브라우저, 웹 서버 및 요청 헤더의 정보 관련 메소드



|메소드|설명 |
|:------:|:------:|
|String getProtocol() | 웹 서버로 요청 시, 사용 중인 프로토콜을 리턴한다.|
|String getServerName() |웹 서버로 요청 시, 서버의 도메인 이름을 리턴한다. |
|String getMethod() |웹 서버로 요청 시, 요청에 사용된 요청 방식(GET, POST, PUT 등)을 리턴한다. |
|String getQueryString() |웹 서버로 요청 시, 요청에 사용된 QueryString을 리턴한다. |
|String getRequestURI() |웹 서버로 요청 시, 요청에 사용된 URL 로부터 URI 값을 리턴한다.|
|String getRemoteAddr() |웹 서버로 정보를 요청한 웹 브라우저의 IP주소를 리턴한다. |
|int getServerPort() |웹 서버로 요청 시, 서버의 Port번호를 리턴한다. |
|String getContextPath() |해당 JSP 페이지가 속한 웹 어플리케이션의 콘텍스트 경로를 리턴한다. |
|String getHeader(name) |웹 서버로 요청 시, HTTP 요청 헤더(header)의 헤더 이름인 name에 해당하는 속성값을 리턴한다. |
|Enumeration getHeaderNames() |웹 서버로 요청 시, HTTP 요청 헤더(header)에 있는 모든 헤더 이름을 리턴한다. |



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



## response


- response 객체는 웹 브라우저로 응답할 응답 정보를 가지고 있다.
- 웹 브라우저에 보내는 응답 정보는 HttpServletResponse 객체를 사용한다.
- response 객체는 응답 정보와 관련하여 주로 헤더 정보 입력, 리다이렉트 하기 등의 기능을 제공한다.


###### 응답에 관한 메소드

|메소드 |설명 |
|:-------:|:-------:|
|void setHeader(name, value) |헤더 정보의 값을 수정하는 메소드로, name에 해당하는 헤더 정보를 value값으로 설정한다. |
|void setContentType(type) |웹 브라우저의 요청의 결과로 보일 페이지의 contentType을 설정한다. |
|void sendRedirect(url) |페이지를 이동시키는 메소드로, url로 주어진 페이지로 제어가 이동한다. |
