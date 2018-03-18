---
layout: post
title: "[Spring] tiles 적용하기"
categories:
  - Spring
tags:
  - spring
  - tiles
---


스프링은 타일즈를 통해 웹페이지의 레이아웃을 설정합니다.

타일즈를 적용하는 방법을 학습합니다.


### 1. 타일즈 라이브러리 추가하기

- maven 프로젝트라는 가정하에 pom.xml에 Dependency를 추가한다.

##### pom.xml

```xml
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-api</artifactId>
	<version>3.0.5</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-autotag-core-runtime</artifactId>
	<version>1.1.0</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-core</artifactId>
	<version>3.0.5</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-jsp</artifactId>
	<version>3.0.5</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-request-api</artifactId>
	<version>1.0.6</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-request-jsp</artifactId>
	<version>1.0.6</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-request-servlet</artifactId>
	<version>1.0.6</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-servlet</artifactId>
	<version>3.0.5</version>
</dependency>
<dependency>
	<groupId>org.apache.tiles</groupId>
	<artifactId>tiles-template</artifactId>
	<version>3.0.5</version>
</dependency>
```



### 2. DispatcherServlet 설정하기 ( servlet-context.xml )

- ***servlet-context.xml*** 파일에 아래 설정 파일을 추가한다.

##### servlet-context.xml

```xml
<!-- 타일즈 설정 -->
<bean id="tilesConfigurer" class="org.springframework.web.servlet.view.tiles3.TilesConfigurer">
	<property name="definitions">
		<list>
			<value>/WEB-INF/views/layouts.xml</value>
		</list>
	</property>
</bean>

<bean id="viewResolver" class="org.springframework.web.servlet.view.UrlBasedViewResolver">
	<property name="requestContextAttribute" value="requestContext"/>
	<property name="viewClass" value="org.springframework.web.servlet.view.tiles3.TilesView"></property>
</bean>
```



### 3. layout.xml 생성하기

- ***/WEB-INF/views/layouts.xml*** 해당 경로에 해당 파일을 추가한다.

##### layout.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE tiles-definitions PUBLIC "-//Apache Software Foundation//DTD Tiles Configuration 3.0//EN" "http://tiles.apache.org/dtds/tiles-config_3_0.dtd">


<!-- tiles를 생성하는 설정 -->
<tiles-definitions>

<definition name="main.tiles" template="/WEB-INF/views/layouts-tiles.jsp">
	<put-attribute name="header" value="/WEB-INF/views/header.jsp"/>
	<put-attribute name="menu" value="/WEB-INF/views/menu.jsp"/>
	<put-attribute name="content" value="/WEB-INF/views/main.jsp"/>
	<put-attribute name="footer" value="/WEB-INF/views/footer.jsp"/>
</definition>

</tiles-definitions>
```

- Controller에서 ***main.tiles*** 를 통하는 연결은 해당 타일즈 레이아웃을 갖는다.
- 템플렛은 ***/WEB-INF/views/layouts-tiles.jsp*** 을 사용한다.
- header, menu, main, footer 는 정해진 경로에 있는 파일로 추가한다.



##### layouts-tiles.jsp

- tiles 가 사용하는 템플렛
- 정해진 위치에 파일을 추가하여 템플렛을 완성한다.


```html
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://tiles.apache.org/tags-tiles" prefix="tiles" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

<table border="1" width="100%" heigth="100%" bordercolor="Gray">
	<tr align="center">
		<td height="10%" colspan="2">
			<tiles:insertAttribute name="header"/>
		</td>
	</tr>
	<tr>
		<td width="30%" align="left" valign="top">
			<tiles:insertAttribute name="menu"/>
		</td>
		<td>
			<tiles:insertAttribute name="content"/>
		</td>
	</tr>
	<tr align="center">
		<td height="10%" colspan="2">
			<tiles:insertAttribute name="footer"/>
		</td>
	</tr>
</table>

</body>
</html>
```


### 4. Tiles 적용 후 모습

![tiles 적용 모습](https://i.imgur.com/sJbnxa0.png)

- 각 부분이 독립적인 파일로 관리된다
