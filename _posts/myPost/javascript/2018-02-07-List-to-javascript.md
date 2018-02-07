---
layout: post
title: '[javascript] List 객체를 javascript로 parsing하는 방법'
categories:
  - javascript
tags:
  - javascript
  - List
  - List2javascript
  - List파싱
---


html이나 jsp가 갖는 ```List``` 객체를 javascript 리스트로 파싱하는 방법을 제시한다.


## jsp 객체에 접근

```javascript
alert("<%=list.get(0).getName()%>");
```

- javascript를 사용해서 jsp List객체에 접근할 수 있다.



## List 파싱하기


#### 1. json으로 파싱하기



```javascript
//json 으로 가져온다.
var myList = {
  number:"<%=list.get(0).getNumber()%>",
  name: "<%=list.get(0).getName()%>"
};
```

- 반복문을 적절히 사용하여 myList를 세팅할 수 있다.


#### 2. list

```javascript
// list로 가져온다.d
var mylist = [];
var loop=0;

<%
for(int i=0; i<list.size(); i++){
  %>
  mylist[loop] = {
    number:"<%=list.get(i).getNumber()%>",
    name: "<%=list.get(i).getName()%>"
  };
  loop++;
  <%
}
%>

for(i=0; i< mylist.length; i++){
  console.log("list: "+mylist[i]);
}
```

- javascript 내부에서 scriptlet을 사용할 수 있다.
- scriptlet을 사용한 반복문으로 mylist를 파싱한다.
