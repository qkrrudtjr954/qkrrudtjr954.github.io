---
layout: post
title: '[jsp] 페이지 처음에 생기는 에러'
categories:
  - jsp
tags:
  - jsp
  - 에러
  - first page error
---


eclipse에서 JSP 페이지를 추가시켰을때, JSP 첫 라인에 에러가 생길 경우의 해결법을 제시합니다.



# jsp 제일 처음에 생기는 에러


- 이 에러는 ```javax.servlet.http.HttpServlet``` 가 **Build Path** 에 존재하지 않기 때문에 발생한다.
- tomcat은 기본적으로 ```javax.servlet.http.HttpServlet``` 내장하고 있기 때문에 tomcat 라이브러리를 추가해주면 에러를 해결할 수 있다.


# 해결 방법

#### step1.


![step1](https://i.imgur.com/7YL0XBT.png)

- jsp를 추가하면 컴파일 에러가 발생한다.




#### step2.


![step2](https://i.imgur.com/VB55AiQ.png)


- 프로젝트를 **우클릭** 하고 **Build Path** -> **Confiqure Build Path** 를 클릭한다.



#### step3.


![step3](https://i.imgur.com/PI3wtWf.png)

- **Libraries** 탭을 선택한다.
- **Add Library** 를 클릭한다.


#### step4.


![step4](https://i.imgur.com/KR7O2A4.jpg)


- **Server Runtime** 을 선택한다.


#### step5.



![step5](https://i.imgur.com/jz2EzF6.jpg)

- tomcat 서버를 선택한다.
- tomcat이 ```HttpServlet``` 을 포함하고 있다.
- **apply** 를 누르면 에러가 사라진다.
