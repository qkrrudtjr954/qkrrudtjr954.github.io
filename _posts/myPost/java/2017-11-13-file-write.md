---
layout: post
title: "Java 파일 쓰기 (Write)"
categories:
  - Java
tags:
  - Java
  - File
  - java.io.File
  - 파일 쓰기
  - FileWriter
  - BufferedWriter
  - PrintWriter
---

파일을 읽는 방법을 알아봤으니 파일을 쓰는 방법을 알아보자.

파일에 데이터를 쓰는 방법은 여러가지이다. 그리고 쓰기 기능을 제공하는 클래스도 여러가지가 있다.

기능별 차이점과 사용방법을 알아보자.
<br><br>
+ FileWriter
+ FileWriter with append (파일을 덮어 쓰지 않고 이어서 작성한다.)
+ BufferedWriter
+ PrintWriter




<br><br>

## FileWriter

파일을 쓰는 기본적인 클래스는 ```java.io.FileWriter``` 이다. ```FileReader``` 와 쌍을 이루고 있으며 기본적으로 문자열, ```int``` 등 파일에 쓰는 것이 가능하다.
```java
public class fileWriter {
  public static void main(String[] args) {
    //파일 객체 생성
    File file = new File("/Users/kyungseok_park/Desktop/hello.txt");

    try {
      //파일에 문자열을 쓴다.
      //하지만 이미 파일이 존재하면 모든 내용을 삭제하고 그위에 덮어쓴다
      //파일이 손산될 우려가 있다.
      FileWriter fw = new FileWriter(file);
      fw.write("hello world");
      fw.close();
    } catch (IOException e) {
      e.printStackTrace();
    }
  }
}

```

```FileWriter``` 는 기존의 파일의 내용을 모두 삭제하고, 그 위에 새로 쓰기 때문에 신중하게 사용해야한다.

<br><br>

## FileWriter

하지만 ```FileWriter``` 가 파일을 덮어쓰는 방법만 있는 것은 아니다.

***파일이 이미 존재한다면, 파일의 마지막부터 이어서 쓰는 방법도 있다.***

```java
public class fileAppend {
    public static void main(String[] args) {
        File file = new File("/Users/kyungseok_park/Desktop/hello.txt");

        try {
            //파일에 문자열을 쓴다
            //하지만 파일이 존재한다면 덮어쓰는게 아니라 .
            //그 뒤에 문자열을 이어서 작성한다.
            FileWriter fw = new FileWriter(file, true);
            fw.write("hello world");
            fw.close();
        } catch (IOException e) {
            e.printStackTrace();
        }


    }
}
```

```FileWriter``` 의 선언 부분에 두번째 인자로 boolean 타입의 ```true```를 같이 보내면 된다.

아주 간단한 방법으로 파일 이어쓰기 기능을 제공한다.

<br><br>

## BufferedWriter

 ```BufferedWriter``` 역시 파일 쓰기를 담당한다. ```FileWriter``` 객체를 인자로 ```BufferedWriter``` 객체를 생성하고, 그 사용법은 ```FileWriter```와 동일하다.

```java
public class bufferedWriter {
  public static void main(String[] args) {
    File file = new File("/Users/kyungseok_park/Desktop/hello.txt");

    try {
      BufferedWriter bw = new BufferedWriter(new FileWriter(file));
      bw.write("hello world!");
      bw.write("this is buffered writer!");
      bw.close();
    } catch (IOException e) {
      e.printStackTrace();
    }

  }
}
```

그렇다면 ```FileWriter``` 와 ```BufferedWriter```의 차이는 무엇일까?

이름에서 느껴지는 것 처럼 ```BufferedWriter```는 버퍼를 갖고 있다. 그리고  ```BufferedWriter```가 다음 두가지 조건에서 ```FileWriter``` 보다 효과적이다.

+ 버퍼 보다 작은 크기의 쓰기일 경우
+ 한 곳이 아닌 여러 곳에서 쓰기가 이루어 지는 경우

***항상*** ```BufferedWriter```  ***가 효과적인 것은 아니다.***

<br><br>





## PrintWriter

```PrintWriter``` 는 ```BufferedWriter``` 의 차이는 단 하나 이다. (사실 기능적으로 많은 차이가 있겠지만, 내가 느끼기엔 하나다...)

***개행을 하는 문자열을 넣을 수 있다.*** 다른 쓰기 메소드들은 개행을 하는 문자를 따로 적어주어야 했는데, ```PrintWriter```는 ```.println```메소드를 통해 파일에 개행된 문자열을 넣을 수 있다.

```.print``` 는 ```.write``` 메소드와 동일하다.

```java
public class printWriter {
    public static void main(String[] args) {
        File file = new File("/Users/kyungseok_park/Desktop/hello.txt");

        try {
            PrintWriter pw = new PrintWriter(new BufferedWriter(new FileWriter(file)));
            pw.println(10);
            pw.println('a');
            pw.println(10.44);
            pw.println("hello world!");
            pw.println();

            pw.print(10);
            pw.print('a');
            pw.print(10.44);
            pw.print("hello world!");

            pw.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

#### hello.txt

```java
10
a
10.44
hello world!

10a10.44hello world!
```
