---
layout: post
title: "Singleton Pattern 싱글톤 패턴"
categories:
  - Design Pattern
tags:
  - Java
  - Singleton Pattern
  - 싱글톤 패턴
  - 디자인 패턴
---
디자인 패턴 중 가장 많이 사용하는 패턴의 종류로 여러 클래스가 하나의 공통 변수를 중재할 때 많이 사용된다.
싱글턴의 가장 큰 특징은 ***메모리상에 하나의 인스턴스*** 만을 갖는 것이다.


<br>
<br>


## Singletone Pattern

![a클래스와 b클래스의 값 주고받기](https://i.imgur.com/dhfimPj.png)


A class 의 값을 B class 가 필요로 한다면, Main class 에서 A class 의 값을 get 하고 B class 에 set 해야한다.
이때, 반드시 Main을 거치지 않고 (Main 몰래) 값을 전달하고 받는 패턴이 ```Singletone Pattern``` 이다.


![싱글톤 패턴](https://i.imgur.com/etof3BM.png)

Main class 가 아닌 Singletone class를 만들어서 값을 주고 받는다.
Singletone class 의 멤버는 다른 클래스들에 의해 공유되어야 하기 때문에, 여러개의 객체가 생성되면 안된다.
그렇기 때문에 ```Singletone class``` 객체는 여러개가 생성되지 않고 딱 하나의 인스턴스만 생성되어 heap 메모리에 생성되고 나머지 클래스들이 이를 공유한다.
Singletone이 중재자가 되어, 하나의 인스턴스를 사용해 값을 주고 받는다.

<br><br>


#### Singleton.java
```java
class Singleton{
  private static Singleton instance = null;

  private Singleton{
    // default constructor
  }

  public static Singleton getInstance(){
    if(instance == null){
      instance = new Singleton();
    }
    return instance;
  }
}
```
위는 싱글톤의 기본 클래스이다. ```instance```(객체) 는 ```static``` 으로 선언되어 객체화 없이 접근이 가능하다.
하지만 ```private```이기 때문에 외부에서 ```new```로 선언할 수 없다.

<br>

#### Singletone 객체 접근
Singletone 객체는 ```Singletone class``` 내부에 선언된 ```getInstance()``` 메소드로만 접근할 수 있다.
메소드 ```getInstance()```를 사용해서 생성된 인스턴스가 **없다면** 인스턴스를 생성해서 리턴하고,
이미 생성된 인스턴스가 **있다면** 멤버 인스턴스를 리턴한다.

위와 같은 방법을 통해 메모리에는 단 하나의 Singletone 객체만 생성되고 사용되며, 객체 내부의 멤버들이 여러 클래스에 의해 공유될 수 있다.

![여러 클래스의 싱글톤 객체 접근](https://i.imgur.com/EAwIjs2.png)
