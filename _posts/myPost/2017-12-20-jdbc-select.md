---
layout: post
title: "[JDBC] JDBC의 SELECT"
categories:
  - JDBC
tags:
  - Java
  - JDBC
  - SELECT
  - JDBC 선택
---

java 코드와 Database를 연결하고 조건에 일치하는 값을 데이터 베이스에서 불러오는 방법을 학습합니다.



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


## UserDto.java

- 하나의 ```User``` 정보를 저장하는 ```Dto``` (Data Tranfer Object)


```java
public class UserDto {
  String id;
  String name;
  int age;
  String date;

  public UserDto() {
  	// TODO Auto-generated constructor stub
  }
  public UserDto(String id, String name, int age, String date) {
    super();
    this.id = id;
    this.name = name;
    this.age = age;
    this.date = date;
  }
  public String getId() {
    return id;
  }
  public void setId(String id) {
    this.id = id;
  }
  public String getName() {
    return name;
  }
  public void setName(String name) {
    this.name = name;
  }
  public int getAge() {
    return age;
  }
  public void setAge(int age) {
    this.age = age;
  }
  public String getDate() {
    return date;
  }
  public void setDate(String date) {
    this.date = date;
  }
  @Override
  public String toString() {
    return "UserDto [id=" + id + ", name=" + name + ", age=" + age + ", date=" + date + "]";
  }
}
```


## SelectTest.java

- ```.search()```
  - 선택한 하나의 객체값( ```UserDto``` )을 가져오는 메소드
- ```.getUsers()```
  - 데이터 베이스에 저장된 모든 ```UserDto``` 를 가져오는 메소드

```java
public class SelectTest {

  // 하나의 데이터
  public UserDto search(String id) {

    String sql = " select id, name, age, joindate "
      + " from userdto "
      + " where id='" + id + "' ";

    Connection conn = DBConnection.makeConnection();
    PreparedStatement pstmt = null;
    ResultSet rs = null;
    UserDto dto = null;

    System.out.println("sql : "+sql);

    try {
      pstmt = conn.prepareStatement(sql);
      rs = pstmt.executeQuery(sql);	// query 를 실행하라 그리고 그 값을 rs에 저장해라.

      if(rs.next()) {
        dto = new UserDto();
        dto.setId(rs.getString("id"));
        dto.setName(rs.getString("name"));
        dto.setAge(rs.getInt("age"));
        dto.setDate("joindate");
      }
    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } finally {
      DBClose.close(pstmt, conn, rs);
    }
    return dto;
  }

  public List<UserDto> getUsers(){
    String sql = " select id, name, age, joindate from userdto ";

    Connection conn = DBConnection.makeConnection();
    PreparedStatement pstmt = null;
    ResultSet rs = null;

    List<UserDto> list = new ArrayList<UserDto>();

    System.out.println("sql : "+sql);

    try {
      pstmt = conn.prepareStatement(sql);
      rs = pstmt.executeQuery(sql);	// query 를 실행하라 그리고 그 값을 rs에 저장해라.


      while(rs.next()) {
        String id = rs.getString("id");
        String name = rs.getString("name");
        int age = rs.getInt("age");
        String joindate = rs.getString("joindate");

        UserDto dto = new UserDto(id, name, age, joindate);
        list.add(dto);
      }

    } catch (SQLException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } finally {
      DBClose.close(pstmt, conn, rs);
    }
    return list;
  }
}
```



## Main.java

```java
public class mainClass {
  public static void main(String[] args) {
    SelectTest st = new SelectTest();

    // Database에서 Id가 일치하는 유저를 가져온다.
    UserDto user = st.search("Your Id");

    // Database에 저장된 모든 유저를 가져온다.
    List<UserDto> users = st.getUsers();
  }
}

```
