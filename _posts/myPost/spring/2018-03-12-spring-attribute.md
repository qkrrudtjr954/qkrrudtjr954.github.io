---
layout: post
title: "[Spring]의 기본"
categories:
  - Spring
tags:
  - Spring
  - Framework
  - container
  - 컨테이너
  - IoC
  - Inversion of Control
  - 제어의 역전
  - DI
  - Dependency Injection
  - 의존성 주입
---


Spring Framework 가 갖는 기본 성질과 Container, Ioc, DI 의 개념에 대해 학습합니다.

출처 : http://springmvc.egloos.com/487497


## container

- 컨테이너란 당신이 작성한 코드의 처리과정을 위임받은 독립적인 존재.
- 컨테이너는 적절한 설정만 되있다면 누구의 도움 없이도 프로그래머가 작성한 코드를 스스로 참조한 뒤 알아서 객체의 생성과 소멸을 컨트롤해준다.
- 프로그래머가 작성한 코드는 컨테이너를 사요하게 됨으로서 프로그래머의 손을 떠나 컨테이너 의 영역으로 떠나버리게 된다.
- Spring 의 태표적인 컨테이너를 예로 들자면 톰캣과 같은 WAS(Web Application Service)이다.


## IoC / DI

- Inversion of Control / Dependency Injection의 줄임말이다.
- 제어의 역전 / 의존적 주입
- 대신 해줌 (IoC) / 미리 찜 해놓음 (DI)
- ***정신 나간듯 언제 사용될 지도 모르는 코드를 쳐대면서 (IoC) 동시에 사용하고 있는 코드가 뭔지도 모르면서 일단 갖다 쓰는(DI) 획기적이고 진보적인 프로그래밍 작성방식***


#### IoC

- 우리의 제어를 대신 해주는 것
- 컨테이너이다.
- 스프링은 IoC 방식을 철저하게 준수한다.
- 하지만, IoC는 스프링만의 고유한 방식은 아니다.


#### DI

- 주는 놈은 생각도 않았는데 먼저 말부터 꺼내놓는 파렴치한 코딩방식
- "저는 짜장면 안먹고 양장피 먹겠습니다."
- 현재 사용하고 있는 객체의 메서드가 어떻게 작성되었는지 알 필요가 없고, 그 클래스의 메소드가 잘 구현되어 있는지 조차 알필요가 없다.
- 클래스의 기능을 추상적으로 묶어둔 인터페이스를 가져다가 쓰면 된다.

```java
public interface StrategyPattern {
  void dependency_injection();
}

class StrategyPatternImpl implements StrategyPattern {
  @Override
  public void dependency_injection(){
    System.out.println("저는 짜장면 안먹고 양장피 먹겠습니다.");
  }
}

class StrategyPatternService {
  public static void main(String[] args){
    StrategyPattern sp = new StrategyPatternImpl();
    sp.dependency_injection();
  }
}
```


```
저는 짜장면 안먹고 양장피 먹겠습니다.
```

- ```StrategyPatternService```에 ```sp``` 객체는 인터페이스 객체인 ```StrategyPattern```으로 선언되어 있고, ```StrategyPattern```의 ```dependency_injection()``` 메서드를 호출하고 있다.
- 하지만 선언부에 ```new StrategyPatternImpl()``` 로 ***의존성을 주입*** 시킴으로서 ```StrategyPatternImpl``` 의 ```dependency_injection()``` 을 호출하게 된다.



## 서비스 추상화

- 추상화란 하위 시스템의 공통점을 뽑아내서 분리시키는 것을 말한다.
- 하위 시스템이 어떤 것인지 알지 못해도, 또는 하위 시스템이 바뀌더라도 일돤된 방법으로 접근할 수 있다.
- 위의 예제에서 ```StrategyPattern``` 이란 인터페이스로 기능을 분리시킴으로서 하위시스템, 즉 클래스가 그 무엇으로 교체되더라도 해당 메서드는 반드시 존재할 것이란 보장을 받음.
a


<br>
<br>


출처 : http://springmvc.egloos.com/487497
