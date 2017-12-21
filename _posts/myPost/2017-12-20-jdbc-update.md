---
layout: post
title: "[JDBC] JDBC의 UPDATE"
categories:
  - JDBC
tags:
  - Java
  - JDBC
  - UPDATE
  - JDBC 수정
---

java 코드와 Database를 연결하고 조건에 일치하는 값을 데이터 베이스에서 수정하는 방법을 학습합니다.


## DBConnection.java


데이터 베이스와 연결을 하는 코드를 별도의 ```Class``` 파일로 관리한다.

```java
public class DBConnection {
  // 드라이버가 존재하는지 확인한다.
  public static void initConnect() {
    try {
      Class.forName("oracle.jdbc.driver.OracleDriver");
      System.out.println("Driver Loading Success!!");
    } catch (ClassNotFoundException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }

  // 데이터 베이스와 연결한다.
  public static Connection makeConnection() {
    Connection conn = null;

    try {
      conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe", "Your Id", "Your Pwd");
      System.out.println("Data Base is connected.");
    } catch (SQLException e) {
      e.printStackTrace();
    }

    return conn;
  }
}
```

## DBClose.java

생성된 ```DBConnection```을 닫기 위한 함수를 따로 생성한다.


```java
public class DBClose {
  public static void close(Statement stmt, Connection conn, ResultSet rs) {
    try {
      if (stmt != null) {
        stmt.close();
      }
      if (conn != null) {
        conn.close();
      }
      if (rs != null) {
        rs.close();
      }
    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }
}
```


## UpdateTest.java

```java
public class UpdateTest {

  public int update(String id, String name) {
    Connection conn = DBConnection.makeConnection();
    Statement stmt = null;

    String sql = "update userdto set name='"+name+"' where id='"+id+"'";

    int count = 0;

    try {
      stmt = conn.createStatement();
      count = stmt.executeUpdate(sql.toString());
    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }

    return count;
  }

  public int update(String id, int age) {
    Connection conn = DBConnection.makeConnection();
    Statement stmt = null;

    String sql = "update userdto set age="+age+" where id='"+id+"'";

    int count = 0;

    try {
      stmt = conn.createStatement();
      count = stmt.executeUpdate(sql.toString());
    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }

    return count;
  }

}
```
- 첫번째 ```update()```
  - ```id, name```을 입력 받아 이름을 수정하는 메소드
- 두번째 ```update()```
  - ```id, age```를 입력 받아 나이를 수정하는 메소드


## Main.java

```java
public class Main {
  public static void main(String[] args) {
    UpdateTest ut = new UpdateTest();

    // 해당 Id의 유저의 이름을 Change로 변경한다.
    ut.update("Your Id", "Change");

    // 해당 Id의 유저의 나이를 30으로 변경한다.
    ut.update("Your Id", 30);
  }
}
```
