---
layout: post
title: "Observer Pattern 옵저버 패턴"
categories:
  - Design Pattern
tags:
  - Java
  - Observer Pattern
  - 옵저버 패턴
  - 디자인 패턴
---



해킹이나 보안 쪽에서 많이 사용되는 옵저버 패턴에 대해 학습한다.
옵저버는 우리가 익숙한 스타크래프트의 그 옵저버와 의미를 같이한다.
정찰, 관찰, 검사 등으로 해석할 수 있으며, 다른 클래스를 감시하는데 사용된다.


#### ObserverClass.java

```java
public class testClass extends Observable {
  private String preArg = null;

  public void notifyObservers(Object arg) {
    String str = (String)arg;

    // 값의 변화가 없다면 옵저버 클래스를 가동하지 않는다.
    if(str.equals(preArg)) return;

    preArg = str;

    //observer 안에 있는 함수 -> reset
    setChanged();

    super.notifyObservers(arg);
    clearChanged();
  }
}
```
.```Observable``` 을 상속받은 ```testClass```는 ```Observer```를 등록하여 값의 변경 등을 감지할 수 있다.


#### ObserverA.java
```java
public class ObserverA implements Observer {

  @Override
  public void update(Observable o, Object arg) {
    // TODO Auto-generated method stub
    String str = (String)arg;

    System.out.println("Observer A: "+str);

  }
}
```

#### ObserverB.java
```java
public class ObserverB implements Observer {

  @Override
  public void update(Observable o, Object arg) {
    // TODO Auto-generated method stub
    String str = (String)arg;

    System.out.println("Observer B: "+str);

  }

}
```
감시를 하기 위한 옵저버 객체 ```ObserverA, ObserverB```

#### Main.java
```java
public class mainClass {
  public static void main(String[] args) {
    // 감시할 대상
    testClass obMan = new testClass();


    // 감시자들 추가
    obMan.addObserver(new ObserverA());
    obMan.addObserver(new ObserverB());

    obMan.notifyObservers("secret chat");

    obMan.notifyObservers("this is classify");
  }
}
```
```
Observer B: secret chat
Observer A: secret chat
Observer B: this is classify
Observer A: this is classify
```

다른 값이 들어오면 변화를 감지하고 문자열을 출력시킨다.
.```Observer``` 들이 변경을 감지할 수 있다.
