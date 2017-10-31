---
layout: post
title: "Java의 변수"
categories:
  - Java
tags:
  - Java
  - 변수
  - variable
---

자바에서 사용하는 변수의 정의와 변수의 종류에 대해 학습합니다.<br>
그리고, 변수에 값을 저장하고 저장한 값을 출력하는 방법을 학습합니다.

+ 변수란 무엇인가
+ 변수의 종류
+ 변수의 선언
+ 변수의 사용


### 변수란 무엇인가
#### 상수와 변수
+ [상수](https://ko.wikipedia.org/wiki/%EC%88%98%ED%95%99_%EC%83%81%EC%88%98) : 상수란 일반적으로 사용하는 변하지 않는 수를 나타낸다.
+ [변수](https://ko.wikipedia.org/wiki/%EB%B3%80%EC%88%98_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99)) : 변수란 변하는 수라는 의미로 프로그래밍에서 변수는 타입이 지정된 데이터를 저장하기 위한 작은 저장공간이라는 의미로 봐도 무방하다.
<br><br><br>

## 변수의 종류
변수의 종류는 크게 정수, 실수, 문자, 참/거짓이 있다.
<br>
<br>
정수형 변수
+ byte
+ short
+ int
+ long

실수형 변수
+ float
+ double

문자
+ char

참/거짓
+ boolean
<br>
<br>
![변수의 종류](https://i.imgur.com/KAtGm1n.jpg)
<br>
<font style="color:pink; font-size:15px;">
▶︎위 표는 변수의 종류와 크기, 범위를 나타내는 표입니다. <br>
▶︎암기를 강요하는 것은 아니지만 종류와 크기, 그리고 범위는 외워놓는 것이 좋습니다.
</font>
<br><br><br>
## 변수의 선언
변수의 선언을 하기 전에, 변수에 어떤 데이터 타입이 적절한지 판단한다.<br>
<span style="color:pink; font-size:15px;">***저장하려는 데이터가 정수인지 실수인지 문자인지 판단하고, 범위를 판단하여 변수 타입을 지정한다.***</span>
<br>
Ex)
+ 키를 저장하기 위해선 178.95, 188.03 등 소수점이 필요하므로 실수형 변수인 float나 double을 사용한다.<br>
+ 나이를 저장하기 위해선 14살, 25살, 58살 등 소수점이 필요하지 않으므로 정수형 변수인 short, int, long을 사용한다.<br>
<br>
<br>

#### 정수형 변수의 선언
```java
	byte by;
    short sh;
    int i;
    long l;
```



#### 실수형 변수의 선언
```java
	float f;
    double d;
```



#### 문자형 변수의 선언
```java
	char ch;
    String str;
```
<span style="color:pink; font-size:15px;">***정확하게 String은 데이터 타입이 아닌 클래스 입니다. <br>하지만 지금은 클래스의 개념이 명확하지 않음으로 변수의 한 종류라고 생각하셔도 무방합니다.***</span>
<br><br>






#### boolean, 참/거짓 변수의 선언
```java
	boolean b;
```
<br><br><br>
## 변수의 사용
<br>





#### 정수형 변수의 선언과 사용
```java
      byte by;		
			// 크기: 1byte == 8bit
      by = 127;		
      System.out.println("by="+by);

      short sh;     
			// 크기: 2byte == 16bit
      sh = 1234;
      System.out.println("short="+sh);

      int i;        
			// 크기: 4byte == 32bit
      i = 12341234;
      System.out.println("int="+i);

      long l;       
			// 크기: 8byte == 64bit
      l = 123412341234L;      
			// compiler 에게 long 타입임을 명시하기 위해 숫자 맨 뒤에 L을 붙인다.
      System.out.println("long="+l);
```
실행결과
```
	by=127
    short=1234
    int=12341234
    long=123412341234
```



#### 실수형 변수의 선언과 사용
```java
      float f;      
			// 크기: 4byte == 32bit
      f = 123.456F;
      System.out.println("float="+f);

      double d;      
			// 크기: 8byte == 64bit
      d = 123.4561234;
      System.out.println("double="+d);
```
<span style="color:pink; font-size:15px;">***float자료형은 실수 값에 대한 오차가 크기 때문에 주로 double형을 자주 사용한다.***</span>
실행결과
```
	float=123.456
	double=123.4561234
```



#### 문자형 변수의 선언과 사용
```java
      char ch;      
			// 크기: 2byte == 16bit
      ch = 'a';
      ch = '한';
      System.out.println("char="+ch);


      //문자열
      String str;
      String str2;
      str = "Hello world";
      str2 = "!!!!!";
      System.out.println(str+str2);
```
실행결과
```
	char=한
	Hello world!!!!!
```

- [ASCII 코드](https://namu.wiki/w/%EC%95%84%EC%8A%A4%ED%82%A4%20%EC%BD%94%EB%93%9C)<span style="color:pink; font-size:15px;"> ***는 문자를 표현하는 일종의 규약이다.***</span><br>
- [uni 코드](https://ko.wikipedia.org/wiki/%EC%9C%A0%EB%8B%88%EC%BD%94%EB%93%9C)<span style="color:pink; font-size:15px;"> ***는 ASCII코드로 문자를 표현하는 것에 한계가 있어서 만들어진 규약이다.***</span><br>
- [multi byte 코드]()<span style="color:pink; font-size:15px;"> ***uni코드보다 더 많은 문자를 표현할 수 있는 규약이다.***</span><br>
- [세 코드 비교하기](http://egloos.zum.com/HardCoding/v/557949)


#### 참/거짓, boolean타입 변수의 선언과 사용
```java
      //참/거짓
      boolean b;      
			// 크기: 1byte == 8bit
      b = true;
      System.out.println("b="+b);

      b = false;
      System.out.println("b="+b);
```
실행결과
```
	b=true
	b=false
```
