---
layout: post
title: "Java 피보나치 수열"
categories:
  - Java
tags:
  - Java
  - fibonaci
  - 피보나치
  - 알고리즘
  - algorithm
---



피보나치 수열은 프로그래밍을 하는 사람이라면 반복문을 배우고 바로 작성해보는 코드라고 생각한다.

피보나치 수열에 대한 수학적인 자세한 설명은 [피보나치 수열](https://ko.wikipedia.org/wiki/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98_%EC%88%98) 본 링크를 참조하면 된다.

피보나치 수열에 대해 간단히 설명을 하면 앞의 두 수를 더한 값이 다음의 수를 정의한다.

+ 첫번째 수가 1이고 두번째 수가 1일 때 세번째 수는 1 + 1인 2가 된다.
+ 두번째 수가 1이고 세번째 수가 2일 때 네번째 수는 1 + 2인 3이 된다.
+ 처음 수가 증가하는 폭은 굉장히 작지만, 20번 이상 진행되면 수가 급격히 증가한다.
+ 증권가의 막대그래프 조사 등에 사용된다고 한다.



## 피보나치 수열 코드

```java
class fibonaci{
  public static void main(String[] args){
    // TODO 피보나치
    long a=1;		//숫자가 굉장히 커지기 때문에 long으로 선언한다.
    long b=1;
    long c;

    long arrNum[] = new long[20];		//20번째까지의 피보나치 수열을 담는다.

    int w=0;	//루프변수 초기화

    arrNum[0] = a;	//첫번째 수와
    arrNum[1] = b;	//두번째 수 세팅

    // 1	1	2	3	5	8
    // a	b	c
    //		a	b	c(a+b)	.....
    //
    //c는 a와 b를 더한값이 되고, 현재 b값은 a변수에 현재 c값은 b변수에 전달하며 한칸씩 나아간다.
    //20번을 돌아가며 a, b, c의 자리를 변경해준다.
    while(w < 18) {
      c = a+b;
      a = b;
      b = c;
      arrNum[w+2] = c;
      w++;
    }

    for (int i = 0; i < arrNum.length; i++) {
      System.out.println(arrNum[i]);
    }
  }
}
```

```
1
2
3
5
8
13
21
34
55
89
144
233
377
610
987
1597
2584
4181
6765
10946
```
