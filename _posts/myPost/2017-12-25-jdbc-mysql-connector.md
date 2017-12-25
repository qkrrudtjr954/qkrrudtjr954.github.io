---
layout: post
title: "[JDBC] Java와 MySQL 연결"
categories:
  - JDBC
tags:
  - Java
  - JDBC
  - MySQL
  - Connector/J
---

Java와 MySQL을 연결하는 방법에 대해 학습합니다.

```java
public class MySqlConnection implements DBConnection{

  public static void initConnect() {
    try {
      Class.forName("com.mysql.jdbc.Driver");
      System.out.println("Driver Loading Success!!");
    } catch (ClassNotFoundException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }

  public static Connection makeConnection() {
    Connection conn = null;

    try {
      conn = DriverManager.getConnection("jdbc:mysql://localhost/test", "root", "root");
      System.out.println("Data Base is connected.");
    } catch (SQLException e) {
      e.printStackTrace();
    }

    return conn;
  }

}
```

- 프로젝트에 MySQL Driver 를 추가한다. [다운로드 링크](https://dev.mysql.com/downloads/connector/j/5.1.html)
- DriverManager 를 통해 ```localhost```에서 실행되는 MySQL과 연결할 수 있다.
