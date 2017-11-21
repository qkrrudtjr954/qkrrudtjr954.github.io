---
layout: post
title: "Java 의 다형성에 접근하는 방법"
categories:
  - Java
tags:
  - Java
  - 다형성
  - instanceof
---



[자바의 다형성](https://qkrrudtjr954.github.io/java/2017/11/17/overloading-overriding.html)에 의해 부모의 클래스로 정의된 자식 클래스는 자신의 멤버에 접근할 수 없다.

하지만 접근할 수 있는 방법이 없는 것은 아니다.

자식 클래스가 자신의 멤버에 접근하는 방법을 학습하고, 부모 클래스로 형성된 객체의 타입을 확인하는 방법을 학습해보자.

<br>

<br>


## 다형성 예제

#### AAA.java


```java
class AAA {
  public void methodAAA(){
    System.out.println("AAA method");
  }
}
```

#### BBB.java

```java
//AAA를 상속받는 클래스
class BBB extends AAA {
  public void methodBBB(){
    System.out.println("BBB method");
  }
}
```


#### CCC.java

```java
//AAA를 상속받는 클래스
class CCC extends AAA {
  public void methodCCC(){
    System.out.println("CCC method");
  }
}
```


#### Main.java
```java
class Main{
  public static void main(String[] args) {
    //부모의 클래스로 자식 클래스의 객체를 생성할 수 있다.
    AAA arrAAA[] = new AAA[2];

    AAA b1 = new BBB();
    AAA c1 = new CCC();
    //하나의 배열로 여러 자식 클래스를 관리할 수 있다.
    arrAAA[0] = b1;
    arrAAA[1] = c1;

    //부모 클래스의 메소드에 접근할 수 있다.
    b1.methodAAA();//==arrAAA[0].methodAAA();
    c1.methodAAA();

    //하지만 부모의 클래스로 정의되었기 때문에
    //자기 자신의 멤버에는 접근할 수 없다.
    //에러가 난다.
    b1.methodBBB();
    c1.methodCCC();
  }
}
```
다형성을 위해 부모의 클래스로 형성된 객체는 자신의 멤버에는 접근할 수 없다.
***하지만, 접근할 수 있는 방법이 없는 것은 아니다.***
<br>
<br>

## 강제 형변환



<p>
부모 클래스로 선언되어 자기 자신의 멤버에 접근할 수 없는 객체는 _강제 형변환_ 을 통해 부모 클래스로 정의된 객체의 형을 자신의 클래스로 강제 변경하는 것이다.
</p>



#### Main.java


```java
class Main{
  public static void main(String[] args) {
    AAA arrAAA[] = new AAA[2];

    //부모의 클래스로 자식 클래스의 객체를 생성할 수 있다.
    AAA b1 = new BBB();
    AAA c1 = new CCC();

    //하나의 배열로 여러 자식 클래스를 관리할 수 있다.
    arrAAA[0] = b1;
    arrAAA[1] = c1;

    //부모 클래스의 메소드에 접근할 수 있다.
    b1.methodAAA();//==arrAAA[0].methodAAA();
    c1.methodAAA();//==arrAAA[1].methodAAA();

    //b1을 BBB로 강제 형변환하였다.
    //형변환 방법은 일반 변수의 형변환과 같다.
    BBB b2 = (BBB)b1;
    //c1을 CCC로 강제 형변환하였다.
    CCC c2 = (CCC)c1;

    //정상적으로 접근이 가능하다.
    b2.methodBBB();
    c2.methodCCC();
  }
}
```
<code>arrAAA</code> 배열에 자식 객체를 저장하고 관리할 수 있다. 각 원소는 자식 클래스의 객체를 담고 있기 때문에 ```arrAAA[0].method()``` 같은 접근도 가능하다.
<br>
<br>
***그렇다면, 배열에 저장된 객체가 어떤 자식 클래스(BBB or CCC)를 나타내는지 확인할 수 있는 방법은 무엇일까?***
<br>
<br>
## instanceof

이럴때 사용하는 것이 ```instanceof``` 예약어 이다.
#### 사용방법
```
(클래스 객체) instanceof (클래스 이름)
```
**클래스 객체가 클래스 이름과 일치하면 true를 일치하지 않으면 false를 반환한다.**
<br>
#### Main.java


```java
class Main{
  public static void main(String[] args) {
    AAA arrAAA[] = new AAA[2];

    //부모의 클래스로 자식 클래스의 객체를 생성할 수 있다.
    AAA b1 = new BBB();
    AAA c1 = new CCC();

    //하나의 배열로 여러 자식 클래스를 관리할 수 있다.
    arrAAA[0] = b1;
    arrAAA[1] = c1;

    for (int i=0; i < arrAAA.length; i++) {
      if(arrAAA[i] instanceof BBB){
        //arrAAA[i]의 객체가 BBB클래스이면 true
        System.out.println("This is BBB class");
      }else if(arrAAA[i] instanceof CCC){
        //arrAAA[i]의 객체가 CCC클래스이면 true
        System.out.println("This is CCC class");
      }
    }
  }
}
```
```
This is BBB class
This is CCC class
```
<br>
첫번째 원소는 ```BBB``` 클래스이고 두번째 원소는 ```CCC``` 클래스이기 때문에 다음과 같은 결과값이 나온다.
```instanceof``` 를 사용하면 객체가 어떤 클래스의 객체인지 확인할 수 있다.
