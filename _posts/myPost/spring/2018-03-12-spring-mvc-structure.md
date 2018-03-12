---
layout: post
title: "[Spring] DispatcherServlet 의 이해"
categories:
  - Spring
tags:
  - Spring
  - Framework
  - DispatcherServlet
  - <url-pattern/>
  - servlet-context.xml
---


Spring Framework 에서 사용되는 ***DispatcherServlet*** 의 개념과 동작 순서 및 방식에 대해 학습합니다.

<br><br>


![spring mvc structure](http://img1.daumcdn.net/thumb/R1920x0/?fname=http%3A%2F%2Fcfile1.uf.tistory.com%2Fimage%2F2364CF4356DE4AAF275D1D)


<br>


1. 클라이언트가 해당 어플리케이션에 접근하면 접근한 URL 요청을 ***DispatcherServlet*** 이 가로챕니다. 이렇게 요청을 가로챌 수 있는 이유는 ***web.xml*** 에 등록된 ***DispatcherServlet*** 의 ```<url-pattern>```이 '/' 와 같이 해당 어플을 통과하는 모든 URL로 등록했기 때문입니다. 특정 URL 만 적용하고 싶다면 ```<url-pattern>``` 의 내용을 바꿔주어 범위를 변경시켜주면 됩니다.

2. 가로챈 정보를 ***HandlerMapping*** 에게 보내 해당 요청을 처리할 수 있는 ***Controller*** 를 찾아냅니다. (스프링은 기본적으로 5가지의 핸들러 매핑을 제공합니다.)  이 부분은 스프링의 디폴트 전략에 의해 ***BeanNameUrlHandlerMapping*** 과 ***DefaultAnnotationHandlerMapping*** 이 기본으로 Spring MVC에 탑재되있기 때문에 특별한 경우가 아니면 따로 설정할 필요가 없습니다.

3. 핸들러 매핑이 해당 요청을 처리할 컨트롤러를 찾아냈다면 요청을 컨트롤러에 보내줍니다. 컨트롤러는 사용자가 직접 구현해주는 부분입니다. ```@MVC```는 매우 다양한 코딩방식과 직관적이고 편리한 컨트롤러 작성방법을 제공하므로 이 부분에 대해서는 차후 심층적인 분석으로 자신에게 알맞는 전략을 선정해야합니다.


4. 해당 요청을 처리한 후에 컨트롤러는 요청을 응답받을 View 의 이름을 리턴하게 됩니다. ( 물론 다른 핸들러 매핑 전략을 이용한다면 응답 과정이 다를 수도 있습니다. ) 그 때 이 이름을 ***ViewResolver*** 가 먼저 받아 해당하는 View가 존재하는지 검색합니다.

5. 컨트롤러에서 보내온 View 이름을 토대로 처리 View 를 검샙합니다.

6. 해당 View가 있다면 처리결과를 View에 보낸 후  ***7.*** 이 결과를 다시 ***DispatcherServlet*** 에 보낸 후 ***8. DispatcherServlet*** 은 최종 결과를 클라이언트에 전송합니다.


출처 : [http://egloos.zum.com/springmvc/v/504151](http://egloos.zum.com/springmvc/v/504151)


<br>

#### 자원의 분리

- '/' 요청에 대한 모든 처리를 ***DispatcherServlet*** 이 담당한다면, 비어플리케이션 자원 (js, css ...)에 대해서도 컨트롤러를 찾아 해매는 에러가 발생할 수 있다.
- 그에 따라 Spring 은 자원을 분리할 수 있는 기능을 추가 시켜놓았다.

<br>

###### servlet-context.xml



```xml
<resources mapping="/resources/-*" location="/resources/" />
```

- ```<mvc:resources>``` 는 디스패처 서블릿이 해당 요청을 컨트롤러에서 찾지 못했을 때 2차적으로 위의 설정된 경로를 검색하여 해당 자원을 찾아내게 하는 것입니다.
- 어플리케이션 자원과 비어플리케이션 자원( js, css ...)을 분리하여 resources 폴더에서 따로 관리 가능하도록 한 것 입니다.
