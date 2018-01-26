---
layout: post
title: "[JDBC] JDBC의 INSERT"
categories:
  - JDBC
tags:
  - Java
  - JDBC
  - INSERT
  - JDBC 추가
---


java 코드와 Database를 연결하고 생성된 값을 통해 데이터 베이스에 하나의 행을 추가하는 코드에 대해 학습합니다.


## Insert.java

```java
public class InsertTest {

  // 연결 준비
  public InsertTest() {
    try {
      // oracle 데이터 베이스와 java 코드를 연결해주는 Driver가 있는지 체크한다.
      // Driver 가 없다면 Exceiption 이 발생한다.
      Class.forName("oracle.jdbc.driver.OracleDriver");
      System.out.println("Driver Loading Success!!");
    } catch (ClassNotFoundException e) {
      e.printStackTrace();
    }

  }

  // Database 연결
  public Connection makeConnection() {
    Connection conn = null;

    try {
      // oracle thin Database 와 연결하는 코드
      // 첫번째 변수는 계정 이름이다.
      // 두번째 변수는 비밀 번호 이다.
      conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe", "Your Id", "Your Pwd");
      System.out.println("Data Base is connected.");
    } catch (SQLException e) {
      e.printStackTrace();
    }

    return conn;
  }

  // Database에 쿼리를 전송한다.
  public int insert(String id, String name, int age) {
    // 입력값을 통해 쿼리를 String 형태로 만든다.
    String sql = "insert into userdto(id, name, age, joindate) "
      + "values('"+id+"', '"+name+"', "+age+", sysdate)";

    // Database와의 접속을 가져온다.
    Connection conn = makeConnection();
    Statement stmt = null;

    int count = 0;

    System.out.println("sql : " + sql);

    try {
      //	Statement 는 데이터 베이스와 쿼리를 실행하기 위한 준비이다.
      stmt = conn.createStatement();

      // .executeUpdate() : 데이터베이스를 바꾸는 작업 (insert, update, delete)
      // count는 바뀐 row의 수
      count = stmt.executeUpdate(sql);

    } catch (SQLException e) {
      e.printStackTrace();
    } finally {
      try {
        if (stmt != null) {
          stmt.close();
        }
        if (conn != null) {
          conn.close();
        }
      } catch (SQLException e) {
        e.printStackTrace();
      }
    }
    return count;
  }
}
```

- 실행순서
  1. 파라미터를 통해 쿼리를 생성한다.
  2. 데이터 베이스와 연결한다.
  3. ```Statement```를 준비한다.
  4. 준비한 쿼리문을 데이터베이스로 전송한다.
  5. 리턴값을 받는다.



## Main.java

```java
public class Main {
  public static void main(String[] args) {
    InsertTest it = new InsertTest();

    int count = it.insert("ABD" , "KYUNG", 52);
    System.out.println(count+ " 개 행이 추가되었습니다.");
  }
}
```
