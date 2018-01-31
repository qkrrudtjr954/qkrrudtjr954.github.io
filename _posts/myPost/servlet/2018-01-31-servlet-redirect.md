---
layout: post
title: '[Servlet] redirect'
categories:
  - servlet
tags:
  - servlet
  - redirect
---


servlet에서 처리를 마치고 다른 페이지로 전환을 시켜주는 방법에 대해 학습합니다.



## Redirect

- servlet은 java코드로 작성되어 있다.
- 웹에서 특정 요청을 지시하면 servlet에서 처리를 한다.
- 처리를 하고 다른 웹으로 이동을 시켜줄때 ***redirect*** 를 사용한다.
- servlet 뿐만 아니라 많은 웹 개발에서 사용되는 개념이다.



## 정적 html파일로 redirect

- 같은 디렉토리나 프로젝트 안에 있는 정적인 html파일로 이동하는 법을 제시한다.

#### HelloServlet.java

```java
public class HelloServlet extends HttpServlet{
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		String url = req.getParameter("url");
		System.out.println(url);

		if(url.equals("daum")) {
			resp.sendRedirect("daum.html");
		}else {
			resp.sendRedirect("something.html");
		}
	}
}
```

- post 방식으로 전달된 값(url)이 **"daum"** 이라면 ```resp.sendRedirect("daum.html");``` 함수를 통해 **daum.html** 파일로 이동한다.



## 외부 url로 redirect

- 같은 프로젝트 내로 이동하는 것이 아니라 외부 url로 이동하는 법을 제시한다.


#### HelloServlet.java

```java
public class HelloServlet extends HttpServlet{
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		String url = req.getParameter("url");
		System.out.println(url);

		if(url.equals("daum")) {
			resp.sendRedirect("https://www.daum.net");
		}else {
			resp.sendRedirect("https://www.google.com");
		}
	}
}
```

- post 방식으로 전달된 값(url)이 **"daum"** 이라면 ```resp.sendRedirect("https://www.daum.net");``` 함수를 통해 **https://www.daum.net** 으로 이동한다.
