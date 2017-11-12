---
layout: post
title: "Java 가변 인수"
categories:
  - Java
tags:
  - Java
  - 가변 인수
  - 가변 인자
---



함수를 호출할 때, 사용하는 인자의 값은 한정되어 있다.

만약 여러개의 인자를 보내주고 싶다면, 배열을 선언하고 배열에 값을 넣어 인자로 보내는 방법을 사용하는 방법이 있다.

자바는 배열을 선언하는 방법 외에 ***가변 인자*** 라고 하는 방법이 존재한다. 이름만 풀어서 해석하면 변할 수 있는 인자. 즉, 인자가 자유자재로 변하는 것이 가능하다는 뜻이다.

<br><br>

## 사용 방법

일반 변수를 사용하는 것과 비슷하지만 자료형과 변수명 사이에 ```…```만 추가해주면 함수 내부에서 배열처럼 사용이 가능하다.

```
static int 테스트함수(자료형...변수명){
  변수명[0], 변수명[1], 변수명[2], ...
}
```



<br>

<br>

## 예제 코드

```java
package valiableValiable;

public class mainClass {
  public static void main(String[] args) {
	//disp 함수는 int형 변수를 가변인자로 받고 있다.
    //1부터 7까지 수를 가변인자로 함수에 전달한다.
    int sum = disp(1,2,3,4,5,6,7);

    System.out.println(sum);

    sum = disp2("hello", 1,2,3,4);
    System.out.println(sum);

  }
  static int disp(int... num) {
    //main에서 받은 1부터 7까지의 수를
    //가변인자로 받아 배열처럼 사용한다.
    int sum=0;
    for(int i=0; i<num.length; i++) {
      sum = sum + num[i];         
    }
    //1부터 7까지의 합을 리턴
    return sum;
  }

  //다른 인자와 함께 사용하는 것이 가능하다.
  static int disp2(String str, int...num) {
    int sum=0;
    //str 출력
    System.out.println(str);
    //가변인자 사용
    for(int i=0; i<num.length; i++) {
      sum = sum + num[i];         
    }
    return sum;
  }

}
```

disp2 와 같이 가변인자와 다른 인자를 같이 전송하는 것이 가능 하다.

<br>

***하지만*** 가변인자를 항상 마지막에 두어야한다. 왜냐하면 처음에 가변인자를 두게 되면 어디까지가 가변인자의 인수로 선언되었는지 컴파일러는 확인을 할 수 없기 때문이다.

```java
static void disp2(int...num, int test, int test2) {
  System.out.println(test);
  System.out.println(test2);
  //가변인자 사용
  for(int i=0; i<num.length; i++) {
    System.out.println(num[i]);
  }
}
```

main에서 위와 같은 메소드를  ```disp2(1,2,3,4,5,6,7,8,9,10);``` 이렇게 호출시켰다고 생각한다면, 컴파일러는 가변인자에 1부터 10까지를 넣어야하는지 9까지 넣어야하는지에 대한 정보를 알지 못하기 때문에 컴파일러는 에러를 발생시킨다.
