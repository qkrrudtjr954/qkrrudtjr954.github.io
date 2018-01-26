---
layout: post
title: "continue vs break"
categories:
  - Java
tags:
  - Java
  - continue
  - break
  - 반복문
---



반복문을 쓸 때, 반복을 중단 시키는 용도의 break에 대해 학습하고, 또 break문에 반대되는 반복문을 계속 시키는 continue문에 대해 학습합니다.





+ break문
+ continue문





## break문

우리는 특정 작업을 반복해서 해야할 때 반복문을 사용한다. 20번을 반복한다거나, 변수가 10보다 작을때 계속 반복한다 등의 조건을 갖는다. 그렇다면 ***반복문을 돌면서 양수를 20번 입력 받는다. 하지만, 중간에 음수가 입력되면 반복문을 종료한다.*** 다음과 같은 조건을 처리하기 위해서 ***break문*** 을 사용한다.

```java
import java.util.Scanner;

class breakClass{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
  	int num;
  	int w = 0;
  	while(w < 20)
  		System.out.print("숫자를 입력하세요: ");
    	num = scanner.nextInt();
    	System.out.println("입력한 수는 :"+ num + "입니다.");
  		w++;
    }
  }
}
```

위 코드는 ***20번을 돌면서 입력을 받고 입력 받은 값을 출력한다.*** 하지만 음수가 입력이 되어도 출력을 하기 때문에 입력된 값이 음수인지 검사하는 조건문을 추가 해주어야 한다.

그리고 입력된 값이 음수라면 반복문을 끝내야한다. 이때 break문을 사용하는데 break문은 독단적으로 사용될 수 없고 반복문과 함께 사용되어야 한다. 그 용도는 ***break문이 선언되어 있는 상위의 반복문을 강제 종료*** 시킨다.





```java
import java.util.Scanner;

class breakClass{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    int num;
    int w = 0;
    while(w < 20)
      System.out.print("숫자를 입력하세요: ");
      num = scanner.nextInt();
      if(num > 0){
        System.out.println("입력한 수는 :"+ num + "입니다.");
      w++;
      }else{
        System.out.println("음수를 입력하셨습니다.");
        break;
      }
    }
    System.out.println("w 의 값: "+w);
  }
}
```

```
숫자를 입력하세요: 3
입력한 수는 :3입니다.
숫자를 입력하세요: 3
입력한 수는 :3입니다.
숫자를 입력하세요: 2
입력한 수는 :2입니다.
숫자를 입력하세요: 1
입력한 수는 :1입니다.
숫자를 입력하세요: -5
음수를 입력하셨습니다.
w 의 값: 4
```

num을 입력받은 후 조건문을 통해 num이 0보다 큰지 검사한다. 크다면 입력받은 수를 출력하고 w를 1증가 시킨다. 하지만 **0보다 작다면** "음수를 입력하셨습니다." 문자열을 출력하고 while 문을 강제종료 시킨다. 음수가 입력되어 강제 종료되었기 때문에 while문은 20번을 돌지 못하고 w의 값이 4가 나온다.



### 무한루프와 break

***무한루프를 사용할 때는 반드시 break를 적절히 사용해주어야 한다.*** 그렇지 않으면 반복문은 종료가 되지 않고 프로그램은 반복문이 돌고 있는 동안 아무 동작을 하지 못할 것이다.

***음수 5개를 입력 받으면 종료되는 프로그램*** 을 작성해보자. 하지만 입력을 5번만 받는 것이 아니라 음수가 5개 입력될 때까지 무한으로 받는다.

```java
class loopBreak{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);

    int count = 0;		//입력받은 음수의 갯수를 저장하는 변수
    int number;			//입력받는 수를 담는 변수
    while(true){
      System.out.print("숫자를 입력하세요: ");
      number = scanner.nextInt();

      if(number < 0){
        //입력한 수가 음수이면, 입력한 음수를 출력하고 count를 증가한다.
        System.out.println("입력하신 음수는 : "+number);
        count++;
      }else{
        //입력한 수가 양수이면, 다시 입력하라는 메세지를 출력한다.
        System.out.println("입력하신 수는 양수입니다. 다시 입력해주세요.");
        System.out.println("입력한 음수의 갯수: "+count);
      }

      if(count == 5){
        //입력한 음수의 갯수가 5개면 while문을 종료한다.
        //count변수의 증가는 음수를 입력했을때만 증가하기 때문에,
        //양수를 무한으로 입력해도 반복문은 끝나지 않는다.
        break;
      }
    }
  }
}
```

음수를 입력하면 count변수를 증가하고 count변수가 5가 되면 break문을 실행하여 프로그램을 종료시킨다.





## continue문

continue문은 break문과 반대의 동작을 한다고 생각하면 된다. continue문도 break문과 마찬가지로 독단적으로는 사용될 수 없으며 반복문과 함께 사용되어야 한다. break문은 반복문을 강제 종료시키는 동작을 하는 문법이었다. 그렇다면 continue문은 이름에서 풍겨지는 것처럼 ***반복문을 계속 진행시키라는 의미*** 이다. 반복문을 진행하던 중에 continue를 만나면 ***그 이후 코드가 무엇이든 상관하지 않고 반복문의 제일 처음으로 돌아간다.***



```java
class continueClass{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    int flag;
    while(true){
      System.out.println("반복문을 종료하려면 0을 입력하세요");
      flag = scanner.nextInt();

      if(flag!=0){
      	continue;
      }

      System.out.println("프로그램이 종료됩니다");
      break;

    }
  }
}
```

flag에 숫자를 입력받는다. 입력받은 수가 0이 아닐 경우는 continue를 실행한다. continue를 실행하게 되면, 아래의 코드를 무시하고 ```System.out.println("반복문을 종료하려면 0을 입력하세요");```의 문장을 다시 실행한다. 0 이 입력될 경우 continue를 실행하지 않고 종료를 알리는 문자열을 출력하고 break를 실행하여 반복문을 종료시킨다. 위 프로그램은 0 이 입력되지 않는 한 끝나지 않는 프로그램이다.



### continue의 사용 for문 < while문

보편적으로 ***continue문은 for문 보다는 while문 에서 자주 사용된다.*** 그 이유는 for문의 증감 연산자는 루프 상단에 있기 때문에 continue로 반복문 상단으로 이동하면 증감 연산자에 의해 루프 변수의 값이 변경된다.

```java
class forContinueClass{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    int flag;

    for(int i=0; i<20; i++){
      System.out.println("for문 i의 값: "+i);
      System.out.println("반복문을 종료하려면 0을 입력하세요");
      flag = scanner.nextInt();

      if(flag!=0){
      	continue;
      }

      System.out.println("프로그램이 종료됩니다");
      break;
    }
  }
}
```

```
for문 i의 값: 0
반복문을 종료하려면 0을 입력하세요
1
for문 i의 값: 1
반복문을 종료하려면 0을 입력하세요
1
for문 i의 값: 2
반복문을 종료하려면 0을 입력하세요
1
for문 i의 값: 3
반복문을 종료하려면 0을 입력하세요
1
for문 i의 값: 4
반복문을 종료하려면 0을 입력하세요
.
.
.
for문 i의 값: 19
반복문을 종료하려면 0을 입력하세요
```

루프 변수 i의 값을 반복문 상단에 찍어보았을 때, continue문이 제대로 동작했음에도 i의 값이 계속 증가하고 있다. 0이 입력되기 전까지 프로그램은 100번이건 1000번이건 계속 실행되어야한다. 하지만 for문은 상단에서 루프변수에 연산을 진행하기 때문에 20번 반복을 진행하고 반복문을 종료시킨다. while문은 연산의 위치를 자유롭게 조정할 수 있기 때문에 continue는 for문 보다는 while문에서 많이 사용된다.





### continue 예제

***학생의 점수를 받아서 합계와 평균을 구하는 프로그램***  을 작성하세요.

(단, 학생의 수는 유저가 직접 입력해야하며, 음수를 입력 받았을 경우 다시 입력받아야 한다.)

```java
class continueExam{
  public static void main(String[] args){
    Scanner scanner = new Scanner(System.in);
    System.out.println("학생은 몇명입니까?");
    int student = scanner.nextInt();		//학생이 몇명인지 입력받는다.
    int score[] = new int[student];			//입력 받은 수 만큼 점수를 입력할 배열을 동적 생성한다.

    int w = 0;			//루프 변수
    int temp;       	//학생 점수를 임시 저장할 변수
    int sum = 0;		//총점을 구하기 위한 변수
    int avg = 0;		//평균을 구하기 위한 변수

    //학생의 수만큼 반복문을 돌려야한다.
    while(w < score.length ){
        System.out.print((w+1)+" 번째 학생의 점수를 입력하세요: ");
        //학생의 점수를 임시로 저장
        temp = scanner.nextInt();

        if(temp < 0){
            //학생의 점수가 음수면 입력이 올바르지 않으므로 루프의 상단으로 올라간다.
            System.out.println("입력이 올바르지 않습니다.");
            continue;		//학생의 점수를 다시 입력받는 while문 상단으로 강제 이동한다.
        }
        //입력값이 정상일 경우 임시 저장된 값을 배열 원소에 옮기고 총점을 더한다
        score[w] = temp;		//임시 저장된 점수를 배열에 옮긴다.
        sum += score[w];		//총점에 더한다.
        w++;			        //입력한 학생의 수를 증가 시켜준다.
    }

    avg = sum/student;			//평균값

    System.out.println("총점은 "+sum+" 입니다. \n평균은 "+avg+" 입니다.");
  }
}
```

```
학생은 몇명입니까?
3
1 번째 학생의 점수를 입력하세요: 123
2 번째 학생의 점수를 입력하세요: 23
3 번째 학생의 점수를 입력하세요: -3
입력이 올바르지 않습니다.
3 번째 학생의 점수를 입력하세요: 34
총점은 180 입니다.
평균은 60 입니다.
```

학생의 수를 동적으로 정해야하기 때문에 student에 학생의 수를 입력받은 후, student수 만큼 배열을 생성한다. 학생의 점수를 입력받고 임시 변수 temp에 저장하고 값을 비교한다. ***음수일 경우 continue문에 따라 입력을 받는 반복문의 상단으로 강제 이동*** 된다(이때, w값은 아무런 변화가 일어나지 않는다.). 입력값이 양수로 정상일 경우 배열에 저장하고 총점에 값을 더한 후 w를 증가 시킨다. 반복을 하다가 w가 score.length 즉 학생수보다 크다면 반복문을 종료하고 값을 출력한다.





## 정리

continue와 break는 반봅문에서 심심치 않게 등장하는 문법들이다. 둘다 독립적으로 사용될 수 없고 반복문과 함께 사용되기 때문에 반복문을 공부할때 같이 공부하는 것이 좋다. 쉽게 continue는 아래의 코드를 ***skip*** 하고 다시 반복문의 상단으로 돌아가 반복문을 ***계속*** 실행하라는 의미이고, break는 여기에서(break문이 실행되는 곳) 반복문을 멈추라는 의미이다.
