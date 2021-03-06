---
layout: post
title: "Java final"
categories:
  - Java
tags:
  - Java
  - final
---


자바의 예약어 중 간혹 등장하는 ```final```이 무엇인지 알아보고 어디에 사용되는지 학습한다.





## final과 변수
final은 앞으로 더이상 변하지 않는 변수, 메소드, 클래스를 정의하는데 사용된다.


```java
public static void main(String[] args) {
  int num = 10; //변수
  fianl int num2 = 20;  //변수를 상수로 변경

  num = 30;
  System.out.println(num);  //num이 30으로 변경된다.

  num2 = 40;  //에러가 난다.
}
```


***final을 사용하면 변수가 아닌 변경할 수 없는 상수가 되기 때문에***, 값을 변경하려 하면 에러가 난다.


<br>
<br>
<br>

## final과 class

final은 변수에만 사용되는 것이 아니다.

#### Super.java
```java
final class Super{
  //final로 정의된 Super 클래스
}
```

#### Child.java
```java
class Child extends Super{
  //에러가 난다.
}
```


final로 정의된 class는 더이상 상속할 수 없다.
때문에 ```final```로 정의된 ```Super```클래스는 상속될 수 없고, 이를 상속한 ```Child```클래스는 에러를 발생 시킨다.
<br>
<br>
<br>

## final과 method

final은 메소드에도 사용이 가능하다.
#### Super.java
```java
class Super{
  public void method(){
    System.out.println("Super Class method!");
  }
  final public void finalMethod(){
    System.out.println("Super Class final method!");
  }
}
```
#### Child.java
```java
class Child extends Super{
  public void method(){
    System.out.println("Child Class method!");
  }
  //에러가 발생한다.
  public void finalMethod(){
    System.out.println("Child Class final method!");
  }
}
```
fianl을 선언하면 더이상 변경하지 않겠다는 의미이기 때문에 final로 정의된 메소드는 상속 후 ***오버라이딩*** 될 수 없다.

<br>
<br>
<br>

## 정리
final로 선언된 변수, 메소드, 클래스는 더이상 변경될 수 없다는 의미를 가지며
***메소드는 하위 클래스에서 오버라이딩 될 수 없고***,
***클래스는 더이상 상속을 할 수 없다.***.
