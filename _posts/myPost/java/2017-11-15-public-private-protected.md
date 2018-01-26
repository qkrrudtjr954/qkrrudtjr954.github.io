---
layout: post
title: "Java 접근 지정자"
categories:
  - Java
tags:
  - Java
  - 접근 지정자
  - public
  - private
  - protected
---

자바는 클래스가 클래스에 접근하는 것을 제한할 수 있다.

자신의 클래스 멤버를 개방하여 다른 클래스에서 멤버들을 가져다 사용할 수 있도록 할 수도 있고, 외부에서 자신의 멤버에 아예 들어올 수 없도록, 통제하는 방법도 있다.

이런 제한을 걸어주는 예약어를 ***접근 지정자*** 라고 한다.

접근 지정자에는 3가지 종류가 있다.

1. public
2. private
3. protected

<br><br>

## Public

```public``` 은 main 함수를 사용하면 무조건 마주치는 접근 지정자이다.

'공공의' 라는 뜻으로 이 지정자가 붙은 클래스나 멤버 변수, 멤버 메소드는 다른 클래스에서 얼마든지 참조가 가능하다.

#### Test.java

```java
class Test{

  public int hello = "123";

  public void testMethod(){
    System.out.println("This is public!");
  }
}
```

#### Main.java

```java
class Main{
  public static void main(String[] args){
    Test test = new Test();
    //public 멤버 변수에 접근한다.
    System.out.println(test.hello);
    //public 멤버 메소드에 접근한다.
    test.testMethod()
  }
}
```

```
123
This is public!
```

클래스 자체가 ```private``` 나 ```protected``` 가 아닌 이상 ```public``` 으로 선언된 모든 멤버는 외부에서 참조가 가능하다.

하지만 변경이 되어서는 안될 멤버에 ```public``` 을 선언하면 보안상 큰 문제가 될 수 있으니 조심해야 한다.

<br><br>

## Private

```private``` 는 클래스 내부에서만 사용이 가능하고 외부에서는 절대 직접 접근할 수 없다.

```private``` 지정자가 등록된 변수에 값을 가지고 오고 싶다면 ```getter``` 함수를 이용해서 가지고 올 수 있지만, 변수에 직접 접근할 수는 없다.

#### Test.java

```java
class Test{
  private int secret = 142;

  void testMethod(){
    System.out.println("This is private"+secret);
  }
  public int getSecret(){
    return this.secret;
  }
}
```

#### Main.java

```java
class Main{
  public static void main(String[] args){
    Test test = new Test();
    test.secret = 3;	//접근 지정자가 private이기 때문에
    					//해당 코드는 에러가 난다.
    test.testMethod();	//클래스 내부에서는 접근이 가능하기 때문에
    					//This is private142 를 출력한다.
    //secret의 값을 가지고 올 수는 있다.
    //하지만 secret 변수에 직접 접근해서 가지고 온 것이 아니고
    //secret의 복사본을 넘겨 받은 것이다.
    int temp = test.getSecret();
    System.out.println(temp);
  }
}
```

```
This is private142
142
```

외부 클래스에서 절대 접근하면 안되거나 변경되어서는 안되는 중요한 변수에 있어서는 ```private``` 지정자를 써준다.

멤버 변수 뿐 아니라 멤버 메소드 역시 ```private``` 로 지정되면 내부에서는 사용가능하지만 외부에서 참조 사용은 불가능하다.

<br><br>





## Protected

```protected``` 지정자는 동일한 패키지에 포함되어 있는 클래스와 자신을 상속하는 하위 클래스만 접근할 수 있도록 해주는 지정자이다.

실제로 사용되는 빈도는 낮다고 한다.

+ 동일한 패키지 안에 있는 다른 클래스 파일에 ```protected```가 지정된 멤버가 있다면 ```public``` 처럼 사용이 가능하다.
+ 상속하고 있는 상위 클래스의 멤버 중 ```protected``` 가 지정된 멤버가 있다면  ```public``` 처럼 사용이 가능하다.
+ 동일한 패키지가 아니거나 상속하는 경우가 아니라면 클래스의 멤버는 ```private``` 처럼 취급되어 접근할 수없다.
