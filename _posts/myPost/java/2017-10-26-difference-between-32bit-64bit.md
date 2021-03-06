---
layout: post
title: "윈도우 운영체제 32bit vs 64bit 차이"
categories:
  - Operating System
tags:
  - os
  - window
---



윈도우 운영체제를 보면 32bit 라고 표기된 것이 있고 64bit 라고 표기된 것이 있다. <br>
이 둘에는 어떤 차이가 있을까?


### 레지스터
컴퓨터의 [중앙 처리 장치(CPU)](https://ko.wikipedia.org/wiki/%EC%A4%91%EC%95%99_%EC%B2%98%EB%A6%AC_%EC%9E%A5%EC%B9%98)는 메인보드 위에서 컴퓨터 내의 모든 연산과 데이터 처리를 담당하고 있다.<br>
CPU 가 메모리 또는 기타 입출력 장치와 데이터를 주고 받을 때 사용하는 고속의 저장 장소가 바로 [레지스터](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%84%9C_%EB%A0%88%EC%A7%80%EC%8A%A4%ED%84%B0) 이다. <br>
즉, 레지스터의 크기는 CPU가 주고 받을 수 있는 데이터의 최대 크기와 같고 운영체제의 32bit, 64bit의 크기는 레지스터의 크기( CPU가 주고 받을 수 있는 데이터의 최대 크기 )이다.
+ 32bit 컴퓨터의 레지스터의 크기는 32bit
+ 64bit 컴퓨터의 레지스터의 크기는 64bit






### 비트와 바이트
컴퓨터는 오직 0과 1 두가지의 데이터만을 읽고 처리할 수 있다. <br>
그리고 그 0과 1을 처리하는 단위가 bit ( 컴퓨터가 데이터를 처리하는 최소한의 단위 )이다.

![bitimg](https://i.imgur.com/cE2pSy0.png)
+ 1KB	= 1024 byte
+ 1MB	= 1024 KB
+ 1GB	= 1024 MB
+ 1TB 	= 1024 GB
+ 1PB	= 1024 TB
<br>
<br>

### 요약
시대가 흘러 하드웨어가 발전하게 되면서 데이터를 처리하는 양이 월등히 증가했다. 따라서 CPU가 처리하는 데이터의 양도 증가했고 자연스럽게 레지스터의 크기도 증가했다. (32bit에서 64bit으로 바뀌고 있다)<br>
전세계 사용자들이 32bit와 64bit 컴퓨터를 혼용해서 사용하고 있기 때문에, <br> 프로그램을 제공하는 회사에서는 호환성의 문제를 고려하려 프로그램을 32bit용 프로그램과 64bit용 프로그램을 따로 나누어 제공한다.

### 도트와 픽셀(dot & pixel)
우리가 보는 모니터 화면은 dot와 pixel로 표현되고, 이는 CPU 에서 보낸 컬러값(rgba)에 의해 표시된다. <br>
1byte의 표현 범위가 0 ~ 255임을 생각 했을 때, 32bit 컴퓨터는 총 32bit(4byte)의 컬러값을 표현할 수 있다.
![dotimg](https://i.imgur.com/6C0lbX3.png)
그것이 우리가 잘 알고 있는 rgba 이다.

>64bit 컴퓨터는 한 pixel에 32bit 보다 2배의 컬러값을 보낼 수 있다.
