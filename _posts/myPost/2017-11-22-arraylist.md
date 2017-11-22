---
layout: post
title: "Java ArrayList"
categories:
  - Java
tags:
  - Java
  - Collection
  - ArrayList

---

이전 포스트에서 [Collection]()에 대한 간단한 설명을 했다.
오늘은 그중 배열과 사용방법이 제일 유사한 배열 리스트 ```ArrayList```에 대해 학습한다.
<br>

## ArrayList

- 배열 처럼 사용할 수 있는 리스트
- 선형(linier) 구조를 가지고 있다.
- 검색 속도가 굉장히 빠르다.
- 배열과 마찬가지로 **index** 로 관리된다.
- [Generic](generic.html)으로 내부의 자료형을 정할 수 있다.

<br>
<br>

#### Main.java

```java
class Main{
  public static void main(String[] args) {
    //Integer 를 담는 ArrayList 생성
    ArrayList<Integer> arrList = new ArrayList<Integer>();
  }
}
```
<br>


## ArrayList 의 기본 사용법


```java
class Main{
  public static void main(String[] args) {
    ArrayList<Integer> arrList = new ArrayList<Integer>();

    System.out.println("------------리스트 끝에 요소 추가------------");
    //.add( element )
    //리스트 끝에 원소 추가
    Integer i = new Integer(111);
    arrList.add(i);   //Integer 객체 생성 후 add ( 정석 )
    arrList.add(222); //자동으로 Integer객체를 생성해서 add
    arrList.add(new Integer(333));


    System.out.println("------------요소 삭제------------");
    //.remove( index )
    //요소 삭제
    arrList.remove(1);	//2번째 자리의 원소를 삭제한다.
                        //배열의 index와 사용방법이 같다.


    System.out.println("------------배열 출력------------");
    //.get(index)
    //index 번째에 있는 객체를 가져온다.
    for (int i=0; i<arrList.size(); i++) {
      System.out.println(arrList.get(i));
    }


    System.out.println("------------원하는 위치에 추가------------");
    //.add(index, element)
    //원하는 위치에 값을 삽입하는 함수
    //2번지는 사라졌기 때문에 1번지에 값을 넣어야 2번지로 값이 들어간다.
    arrList.add(1, 777);


    System.out.println("------------검색------------");
    //.indexOf(element)
    //검색
    //element요소가 있는 index를 반환한다.
    int index = arrList.indexOf(333);
    System.out.println("333의 위치는 "+index+"번지 입니다.");
    //해당값이 없는 숫자면 -1이 반환된다.
    index = arrList.indexOf(10000);
    System.out.println("10000의 위치는 "+index+"번지 입니다.");


    System.out.println("------------수정------------");
    //.set( index, element )
    //원하는 index에 원하는 값으로 수정한다.
    arrList.set(3, 999);


    System.out.println("------------forEach로 출력------------");
    //forEach 문으로 출력이 가능하다.
    for (Integer integer : arrList) {
      System.out.println(integer);
    }
  }
}
```

.```ArrayList```가 기본적으로 제공하는 함수들을 활용하여 데이터를 가공할 수 있다.
사용법은 배열보다는 확실히 가볍고 직관적으로 이해할 수 있다.
하지만 배열보다 함수의 사용에 있어서 오버헤드가 크기 때문에 상황에 맞는 알고리즘을 선택해 사용해야한다.

<br>
<br>
<br>

## 활용

.```ArrayList```를 이용한 ```myClass``` 의 생성, 삽입, 수정, 삭제, 검색

###myClass.java (DTO)
DTO ( Data Transfer Object ) : 데이터의 틀을 담당하는 객체

```java
public class myClass {
  private int num;
  private String name;

  public myClass() {
    // TODO Auto-generated constructor stub
  }

  public myClass(int num, String name) {
    super();
    this.num = num;
    this.name = name;
  }

  public int getNum() {
    return num;
  }

  public void setNum(int num) {
    this.num = num;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  @Override
  public String toString() {
    return "myClass [num=" + num + ", name=" + name + "]";
  }
}
```

## Main.java (DAO)
DAO ( Data Access Object ) : 데이터를 가공하는 객체


```java
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;


public class mainClass {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    ArrayList<myClass> arrList = new ArrayList<myClass>();



    //insert
    System.out.println("--------------------insert----------------------");
    myClass cls = new myClass(1, "park");
    arrList.add(cls);

    arrList.add(new myClass(2, "kyung"));

    cls = new myClass(3, "seok");
    arrList.add(cls);

    //print
    arrList.stream().forEach(System.out::println);


    //insert where you want
    System.out.println("\n------------insert where you want--------------");
    cls = new myClass(4, "jeon");
    arrList.add(2, cls);

    //print
    arrList.stream().forEach(System.out::println);


    //delete
    //lambda -> functional programming -> java 8
    System.out.println("\n------------------delete----------------------");
    List<myClass> result = arrList.stream()
      .filter(my -> !my.getName().equals("kyung"))
      .collect(Collectors.toList());
    //delete kyung
    result.stream().forEach(System.out::println);


    //select
    System.out.println("\n------------------select----------------------");
    String name = "park";
    int findIndex = -1;
    for (int i = 0; i < arrList.size(); i++) {
      myClass my = arrList.get(i);
      if(my.getName().equals(name)) {
        findIndex = i;
        break;
      }
    }
    System.out.println("findIndex = "+findIndex+ " , "+arrList.get(findIndex));

    //edit
    System.out.println("\n------------------edit----------------------");
    cls = new myClass(8, "eun");
    arrList.set(1, cls);
    arrList.stream().forEach(System.out::println);
  }
}
```

```
--------------------insert----------------------
myClass [num=1, name=park]
myClass [num=2, name=kyung]
myClass [num=3, name=seok]

------------insert where you want--------------
myClass [num=1, name=park]
myClass [num=2, name=kyung]
myClass [num=4, name=jeon]
myClass [num=3, name=seok]

------------------delete----------------------
myClass [num=1, name=park]
myClass [num=4, name=jeon]
myClass [num=3, name=seok]

------------------select----------------------
findIndex = 0 , myClass [num=1, name=park]

------------------edit----------------------
myClass [num=1, name=park]
myClass [num=8, name=eun]
myClass [num=4, name=jeon]
myClass [num=3, name=seok]
```

.```myClass``` 객체를 ```ArrayList```를 사용해서 생성 삽입 삭제 등의 관리를 하는 소스코드이다.
리스트를 전부 출력하는 부분에서는 Java8의 람다식을 이용했다. 일반 배열을 사용할때 보다 리스트의 길이 등 신경써줘야할 부분이 현저히 줄어들어 활용하기 편하다.
