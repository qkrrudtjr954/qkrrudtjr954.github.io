---
layout: post
title: "Factory Pattern 팩토리 패턴"
categories:
  - Design Pattern
tags:
  - Java
  - Factory Pattern
  - 팩토리 패턴
  - 디자인 패턴
---



디자인 패턴 중에 널리 사용되고 있는 패턴 중에 하나이다.
**Factory** 는 공장이라는 뜻으로 원하는 물건을 찍어낼 수 있는 곳이다.
**Factory Pattern** 은 이와 같은 의미로 사용되며, 원하는 객체를 만들 수 있는 것이다.





## 예제 코드

.```Main``` 클래스에서 ```AnimalFactory```를 사용해서 ```Animal``` 인터페이스를 상속받는 동물 객체를 생성한다.
.```AnimalFactory``` 를 사용하여 다른 동물 객체를 생성하고, 내부 객체 필드 메소드에 접근하는 방법을 사용해보자.

#### Animal.Java
```Java
public interface Animal(){
  public void printDescript();
}
```
동물의 행동을 표현하는 ```Animal``` 인터페이스이다.

<br><br>


#### Dog.java
```Java
public class Dog implements Animal{
  public void printDescript(){
    System.out.println("멍멍!");
  }
  public void dogMethod(){
    System.out.println("강아지입니다.");
  }
}
```

#### Cow.java
```Java
public class Cow implements Animal{
  public void printDescript(){
    System.out.println("음메!");
  }
  public void cowMethod(){
    System.out.println("소입니다.");
  }
}
```


#### Cat.java
```Java
public class Cat implements Animal{
  public void printDescript(){
    System.out.println("야옹!");
  }
  public void catMethod(){
    System.out.println("고양이입니다.");
  }
}
```
.```Animal``` 인터페이스를 상속받는 ```Dog, Cat, Cow``` 클래스

<br><br>



#### AnimalFactory.java
```Java
public class AnimalFactory {
  public static Animal Create(String animalName) {
    if(animalName.equals("")) {
      System.out.println("생성할 클래스가 없습니다.");
    }

    if (animalName.equals("강아지")) {
      return new Dog();
    }else if(animalName.equals("고양이")) {
      return new Cat();
    }else if (animalName.equals("소")) {
      return new Cow();
    }

    return null;
  }

}
```
.```animalName``` 에 따라 다른 동물 객체를 생성한다.

<br><br>

#### Main.java
```java

public class Main {

  public static void main(String[] args) {
    // 고양이 객체 생성
    Animal animal1 = AnimalFactory.Create("고양이");
    animal1.printDescript();
    Cat cat = (Cat)animal1;
    cat.CatMethod();
    // 소 객체 생성
    Animal animal2 = AnimalFactory.Create("소");
    animal2.printDescript();
    Cow cow = (Cow)animal2;
    cow.CowMethod();
    // 강아지 객체 생성
    Animal animal3 = AnimalFactory.Create("강아지");
    animal3.printDescript();
    Dog dog = (Dog)animal3;
    dog.DogMethod();
  }
}
```
객체를 생성할 때, ```new``` 키워드를 사용하는 것이 아니고, ```AnimalFactory``` 내부 ```Create(String animalName)``` 에 생성하고 싶은 동물 객체의 이름을 보내면 객체가 반환된다.

***하나의*** ```AnimalFactory``` ***로 여러개의 객체를 생성하고 사용할 수 있다는 장점을 갖는다.***
