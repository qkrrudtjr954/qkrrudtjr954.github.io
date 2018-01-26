---
layout: post
title: "Java의 이중배열"
categories:
  - Java
tags:
  - Java
  - array
  - 배열
  - 이중 배열
---


Java의 배열은 동일한 목적을 갖는 여러개의 변수를 한번에 선언해서 관리할 수 있는 기능을 제공한다.
앞에서 사용한 배열은 변수를 선형으로 담는 1차원 배열이다. 하지만 자바 그외의 다른 언어들은 선형의 1차원 배열이 아니라 2차원 배열도 제공한다.

<br><br>

+ 2차원 배열의 개요
+ 2차원 배열의 선언
+ 2차원 배열의 사용방법
+ 2차원 배열의 사용

<br>

<br>







## 2차원 배열의 개요

백문이 불여일견이기 때문에 그림으로 위의 구조를 설명해보자.



![변수의 설명](https://i.imgur.com/yBb3vJ3.png)

> 변수는 특정 타입의 값(빨간색 원)을 저장하는 저장공간(파란 박스)이다.

![1차원 배열의 설명](https://i.imgur.com/CTEnGl3.png)
> 1차원 배열은 여러 개의 변수를 한번에 선언하고 사용한다. 배열(노란색 박스)안에는 여러개의 변수(파란색 박스)가 존재한다.

![2차원 배열의 설명](https://i.imgur.com/GbSzNq2.png)
> 2차원 배열은 여러 개의 1차원 배열을 한번에 선언하고 사용한다. 2차원 배열(초록색 박스)안에는 여러개의 1차원 배열(노란색 박스)이 존재한다.

<br><br>
아직은 개념이 명확하게 잡히지 않을 것이다. 쉽게 1차원 배열을 변수 여러개를 한번에 선언해서 사용하는 것이고 ***2차원 배열은 1차원 배열 여러개를 한번에 선언해서 사용하는 것이다.***<br><br>




## 2차원 배열의 선언
2차원 배열의 선언과 사용방법은 1차원 배열과 거의 비슷하다. 차이점은 1차원 배열에는 대괄호가 ```int[]``` 하나 붙었지만 2차원 배열에는 ```int[][]``` 두개 붇는다는 것이다.

```java
class doubleArray{
  public static void main(Strin[] args){
    int arr = new int[5];					//크기가 10인 int형 1차원 배열
    int doubleArr[][] = new int[2][5]; 		//크기가 20인 int형 2차원 배열
  }
}
```

2차원 배열의 선언은 1차원 배열의 선언과 굉장히 흡사하다. 그림으로 선언문을 이해하면 더 명확하게 이해할 수 있다.



![1차원 배열의 선언](https://i.imgur.com/2xgrW0D.png)

1차원 배열은 0부터 4까지의 이름을 갖는 변수를 원소로 하는 1차원 배열을 생성했다. 각 원소(파란 박스)에 ```arr[0], arr[1], arr[2]…``` 로 접근할 수 있다.



![2차원 배열 선언](https://i.imgur.com/tObJTRW.png)

2차원 배열은 0부터 1까지 이름을 갖는 <span style="color:orange;">배열(노란색 박스)</span>을 원소로 하는 2차원 배열을 생성했다. 2차원 배열의 <span style="color:orange;">원소(노란색 박스)</span>는 0부터 4까지 <span style="color:blue;">변수(파란 박스)</span>를 원소로 갖는다. 2차원 배열은 각 <span style="color:orange;">원소(노란색 박스)</span>에 ```doubleArr[0], doubleArr[1]``` 로 접근할 수 있다. 

***doubleArr[0], doubleArr[1] 로 접근한 원소(노란색 박스)는 1차원 배열이다. 따라서 1차원 배열의 원소(변수(파란 박스))로 접근하기 위해서는 ```doubleArr[0][0], doubleArr[0][1] … ``` 로 접근할 수 있다.***

+ 0의 노란 박스 속에 2 파란 박스에 접근 : ```doubleArr[0][2]``` 
+ 1의 노란 박스 속에 3 파란 박스에 접근 : ```doubleArr[1][3]```
+ 1의 노란 박스 속에 4 파란 박스에 접근 : ```doubleArr[1][4]```





## 2차원 배열의 사용방법

2차원 배열을 선언하는 방법을 배웠으니 2차원 배열을 어떻게 사용하는 지에 대해서 학습합니다. 2차원 배열에 값에 접근하기 위해서는 2번의 접근이 필요합니다. 

```java
class array2Class{
  public static void main(String[] args){
    
    // new int[ 노란 박스의 개수 ][ 파란 박스의 개수 ];
    int doubleArr[][] = new int[3][2];	//초록색 박스 생성
    
    //값을 일일히 초기화하는 방법
    doubleArr[0][0] = 00;	//파란 박스에 접근
    doubleArr[0][1] = 01;	//파란 박스에 접근
    
    doubleArr[1][0] = 10;	//파란 박스에 접근
    doubleArr[1][1] = 11;	//파란 박스에 접근
    
    doubleArr[2][0] = 20;	//파란 박스에 접근
    doubleArr[2][1] = 21;	//파란 박스에 접근

    
    //값을 선언과 동시에 초기화하는 방법
    int doubleArr2[][] = {	//초록색 박스
      {00, 01, 02},	//노란 박스
      {10, 11, 12},	//노란 박스
      {20, 21, 22},	//노란 박스
      {30, 31, 32}	//노란 박스
    };
    
    //doubleArr.length는 3이다.
    for(int i=0; i<doubleArr.length; i++){
      //doubleArr[i].length는 2이다.
      for(int j=0; j<doubleArr[i].length; j++){
        System.out.print(" "+doubleArr[i][j]);
      }
      System.out.println();
    }
    
    System.out.println();
    
    //doubleArr2.length는 4이다.
    for(int i=0; i<doubleArr2.length; i++){
      //doubleArr2[i].length는 3이다.
      for(int j=0; j<doubleArr2[i].length; j++){
        System.out.print(" "+doubleArr2[i][j]);
      }
      System.out.println();
    }
  }
}
```

```
0	1
10	11
20	21

0	1	2
10	11	12
20	21	22
30	31	32
```

두 방법 모두 값이 제대로 들어가서 출력까지 된다. 출력문을 보았을 때, 익숙한 모양이라는 생각이 들 수 있다. 출력의 모양은 ***행렬*** 과 유사하다. 실제로 행렬의 연산과 처리를 할 때 2차원 배열을 사용한다. 값을 초기화 하거나 2차원 배열을 생성할 때 행렬을 생각하면 쉽게 이해할 수 있다.



```
int arr[][] = new int[행의 갯수][열의 갯수];
```

+ 2 X 4의 행렬 : ```new int[2][4]```

  ```
  |	00	01	02	03	|
  |	10	11	12	13	|
  ```

  ​

+ 4 X 6의 행렬: ```new int[4][6]```

  ```
  |	00	01	02	03	04	05	|
  |	10	11	12	13	14	15	|
  |	20	21	22	23	24	25	|
  |	30	31	32	33	34	35	|
  ```







## 2차원 배열의 사용

2차원 배열의 기본 초기화나 생성은 int이 외의 다른 자료형으로 5번 정도 응용해보면 바로 익힐 수 있다. 2차원 배열의 개념과 사용법을 숙지했다고 가정하고, 2차원 배열을 사용하여 프로그램을 작성해보자.



***학급의 학생 1명에게 3가지 과목의 점수를 입력 받고 개인 총점과 평균 그리고 학급 전체의 총점과 평균을 구하시오.***

![학급 설명 그림](https://i.imgur.com/0xC0Ayb.png)

+ <span style="color:orange;">학생(노란 박스)</span> 은 <span style="color:blue;">과목에 대한 점수(파란 박스)</span>를 3개 가지고 있어야 한다.
+ <span style="color:green;">학급(초록 박스)</span> 은 <span style="color:orange;">학생(노란 박스)</span>을 여러개 가지고 있어야 한다.



```java
class doubleArrayExam{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    System.out.print("학생은 총 몇명입니까?");
    int student = scanner.nextInt();
    int personalSum=0;		//개인 총점
    int personalAvg=0;		//개인 평균
    int sum=0;				//전체 총점
    int avg=0;				//전체 평균

    int score[][] = new int[student][3];		//학생 수는 입력받고, 과목은 3개로 정해져 있다.

    //score.length는 입력받은 학생 수 만큼의 길이를 갖는다.
    for(int i=0; i<score.length; i++){
      System.out.println((i+1)+"번째 학생");
      //score[i].length는 과목의 수만큼의 길이를 같는다. == 3
      for(int j=0; j<score[i].length; j++){
          System.out.print("\t"+(j+1)+"번째 과목 점수를 입력하세요.");
          //score[i][j]는 i번째 학생의 j번째 점수라는 의미를 갖는다.(i와 j는 0부터 시작.)
          score[i][j] = scanner.nextInt();
      }
    }

    for(int i=0; i<score.length; i++){
      for(int j=0; j<score[i].length; j++){
          sum += score[i][j];
      }
    }
    
    avg = (sum/student + sum%student);		//student는 학생의 수
    System.out.println("학급 총점: "+sum+"\t학급 평균: "+avg);

    //학생 개인의 총점
    for(int i=0; i<score.length; i++){
      personalSum = 0;	//학생 1명의 총점을 구하고 다음 학생의 총점을 구하기 전에 0으로 변수를 초기화한다.
      					//초기화를 하지 않으면 점수가 전부 더해져 전체 학급 총점이 된다.
      for(int j=0; j<score[i].length; j++){
          //i번째 학생의 0, 1, 2번째 과목의 총점을 구한다.
          personalSum += score[i][j];
      }
      //student[i].length는 과목의 개수
      personalAvg = (personalSum/score[i].length + personalSum%score[i].length);
      System.out.println((i+1)+"번째 학생의 개인 총점: "+personalSum+"\t개인 평균: "+personalAvg);
    }
  }
}
```

```
학생은 총 몇명입니까?3
0번째 학생
	0번째 과목 점수를 입력하세요.10
	1번째 과목 점수를 입력하세요.20
	2번째 과목 점수를 입력하세요.30
1번째 학생
	0번째 과목 점수를 입력하세요.40
	1번째 과목 점수를 입력하세요.50
	2번째 과목 점수를 입력하세요.60
2번째 학생
	0번째 과목 점수를 입력하세요.0
	1번째 과목 점수를 입력하세요.10
	2번째 과목 점수를 입력하세요.30
학급 총점: 250	학급 평균: 84
0번째 학생의 개인 총점: 60	개인 평균: 20
1번째 학생의 개인 총점: 150	개인 평균: 50
2번째 학생의 개인 총점: 40	개인 평균: 14
```

위의 코드가 이해하기 힘들다면 2차원 배열에서 i와 j가 가르키는 값이 어떤 값을 의미하는지 이해가 부족하기 때문이다.  

+ 첫번째 학생의 두번째 과목
  + ```score[0][1]``` 으로 접근하면 된다.
+ 두번째 학생의 세번째 과목
  + ```score[1][2]``` 으로 접근하면 된다.
+ 두번째 학생의 첫번째 과목
  + ```score[1][0]``` 으로 접근하면 된다.
+ 세번째 학생의 세번째 과목
  + ```score[2][2]``` 으로 접근하면 된다.



```score[0], score[1], score[2]... ```는 학생 한명 한명을 나타내고, <br>```score[0][0], score[1][0], score[2][1]``` 는 몇번째 학생의 몇번째 과목 점수라는 개념을 잘 자리잡고 다시 코드를 이해하면 조금 더 쉽게 이해할 수 있을 것이다.