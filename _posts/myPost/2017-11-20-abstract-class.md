---
layout: post
title: "Java 추상(abstract) 클래스"
categories:
  - Java
tags:
  - Java
  - 추상 클래스
  - 추상 메소드
  - abstract
---





자바의 클래스에는 ***추상(abstract)*** 가 존재한다.
추상은 형식이 구현되지 않은 추상적인 메소드나 클래스를 나타낼 때 사용된다.





#### Abstract.java

```java
abstract class AbstractClass{
  //추상 메소드
  abstract public void abstractMethod();

  //일반 메소드
  public void method(){
    System.out.println("일반 메소드");
  }
}
```
위는 간단한 추상 클래스에 추상 메소드를 정의한 것이다.
추상 메소드의 특징
+ 완성이 되지 않은 선언만 되어 있는 요소(메소드, 클래스)
+ 하나 이상의 추상 메소드를 포함하고 있는 클래스
+ 독립적인 객체 생성은 불가능하다
+ 반드시 다른 클래스가 상속을 한 후 추상 메소드의 내부를 정의해야한다.
<br>
<br>

#### Child.java

```java
class Child extends AbstractClass{
  public void abstractMethod(){
    System.out.println("오버라이드한 추상 메소드");
  }
}
```
위 ```AbstractClass```를 상속하는 ```Child``` 클래스는 반드시 ```abstractMethod()```를 오버라이딩 하고 구체적인 구현을 해야한다.


#### Main.java
```java
class Main{
  public static void main(String[] args) {
    //생성할 수 없다.
    //추상클래스는 독립적으로 생성할 수 없다.
    AbstractClass ab = new AbstractClass(); //에러

    //반드시 상속한 객체로 생성해야한다.
    Child abChild = new Child();
    //자식 클래스에서 오버라이딩한 메소드 출력
    abChild.abstractMethod();
    abChild.method();


    //자바의 다형성에 의한 선언도 가능하다.
    AbstractClass abChild2 = new Child();
    abChild2.abstractMethod();
    abChild2.method();

  }
}
```
```
오버라이드한 추상 메소드
일반 메소드
오버라이드한 추상 메소드
일반 메소드
```

<br>
## 정리
추상 클래스는 구현을 하지 않고 선언만한 추상 메소드를 1개 이상 갖고 있는 클래스를 의미한다.
추상 클래스는 독립적으로 선언이 될 수 없고, 추상 클래스를 상속한 자식클래스가 추상 클래스의 추상 메소드를 정의해야 객체로 생성이 될 수 있다.
