---
layout: post
title: "Java 파일과 디렉토리의 생성"
categories:
  - Java
tags:
  - Java
  - File
  - java.io.File
  - 파일
---




자바 언어는 파일을 다루는 클래스와 함수를 제공한다.

이를 활용하면 파일을 생성, 삭제, 읽기, 쓰기 등의 동작을 자바 코드로 할 수 있다.

+ 파일과 디렉토리의 정보
+ 파일의 생성
+ 디렉토리의 생성
+ 파일을 다루는 여러가지 함수



<br><br>

## 파일과 디렉토리의 정보

파일을 다루는 클래스는 ```java.io.File``` 이다. File을 다루는 기술은 그 문법을 외우는 것보단 이해를 하고 필요할때, 찾아서 사용하는 것이다. 따라서 문법을 외우려고 너무 노력하지 않아도 된다.

```java
class createFileAndDir{
  public static void main(String[] args){
    //해당 경로에 있는 파일에 대한 정보를 담는다.
    //객체의 인자인 문자열은 디렉토리로 파일을 생성하거나,
    //원하는 위치의 디렉토리를 설정하면 된다.
    File fileDir = new File("/Users/kyungseok_park/development/folder");
    //위의 folder는 파일이 아닌 디렉토리이기 때문에
    //.list() 함수를 사용하면 해당 디렉토리의 파일, 디렉토리 정보를 모두 볼 수 있다.
    String fileList[] = fileDir.list();
    Arrays.stream(fileList).forEach(System.out::println);
  }
}
```

```
.DS_Store
.idea
chatApp
fileIO
rspApp
site-crawler
site-crawler2
socketApp
SutdaGame
```

파일과 디렉토리의 이름을 문자열 배열로 저장하고 출력한다.

<br><br>

```java
class createFileAndDir{
  public static void main(String[] args){
    File fileList2[] = fileDir.listFiles();
    Arrays.stream(fileList2).forEach(file -> {
      if(file.isFile()){
        System.out.println("[  file   ]\t:"+file);
      }else if(file.isDirectory()){
        System.out.println("[directory]\t:"+file);
      }else{
        System.out.println("[??????]\t:"+file);
      }
    });
  }
}
```

위의 코드와 조금 다른듯 보이지만 같은 동작을 하는 코드이다. 파일의 정보를 모두 배열에 담고 출력하는 코드인데, 차이점은 정보를 ```File``` 타입으로 저장했기 때문에 ```isFile()```, ```isDirectory()``` 와 같은 함수를 사용할 수 있다.

+ ```isFile()``` 은 파일이면 ```true``` 를 반환하고, 파일이 아니면 ```false``` 를 리턴한다.
+ ```isDirectory()``` 은 디렉토리면 ```true```를 아니면 ```false``` 를 리턴한다.



## 파일의 생성

```java
class createFile{
  public static void main(String[] args){
    //파일의 생성
    //파일은 이시점에 생성되는 것이 아니다
    File newFile = new File("/Users/kyungseok_park/Desktop");
    try {
      if(newFile.createNewFile()){    //파일이 생성되는 시점
        System.out.println("파일이 생성되었습니다.");
      }else {
        System.out.println("파일을 생성하지 못했습니다.");
      }
    } catch (IOException e) {
      e.printStackTrace();
      System.out.println("예외 처리");
      System.out.println("파일을 생성하는 과정에서 오류가 발생했습니다.");
    }
  }
}
```

```
파일이 생성되었습니다.
```

```.createNewFile()``` 을 함수 실행시키면, 파일이 생성된다. ```true```를 리턴하고, 생성하지 못하면 ```false``` 를 리턴한다.

예외 처리 부분은 파일을 생성하는 도중에 문제가 생긴다면 ```IOException``` 을 발생시킨다.

<br>

<br>



## 디렉토리의 생성

```java
class createDir{
  public static void main(String[] args){
    String dirStr = "/Users/kyungseok_park/Desktop/hello";
	//경로를 문자열로 받을 수도 있다
    File newFile2 = new File(dirStr);
    if(newFile2.mkdir()){   //만드려는 디렉토리가 하나일 경우
      System.out.println("디렉토리를 생성했습니다.");
    }else{
      System.out.println("디렉토리를 생성하지 못했습니다.");
    }
  }
}
```

```
디렉토리를 생성했습니다.
```

hello 를 생성하고 싶다면 File을 선언한 후에 ```.mkdir()``` 함수를 동작시키면 hello 라는 이름의 디렉토리가 생성된다. 파일을 생성하는 함수와 마찬가지로 생성되면 ```true``` 를 실패한다면 ```false```를 반환한다.

하지만 파일 생성과는 다르게 예외처리를 따로 필요로 하지 않기 때문에 파일 생성보다는 제약이 심하지 않다.

<br>

<br>

## 디렉토리 + 파일의 생성

```java
class createFileAndDir{
  public static void main(String[] args){
    String dirStr2 =  "/Users/kyungseok_park/Desktop/world/";
    String filename = "test"+".txt";    //파일의 이름은 scanner등을 통해 직접 정할 수 있다.
    File myFile = new File(dirStr2 + filename);

    try {
      if(myFile.createNewFile()){    //파일이 생성되는 시점
        System.out.println("파일이 생성되었습니다.");
      }else {
        System.out.println("파일을 생성하지 못했습니다.");
      }
    } catch (IOException e) {
      e.printStackTrace();
      System.out.println("예외 처리");
      System.out.println("파일을 생성하는 과정에서 오류가 발생했습니다.");
    }
  }
}
```

```
파일이 생성되었습니다.
```

파일 디렉토리 주소와 파일의 이름을 문자열로 합쳐서 파일의 생성 경로를 만들어 줄 수 있다.

<br>

<br>

## 파일을 다루는 여러가지 함수

```java
class fileFunction{
  public static void main(String[] args){
    File myFile = new File("/User/hello/world.txt");
    try {
      if(myFile.createNewFile()){
        System.out.println("파일이 생성되었습니다.");
      }else {
        System.out.println("파일을 생성하지 못했습니다.");
      }
    } catch (IOException e) {
      e.printStackTrace();
      System.out.println("예외 처리");
      System.out.println("파일을 생성하는 과정에서 오류가 발생했습니다.");
    }

    //파일의 존재여부를 판단하는 함수
    //.exists()
    if(myFile.exists()){
      System.out.println("파일이 존재합니다.");
    }else{
      System.out.println("파일이 존재하지 않습니다.");
    }

    //파일을 읽고 쓸 수 있는지 체크하는 함수
    //.canRead(), .canWrite()
    if(myFile.canRead()){
      System.out.println("파일을 읽을 수 있습니다.");
    }else{
      System.out.println("파일을 읽을 수 없습니다.");
    }

    if(myFile.canWrite()){
      System.out.println("파일을 쓸 수 있습니다.");
    }else{
      System.out.println("파일을 쓸 수 없습니다.");
    }

    //파일을 삭제하는 함수
    //.delete()
    if(myFile.delete()){
      System.out.println("파일이 삭제 되었습니다.");
    }else{
      System.out.println("파일이 삭제되지 않았습니다.");
    }
  }
}
```

```
파일이 존재합니다.
파일을 읽을 수 있습니다.
파일을 쓸 수 있습니다.
파일이 삭제 되었습니다.
```

위의 함수들은 파일 클래스에 내장된 기본 메소드로 동작이 성공하면 ```true```를 실패하면 ```false```를 반환한다.

***하지만 파일이 존재하지 않는다면, 예외를 발생시키기 때문에 사용에 주의를 해야한다.***
