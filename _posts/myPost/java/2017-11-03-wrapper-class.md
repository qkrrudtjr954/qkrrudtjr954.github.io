---
layout: post
title: "wrapper 클래스"
categories:
  - Java
tags:
  - Java
  - wrapper class
  - wrapper 클래스
---



wrapper 클래스는 기본 자료형(int, shot, float 등등)을 ***클래스화*** 한 객체이다. 하지만 그 사용법은 기본 자료형을 사용하는 방법과 비슷하다.

우리는 여기서 String이 클래스라는 비밀을 풀 수 있을 것이다. wrapper 클래스를 배워보자.



+ wrapper 클래스
+ wrapper 클래스 사용 방법



<br>

<br>

<br>



## wrapper 클래스

wrapper 클래스는 별다를 설명이 없이 ***일반 자료형을 클래스화한 것이다.***  라는 말로 정리된다.

| 일반 자료형   | wrapper클래스 |
| -------- | ---------- |
| boolean  | Boolean    |
| char     | Character  |
| byte     | Byte       |
| short    | Short      |
| * int    | * Integer  |
| float    | Float      |
| * double | * Double   |
| * char[] | * String   |

대문자로 시작하는 wrapper 클래스들은 일반 자료형을 업그레이드한 것이라고 생각하면 된다. 자료형을 선언하는 것 뿐만 아니라 클래스가 제공하는 메소드를 활용하여 일반 자료형보다 폭넓은 활용을 보일 수 있다. 하지만 객체로 선언을 할 경우 일반 자료형보다 더 많은 메모리 공간을 차지하게 된다. 따라서 무분별한 사용을 삼가하는 것이 좋다.

String의 비밀은 char[]를 확장한 ***wrapper 클래스*** 였다.



<br>

<br>

<br>



## wrapper 클래스 사용 방법

wrapper 클래스는 일반 자료형과 같이 사용하는 방법과 객체를 생성하는 방법이 있다. 하지만 이 둘은 선언의 차이일 뿐이며, 둘 중 어느 것을 사용해도 무방하다.

```java
class wrapperClass{
  public static void main(String[] args){
    //일반 변수의 선언과 사용
    int num1 = 123;
    System.out.println(num1);

    //wrapper 클래스의 선언과 사용
    Integer Num1 = 123;					//일반 변수와 같은 방법
    System.out.println(Num1);

    Double f1 = 1.2;
    System.out.println(f1);

    Integer Num2 = new Integer(123);	//객체화하는 방법
    System.out.println(Num2);

    Double f2 = new Double(1.2);
    System.out.println(f2);

  }
}
```

```
123
123
1.2
123
1.2
```

wrapper 클래스를 선언하는 방법에는 두가지가 있다.

+ 일반 변수와 같은 방법으로 선언하는 방법
+ new를 선언하여 객체화를 하는 방법
  + wrapper 클래스도 클래스이기 때문에 일반 int형 123을 인자로 Num2라는 이름의 Integer 객체를 생성했다.

하지만 두 방법을 사용하는데 있어서 차이점은 없다.

<br>

<br>

<br>

이쯤되면 사용법도 일반 변수와 비슷한데,  ***왜? wrapper 클래스를 사용하는가?*** 하는 의문이 들 것이다.

단순히 wrapper 클래스를 변수처럼 생각하고 사용한다면, 그렇게 느낄 수 있다. 하지만 앞에서 부터 강조했듯이 wrapper 클래스는 클래스이다. 클래스의 내부는 다양한 메소드와 멤버 변수들을 함축한 것이라고 생각하면 된다. 따라서 앞의 의문에 대한 대답은  wrapper 클래스는 클래스이기 때문에 자료형의 선언 뿐만 아니라 다양한 함수를 제공하기 때문에 사용한다. 라고 답할 수 있다.

그렇다면, wrapper 클래스가 제공하는 함수는 어떤 것이 있는지 살펴보자.

```java
class wrapperClass{
  public static void main(String[] args){
    //ch1 과 ch2 를 비교할 때,
    char c1 = 'a';
    char c2 = 'a';

    Character ch1 = 'a';
    Character ch2 = new Character('a');

    System.out.println(c1==c2);
    System.out.println(ch1==ch2);
    System.out.println(ch1.equals(ch2));
  }
}
```

```
true
false
true
```

wrapper 클래스는 그 값을 비교할 수 있는 ```.equals()``` 함수를 제공한다. 이전 포스팅 String에서 사용한 경험이 있다. 우리가 ```String```에서 ```.equals()``` 를  사용할 수 있었던 이유는 ```String```도 wrapper 클래스 이기 때문이었다.

하지만 두번째 줄 ```System.out.println(ch1==ch2);``` 의 결과는 ```false```를 리턴하고 있다. 그 이유는 클래스에 ```==``` 를 사용하면 객체의 주소를 검사하기 때문에 ```false``` 를 반환한다. ```ch1``` 과 ```ch2``` 는 서로 다른 객체이기 때문에 ```false``` 를 리턴한다. 따라서 ***wrapper 클래스 내부의 값을 비교하고 싶을 때는 꼭 ```.equals()``` 를 사용해야 한다.***

<br>

<br>



## 여러가지 wrapper 클래스

```.equalse()``` 이 외에도 많은 함수를 제공하는데, 몇가지 중요한 함수들에 대한 사용법을 간단하게 정의하고 사용해보자.

```java
class wrapperClass{
  public static void main(String[] args){
    //.valueOf() : 숫자를 문자열로 변환하는 함수
    int num = 123;
    String str1;
    str1 = String.valueOf(num);
    System.out.println(".valueOf() : "+str1);

    //int형 변수를 Integer클래스로 전환.
    //.intValue() : wrapper 클래스 안에 숫자(int타입)를 가져오는 함수
    int i1 = 123;
    Integer int1 = new Integer( i1 );      //일반 변수를 wrapper class로 변환
    int num1 = int1.intValue();            //int num1 = int1; 은 에러가 난다. 일반변수에 wrapper class전체를 넘겨주었기 때문에
    System.out.println(".intValue() : "+num1);

    //.toString() : 숫자를 문자열로 변환
    System.out.println("toString() : "+int1.toString()+10);   //연산이 진행되지 않고 뒤에 10이 더해져 출력된다. int1이 문자열로 형이 변환되었음을 의미한다.
    System.out.println(int1+10);              //연산이 진행되어 10을 더한 값이 출력된다.

    //.parseInt() : 문자열을 숫자로 변환
    String str2 = "123";
    int i2 = Integer.parseInt(str2);    //숫자가 아닌 문자가 포함되어 있다면 에러가 발생한다
    System.out.println("parseInt()"+(i2+10));          //i1의 123은 문자열이 아닌 int형으로 형이 변환되어 10을 더한 133이 출력된다.

    //숫자를 문자로 변환 시키는 방법
    Integer _num = 123;
    String str3_1 = _num.toString();    //정석은 .toString() 함수를 사용
    String str3_2 = ""+_num;            //이 방법은 자동으로 형을 변환한다.

    //실수 -> 문자열
    Double d1 = new Double(3.14);
    Double d2 = 3.14;

    System.out.println("Double : "+ (d1+23));               //타입이 Double이기 때문에 23을 더한 값을 출력한다
    System.out.println("Double to String1 : "+ (d1.toString()+23));    //타입이 String이므로 23을 뒤에 더한 문자열이 출력된다
    System.out.println("Double to String2 : "+ (d1 + "" + 23));        //타입이 String이므로 23을 뒤에 더한 문자열이 출력된다

    //문자열 -> 실수
    String str5 = "3.14";
    double d3 = Double.parseDouble(str5);       //int형은 .parseInt() , double형은 .parseDouble()을 사용한다.
    System.out.println(".parseDouble : "+ (d3+23));   //타입이 Double형으로 변환되었기 때문에 연산이 된 값을 출력한다
  }
}
```

```
.valueOf() : 123
.intValue() : 123
toString() : 12310
133
parseInt()133
Double : 26.14
Double to String1 : 3.1423
Double to String2 : 3.1423
.parseDouble : 26.14
```
<br>

<br>

<br>
wrapper 클래스는 문자열을 숫자로 변환할 때, 숫자를 문자열로 변환할 때 자주 사용된다. 사실 위의 함수를 사용하는 법만 익혀둔다면 wrapper 클래스를 몰라서 고생하는 일은 없을 것이다.
