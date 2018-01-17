---
layout: post
title: "[javaScript] 자바스크립트의 상속"
categories:
  - JavaScript
tags:
  - javaScript
  - 자바 스크립트
  - 자바 스크립트 상속
  - inheritance
---


상속은 이미 작성된 코드를 재사용하는 아주 훌륭한 방법이다.
객체지향 방법론으로 잘 설계된 프로그램은 상속 개념을 효율적으로 사용하고 있을 것이다.


## 자바스크립트의 상속

- 자바스크립트는 객체지향 언어이기 때문에 객체에 대한 상속을 나타내줄 수 있다.

#### 예제

```javascript
function Man(){
  this.name = "Anonymous";
  this.gender = "Man";
  this.Run = function (){
    return this.name+" is Running.";
  }
  this.Sleep = function () {
    return this.name+" is Sleeping."
  }
}
```


- ```Man``` 속성을 가진 객체 생성

<br>



```javascript
function SoccerPlayer (){
  this.base = new Man();
  this.name = "Anonymous Soccer Player.";
  this.Run = function () {
    // overriding 이 가능하다.
    return this.base.Run();
  }
  this.Pass = function () {
    return this.name+" is passing to other player!";
  }
};
```


- ```SoccerPlayer``` 속성을 가진 객체 생성

<br>



```javascript
SoccerPlayer.prototype = new Man();
var player = new SoccerPlayer();
```


- ```SoccerPlayer``` 의 원형은 ```Man``` 이다.
- ```SoccerPlayer``` 로 객체화한다.

<br>



```javascript
player.name;  // Anonymous Soccer Player.
player.gender;  // Man
player.Run(); // Anonymous is Running.  원형의 메소드를 실행한다.
player.Pass(); // Anonymous Soccer Player is passing to other player!
player.Sleep(); // Anonymous Soccer Player is Sleeping.
```

- ```player.name``` 은 ```SoccerPlayer``` 객체의 이름이 출력된다.
- ```player.gender```는 부모 클래스의 성별이 출력된다.
- ```player.Run()``` 는 부모 클래스의 함수를 호출하기 때문에 이름이 ```Anonymous Soccer Player```가 아닌 ```Anonymous``` 이다.
- ```player.Pass();```와 ```player.Sleep();```은 자식클래스로 객체화 되었기 때문에 이름이 ```Anonymous Soccer Player```이다.
