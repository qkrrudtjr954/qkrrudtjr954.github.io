---
layout: post
title: "Java 야구 게임"
categories:
  - Java
tags:
  - Java
  - baseball
  - 야구 게임
---



3가지의 랜덤 숫자와 유저가 입력한 수를 비교하여 *숫자도 같고, 자리도 같으면* ***스트라이크***, *숫자는 같지만 자리가 틀리면* ***볼*** 을 출력하는 야구게임을 작성하시오.



```java
package baseball;

import java.util.Scanner;

public class mainClass {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    //baseball
    int r_num[] , u_num[];
    boolean clear;

    //init
    r_num = new int[3];	//random number
    u_num = new int[3];	//user number

    clear = false;
    //random
    random(r_num);	//random 수를 배열에 삽입

    /////////////////////////////////   loop
    //finding
    //user input 유저의 입력
    //message	결과를 출력
    clear = loop(r_num, u_num);	//게임 동작
    ////////////////////////////////   release

    //result print
    result(clear);	//게임 결과 출력
  }
  static void random(int r_num[]) {
    int w = 0;
    int r;
    boolean[] swit = new boolean[10];

    for(int i = 0;i < 10; i++){
      swit[i] = false;   // 00000 00000
    }

    while(w < 3){
      r = (int)(Math.random() * 10);   // 0 ~ 9
      if(swit[r] == false){
        swit[r] = true;      // r이 2일 경우: 00100 00000  
        r_num[w] = r + 1;   // 1 ~ 10
        w++;
      }
    }

    for(int i = 0;i < r_num.length; i++){
      System.out.println("r_num[" + i + "] = " + r_num[i]);
    }
  }
  //게임 로직
  static boolean loop(int[] r_num, int[] u_num) {
    //finding
    boolean clear = false;
    int strike;
    int ball;
    int w = 0;

    while(w < 10) {
      strike = 0;
      ball = 0;
      //user 의 숫자 입력
      userInput(u_num);
      // ball
      for(int i = 0;i < 3; i++){
        for(int j = 0;j < 3; j++){
          //숫자는 같지만 자리가 다르면 볼
          if(u_num[i] == r_num[j] && i != j){
            ball++;
          }
        }
      }
      // strike
      for(int i = 0;i < 3; i++){
        //숫자도 같고 자리도 같으면 스트라이크
        if(u_num[i] == r_num[i]){
          strike++;
        }
      }
      if(strike > 2){
        clear = true;
        break;
      }

      // message ..strike ..ball
      System.out.println(strike + "스트라이크 " + ball + "볼입니다");
      w++;
    }

    return clear;
  }

  static void userInput(int[] u_num) {
    int w =0;
    Scanner scanner = new Scanner(System.in);

    while(w < 3){
      System.out.print((w + 1) + "번째 수:");
      u_num[w] = scanner.nextInt();
      w++;
    }
  }
  static void result(boolean clear) {
    if(clear) {
      System.out.println("축하합니다!!");
    }else {
      System.out.println("아쉽습니다..");
    }
  }

}
```
