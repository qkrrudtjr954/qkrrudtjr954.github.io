---
layout: post
title: '[jsp] jdbc 여러 데이터 삭제하기'
categories:
  - jsp
tags:
  - jsp
  - jdbc
  - jsp&database
  - multiDelete
  - addBatch()
  - 배치
---


jdbc를 사용할때 데이터를 삭제하기 위해서 하나의 ```delete``` 쿼리를 날린다. 하지만 삭제해야하는 데이터가 여러개일 경우 데이터를 삭제하는 쿼리를 날리는 방법을 학습합니다.


# jsp 여러개의 데이터 삭제하기

- 하나의 데이터를 삭제하는 메소드를 for문으로 여러번 호출해주는 방법도 가능하다.
- 하지만, 조금 더 jdbc영역에서 해결을 하기 위한 방법을 제시한다.


```java
public boolean multiDelete(String[] ids) {
  DBConnection DBConnector = new MySqlConnector();

	String sql = " delete from member where id=?";

	Connection conn = null;
	PreparedStatement ptmt = null;
	int count[] = new int[ids.length];

	try {
		conn = DBConnector.makeConnection();
		// 삭제중 문제가 발생하지 않기 위해
		// auto commit 을 잠시 꺼둔다.
		conn.setAutoCommit(false);
		ptmt = conn.prepareStatement(sql);

		for(int i=0; i<ids.length; i++) {
			ptmt.setString(1, ids[i]);
			ptmt.addBatch();
		}

		count = ptmt.executeBatch();

		conn.commit();

	} catch (SQLException e) {
		// TODO Auto-generated catch block
		e.printStackTrace();
		// 문제 발생시 롤백한다.
		try {
			conn.rollback();
		} catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
	} finally {
		// auto commit을 다시 켜둔다.
		try {
			conn.setAutoCommit(true);
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		DBConnector.close(conn, ptmt, null);
	}

	boolean result = true;

	for(int i=0; i<count.length; i++) {
		if(count[i] != -2) {
			result = false;
			break;
		}
	}

	return result;
}
```


#### 설명1.

```java
conn.setAutoCommit(false);
```
- 삭제중 문제가 발생하지 않게 하기 위해 삭제 쿼리를 날리기 전 auto commit 을 잠시 꺼둔다.



#### 설명2.

```java
for(int i=0; i<ids.length; i++) {
  ptmt.setString(1, ids[i]);
  ptmt.addBatch();
}
```

- 쿼리를 날리는 ```ptmt```에 batch를 더한다.
  - [batch](https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B4%84_%EC%B2%98%EB%A6%AC)는 **일괄 처리** 라는 의미를 갖는다.
  - ```ptmt```를 일괄처리하기 위해 batch를 더한다.


#### 설명3.


```java
count = ptmt.executeBatch();
```

- batch를 등록한 ptmt를 일괄 실행한다.
- 리턴값으로 ```int[]```을 받아온다.
  - 리턴값 ***-2*** 는 성공은 했지만, 변경된 row의 갯수를 알수 없을때 리턴되는 값이다.
  - [.executeBatch()의 리턴값](https://stackoverflow.com/questions/19022175/executebatch-method-return-array-of-value-2-in-java)


#### 설명4.


```java
catch (SQLException e) {
  // TODO Auto-generated catch block
  e.printStackTrace();
  // 문제 발생시 롤백한다.
  try {
    conn.rollback();
  } catch (SQLException e1) {
    // TODO Auto-generated catch block
    e1.printStackTrace();
  }
}
```


- Exception 이 발생한다면 지금까지 변경된 사항을 ***rollback*** 한다.



#### 설명5.


```java
finally {
  // auto commit을 다시 켜둔다.
  try {
    conn.setAutoCommit(true);
  } catch (SQLException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
  }
  DBConnector.close(conn, ptmt, null);
}
```


- 자동 커밋 기능을 다시 켜준다.
- 열려있는 스트림들을 전부 ***close해준다.***
