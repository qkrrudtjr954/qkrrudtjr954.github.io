---
layout: post
title: "Scanner를 통한 input"
categories:
  - Java
tags:
  - Java
  - input
  - Scanner
  - java.util.Scanner
---

자바 콘솔에서 입력을 변수의 데이터 타입별로 입력을 받은 후, 변수에 저장하고 콘솔에 출력하는 방법까지 과정을 학습합니다.

+ 자바의 입출력( 스캐너를 사용한 입력, println과 printf를 이용한 출력 )



## 자바의 입출력
자바의 입력은 스캐너를 사용한 입력 이 외에도 많지만, 콘솔을 이용한 입출력을 할때는 [java.util.Scanner](https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html) 클래스를 이용한다.
+ Scanner class를 import 한다.
	+ main method는 Scanner가 어디에 있는지 알수가 없다.
	+ 폴더에 파일의 경로를 입력해주듯이 main method에 Scanner가 저장되어 있는 곳을 알려주어야(Link) 한다.
	+ import java.util.Scanner;
		+ java 안에 uill 안에 Scanner 클래스를 연결(import)해주는 코드이다.
+ Scanner 객체를 생성한다.
	+ 입력을 받을 수 있는 실질적인 Scanner 객체를 만들어주어야 한다.
+ 콘솔에서 입력을 받는다
	+ 자료형 별로 입력을 받는 함수가 다르므로 잘 지정하여 사용해야한다.


```java
import java.util.Scanner;

class scannerClass{
	public static void main(String[] args){
        Scanner scanner = new Scanner(System.in);	//값을 입력 받을 주체(객체)인 scanner 생성

        System.out.println("----------input-----------");
        System.out.print("integer: ");
        // int 형의 값을 입력 받음
        int i = scanner.nextInt();			//콘솔에서 int 타입의 입력을 기다림

        System.out.print("boolean: ");
        // boolean 형의 값을 입력 받음
        boolean b = scanner.nextBoolean();	//콘솔에서 boolean 타입의 입력을 기다림

        System.out.print("double: ");
        // double 형의 값을 입력 받음
        double d = scanner.nextDouble();	//콘솔에서 double 타입의 입력을 기다림

        String str;
        System.out.print("String: ");
        // String 형의 값을 입력 받음
        str = scanner.next();				//콘솔에서 String의 입력을 기다림

        System.out.println("----------output println----------");
        System.out.println("integer: "+i);
        System.out.println("boolean: "+b);
        System.out.println("double: "+d);
        System.out.println("String: "+str);
        System.out.println("----------output printf----------");
        System.out.printf("integer: %d \n",i);
        System.out.printf("boolean: %b \n",b);
        System.out.printf("double: %f \n",d);
        System.out.printf("String: %s \n",str);


	}
}

```
실행결과
```
----------input-----------
integer: 10
boolean: true
double: 4.666
String: hello~
----------output println----------
integer: 10
boolean: true
double: 4.666
String: hello~
----------output printf----------
integer: 10
boolean: true
double: 4.666
String: hello~
```
<span style="color:pink; font-size:15px;">printf 의 f 는 format으로 특정 형식에 따른 문자열 출력을 다룬다. <br>
%d, %s 등의 문자는</span>
[형식 지정자](http://java-space.tistory.com/entry/%ED%98%95%EC%8B%9D-%EC%A7%80%EC%A0%95%EC%9E%90)
<span style="color:pink; font-size:15px;">로 특정 타입에 대한 변수를 출력한다.</span>
