---
layout: post
title: "Java 의 이해"
categories:
  - Java
tags:
  - Java
  - JVM
  - Java compiler
---

---
​	Java를 공부하기 전에, 과연 Java는 무엇이고, 어떤 특징을 갖고 있는지 확인해보고 Java 컴파일러, JVM 등에 대해 알아본다.
---





### Java 란?

<p>

가정용 단말기에 사용하려는 목적으로 만들어진 OAK언어에서 비롯 되었어 만들어진 가장 대표적인 객체 지향 언어이다.  현재 Java 언어는 앱개발, 웹개발 등 에서 사용되는 대표적인 프로그래밍 언어이다.

[Java란?](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))

</p>



### Java 의 특징

+ 이식성이 좋다
  + 컴파일러에 의해 생성된 Java Byte Code는 하드웨어 또는 소프트웨어 플랫폼에서 효율적으로 전송이 가능하다
  + 어떤 환경이든 관계없이 JVM만 설치되어 있다면 Java Byte Code를 실행할 수 있다.
+ 객체지향 언어
  + Java는 대표적인 객체 지향 언어이다.
+ 꾸준한 버젼 업데이트
  + Java는 꾸준한 버젼 업데이트를 제공한다.
  + 최근 버젼 9 까지 제공되었다
  + 버젼 8에서는 함수형 프로그래밍이 추가 되었다.
+ 가비지 컬렉션을 통한 메모리 관리
  + Java는 특별한 메모리 관리를 하지 않아도 가비지 컬렉터가 자동 실행 되어 메모리 공간을 효율적으로 다룰 수 있다.
+ 다양한 어플리케이션 개발
  + Java는 안드로이드 앱부터 웹까지 애플리케이션을 개발하는 전범위적인 프로그래밍 언어로 자리잡았다.





### Java 컴파일러

<p>

Java 코드는 .java 파일로 작성되어 있다. 이 파일은 사용자가 작성했거나 다른 누군가가 작성한 코드로 사람이 보기 좋은(사람이 알아볼 수 있는) 코드로 되어 있다. 하지만 컴퓨터는 오직 0과 1만 읽을 수 있기 때문에 .java 파일을 읽을 수 없다.

_때문에,_ .java 파일을 컴퓨터가 알아볼 수 있는 Java Byte Code 로 변환을 시켜주어야 하는데 이 역할을 담당하는 것이 바로 <span style="color:red">Java 컴파일러</span> 이다.

Java 컴파일러를 거친 .java 파일은 .class 파일로 변환되어 컴퓨터가 알아볼 수 있는 class 파일로 변환된다.

또한, 운영체제에 독립적이기 때문에 운영체제에 가상 머신만 설치되어 있다면 언제든 Java 컴파일러를 실행 가능하다.

</p>





### 자바 가상 머신 JVM (Java Virtual Machine)

<p>

자바 가상 머신(이하 JVM)은 운영체제가 _Java 컴파일러_ 에 의해 변환 된 자바 바이트 코드를 실행할 수 있도록 해주는 주체이다.

 JVM의 가장 큰 장점은 어떤 플랫폼(CPU, OS)에 상관없이 동일한 형태로 _자바 바이트 코드_를 실행할 수 있다는 점이다.

> JVM이 깔려 있다면 어떠한 컴퓨터 또는 어떠한 환경이든 상관없이 Java Byte Code (class 파일)를 실행할 수 있다.

[자바 가상 머신이란?][https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_%EA%B0%80%EC%83%81_%EB%A8%B8%EC%8B%A0]

</p>

### Java 의 역사

<p>

1991년 6월 자바는 [제임스 고슬링][https://ko.wikipedia.org/wiki/%EC%A0%9C%EC%9E%84%EC%8A%A4_%EA%B3%A0%EC%8A%AC%EB%A7%81]에 의해 탄생했다. 제임스 고슬링의 목표는 C/C++ 스타일의 언어와 가상 머신을 만드는 것이었다.

1995년에 자바 1.0이 공개되었고, *" Write Once, Run Anywhere "* 한번 만들면 어디서든 실행 가능하게 하겠다는 약속과 함께 인기 플랫폼에 무료 런타임을 제공하였다.

자바2의 출현으로 여러 플랫폼에서 사용할 수 있는 설정들이 만들어졌다.

</p>

+ Java EE
  + **자바 플랫폼, 엔터프라이즈 에디션**
  + 자바를 이용한 서버측 개발을 위한 플랫폼
  + PC에 동작하는 표준 플랫폼인 Java SE에 부가하여, 웹 애플케이션 서버에 기능을 추가한 서버를 위한 플랫폼
  + 명칭이 J2EE 에서 Java EE로 개정된
+ Java SE
  + **자바 플랫폼 스탠더드 에디션 **
  + 데스크톱 및 서버, 최근 고사양 임베디드 시스템을 위한 표준 자바 플랫폼
+ Java ME
  + **자바 플랫폼, 마이크로 에디션**(Java Platform, Micro Edition)은 Java 2 Platform, Micro Edition
  + 자바 ME(Java ME) 혹은 **J2ME** 등으로도 널리 알려져 있다.
  + 제한된 자원을 가진 [휴대 전화](https://ko.wikipedia.org/wiki/%ED%9C%B4%EB%8C%80_%EC%A0%84%ED%99%94), [PDA](https://ko.wikipedia.org/wiki/PDA), [세트톱박스](https://ko.wikipedia.org/wiki/%EC%84%B8%ED%8A%B8%ED%86%B1%EB%B0%95%EC%8A%A4) 등에서 [Java 프로그래밍 언어](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))를 지원하기 위해 만들어진 [플랫폼](https://ko.wikipedia.org/wiki/%EC%BB%B4%ED%93%A8%ED%8C%85_%ED%94%8C%EB%9E%AB%ED%8F%BC) 중 하나를 가리킨다.





 _Parker_	- 2017.10.25
