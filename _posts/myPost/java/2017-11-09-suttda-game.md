---
layout: post
title: "Java 섯다 게임"
categories:
  - Java
tags:
  - Java
  - 섯다
  - 섯다 게임
---




화투 1월 부터 10월까지의 패 각 2장씩을 섞어 2장의 카드를 뽑아 점수를 매기는 게임

[섯다](https://namu.wiki/w/%EC%84%B0%EB%8B%A4)



```java
package suttdaGame;

import java.util.Scanner;

public class mainClass {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    int card[] = new int[20];
    int userCard[] = new int[2];
    int comCard[] = new int[2];
    int win = 0;
    int draw = 0;
    int lose = 0;
    String again;
    Scanner scanner = new Scanner(System.in);
    do {
      //카드 섞기
      shuffle(card);

      //카드 분배
      //섞인 카드를 유저와 컴퓨터가 2장씩 나눠 가진다.
      getCard(userCard, comCard, card);

      //유저 카드, 컴퓨터 카드 출력
      System.out.println("유저와 컴퓨터가 뽑은 카드");
      System.out.println("player card: "+userCard[0]+"월, "+userCard[1]+"월");
      System.out.println("computer card: "+comCard[0]+"월, "+comCard[1]+"월");

      //유저와 컴퓨터의 점수를 가져온다.
      //장땡 = 30, 구땡 = 29,..., 알리 = 20, ... 등등
      int userScore = getScore(userCard);
      int comScore = getScore(comCard);

      //가져온 점수를 비교해서 승패를 나눈다.
      int result = sorceCheck(userScore, comScore);

      //result == 1이면 승리, 2이면 무승부, 3이면 패배
      if(result==1)   win++;
      else if(result==2) draw++;
      else   lose++;

      System.out.println(win+"승 "+draw+"무 "+lose+"패");
      System.out.print("한판 더 하시겠습니까? ");
      again = scanner.next();
    }while(again.equals("y")||again.equals("yes")||again.equals("Y")||again.equals("Yes"));
    System.out.println("안녕히 가세요.");

  }
  //유저와 컴퓨터의 점수를 받아 승패여부를 result값으로 리턴한다.
  static int sorceCheck(int player, int com) {
    if(player > com) {
      System.out.println("승리했습니다.");
      return 1;
    }else if(player == com) {
      System.out.println("비겼습니다.");
      return 2;
    }else {
      System.out.println("패배했습니다.");
      return 3;
    }
  }
  //플레이어의 카드에 따라 점수를 리턴한다.
  static int getScore(int[] playerCard) {
    int player = 0;
    //score check
    if(playerCard[0] == playerCard[1]) {
      player = playerCard[0]+20;
    }else if(playerCard[0]==1){
      if(playerCard[1] ==2 ) {
        player = 20;      //알리 (1월, 2월)
      }else if( playerCard[1] ==4 ) {
        player = 19;      //독사 (1월, 4월)
      }else if(playerCard[1] ==9 ) {
        player = 18;      //구삥 (1월, 9월)
      }else if(playerCard[1] ==10 ) {
        player = 17;      //장삥 (1월, 10월)
      }
    }else if(playerCard[0]==4) {
      if(playerCard[1] ==6 ) {
        player = 16;      //세륙 (4월, 6월)
      }else if( playerCard[1] ==10 ) {
        player = 15;      //장사 (4월, 10월)
      }      
    }else{
      player = (playerCard[0]+playerCard[1])%10;
    }   
    return player;
  }

  //유저와 컴퓨터에게 카드를 분배한다.
  static void getCard(int[] userCard, int[] comCard, int[] card) {
    int temp;
	//card배열은 이미 shuffle되어 있기 때문에 순서대로 주어도
    //랜덤한 카드를 받는다.
    userCard[0] = card[0];
    comCard[0] = card[1];
    userCard[1] = card[2];
    comCard[1] = card[3];

    //카드 정렬
    //작은 숫자가 앞에 오게 swap
    if(userCard[0] > userCard[1]) {
      cardSwap(userCard);
    }
    if(comCard[0] > comCard[1]) {
      cardSwap(comCard);
    }
  }

  static void cardSwap(int[] playerCard) {
    int temp;

    temp = playerCard[0];
    playerCard[0] = playerCard[1];
    playerCard[1] = temp;
  }

  //카드 섞기
  static void shuffle(int[] card) {
    boolean swit[] = new boolean[card.length];
    int w = 0;
    int r;

    //random
    while(w < card.length) {
      r = (int)(Math.random()*card.length);
      if(!swit[r]) {
        swit[r] = true;
        card[w] = (r%10)+1;         //1~20
        w++;
      }
    }
  }

}
```
