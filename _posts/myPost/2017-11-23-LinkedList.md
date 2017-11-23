---
layout: post
title: "Java LinkedList 연결리스트"
categories:
  - Java
tags:
  - Java
  - LinkedList
  - 연결 리스트

---




연결리스트는 c언어에 등장함
각 객체에 다음 객체의 주소를 가르키는 필드를 갖고 있다.
배열보다 사용법이 간결하며 제약 사항이 적다.


## 리스트

리스트의 각 원소는 ***다음 원소의 주소값을 가르키는 필드*** 를 가지고 있다.
<span style ="color:green">초록색 박스</span>는 다음 객체의 주소값을 가지고 있어서 현재 원소에서 다음 원소로 접근, 이동이 가능하다.


![리스트](https://i.imgur.com/YWUCKT9.png)

```java
class Main{
	public static void main(String[] args) {
		//String 을 저장하는 LinkedList
		LinkedList<String> linkList1 = new LinkedList<String>();
		//Integer 를 저장하는 LinkedList
		LinkedList<Integer> linkList2 = new LinkedList<Integer>();
		//Double 를 저장하는 LinkedList
		LinkedList<Double> linkList3 = new LinkedList<Double>();
	}
}
```
[제네릭](generic.html)을 사용하여 리스트에 저장되는 요소를 정의할 수 있다.
이따 저장되는 요소는 반드시 클래스여야 한다. ( int, double 등 기본타입은 안됨 )


<br>
<br>



## 리스트의 추가


리스트에 원소를 추가하기 위해서는 다음 원소를 가르키는 필드에 추가하고 싶은 원소의 주소값을 넣으면 된다.


![리스트 추가](https://i.imgur.com/23BWu8k.png)


```java
class Main{
	public static void main(String[] args) {
		//String 을 저장하는 LinkedList
		LinkedList<String> linkList1 = new LinkedList<String>();
		//Integer 를 저장하는 LinkedList
		LinkedList<Integer> linkList2 = new LinkedList<Integer>();
		//Double 를 저장하는 LinkedList
		LinkedList<Double> linkList3 = new LinkedList<Double>();

		//String LinkedList
		linkList1.add("Hello");
		String str = "World";
		linkList1.add(str);
		linkList1.add(new String("!!!"));

		//Integer LinkedList
		linkList1.add(123);
		Integer i = new Integer(456);
		linkList1.add(i);
		linkList1.add(new String(789));

		//Double LinkedList
		linkList1.add(1.1);
		Double d = new Double(3.14)
		linkList1.add(d);
		linkList1.add(new String(5.3));
	}
}
```
```
현재 리스트의 상태 ( 출력 결과 아님 )

linkList1:	Hello	-> World 	-> !!!
linkList2:	123 	-> 456 		-> 789
linkList3:	1.1	-> 3.14 	-> 5.3
```



<br>
<br>


## 리스트 중간에 추가
기존 리스트의 중간에 원소를 추가하는 것도 굉장히 간편하다.
추가하려는 위치가 1번지와 2번지 사이(0번지 ~ 3번지)라고 가정했을 때,
1. 1번지가 가지고 있는 <span style="color: green;">다음 원소의 주소</span>에 추가할 원소의 주소를 넣는다.
2. 추가할 원소 내부에 <span style="color: green;">다음 원소의 주소</span> 에 2번지에 주소를 넣는다.



![리스트 중간에 추가](https://i.imgur.com/UVt4PDs.png)



```java
class Main{
	public static void main(String[] args) {
		//String 을 저장하는 LinkedList
		LinkedList<String> linkList1 = new LinkedList<String>();
		//Integer 를 저장하는 LinkedList
		LinkedList<Integer> linkList2 = new LinkedList<Integer>();
		//Double 를 저장하는 LinkedList
		LinkedList<Double> linkList3 = new LinkedList<Double>();

		//String LinkedList
		// 1번지에 삽입
		linkList1.add(1, "YEAH");

		//Integer LinkedList
		// 0번지에 삽입
		linkList2.add(0, 000);

		//Double LinkedList
		// 2번지에 삽입
		linkList3.add(2, 100.4);
	}
}
```
```
현재 리스트의 상태 ( 출력 결과 아님 )

linkList1:	Hello	-> YEAH	-> World -> !!!
linkList2:	000	-> 123 	-> 456 	-> 789
linkList3:	1.1	-> 3.14 -> 5.3	-> 100.4
```



## 리스트의 삭제
배열에서 원소를 삭제할 경우 해당 배열 값을 초기화하는 방법 뿐이다. 만약 중간값을 초기화한다면 배열의 중간은 비어있는 상태로 남게 된다.
리스트의 경우 1번지와 3번지 사이의 2번지 원소를 삭제하려고 한다면 ( 0번지 ~ 4번지 ),
+ 2번지가 가르키는 다음 원소의 주소를 1번지가 가르킨다
+ 2번지를 메모리에서 지운다.


![리스트의 삭제](https://i.imgur.com/bvM4b8w.png)



```java
class Main{
	public static void main(String[] args) {
		//String 을 저장하는 LinkedList
		LinkedList<String> linkList1 = new LinkedList<String>();
		//Integer 를 저장하는 LinkedList
		LinkedList<Integer> linkList2 = new LinkedList<Integer>();
		//Double 를 저장하는 LinkedList
		LinkedList<Double> linkList3 = new LinkedList<Double>();

		//String LinkedList
		// 1번지에 삽입
		linkList1.remove(1);

		//Integer LinkedList
		// 0번지에 삽입
		linkList2.remove(2);

		//Double LinkedList
		// 2번지에 삽입
		linkList3.remove(0);
	}
}
```
```
현재 리스트의 상태 ( 출력 결과 아님 )

linkList1:	Hello	-> World -> !!!
linkList2:	000	-> 123 	-> 789
linkList3:	3.14 -> 5.3	-> 100.4
```

해당 index에 저장되어있는 값을 제거한다.



## 리스트의 출력
리스트를 출력하기 위해서 ```for, foreach``` 같은 문법이 사용될 수 있다.
하지만 오늘 설명할 출력 방법은 ```Iterator```를 사용한 출력 방법이다. ```Iterator``` 는 ***반복자*** 라는 의미를 가지며, 리스트의 모든 원소를 순서대로 줄을 세워주는 역할을 한다.

<br>

![Iterator 구조](https://i.imgur.com/WKC4Chf.png)
개인적으로 ```List```를 ```Iterator```로 만들면 이런 구조라고 생각하고 이해하면 편하다.
<span style =" color:red">빨간 네모</span> 는 객체를 나타내고 <span style="color:blue">파란 원통</span>은 ```Iterator``` 내부를 나타낸다.
(지극히 개인적인 생각입니다. 사실은 이렇게 안생겼을겁니다...)
<br>
#### Iterator를 사용한 출력
```java
class Main{
	public static void main(String[] args) {
		LinkedList<Integer> list = new LinkedList<>();
		list.add(1);
		list.add(2);
		list.add(3);
		list.add(4);
		list.add(5);

		// 리스트를 Iterator
		Iterator<Integer> it = ls.iterator();

		// .hasNext()
		// Iterator 가 다음 요소를 갖는다면 true,
		// 다음 요소를 갖지 않는다면 false 를 반환한다.
		while(it.hasNext()){
			// .next()는 현재 Iterator 에 있는 값을 str에 넘겨주고,
			// 다음 요소를 가르킨다.
			String str = it.next();
			System.out.println(str);
		}
	}
}
```
```
1
2
3
4
5
```



## 리스트의 여러가지 함수
이 외에도 연결 리스트는 ```ArrayList``` 와 유사한 여러가지 함수를 제공한다.




#### Main.java

야구 팀을 저장하고 데이터를 관리하는 프로그램
```java
class Main{
	public static void main(String[] args) {
		LinkedList<String> list = new LinkedList<>();

		// .isEmpty()
		// 리스트가 비어있다면 true, 비어있지 않으면 false 를 반환한다.
		if(list.isEmpty()) {
			System.out.println("데이터가 없습니다.");
		}

		// .add()
		// 리스트에 원소를 추가한다.
		// 제네릭으로 String 원소를 저장하는 리스트를 만들었기 때문에,
		// 문자열을 저장한다.
		list.add("타이거즈");
		list.add("자이언츠");
		list.add("베어스");

		// 리스트 출력
		list.stream().forEach(string -> System.out.println(string));

		//interator 를 사용한 출력
		Iterator<String> it;
		it = list.iterator();
		while(it.hasNext()) {
			String str = it.next();	//리턴을 해주면서 다음 요소로 이동한다.
			System.out.println(str);
		}

		//.addFirst( element )
		// 제일 앞에 요소를 추가하는 함수
		list.addFirst("라이언즈");
		list.stream().forEach(string -> System.out.println("string: "+string));

		//.addLast( element )
		// 제일 뒤에 요소를 추가하는 함수
		list.addLast("이글스");
		list.stream().forEach(string -> System.out.println("string: "+string));
	}
}
```


<br>
<br>
<br>


## LinkedList 를 ArrayList 로 변경
```java
class Main{
	public static void main(String[] args) {
		// 아래처럼 빈 LinkedList에 ArrayList를 넣을 수 있다.
		List<String> list = new LinkedList<>();
		List<String> alist = new ArrayList<>();
		alist = list;

		// 아래처럼 생성자에 넣어서 생성하는 방법이 더 좋다
		List<String> alist2 = new ArrayList<>(list);
	}
}
```

연결 리스트와 배열 리스트는 모두 ```List```를 상속하고 있기 때문에 서로와 서로의 변환이 가능하다.
상황에 따라 ```ArrayList``` 와 ```LinkedList```를 사용할 수 있다.
