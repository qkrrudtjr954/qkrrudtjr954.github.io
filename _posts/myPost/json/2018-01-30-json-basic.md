---
layout: post
title: "[json] json의 기본"
categories:
  - json
tags:
  - json
---

javascript object notation의 약자인 json은 javascript에서 데이터를 주고 받을 때, 편하고 간결하게 사용하기 위해 만들어지고 사용되어집니다.

## json의 사용

![json & xml](https://i.imgur.com/RNS4DAX.png)

- client는 사용자가 원하는 요청을 서버에 보낸다. (검색, 이동 등)
- 서버는 client의 요청을 처리하고 client에게 결과를 응답한다.
- ***이때, 요청에 대한 응답을 xml 또는 json의 형태로 만들어 넘긴다.***
- client는 전달 받은 ***xml 또는 json*** 조합하여 사용자가 보기 편하도록 후처리를 한다.

## Get Started

- json은 한쌍으로 관리가 되어진다.
- 키값으로 value값에 접근할 수 있다.

##### 하나의 값을 저장하는 JSON

```json
"key" : "value"
```

##### 여러개의 값을 저장하는 JSON

```json
{
  "key1" : "value1",
  "key2" : "value2",
  "key3" : "value3"
}
```


## 값의 접근

- json 은 key 와 value가 하나의 pair로 묶여있다.
- 하나의 key값으로 하나의 value값에 접근할 수 있다.


<br>



##### case1

- 하나의 key : value

```javascript
var json1 = {"key" : "value"};

console.log(json1.key);
```

```
value
```


<br>


##### case2

- 여러개의 key : value

```javascript
var human = {
  "name" : "parker",
  "age" : "26",
  "height" : "178"
}

console.log("이름은 "+human.name+"입니다.");
console.log("나이는 "+human.age+"입니다.");
console.log("키는 "+human.height+"입니다.");
```

```
이름은 parker입니다.
나이는 26입니다.
키는 178입니다.
```


<br>


##### case3


- 여러개의 key : value


```javascript
var human = {
  "name" : "parker",
  "age" : "26",
  "height" : "178",
  "friends" : {
    "f1" : "yoon ho",
    "f2" : "jun hyek",
    "f3" : "jae won"
  }
}

console.log("이름은 "+human.name+"입니다.");
console.log("나이는 "+human.age+"입니다.");
console.log("키는 "+human.height+"입니다.");
console.log("친구는 "+human.friends.f1+","+human.friends.f2+","+human.friends.f3+"입니다.");
```

```
이름은 parker입니다.
나이는 26입니다.
키는 178입니다.
친구는 yoon ho,jun hyek,jae won입니다.
```



## 예제


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
  </head>
  <body>

    <p id="demo"></p>

    <script type="text/javascript">
      var emp = [
        {
          "firstname":"kyung seok",
          "lastname":"park"
        },
        {
          "firstname":"hun seok",
          "lastname":"kim"
        },
        {
          "firstname":"kyung chul",
          "lastname":"hong"
        }
      ];

      var txt = "";

      // . 을 사용하여 내부 key에 접근이 가능하다.
      for (var i = 0; i < emp.length; i++) {
        txt += emp[i].firstname + " " + emp[i].lastname + "<br>";
      }
      document.getElementById('demo').innerHTML = txt;


      // json은 이중 배열처럼 접근하는 것도 가능하다.
      for (var i = 0; i < emp.length; i++) {
        txt += emp[i]["firstname"] + " " + emp[i]["lastname"] + "<br>";
      }
      document.getElementById('demo').innerHTML = txt;
    </script>
  </body>
</html>
```
