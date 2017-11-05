---
layout: post
title: "Java의 String"
categories:
  - Java
tags:
  - Java
  - 문자열
  - String
---



이전 자바의 변수에 대한 포스트에서 우리는 여러 타입의 변수를 다루는 법을 학습했습니다.

그 중 클래스지만 변수처럼 사용되던 ***String*** 에 대해 학습합니다.





+ String 의 선언과 사용방법
+ String 에 내장된 다양한 기능의 메소드





## String 의 선언과 사용방법

String 은 클래스이지만 다른 자료형과 사용하는 방법이 거의 흡사하다.

지금 수준에서는 String을 자료형이라고 생각하고 사용하면 된다.

```java
class stringClass
{
  public static void main(String[] args)
  {
	//일반 변수처럼 선언하여 사용하는 방법.
    String str;
    str = "Str : Hello World!";
    System.out.println(str);

    //String을 class 객체로 선언하는 방법.
    String str1 = new String("Str1: Hello World!");
    System.out.println(str1);

    //문자 배열을 인자로 String 객체를 선언하는 방법.
    String str2;
    char data[] = {
      'S','t','r','2',':',' ',
      'H','e','l','l','o',' ',
      'W','o','r','l','d','!'
    };
    str2 = new String(data);
    System.out.println(str2);
  }
}
```

```
Str : Hello World!
Str1: Hello World!
Str2: Hello World!
```

위 방법들 처럼 ```String```을 선언하는 방법은 여러가지가 있고 모두 다 정상 동작한다.

하지만, 제일 처음 ***일반 변수처럼 선언하여 사용하는 방법*** 이 가장 많이 쓰이는 방법이다.





## String 에 내장된 다양한 기능의 메소드

자바에 존재하는 대부분의 클래스는 다양한 내장 함수를 가지고 있다.

String 도 역시 클래스이므로 내장 함수를 가지고 있다.



### 문자열을 합치는 방법

```java
class combineClass{
  public static void main(String[] args){
    String str1 = "Hello";
    String str2 = " ";
    String str3 = "World!";

    //str1, str2, str3 가 순서대로
    //붙어있는 문자열을 출력하고 싶을 때
    System.out.print(str1);
    System.out.print(str2);
    System.out.print(str3);

    System.out.println(str1+str2+str3);	//합친 문자열을 출력
  }
}
```

```
Hello World!
Hello World!
```

문자열과 문자열 사이에 ```+```기호를 넣게 되면 문자열이 붙어서 출력된다.

뿐만 아니라 문자열과 ```int```형 변수를 ```+```해주게 되면 ```int```형 변수가 자동으로 ```String```으로 형변환되어 합쳐진 문자열로 출력된다.



```java
class numCombineString{
  public static void main(String[] args){
	//숫자 + 문자열
    String str4 = "Hi! I'm ";
    int age = 20;
    int age2 = 4;
    String str5 = " years old.";

    System.out.println(str4 + age + str5);				
    System.out.println(str4 + age + age2 + str5); 		//소괄호를 사용하지 않았을 때
    System.out.println(str4 + (age + age2) + str5);     //소괄호를 사용했을 때
  }
```

```
Hi! I'm 20 years old.
Hi! I'm 204 years old.		//연산이 진행되지 않고 문자열로 합쳐진다.
Hi! I'm 24 years old.		//연산이 제대로 진행된다.
```

문자열 사이에 연산을 하고 싶을때는 소괄호() 가 반드시 들어가야 한다. 그렇지 않으면 문자열로 인식되어 단순히 문자만 합해진 결과가 나온다.



### 비교 연산

문자열을 처리할 때 문자열이 같은지 다른지 비교해야할 경우가 있다. 이때 사용하는 비교 함수는 ```.equals()```이다. ```String```뿐 아니라 다른 여러 클래스에서도 비교 함수를 제공한다. 앞으로 코딩을 할때 심심치 않게 만날 수 있는 함수이다.

```java
class compareClass{
    public static void main(String[] args){
        String hi = "Hello";
        String hello = "Hell";

        hello = hello + "o";

        System.out.println("hi: "+hi);
        System.out.println("hello: "+hello);

        if (hi == hello){
            System.out.println("두 문자열은 같습니다.");
        }else{
            System.out.println("두 문자열은 다릅니다.");
        }
    }
}
```

```
hi: Hello
hello: Hello
두 문자열은 다릅니다.
```

출력 결과 첫번째 줄과 두번째 줄에서 확인할 수 있듯이 hi 변수에 담긴 문자열은 ***Hello***이고, hello 변수에 담긴 문자열은 ***Hell 에 o를 더한 Hello*** 이다. 하지만 두 문자열은 같지 않다는 출력 결과를 보이고 있다. 같은 "Hello"인데 왜 다르다는 것일까.

String은 클래스 이다. 따라서 String을 사용해 선언한 문자열은 객체이고 객체는 개개인 마다 특정 주소를 지정받는다. 우리가 사용한 ```==``` 비교함수는 객체의 특정 주소를 비교하는 것이기 때문에 다른 객체인 hi와 hello는 같지 않다는 결과를 내게 된다.

하지만, 우리는 두 문자열이 같은 문자열을 갖고 있을 때를 비교하는 함수를 사용하고 싶다. 그때 사용하는 것이 ```.equals```이다.

```java
public equalsClass{
    public static int main(String[] args){
        String hi = "Hello";
        String hello = "Hell";

        hello = hello + "o";

        System.out.println("hi: "+hi);
        System.out.println("hello: "+hello);

        if(hi.equals(hello)){
            System.out.println("두 문자열은 같습니다.");
        }else{
            System.out.println("두 문자열은 다릅니다.");
        }
    }
}
```

```
Hello
Hello
두 문자열은 같습니다.
```

우리가 원하는 결과가 출력됐다. ```.equals()```는 주소값이 아닌 문자열 자체의 값을 비교하므로 같다는 결과가 나온다.



### 특정 문자의 위치

```indexOf()``` 함수는 String 에서 특정 문자가 위치하는 주소를 반환한다.

```java
class indexOfClass{
    public static void main(String[] args){
        String hello = "Hello World!";
      	System.out.println(hello.indexOf('e'));
      	System.out.println(hello.indexOf('W'));
      	System.out.println(hello.indexOf('E'));
    }
}
```

```
1				//1
6				//W
-1				//E
```

문자열에서 해당 문자가 있는 위치를 반환한다. 하지만 문자를 발견하지 못하면 -1을 출력한다. 공백도 문자로 치기 때문에 W의 위치는 6이 나온다.



### 문자열의 길이

```.length()``` 함수는 문자열의 길이를 리턴해준다.

```java
class lengthClass{
  public static void main(String[] args){
    String str = "Hello world!";
    int strLen = str.length();
    System.out.println("Length: "+strLen);
  }
}
```

```
12
```

문자열에 대하여 문자 하나하나 반복문을 돌릴 때  자주 사용한다.





### 이 외 여러 함수들

```java

class stringFunctionClass
{
   public static void main(String[] args)
   {
      //replace()
      //첫번째 인자는 대상 문자열이 오고, 두번째 인자에는 바꾸려하는 문자열이 온다.
      String str1 = "A*B*C*D*E*F*G*H";
      String temp = str1.replace("*", "-");
      System.out.println("replace\t:"+temp);

      //split() tokken 을 사용해서 문자열을 자르고 char[]로 반환된다.
      //tokken은 구별이 가는 특정 문자이다. (*,&,^,% ... 등등)
      String str2 = "hello world this is java, and hello world";
      String charArr[] = str2.split(" ");
      for(int k=0; k<charArr.length; k++){
          System.out.println("split\t:"+charArr[k]);
      }

      //substring() -> 범위내 문자를 잘라서 가져옴 (시작 위치, 종료 위치 전)
      String str3 = "Hello World!!";
      String tempStr = str3.substring(2, 5);
      System.out.println("substring\t:"+tempStr);

      //toUpeerCase() 모든 영문자를 대문자로 변환한다.
      //toLowerCase() 모든 영문자를 소문자로 변환한다.
      String tempStr1 = str3.toUpperCase();
      String tempStr2 = str3.toLowerCase();
      System.out.println("toUpperCase()\t:"+ tempStr1);
      System.out.println("toLowerCase()\t:"+ tempStr2);

      //toString() 특정 자료형을 문자로 변환한다. (Wrapper Class에서 주로 사용된다.)
      String str4 = "안녕하세요, 반가워요";
      System.out.println("toString():\t"+str4.toString());

      //trim() 문자열 앞과 뒤의 공백을 없애준다. (앞과 뒤만 없애줌)
      String str5 ="         Hello          World        !!!           ";
      System.out.println("trim()\t: "+str5+"(before)");
      String trimStr = str5.trim();
      System.out.println("trim()\t: "+trimStr+"(after)");

      //valueOf() 특정 타입의 값을 문자열로 변환해준다.

      int num= 123;
      long lo = 1241323412L;
      double dou = 123.45678;
      //아래 모든 출력은 연산을 하는 것이 아니라 문자열의 합을 실행한다.
      String iStr = String.valueOf(num);
      System.out.println("valueOf()\t:"+iStr + 1000000);
      String lStr = String.valueOf(lo);
      System.out.println("valueOf()\t:"+lStr + 1000000);
      String dStr = String.valueOf(dou);
      System.out.println("valueOf()\t:"+dStr + 1000000);


      //contains() 해당 문자를 포함하고 있는지 여부를 검사한다.
      String str6 = "서울시 강남구";
      String findStr = "서울";
      boolean b1 = str6.contains(findStr);
      System.out.println("contains()\t:"+b1);

      //charAt 문자열의 해당위치의 문자를 char 타입으로 반환한다.
      String str7 = "가나다라마바사아자차카타파하";
      System.out.println("charAt()\t:"+str7.charAt(3));

      //concat 문자열을 합친다. +와 같은 동작
      String str8 = "hello world!!!!";
      String conStr = "Bye Hello world!!!";
      System.out.print("concat()\t:");
      System.out.println(str8.concat(conStr));
   }
}
```

```
A-B-C-D-E-F-G-H
replace	:A-B-C-D-E-F-G-H
split	:hello
split	:world
split	:this
split	:is
split	:java,
split	:and
split	:hello
split	:world
substring	:llo
toUpperCase()	:HELLO WORLD!!
toLowerCase()	:hello world!!
toString():	안녕하세요, 반가워요
trim()	:          Hello          World        !!!           (before)
trim()	: Hello          World        !!!(after)
valueOf()	:1231000000
valueOf()	:12413234121000000
valueOf()	:123.456781000000
contains()	:true
charAt()	:라
concat()	:hello world!!!!Bye Hello world!!!
```

String 클래스는 위 함수들을 제외하고도 많은 함수를 지원한다. 문자열은 프로그래밍에서 굉장히 빈번하게 사용하는 클래스 이므로 위 함수들을 사용하는 법을 어느 정도 숙지 한다면 String 클래스를 프로그래밍할 때 좀 더 유연한 대처를 할 수 있다.
