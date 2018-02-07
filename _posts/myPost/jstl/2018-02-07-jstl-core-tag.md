---
layout: post
title: '[jstl] core tags'
categories:
  - jstl
tags:
  - jstl
  - core tags
  - core
  - 코어
---



jstl 중에 가장 보편적인 기능을 제공하는 ***core tags*** 에 대해 학습합니다.


# core tag의 종류



|Tags	| Description|
|:----------:|:------------:|
|c:out|	It display the result of an expression, similar to the way <%=...%> tag work.|
|c:import	|It Retrives relative or an absolute URL and display the contents to either a String in 'var',a Reader in 'varReader' or the page.|
|c:set|	It sets the result of an expression under evaluation in a 'scope' variable.|
|c:remove	|It is used for removing the specified scoped variable from a particular scope.|
|c:catch	|It is used for Catches any Throwable exceptions that occurs in the body.|
|c:if|	It is conditional tag used for testing the condition and display the body content only if the expression evaluates is true.|
|c:choose, c:when, c:otherwise	|It is the simple conditional tag that includes its body content if the evaluated condition is true.|
|c:forEach	|It is the basic iteration tag. It repeats the nested body content for fixed number of times or over collection.|
|c:forTokens	|It iterates over tokens which is separated by the supplied delimeters.|
|c:param	|It adds a parameter in a containing 'import' tag's URL.|
|c:redirect	|It redirects the browser to a new URL and supports the context-relative URLs.|
|c:url	|It creates a URL with optional query parameters.|




|Tags	| Description|
|:----------:|:------------:|
|c:out| expression을 화면에 출력해주는 태그. <%=..%> 와 비슷한 역할을 한다.|
|c:import|동일한 웹 어플리케이션뿐만 아니라 외부의 다른 자원을 읽어와 포함시킬 수 있도록 해주는 태그. GET방식 또는 <c:param>태그를 이용하여 파라미터를 전송할 수도 있다.|
|c:set| 변수를 jstl이 사용할 수 있도록 설정해주는 태그. |
|c:remove	| 특정 활성 변수를 활성 상태에서 제거 시키는 태그. 변수를 제거하는 태그.|
|c:catch	| body에서 일어나는 모든 exception을 처리할 수 있는 태그.|
|c:if|단순 조건문에 사용되는 태그|
|c:choose, c:when, c:otherwise	| if..elseif..else와 같은 다중 조건문에 사용되는 태그.|
|c:forEach	| 반복문을 사용하는 태그. |
|c:forTokens	| 제공된 delimeters로 분리된 토큰들을 iteration 하는 태그 |
|c:param	| import태그 URL에 포함된 파라미터를 더하는 태그 |
|c:redirect	| 브라우져를 새로운 URL로 리다리랙션 시키는 태그 |
|c:url	| 추가적인 쿼리 변수들을 사용하여 새로운 URL을 만들 수 있는 태그 |


# core tag 사용하기

#### core tag 추가하기

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt"%>
```

- core 태그를 사용하기 위해서는 core를 추가 해주어야한다.
  - prefix는 c를 사용한다.
- fmt 태그를 fmt로 import 를 해주어야 사용이 가능하다.
  - 할게 거의 없다.
  - 문자 인코딩을 맞춰주는 용도로만 사용한다.
- 프로젝트에 [jstl.jar](http://www.java2s.com/Code/Jar/j/Downloadjstl12jar.htm)를 다운받은 후 추가해주어야 한다.



## 1. set tag

- jsp에서 변수를 세팅할 수 있는 태그

```jsp
<%
String data = "this is jstl";
request.setAttribute("data", data);
%>


<c:set var="data" value="this is jstl"/>
```

- 두 코드는 같은 코드이다.
- scriptlet으로 표현된 코드를 jstl로 표현할 수 있다.


```jsp
<c:set var="data" value="this is jstl"/>

<%=data %>  <!--에러 발생-->
${data}   <!-- 문자 출력 -->
```

- ```data```에 ```this is jstl``` 문자열을 넣어 변수를 세팅한다.
- ```data```는 ***attribute*** 에 저장된다.
- ***el tag*** 를 사용하면 값에 접근할 수 있다.


```jsp
<%
application.setAttribute("applicationData", "appliction test");
%>

<c:set var="coreSetTest" value="${applicationData }"/>

${coreSetTest }
```

- ***el tag*** 를 사용해서 내장 객체 ```application```, ```session``` 등에 저장된 값을 set할 수 있다.



## 2. out tag

```jsp
<%
String data = "this is jstl";
request.setAttribute("data", data);

out.println(data);
%>

<c:set var="data" value="this is jstl"/>
<c:out value="${data }"/>
```

- ***el tag*** 로 접근해 가져온 데이터를 html문서 밖으로 출력한다.
- scriptlet으로 표현된 코드를 한줄로 줄일 수 있다.

## 3. remove tag

```jsp
<c:set var="data2" value="testing"/>

<c:remove var="data2"/>

${empty data2 }
```

```
true
```

- attribute 에 설정된 데이터( data2 )를 삭제할 수 있다.


## 4. if tag

```jsp
<%
request.setAttribute("count", 50);
%>

<c:if test="${ count > 20 }">
  <p> count is bigger than 20. </p>
</c:if>
```

```
count is bigger than 20.
```


- ***el tag*** 를 사용하여 조건을 검사할 수 있다.
- 조건이 만족되면 아래 코드가 실행된다.


## 5. forEach tag


#### forEach List

```jsp
<%
  List<JspTestBean> list = new ArrayList<>();

  for (int i = 0; i < 10; i++) {
  	JspTestBean bean = new JspTestBean();
  	bean.setMsg("Message" + i);

  	list.add(bean);
  }

  request.setAttribute("list", list);
%>

<c:forEach var="obj" items="${list }" varStatus="i">
	<c:out value="${i.index }" />
	<br>
	<c:out value="${list[i.index].msg }" />
	<br>
</c:forEach>
```

- ```${i.index}```를 사용해 index 값을 가지고 올 수 도 있다.
- list의 출력은 배열의 형태로 접근한다.



#### forEach HashMap

```jsp
<%
  HashMap<String, String> map = new HashMap<>();

  map.put("1", "a");
  map.put("12", "ab");
  map.put("123", "abc");

  request.setAttribute("map", map);
%>

<c:forEach var="obj" items="${map }">
  <c:out value="${obj.key}" />
  <c:out value="${obj.value}" />
  <br>
</c:forEach>
<br>
<br>
<br>
```


- map 객체는 ***key***, ***value*** 로 이루어져 있다.
- ```map.key```, ```map.value``` 를 사용해서 key, value에 접근할 수 있다.
