---
layout: post
title: "Java 다형성 ( 오버로딩, 오버라이딩 )"
categories:
  - Java
tags:
  - Java
  - 오버로딩
  - 오버라이딩
  - 다형성
---


자바의 다형성은 ***객체를 다양한 형태로 사용하고 관리할 수 있는 자바의 대표적인 특징*** 중 하나이다.

+ 오버라이딩
+ 오버로딩
+ 상속의 다형성


<br><br>


## 오버로딩

오버로딩은 하나의 객체에서 이름이 같은 메소드를 여러개 정의하여 사용하는 것이다.

***단, 메소드에 전달되는 인자의 종류와 갯수는 달라야한다.***

#### OverLoading.java

```java
class OverLoading{
  //함수의 이름은 모두 같지만,
  //전달받는 인자의 타입과 갯수는 전부 다르다.
  public void overLoad(){
    System.out.println("This is overLoad()");
  }
  public void overLoad(int i){
    System.out.println("This is overLoad(int i) : "+i);
  }
  public void overLoad(String str){
    System.out.println("This is overLoad(String str) : "+str);
  }
  public void overLoad(int i, String str){
    System.out.println("This is overLoad(int i, String str) : "+i+", "+str);
  }
}
```

#### Main.java

```java
public class Main {
  public static void main(String[] args) {
    OverLoading ol = new OverLoading();
    //메소드의 이름은 모두 같지만 인자값은 다르다.
    //인자의 타입에 맞는 메소드가 자동으로 실행된다.
    ol.overLoad();
    ol.overLoad(10);
    ol.overLoad("over load");
    ol.overLoad(20, "over load2");
  }
}
```

```
This is overLoad()
This is overLoad(int i) : 10
This is overLoad(String str) : over load
This is overLoad(int i, String str) : 20, over load2
```



<br><br><br>

## 오버라이딩

오버라이딩이란 상속을 받은 하위 객체가 상위 객체의 메소드를 새롭게 정의하고 그대로 덮어쓰고 사용하는 것을 말한다.

***하위 객체의 메소드 이름과 인자값의 타입은 상위 객체의 메소드와 반드시 일치해야 한다.***

####SuperClass.java

```java
public class SuperClass {
  public void method1(){
    System.out.println("SuperClass method1()");
  }
  public void method2(String str){
    System.out.println("SuperClass method2(String str)"+str);
  }
}
```

#### ChildClass.java

```java
public class ChildClass extends SuperClass {
  public void method1(){
    System.out.println("ChildClass method1()");
  }
  public void method2(String str){
    System.out.println("ChildClass method2(String str) : "+str);
  }
}

```
#### Main.java

```java
public class Main {
  public static void main(String[] args) {
    ChildClass cc = new ChildClass();

    cc.method1();
    cc.method2("world");
  }
}
```

```
ChildClass method1()
ChildClass method2(String str) : world
```

원래 부모 클래스를 상속한 자식 클래스에서 부모의 메소드를 호출하면 부모 클래스에 정의된 메소드가 호출된다.
하지만 ```ChildClass```의 메소드가 ```SuperClass```의 메소드를 오버라이딩한다면 ```ChildClass```에 정의된 메소드가 실행된다.
<br>
<br>
<br>




## 상속의 다형성
자바의 상속은 많은 형태의 변화를 가능하게 한다.
상위 클래스를 상속하는 하위 클래스는 상위 클래스로 정의될 수 있다.
```java
class AAA{  
  public void method(){
    System.out.println("super!")
  }
}
```




```java
class BBB extends AAA{  
  public void methodBBB(){
    System.out.println("child bbb!")
  }
}
```




```java
class CCC extends AAA{  
  public void methodCCC(){
    System.out.println("child ccc!")
  }
}
```



```java
class Main{  
  public static void main(String[] args) {
    BBB b = new BBB();  //보통의 정의
    CCC c = new CCC();

    AAA b2 = new BBB(); //부모의 클래스로도 정의가 가능하다.
    AAA c2 = new CCC(); //자바의 다형성


    b2.method();  //접근 가능
    b2.methodBBB(); //접근할 수 없다.

    c2.method();  //접근 가능
    c2.methodCCC(); //접근할 수 없다.
  }
}
```
자식의 클래스가 부모의 클래스를 상속하고 있을때, 부모의 클래스로 정의할 수 있다.
이렇게 정의하게 되면 ```AAA```의 자식 클래스들을 ```AAA```타입으로 관리할 수 있다.
***하지만, 부모의 클래스로 정의된 자식 클래스는 부모 클래스의 멤버에는 접근할 수 있지만 자신의 클래스 멤버에는 접근할 수 없다.***
<br>
<br>
<br>

SuperClass 를 상속받는 ```Child1``` 과 ```Child2``` 클래스가 있다.


```java
class Main{
  public static void main(String[] args){
    //Child1 의 객체를 담는 배열
    Child1 ch[] = new Child1[3];

    ch[0] = new Child1();
    ch[1] = new Child1();
    ch[2] = new Child1();

    ch[0].method();
    ch[1].method();

    //Child2 의 객체를 담는 배열
    Child2 ch2[] = new Child2[3];

    ch2[0] = new Child2();
    ch2[1] = new Child2();
    ch2[2] = new Child2();

    ch2[0].method();
    ch2[1].method();
    // Child1과 Child2를 따로 관리해주어야하는 불펀함이 있다.


    //SuperClass 타입 하날 관리를 해줄 수가 있다.
    SuperClass child1 = new Child1();
    SuperClass child2 = new Child2();

    //Child1, Child2의 관리를
    //하나의 클래스(부모 클래스)로 관리가 가능하다
    SuperClass superArr[] = new SuperClass[4];
    superArr[0] = new Child1();
    superArr[1] = new Child2();
    superArr[2] = new Child1();
    superArr[3] = new Child2();

    //child1에 정의된 메소드를 실행하면
    //에러가 난다. (부모클래스로 정의되었기 때문)
    superArr[0].child1Method();
    // 부모 클래스의 영역 만을 갖고 있기 때문에
    // 자식 클래스의 영역의 메소드에는 접근할 수가 없다.

    //부모 클래스로 정의된 자식 클래스를
    //자식 클래스로 형변환한다.
    Child1 temp = (Child1)superArr[0];
    temp.child1Method();
    //강제 변환을 통해 범위에 없는 메소드에 접근이 가능하다.


    child1.method();
    child2.method();

    //      Child1 ch1 = new Child1();
    //      ch1.method();
    //      
    //      Child2 ch2 = new Child2();
    //      ch2.method();
  }
}
```
부모 클래스로 정의된 자식 클래스는 부모 클래스로서 다뤄질 수 있다. 이는 자바의 가장 큰 특징 중에 하나인 ***다형성*** 에 속한다.
부모 클래스로 정의된 자식 클래스는 자기 자신의 멤버에겐 접근하지 못하는 제한 사항이 있는데 이는 캐스팅 형변환을 통해 접근이 가능하다.
