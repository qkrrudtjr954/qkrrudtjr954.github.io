---
layout: post
title: '[jsp] jdbc로 데이터 베이스 연결하기'
categories:
  - jsp
tags:
  - jsp
  - jdbc
  - jsp&database
---


jsp는 자바를 사용하여 웹페이지를 제작할 수 있는 기술이다. ***따라서 데이터 베이스와의 연결에서 jdbc를 사용할 수 있다.***



# 데이터 베이스 접속


- 오라클 기본 데이터 베이스의 모든 테이블과 데이터를 가져온다.
- 데이터 베이스의 모든 테이블과 정보를 읽어온다.



#### index.jsp

```jsp
<%@page import="java.sql.ResultSetMetaData"%>
<%@page import="java.sql.ResultSet"%>
<%@page import="java.sql.PreparedStatement"%>
<%@page import="java.sql.Connection"%>
<%@page import="java.sql.DriverManager"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
  pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Insert title here</title>
  </head>
  <body>

    <h1>HR Tab</h1>

    <pre>
	select * from tab
	- Show all table in database
	</pre>

    <%!
  public boolean has$(String msg){
  // $가 포함된 데이터 베이스는 제거한다.
  return msg.contains("$");
}
    %>

    <%

    Class.forName("oracle.jdbc.driver.OracleDriver");

    String url = "jdbc:oracle:thin:@localhost:1521:xe";
    String user = "hr";
    String pwd = "hr";


    String sql = "select * from tab";

    Connection conn = DriverManager.getConnection(url, user, pwd);
    PreparedStatement ptmt = null;
    ResultSet rs = null;

    ptmt = conn.prepareStatement(sql);
    rs = ptmt.executeQuery();
    ResultSetMetaData rsmd = rs.getMetaData();	// column 정보

    int count = rsmd.getColumnCount();
    %>


    <table border="1">
      <tr>
        <%
        for(int i=1; i<count+1; i++){
          %>
        <td><%=rsmd.getColumnName(i) %>
          <%
          }
          %>

          <%
          while(rs.next()){
            %>
          <tr>
            <%
            for(int i=1; i<count+1; i++){
              String cols = rs.getString(i);
              if(i == 1 && !has$(cols)){
                %>
            <td>
              <a href="table.jsp?tname=<%=cols%>"><%=cols %></a>
            </td>
            <%
            }else{
              %>
            <td><%=cols %></td>
            <%
            }
            }
            %>
          </tr>
          <%
          }
          %>
    </table>

      <%
      if(rs != null) rs.close();
      if(ptmt != null) rs.close();
      if(conn != null) rs.close();
      %>
      </body>
    </html>
```



#### table.jsp

```jsp
<%@page import="java.sql.ResultSetMetaData"%>
<%@page import="java.sql.ResultSet"%>
<%@page import="java.sql.PreparedStatement"%>
<%@page import="java.sql.DriverManager"%>
<%@page import="java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
  pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Insert title here</title>
  </head>
  <body>
    <%

    Class.forName("oracle.jdbc.driver.OracleDriver");

    String url = "jdbc:oracle:thin:@localhost:1521:xe";
    String user = "hr";
    String pwd = "hr";

    Connection conn = DriverManager.getConnection(url, user, pwd);

    String tname = request.getParameter("tname");
    tname = (tname==null || tname.equals("")) ? "TAB":tname.toUpperCase();

    String sql = "select * from "+tname;
    PreparedStatement ptmt = null;
    ResultSet rs = null;

    ptmt = conn.prepareStatement(sql);
    rs = ptmt.executeQuery();
    ResultSetMetaData rsmd = rs.getMetaData();	// column 정보

    int count = rsmd.getColumnCount();
    %>

    <table border="1">
      <tr>
        <%
        for(int i=1; i<count+1; i++){
          %>
        <td><%=rsmd.getColumnName(i) %></td>
        <%
        }
        %>
      </tr>

      <%
      while(rs.next()){
        %>
      <tr>
        <%
        for(int i=1; i<count+1; i++){
          %>
        <td><%=rs.getString(i) %></td>
        <%
        }
        %>
      </tr>
      <%
      }
      %>
    </table>

    <%
    if(rs != null) rs.close();
    if(ptmt != null) rs.close();
    if(conn != null) rs.close();
    %>

  </body>
</html>
```
