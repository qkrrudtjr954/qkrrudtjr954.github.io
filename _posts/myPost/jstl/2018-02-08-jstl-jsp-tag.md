---
layout: post
title: '[jstl] jsp tag'
categories:
  - jstl
tags:
  - jstl
  - jsp tag
  - jsp
---


jsp 태그는 jsp 페이지 위에서 scriptlet으로 사용되는 자바 코드를 줄이고 태그 코드로 사용할 수 있도록 많은 지원을 해주는 태그다.



# jsp tag


- 사용빈도는 낮지만 고급 태그로 많이 사용한다.
- 자바코드를 줄일 수 있는 유용한 기능을 제공한다.
- scriptlet으로 해결할 수 있는 코드를 태그로 처리할 수 있도록 기능을 지원한다.



## include tag


```
<span>페이지를 가져온다.</span>

<jsp:include page="NewFile.jsp" flush="false"/>

<span>페이지를 가져왔다.</span>
```

- 외부 파일을 읽어와 현재 페이지에 삽입한다.



## forward tag

- 페이지를 이동할 때 사용되는 태그


```
<jsp:forward page="NewFile.jsp"/>
```

- ```NewFile.jsp```로 이동한다.



```
<jsp:forward page="NewFile1.jsp">
	<jsp:param value="Parker" name="name"/>
	<jsp:param value="qkrrudtjr954.github.io" name="url"/>
</jsp:forward>
```

- 페이지 이동시 parameter를 가지고 갈때 사용하는 코드
- ```<jsp:param>```에 파라미터를 설정한다.


## useBean tag

#### Sample.java


```java
package hello;
public class Sample {
	private String name;
	public Sample() {
		// TODO Auto-generated constructor stub
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	@Override
	public String toString() {
		return "Sample [name=" + name + "]";
	}
}
```


#### scriptlet을 사용한 객체 생성


```
<%
Sample _sample = new Sample();

_sample.setName("sample");
%>
```


- jsp에서 클래스를 선언할때 scriptlet을 사용할 수 있다.


```
${_sample}
```

- ***scriptlet으로 생성된 객체는 el tag로 접근할 수 없다.***
  - 아무것도 출력하지 않음.


#### jsp tag를 사용한 객체 생성


```
<jsp:useBean id="_sample2" scope="request" class="hello.Sample"/>

<jsp:setProperty property="name" name="_sample2" value="sample"/>

<jsp:getProperty property="name" name="_sample2"/>
```

- ```<jsp:useBean>```을 사용해서 객체를 만들 수 있다.
  - ```Sample _sample2 = new Sample();``` 와 동일한 코드


- ```<jsp:setProperty>```를 사용해서 값을 set할 수 있다.
  - ```_sample2.setName("sample");```와 동일한 코드


- ```<jsp:getProperty>```를 사용해서 값을 get할 수 있다.
  - ```_sample2.getName();```와 동일한 코드


```
${_sample2}
```

```
Sample [name=sample]
```

- ***jsp tag로 생성된 객체는 el tag로 접근할 수 있다.***

- bean 은 class를 의미한다.
