---
layout: post
title: '[jstl] el tags'
categories:
  - jstl
tags:
  - jstl
  - el tags
  - el
---



***el tag*** 는 [core](/2018-02-07-jstl-core-tag.md)와 함께 사용되는 태그의 종류이다.


## el tag 란?

- el tag 는 ***Expression Language*** 의 약자로 ***표현 언어*** 라는 의미를 갖는다.
- jsp에서 사용하는 ```<%= %>``` 스크립트릿과 그 쓰임새가 비슷하다.
- 설정된 변수를 표현하는데 사용되는 태그이다.


## el tag 를 사용한 접근




#### 1. scriptlet을 사용한 값 출력

```
<%
String sethello = "Hello";
request.setAttribute("str", setHello);
%>

<%
String getHello = request.getAttribute("str");
%>

<p>
<%
out.println("getHello is " + getHello);
%>
</p>
```

- 내장객체 ```out```을 사용하여 값을 출력할 수 있다.

#### 2. scriptlet + el tag 를 사용한 값 출력

```
<%
request.setAttribute("elTest", "This is el practice.");
%>

<p>
${elTest}
</p>  
```

```
This is el practice.
```

- scriptlet으로 설정된 값 역시 ***el tag*** 를 사용하여 가져올 수 있다.
- 여기서 주의할 점은 ***setAttribute의 첫번째 인자값을*** 사용해서 ***el tag*** 를 사용해야하는 것이다.



#### 3. el tag + core tag 사용한 값 출력

```
<c:set var="setHello" value="Hello"/>
<p>
  ${setHello}
</p>
```

- ***el tag***, ***core tag*** 를 사용하여 값을 세팅하고 출력한다.
- 위의 코드를 아주 간단하게 작성할 수 있다.
- 위 코드에서 사용된 ```${}``` 를 ***el tag*** 라고 부른다.

<br>

```
<%= request.getAttribute("data") %>
${data }
```
- ***el tag*** 는 ```request.getAttribute("setHello");``` 를 함축적으로 표현한 태그이다.



## el tag의 활용


#### 1. 빈데이터 체크하기

```
${empty dataasdfawefs }

${not empty dataasdfawefs }
```

- 데이터 변수 앞에 ***empty*** 를 붙이면 데이터가 비었는지 체크한다.
  - 비어있으면 ***true*** 를 리턴한다.
  - 값이 있으면 ***false*** 를 리턴한다.
- ***empty*** 앞에 ***not*** 을 붙이면 데이터가 리턴값이 반전된다.
  - 비어있으면 ***false*** 를 리턴한다.
  - 값이 있으면 ***true*** 를 리턴한다.

#### 2. 연산

```
<span>el tag calc : </span> ${10 + 50 }
```

```
el tag calc : 60
```

- ```el tag```안에 연산을 넣으면 연산된 결과값을 리턴한다.

#### 3. 조건

```
<span>el tag condition : </span> ${10 < 50 }
```

```
el tag condition : true
```

- ```el tag```안에 조건을 넣으면 조건의 결과값을 리턴한다.


<br>


```
<p>
  삼항연산자를 표현한다.
  <%=(3>2)?true:false %>
  ${(3<2)?true:false }
</p>
```

```
삼항연산자를 표현한다. true false
```

- 조건의 결과를 삼항 연산자를 표현할 수 있다.



#### 4. 조건 판정

- 비교 연산을 통해 조건에 대한 판정을 내릴 수 있다.


###### eq tag

```
${a eq b }
${a==b }
```

- eq tag를 사용하여 두개의 값이 같은지 확인할 수 있다.



###### ne tag


```
${a ne b }
${a!=b }
```

- ne tag를 사용하여 두개의 값이 다른지 확인할 수 있다.



###### lt tag & le tag

```
${a lt b}
${a < b}

${a le b}
${a <= b}
```


- lt tag를 사용하여 앞의 값이 뒤의 값보다 ***작은지*** 판단할 수 있다.
- le tag를 사용하여 앞의 값이 뒤의 값보다 ***작거나 같은지*** 판단할 수 있다.


###### gt tag & ge tag

```
${a gt b}
${a > b}

${a ge b}
${a >= b}
```


- lt tag를 사용하여 앞의 값이 뒤의 값보다 ***큰지*** 판단할 수 있다.
- le tag를 사용하여 앞의 값이 뒤의 값보다 ***크거나 같은지*** 판단할 수 있다.




## el tag로 객체 사용하기

```java
public class JspTestBean{
	private String msg;
	public String getMsg() {
		return msg;
	}
	public void setMsg(String msg) {
		this.msg = msg;
	}
}
```

```
<%
JspTestBean bean = new JspTestBean();

bean.setMsg("hello Message!");

request.setAttribute("bean", bean);
%>

1. <%=bean.getMsg() %>

2. ${bean.msg }
```

- msg (변수명) 만 적으면 getter가 자동으로 호출된다.

## el tag로 배열 사용하기

```
<%
String array[] = new String[]{"hello", "world"};

request.setAttribute("array", array);
%>
```

```
${array[0] }
```

- 배열을 객체로 취급한다.
- 기존 배열에 접근하는 것과 같은 방식으로 접근할 수 있다.



## el tag로 List 사용하기

```
<%
List<String> list= new ArrayList<>();

list.add("hello");
list.add("world");

request.setAttribute("list", list);
%>

list index 0 : ${list[0] }
list index 1 : ${list[1] }
```

- List에 접근하기 위해서는 배열처럼 ```[]```을 사용해야한다.

## el tag로 HashMap 사용하기

```
<%
HashMap<String, String> map = new HashMap<>();

map.put("first", "Hi");
map.put("second", "Hello");
map.put("third", "안녕?");

request.setAttribute("map", map);
%>

${map.first }== ${map["first"] }<br>
${map.second }== ${map["second"] }<br>
${map.third }== ${map["third"] }<br>
```

- ```map.first``` 와 같이 객체에 map.key값 으로 value에 접근할 수 있다.
- 또 ```map["first"]``` 로도 접근이 가능하다.



## el param으로 parameter 받기



```
${param.name }
```

- 위 url로 전달되는 parameter에 접근할 수 있다
- url : "http://localhost:8080/index.jsp?name=hello"로 접근할 경우 ```hello```출력
