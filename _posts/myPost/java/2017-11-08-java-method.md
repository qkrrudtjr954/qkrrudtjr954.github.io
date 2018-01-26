---
layout: post
title: "Java 메소드"
categories:
  - Java
tags:
  - Java
  - 함수
  - 메소드
  - function
---

함수를 빼곤 프로그래밍을 얘기할 수 없을 정도로 함수는 중요한 역할을 한다. 특정 기능을 함수에 위임하여 코드를 더 직관적이고 단순하게 만들 수 있기 때문이다.

***메소드와 함수는 같은 의미를 갖고, 명칭을 혼용해서 사용한다. 결국 같은말이다.***

프로그래밍에서의 함수( 메소드 )는 수학에서의 함수와 그 의미를 같이한다.

+ 입력값이 주어진다. (없을 수도 있다.)
+ 입력값에 대한 특정 식(처리)를 실행한다.
+ 처리를 마치고 식에 대한 결과값을 돌려준다. (없을 수도 있다.)

<br><br><br>

## 메소드의 사용방법

```
리턴타입	함수이름	(입력타입	파라미터){
	---사용자 정의 함수(기능 실행)---
  return 리턴값;
}
```

+ 리턴 타입 : 함수가 종료된 후 돌려주어야할 값의 데이터 타입을 명시한다.
+ 함수 이름: 함수를 호출할 때 사용되는 함수의 이름을 정의한다.
+ 입력 타입: 입력값의 데이터 타입을 명시한다.
+ 파라미터
  + 인자, 인수, 입력값이라고도 불린다.
  + 호출할때 입력받은 값이 파라미터 변수에 복사되어 저장된다.
  + 정의된 함수 내에서 변수로 활용할 수 있다.
  + 파라미터가 없는 함수도 있다.
+ 리턴값
  + 입력받은 파라미터를 통해 정의된 기능을 수행하여 생성된 값을 돌려준다.
  + 하나의 함수는 하나의 결과값만을 리턴한다.
  + 리턴값이 없는 함수도 있다.



<br><br><br>

## 메소드의 여러가지 정의 방법

1. 입력값도 있고 반환값도 있는 메소드

![입력값도 있고 반환값도 있는 함수 사진](https://i.imgur.com/6qYgrtr.png)



```java
class methodClass{
  public static void main(String[] args){
    int i;
    System.out.println("호출 순서1 : 함수 호출합니다!");
    i = plusTen(10);	//10(intput)을 전달하면서 함수를 호출한다.
    									//그리고 반환되는 값을 i에 저장한다.
    System.out.println("호출 순서4 : 함수 호출 후 i의 값:\t"+i);
  }
  //number 변수에 main에서 전달한 10을 복사하여 plusTen 함수에서 사용한다.
  static int plusTen(int number){
    int returnNum;
    System.out.println("호출 순서2 : plusTen 함수에 들어왔습니다!");
    returnNum = number + 10;
    System.out.println("호출 순서3 : 10을 더한값을 리턴합니다.");
    return returnNum;
  }
}
```

```
호출 순서1 : 함수 호출합니다!
호출 순서2 : plusTen 함수에 들어왔습니다!
호출 순서3 : 10을 더한값을 리턴합니다.
호출 순서4 : 함수 호출 후 i의 값:	20
```

<br>

2. 입력값이 없고 반환값만 있는 함수



![입력값이 없고 반환값만 있는 함수 그림](https://i.imgur.com/s0BZ1u0.png)

```java
class methodClass{
  public static void main(String[] args){
    System.out.println("호출 순서1 : 함수를 호출합니다!");
    //아무것도 입력값으로 주지 않고 함수를 호출했다.
    //str변수에 getString()의 반환값 String을 저장한다.
    String str = getString();
    System.out.println(str);
    System.out.println("호출 순서4 : main 함수를 종료합니다.");
  }
  //반환값의 타입은 String이고 입력값은 비어있는 함수
  //== 아무것도 입력 받지 않고 문자열을 반환해주는 함수
  static String getString(){
    System.out.println("호출 순서2 : getString()함수에 들어왔습니다!");
    String methodStr = "hello world!";
    System.out.println("호출 순서3 : String을 반환합니다!");
    return methodStr;	//정의한 String을 반환한다.
  }
}
```

```
호출 순서1 : 함수를 호출합니다!
호출 순서2 : getString()함수에 들어왔습니다!
호출 순서3 : String을 반환합니다!
hello world!
호출 순서4 : main 함수를 종료합니다.
```

<br>

3. 반환값 없이 입력만 받는 함수![반환값 없이 입력만 받는 함수](https://i.imgur.com/WUtZmLz.png)

```java
class methodClass{
  public static void main(String[] args){
    System.out.println("호출 순서1 : 함수를 호출합니다!");
    printChar('a');	//문자를 인자로 전달합니다.
    System.out.println("호출 순서4 : main 함수를 종료합니다.");
  }

  //입력값은 문자이고 반환값은 없는 함수
  static void printChar(char ch){
    System.out.println("호출 순서2 : printChar()함수에 들어왔습니다!");
    //메인 메소드에서 전달된 char값을 ch로 복사한 후 전달한다.
    System.out.print("당신이 입력한 문자는~\t"+ch+"입니다!");
    System.out.println("호출 순서3 : char를 출력합니다!");
  }
}
```

```
호출 순서1 : 함수를 호출합니다!
호출 순서2 : printChar()함수에 들어왔습니다!
당신이 입력한 문자는~	a입니다!
호출 순서3 : char를 출력합니다!
호출 순서4 : main 함수를 종료합니다.
```

<br>

4. 입력값도 없고  출력값도 없는 함수

![입력값 없고 반환값 없는 함수 사진](https://i.imgur.com/nhBQo8j.png)

```java
class methodClass{
  public static void main(String[] args){
    System.out.println("호출 순서1 : 함수를 호출합니다!");
	printSomething();	//입력값도 없고 출력값도 저장하지 않는다.
    System.out.println("호출 순서4 : main 함수를 종료합니다.");
  }

  //인자값도 없고 리턴값도 없다.
  static void printSomethig() {
    System.out.println("호출 순서2 : printSomethig()함수에 들어왔습니다!");
		//local 배열은 printSomething 함수 안에서 선언되고 출력되었다.
    //main에서 전달 받은 인자도 없고
    //main으로 다시 돌려주어야할 결과값도 없다.

    //printSomething 내부에서도 main의 내부에서 처럼 변수의 선언과 사용이 가능하다.
    int local[] = {1,2,3,4,5};
    //하지만 main과는 별개의 함수이므로 아무런 영향을 주지 않는다.
    for(int i=0; i<local.length; i++){
      System.out.println("printSomething에서 출력: "+local[i]);
    }
    System.out.println("호출 순서3 : main에 아무것도 돌려주지 않습니다!");
  }
}

```

```
호출 순서1 : 함수를 호출합니다!
호출 순서2 : printSomethig()함수에 들어왔습니다!
printSomething에서 출력: 1
printSomething에서 출력: 2
printSomething에서 출력: 3
printSomething에서 출력: 4
printSomething에서 출력: 5
호출 순서3 : main에 아무것도 돌려주지 않습니다!
호출 순서4 : main 함수를 종료합니다.
```

<br><br><br>

## 정리

메소드는 여러가지의 형태로 정의하고 사용할 수 있다.

+ 입력값이 없고 리턴값만 있는 경우
+ 입력값이 있고 리턴값이 없는 경우
+ 입력값과 리턴값이 모두 있는 경우
+ 입력값과 리턴값이 모두 없는 경우

상황에 맞게 정의하고 사용할 수 있다. 그리고 메소드 예제코드를 보면서 ***main메소드에서 다른 메소드를 사용할 때 실행되는 순서를 주의깊게 확인한다면*** 메소드가 어떤 방식으로 동작하는지 이해하는데 큰 도움을 줄 것이다.
