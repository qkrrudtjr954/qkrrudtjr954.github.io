---
layout: post
title: "Java 배열을 섞는 방법"
categories:
  - Java
tags:
  - Java
  - shuffle
  - 배열 섞기
---





자바에서 배열에 들어있는 원소를 셔플하는(섞는) 여러가지 방법이 등장했고, 사용되고 있다.

그 중 가장 맘에 들고 직관적인 것을 사용하면 된다. 오늘 필자는 2가지의 방법을 소개하려고 한다.

+ boolean 스위치
+ 랜덤 Swap



## Boolean 스위치

```java
class shuffle{
  public static void main(String[] args){
    int arr[] = new int[50];
    boolean _switch[] = new boolean[arr.length];

    //배열에 0부터 49까지의 숫자를 순서대로 삽입한다.
    for (int i=0; i<arr.length; i++){
      arr[i] = i;
    }
    System.out.println("\n섞기 전");
    for (int i=0; i<arr.length; i++){
      System.out.print(arr[i]+" ");
    }

    //불리언 스위치를 true로 전부 초기화 한다.
    for (int i=0; i<_switch.length; i++){
      _switch[i] = true;
    }

    int w=0;
    int r;
    while (w<arr.length){
      //0~49의 랜덤수의 index를 갖는 _switch배열의 원소가
      //true이면 if문을 실행한다.
      //ex 랜덤수가 4이면 _switch[4]는 false가 되고,
      //다음에 다시 4가 나와도 아무일도 일어나지 않고 while문을 돈다.
      //그렇게 모든 switch배열이 false로 바뀌면 shuffle이 완료 된다.
      r = (int)(Math.random()*arr.length);
      if(_switch[r]){
        _switch[r] = false;
        arr[w] = r;
        w++;
      }
    }
    System.out.println("\n섞은 후");
    for (int i=0; i<arr.length; i++){
      System.out.print(arr[i]+" ");
    }
  }
}
```

```
섞기 전
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49
섞은 후
3 27 44 37 47 30 40 14 22 0 2 32 10 46 17 35 29 12 41 21 23 7 4 33 39 48 9 45 25 34 11 31 8 42 13 38 43 18 28 20 5 19 16 36 6 26 24 1 49 15
```

Boolean 타입의 배열의 원소를 스위치로 사용하여 ```arr``` 배열에 원소를 저장할지 안할지를 판단한다.

<br><br><br>

## Random swap(랜덤 스왑)

랜덤한 수를 뽑아서 배열에 인덱스로 사용하여 배열을 마구 잡이로 섞는다.

```java
class shuffle{
  public static void main(String[] args){
    int arr[] = new int[50];
    //배열 초기화
    for (int i=0; i<arr.length; i++){
      arr[i] = i;
    }
    System.out.println("\n섞기 전");
    for (int i=0; i<arr.length; i++){
      System.out.print(arr[i]+" ");
    }

    int w=0;
    int r;
    int temp;
    while(w < arr.length){
      //0~49의 수를 랜덤하게 뽑아낸다.
      r = (int)(Math.random()*arr.length);
      //만약 두 인덱스가 다르다면
      if(w!=r){
        //swap으로 값을 바꾼다.
        temp = arr[w];
        arr[w] = arr[r];
        arr[r] = temp;
        w++;
      }
    }
    System.out.println("\n섞기 후");
    for (int i=0; i<arr.length; i++){
      System.out.print(arr[i]+" ");
    }
  }
}
```

```
섞기 전
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49
섞기 후
31 27 5 37 9 12 2 24 36 30 13 46 26 28 29 44 1 14 38 43 22 3 0 40 15 47 6 19 21 10 11 33 25 45 16 42 7 34 39 20 8 32 18 41 35 48 49 17 23 4
```

위 방법이 조금 더 쉽게 다가갈수 있다. 배열의 주소가 다른 두 원소의 위치를 바꾸기만 하면 된다. 그럼 무작위로 수가 섞이는 효과를 볼 수 있다.



<br><br>

## 정리

위와 같은 방법 뿐만 아니라 다른 많은 섞기 방법이 존재한다. 내가 지금까지 본 섞기 방법보다 획기 적이고 효과적인 방법이기 때문에 포스팅하게 되었다. Boolean 스위치를 이용하는 방법은 실무에서도 적지 않게 사용한다고 하니 숙지해두는 것이 좋을 듯 하다.
