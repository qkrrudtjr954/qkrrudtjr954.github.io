---
layout: post
title: "Java의 형변환"
categories:
  - Java
tags:
  - Java
  - casting
  - 형변환
  - 자동 형변환
  - 강제 형변환
---

변수들은 때때로 자동 또는 수동으로 형변환을 합니다. 자동으로 형 변환이 되는 경우 또 수동으로 형 변환을 해주어야 하는 경우에 대해 학습합니다.

+ 우선 순위


+ 자동 형변환
+ 강제 형변환



```java
short sh = 10;
int i;
i = sh + 10;
System.out.println("auto casting: "+i);
```

```
auto casting: 20
```

자료형을 공부했다면, 위의 코드에서 이상한 점을 발견할 수 있다.

short형 변수로 선언된 sh에 10을 더한 값을 int형 변수인 i에 대입하고 있다. 에러가 일어날 것이라고 생각했지만, 출력 결과는 정상적인 값이 출력된다. short형의 변수가 int형 변수로 변경되어 출력되고 있다.

위와 같은 현상을 ***형변환***이라고 한다.





### 우선 순위

Java의 자료형에는 우선순위가 존재한다. 이것이 중요한 이유는 자료형이 형변환을 할 때 우선순위에 따라***자동형 변환*** ,***강제 형변환*** 의 방식이 정해지기 때문이다. 우선순위는 따로 지정하는 것이 아니고 _컴파일러_ 에 의해 정의되어 있다.

| 우선 순위 |     자료형     |   타입   |  크기   |
| :---: | :---------: | :----: | :---: |
|   1   |   double    |   실수   | 8byte |
|   2   |    float    |   실수   | 4byte |
|   3   |    long     |   정수   | 8byte |
|   4   |     int     |   정수   | 4byte |
|   5   | short, char | 정수, 문자 | 2byte |
|   6   |    byte     |   정수   | 1byte |

<span style="color:pink; font-size:15px;">
▶︎ 크기 순서대로 봤을 때 long의 우선 순위가 float보다 먼저일거라고 생각이 들지만, 크기와 타입을 떠나서 컴파일러에 의해 float가 우선순위가 더 높도록 설정되어 있습니다.
</span>







### 강제 형변환

```java
class powerCastClass{
  public static void main(String[] args){
    long l = 12349999L;
    int i = (int)l;
    System.out.println("Long to Integer: "+i);

    short sh = (short)(i + 1);				//int형 변수 i에 10을 더한 값의 자료형은 int이다.
    System.out.println("Integer to Short: "+ sh);

  }
}
```

```
Long to Integer: 12349999
Integer to Short: 1235000
```

  위는 강제적인 형변환이 일어난 코드이다. 강제 형변환은 ***우선순위가 더 낮은 변수( short )***에 ***우선순위가 더 높은 변수( int )***의 값을 저장할 때 발생한다.

형변환을 하는 방법은 ***우선순위가 더 높은 변수( int )*** 앞에 ***우선순위가 더 낮은 변수( short )*** 의 자료형을 명시해주기만 하면 된다.

<span style="color:pink; font-size:15px;">
▶︎ 강제적인 형변환을 할 때는 변환하는 값이 자료형에 담길 수 있는 범위(크기)인지 항상 확인하고 주의해서 사용하여야 한다.
</span>
<br>
<span style="color:pink; font-size:15px;">
▶︎ 강제적인 형변환은 쉽게 큰 것을 작은 것으로 옮긴다고 생각하면 이해하기 쉽다. 그렇기 때문에 크기를 신경써야 한다.
</span>









### 자동 형변환

```java
class autoCastClass{
  public static void main(String[] args){

    short sh = 10;
    int i = sh + 10;			//sh+10은 short형 값인데 int형 변수 i에 저장
    System.out.println("Casting to Integer: "+i);

    long l = i+4;				// i+4는 int형 값인데 long형 변수 l에 저장
    System.out.println("Casting to Long: "+l);

  }
}
```

```
Casting to Integer: 20
Casting to Long: 24
```

위 코드를 보면 short형 변수는 int형 변수로 변환되었고, 다시 그 int형 변수는 long형으로 타입이 변경되어 저장되었다. 하지만 ***강제 형변환*** 과는 다르게 앞에 타입을 명시해주지 않았다.

***우선 순위가 더 낮은 변수(short)*** 에서 ***우선 순위가 더 높은 변수(int)*** 로 형을 변환할 때는 타입을 명시하지 않아도 자동적으로 변환이 이루어진다.

<span style="color:pink; font-size:15px;">
▶︎ 자동 형변환은 강제 형변환과 반대로 작은 것을 큰 것으로 옮긴다고 생각하면 이해하기 쉽다. 그렇기 때문에 크기에 대해 크게 고려하지 않아도 자동적으로 변환해준다.
</span>







### 실수 ↔︎ 정수의 형변환

위에서는 정수 ↔︎ 정수의 형변환을 다뤘다. 하지만 실수 ↔︎ 정수의 형변환도 가능하다.

```java
class castCalss{
  int i = 40;
  double d = (double)i;
  System.out.println("Integer to Double: "+d);

  float f = (float) 3.65;
  short sh = (short)f;
  System.out.println("Float to Short: "+sh);
}
```

```
40.0
3
```

+ 정수가 실수로 형변환이 일어나면 실수를 나타내는 소수점이 출력된다.
+ 실수가 정수로 형변환이 일어날때는 <span style="color:pink; font-color:pink;">소수점 이후의 숫자<span>는 전부 사라지고 정수값만 남게 된다.
