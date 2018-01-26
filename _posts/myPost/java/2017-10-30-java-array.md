---
layout: post
title: "Java의 배열"
categories:
  - Java
tags:
  - Java
  - 배열
  - Array
---

자바의 배열을 선언하는 법과 배열을 사용하는 법 그리고 배열을 사용하면서 얻는 이점에 대해 학습합니다.

+ 자바의 배열을 사용하는 이유
+ 배열의 선언
+ 배열의 사용 방법



## 배열( Array )
### 배열을 사용하는 이유
우리는 데이터를 저장하기 위해 변수를 선언하고 변수에 값을 저장한다.<br>
내 나이 정보를 담기위해 age 변수를 선언하여 값을 저장하면 된다.
```java
  int age;
  age = 25;
```
그렇다면 학급에 모든 학생들의 정보를 담아야 할땐 어떻게 해야할까? 각 학생의 번호를 이름으로 하여 학생 일일이 변수를 선언해주는 방법이 있다.
```java
	int age1 = 35;		//학급번호 1번의 나이
	int age2 = 23;		//학급번호 2번의 나이
  int age3 = 33;		//학급번호 3번의 나이
  int age4 = 23;		//학급번호 4번의 나이
  int age5 = 22;		//학급번호 5번의 나이
  int age6 = 10;		//학급번호 6번의 나이
  .
  .
  .
  int age40 = 32;		//학급번호 40번의 나이
```
위의 방법을 사용하면 선언부가 너무 길어지고 변수의 이름을 하나하나 직접 입력해줘야 하기 때문에 굉장히 불편하다.<br>
이때 사용하는 것이 바로 ***배열*** 이다. <br>

### 배열의 선언
학급 40명의 나이를 입력받을 변수를 배열을 사용해 생성해보자.



```java
	int[] age = new int[40];

  /*
  int age[] = new int[40];
  int []age = new int[40];      모두 가능하다.

  변수를 초기화하는 과정이 위의 코드와 다를 것이 없어 보이지만, 후에 반복문을 배우면 더 쉽게 배열에 원소를 넣을 수 있다.
  /**/
```
코드가 훨씬 짧아졌다. <span style="color:pink; font-size:15px;">배열은 짧은 코드로 많은 양의 변수를 한번에 생성할 수 있는 이점이 있다.</span><br>
코드를 제일 앞부터 살펴보자.
+ int
	+ 배열에 저장되는 데이터의 타입을 지정한다.
+ []
	+ 일반 변수가 아닌 배열 변수라는 것을 컴파일러가 알수 있도록 표기한다.
+ age
	+ 변수의 이름을 지정한다.
+ new int[40]
	+ 40개의 int 크기만큼 배열을 생성한다.

#### 다른 타입의 배열
```java
	//배열의 선언
	char[] chArray = new char[20];			//20개의 char타입 배열을 생성
	String[] strArray = new String[10];		//10개의 String타입 배열을 생성
  float[] flArray = new float[300];		//300개의 float타입 배열을 생성
  .
  .
  .

```
#### 배열 선언의 여러 방법들
```java
	//1.
	char[] chArray = {'a', 'b' ,'c' ,'d' ,'e' ,'f' ,'g' ,'h'};
  //값을 포함하는 길이 8의 char형 배열을 생성

  //2.
  char[] chArray2;
  //배열을 선언하고
  chArray2 = {'a', 'b' ,'c' ,'d' ,'e' ,'f' ,'g' ,'h'};
	//값을 삽입하여 객체화한다.
   ```
   다른 데이터의 타입도 모두 위 같은 방식으로 사용 가능하다.

   ### 배열의 사용방법
   위와 같은 방법으로 선언한 배열들을 사용하는 방법을 알아봅니다.<br>


   ```java
   	int[] age = new int[40];
    //배열을 생성한 후, 0번 부터 39번까지 배열 원소에 값을 넣어줍니다.
    age[0] = 35;
    age[1] = 23;
    age[3] = 33;
    .
    .
    .
    age[39] = 32;
   ```
  + age[숫자]
  + 위와 같이 접근 가능한 변수를 ***배열의 원소*** 라고 한다.
  + 배열의 원소는 변수와 같은 역할을 하고, 그 사용법도 변수의 사용법과 같다.
  + []안에 들어가는 숫자
  + 해당 숫자는 배열 생성시 갯수에 의해 유동적으로 결정된다.
	+ ex) ```new int[40];```으로 생성된 배열이라면 숫자의 범위는 0부터 39까지 40개이다.
<br><br><br>


#### Math.random()
```Math.random()```은 랜덤한 숫자를 뽑아낼 때 사용하는 함수이다. <br>

```java
int random = (int)(Math.random()*10);
int lotto = (int)Math.random()*44;
int lotto2 = (int)(Math.random()*44+1);
System.out.println(random);				//0부터 10까지의 int형 정수를 출력한다.
System.out.println(lotto);				//0부터 44까지의 int형 변수를 출력한다.
System.out.println(lotto2);				//1부터 45까지의 int형 변수를 출력한다.
```
실행결과
```
3
34
45
```


<br><br><br>


### ```.random()```을 이용한 로또 번호 추첨 기능
random 함수를 사용하여 로또 번호를 추출하고 배열에 저장한 후 출력한다.
```java
import java.util.Arrays;

public class Lotto {
    public static void main(String[] args) {
        int arr[] = new int[6];

        arr[0] = (int)(Math.random()*44+1);
        arr[1] = (int)(Math.random()*44+1);
        arr[2] = (int)(Math.random()*44+1);
        arr[3] = (int)(Math.random()*44+1);
        arr[4] = (int)(Math.random()*44+1);
        arr[5] = (int)(Math.random()*44+1);			//각 배열에 랜덤한 수를 삽입한다.


        System.out.print(arr[0]+" "+arr[1]+" "+arr[2]+" "+arr[3]+" "+arr[4]+" "+arr[5]);
        //삽입된 데이터(각 배열의 원소)를 출력한다.
    }
}
```
