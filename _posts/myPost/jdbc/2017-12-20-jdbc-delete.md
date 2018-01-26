---
layout: post
title: "[JDBC] JDBC의 DELETE"
categories:
  - JDBC
tags:
  - Java
  - JDBC
  - DELETE
  - JDBC 삭제
---



java 코드와 Database를 연결하고 조건에 일치하는 값을 데이터 베이스에서 삭제하는 방법을 학습합니다.


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




## DeleteTest.java


데이터 베이스와 연결해서 쿼리를 날리는 소스 코드


```java
public class DeleteTest {
  public int delete(int age) {
    String sql = "delete from userdto where age<"+age;

    Statement stmt = null;

    Connection conn = DBConnection.makeConnection();

    int count = 0;

    System.out.println("sql : "+sql);

    try {
      stmt = conn.createStatement();
      count = stmt.executeUpdate(sql);

    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } finally {
      DBClose.close(stmt, conn, null);
    }

    return count;
  }
}
```
- 변수 ```age```보다 나이가 작은 모든 데이터를 삭제한다.


## Main.java

```java
public class Main {
  public static void main(String[] args) {
    DeleteTest dt = new DeleteTest();

    // 25살보다 작은 모든 유저를 삭제하고,
    // 삭제된 행의 개수를 반환한다.
    int count = dt.delete(25);
  }
}
```
