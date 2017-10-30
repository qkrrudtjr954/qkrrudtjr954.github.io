---
layout: post
title: "Java 의 Main Method"
categories:
  - Java
tags:
  - Java
---

프로그램을 개발하는데 있어서는 편하고 간편한 것이 최고라고 생각한다. 최근 [통합 개발 환경( 이하 IDE )](https://ko.wikipedia.org/wiki/%ED%86%B5%ED%95%A9_%EA%B0%9C%EB%B0%9C_%ED%99%98%EA%B2%BD) 들이 나날이 발전하면서 개발을 하기에 아주 편리한 시대가 되었다. <br>
[intellij](https://www.jetbrains.com/idea/) , [Eclipse](https://www.eclipse.org/) 와 같은 대표적인 IDE 들을 사용하면 자바 프로그램을 더 쉽고 간편하게 이용할 수 있다.

---
<br><br><br>
``` java
public static void main(String[] args){
	System.out.println("Hello world!");
}
```
위에서 설명한 간편한 IDE를 사용하거나 자바 프로젝트를 만들어본 경험이 있다면 익숙한 코드일 것이다. <br>
<br><br><br>
#### 프로젝트를 한다면 무조건 만나는 main method 의 의미를 알아보자.
+ public
	+ 어디서든 접근 가능한 공용의 메소드
+ static
	+ 정적으로 사용하는 메소드
+ void
	+ 함수를 실행 하고 반환되는 데이터의 타입
+ main
	+ 함수의 이름 (main method는 반드시 main이어야 하지만 다른 메소드들은 자유롭게 정의 가능)
+ (String[] args)
	+ main method에서 사용할 변수의 타입과 이름
+ System.out.println("Hello world!");
	+ 표준 출력 함수
