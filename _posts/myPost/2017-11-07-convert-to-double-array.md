---
layout: post
title: "2차원 배열을 1차원 배열로 변환하는 방법"
categories:
  - Java
tags:
  - Java
  - Array
  - 배열
  - 2차원 배열
  - 1차원 배열
---




자바를 포함한 많은 프로그램들이 메소드를 통해 동작을 수행한다. 그런 메소들 간에 데이터를 주고 받는다. 예를 들어, 학생들의 전화 번호가 담긴 정보를 전송해야할 때 전화 번호를 하나씩 보내는 것이 아니라 1차원 배열이나 2차원 배열에 담아서 전송해주면 편리하다

메소들 간에 데이터를 전송할 때에는 많은 데이터 자료형이 사용되는데 배열에 있어서는 ***2차원 배열보다 1차원 배열*** 을 많이 사용한다. 그렇기 때문에 자신이 가진 데이터가 2차원 배열이라면 1차원 배열로 전환해서 전송해야하는 경우가 적지 않게 발생한다.

따라서 ***2차원 배열을 1차원 배열로 변환하는 방법을 학습해보자.***



<br><br><br>



배열간의 연산을 할때 가장 중요한 것이 ***배열의 인덱스. 즉, 배열의 범위이다.*** 나의 경우에는 배열에 대한 연산을 할 때 꼭 노트를 펴놓고 배열의 인덱스 간의 상관 관계를 따져보면 연산을 진행한다. 배열의 인덱스는 1부터 증가되는 수이기 때문에 규칙을 쉽게 찾을 수 있다.



그렇다면 2차원 배열을 1차원 배열로 바꾸기 위해서 배열 인덱스 간의 규칙을 찾아보자!!!

```java
class singleArr2DoubleArr{
  public static void main(String[] args){
    int from[][] = {
      {00, 01, 02, 03, 04},
      {10, 11, 12, 13, 14},
      {20, 21, 22, 23 ,24},
      {30, 31, 32, 33 ,34}
    }
    int to[] = new int[from.length * from[0].length];
  }
}
```

```from[4][5]``` 만큼의 배열에는 20개의 원소가 들어있다. 이 20개라는 수는 ( 행의 개수 X 열의 개수 )로 구할 수 있는데, 이것을 활용해서 옮겨야할 배열의 크기를 ```new int[from.length * from[0].length];``` 로 동적할당 했다. 저 코드로 인해 ```from``` 배열의 크기가 어떻든 ```to``` 배열은 그 크기를 자동적으로 잡아낼 것이다.

```from ``` 배열의 인덱스를 정보로 ```to``` 배열의 크기를 자동적으로 생성할 수 있었다.





### from의 인덱스와 to 인덱스와의 관계

```from[0][0]``` 은 ```to[0]``` 로		5 * 0 + 0<br>

```from[0][1]``` 은 ```to[1]``` 로		5 * 0 + 1<br>

```from[0][2]``` 은 ```to[2]``` 로		5 * 0 + 2<br>

...

```from[1][0]``` 은 ```to[5]``` 로		5 * 1 + 0<br>

```from[1][1]``` 은 ```to[6]``` 로		5 * 1 + 1<br>

```from[1][2]``` 은 ```to[7]``` 로		5 * 1 + 2<br>

...

```from[2][0]``` 은 ```to[10]``` 로		5 * 2 + 0<br>

```from[2][1]``` 은 ```to[11]``` 로		5 * 2 + 1<br>

```from[2][2]``` 은 ```to[12]``` 로		5 * 2 + 2<br>

...

```from[i][j]``` 일 때, ```to[k]```

​	k = ```from[0].length * i + j``` 로 표현 가능하다.

규칙을 찾은 것 같다…

## 최종 코드

```java
class singleArr2DoubleArr{
  public static void main(String[] args){
    int arr[][] = new int[10][5];
    int arr1[] = new int[arr.length*arr[0].length];
	//배열에 값을 넣는다.
    for(int i=0; i<arr.length; i++) {
      for(int j=0; j<arr[i].length; j++) {
      	arr[i][j]=(i+1)*(j+1);
      }
    }

    System.out.println("2차원 배열");
    //2차원 배열 출력
    for(int i=0; i<arr.length; i++) {
      for(int j=0; j<arr[i].length; j++) {
      	System.out.print("\t"+arr[i][j]);
      }
      System.out.println();
    }

    System.out.println("변환");

    for(int i=0; i<arr.length; i++) {
      for(int j=0; j<arr[i].length; j++) {
        //2차원 배열의 원소를 1차원 배열의 원소로 이동.
      	arr1[( i * arr[i].length ) + j ] = arr[i][j];
      }
    }
	//1차원 배열 출력
    System.out.println("1차원 배열");
    for(int i=0; i<arr1.length; i++) {
      if(i%arr[0].length==0) {
      	System.out.println();
      }
      System.out.print("\t"+arr1[i]);
	}
  }
}
```





파라미터를 1차원 배열로 보내야 할 때 2차원 배열을 간단하게 변환하는 방법을 학습했다. 자주 쓰이는 코드는 아니지만 그래도 종종 나타나는 문제를 쉽게 풀어줄 수 있기 때문에 숙지하는 것이 좋다.
