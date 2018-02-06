---
layout: post
title: '[jsp] 이클립스 외부 jar파일 추가하기'
categories:
  - etc
tags:
  - eclipse
  - add external jar file
  - jar file
---




eclipse 에서 외부 jar파일을 추가하는 방법을 소개한다.


#### step.1

- 필요한 .jar파일을 다운로드한다.
- ```mysql-connector-java-5.1.45.jar``` 를 샘플로 사용한다.


#### step.2


- 프로젝트를 생성한다.
- 생성된 프로젝트에서 ***우클릭*** 을 하고 ***Build Path*** 에 ***Configure Build Path*** 를 클릭한다.

![step2](https://i.imgur.com/KdSbeDw.png)



#### step.3



- ```Libraires``` 탭을 클릭한다.
- ```Add External JARs...``` 를 클릭한다.



![step3](https://i.imgur.com/6YJVrua.png)



#### step.4


- 외부 jar파일을 추가한다.

![step4](https://i.imgur.com/8jkqOFy.png)



#### step.5


- 추가된 jar파일을 확인할 수 있다.
- 확인하고 apply를 누른다.

![step5](https://i.imgur.com/JIkZrCT.png)



## 위의 과정을 진행해도 ClassNotFound Exception이 난다면!



#### step.6


- ```WebContent/WEB-INF/``` 하위의 ```lib``` 폴더를 ***우클릭*** 한다.
- ```import```를 클릭한다.

![step6](https://i.imgur.com/6dZMwpq.png)





#### step.7



- ```File System```을 선택하고 ```Next```를 누른다.


![step7](https://i.imgur.com/18b6DJm.png)



#### step.8



- jar 파일의 경로를 추가하고 jar파일을 import한다.


![step8](https://i.imgur.com/yZOZaep.png)




#### step.9


- ```lib``` 폴더 아래 jar파일이 추가된 것을 확인한다.

![step9](https://i.imgur.com/DNUUo9I.png)
