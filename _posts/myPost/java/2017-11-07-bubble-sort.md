---
layout: post
title: "Java 버블 소트"
categories:
  - Java
tags:
  - Java
  - 정렬
  - 버블 정렬
  - sort
  - bubble sort
  - algorithm
---



버블 소트는 소트들 중 효율이 좋은 방법은 아니다. 하지만 방법이 아주 쉽고 코드 또한 단순하기 때문에 자주 사용되는 소트 중에 하나 이다.

버블 소트는 인접한 두 수를 비교해서 조건에 맞게 두 위치를 바꾼다.



### 버블 소트의 정렬 과정

![버블소트 순서](https://i.imgur.com/cyCfguy.png)

[버블 소트](https://ko.wikipedia.org/wiki/%EA%B1%B0%ED%92%88_%EC%A0%95%EB%A0%AC)

앞의 수가 뒷 수보다 크면 둘의 위치를 바꾸면서 마지막 수까지 비교하며 정렬한다.



### 소스코드

```java
class bubbleSort{
  public static void main(String[] args){
    // TODO Auto-generated method stub
    /*
    * 오름차순 정렬
    * 내림차순 정렬
    * 최신 등록순
    * 가격순
    * 연봉순
    * 입사일
    *
    *
    * 퀵소트 > 머지 소트 > 버블 소트  
    */

    int number[] =
      {1, 3, 4, 65, 46, 46, 84, 51, 23, 4,
      84, 6541, 32, 15, 34, 894, 9874, 651,
      32, 1, 4, 6847, 65, 41};

    int temp;
    //bubble sort
    //number.length-1 마지막은 이미 정렬이 되었기 때문에 비교해줄 필요가 없다.
    for(int i=0 ; i<number.length-1; i++) {
      for (int j = i+1; j < number.length; j++) {
        //앞의 수가 더 크다면 swap
        if(number[i] < number[j]) {		//부호만 바꾸면 내림차순으로 정렬할 수 있다.
          temp = number[i];
          number[i] = number[j];
          number [j] = temp;
        }
      }
    }
	//정렬 출력
    for (int i = 0; i < number.length; i++) {
      System.out.println(number[i]);
    }
  }
}
```

```
1
1
3
4
4
4
15
23
32
32
34
41
46
46
51
65
65
84
84
651
894
6541
6847
9874
```
