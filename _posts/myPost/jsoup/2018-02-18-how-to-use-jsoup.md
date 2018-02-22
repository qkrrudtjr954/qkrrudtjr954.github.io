---
layout: post
title: "[jsoup] jsoup을 사용한 html 파싱"
categories:
  - jsoup
tags:
  - jsoup
  - parsing
  - parse
---



# jsoup을 활용한 외부 html태그 파싱하기



jsoup은 url을 통해 외부 html 소스에서 원하는 요소를 파싱할 수 있는 api 입니다.

jsoup을 사용하면 외부 사이트에서 원하는 정보 ( 영화 순위, 영화 예매율 등등 )를 가져와 자신의 웹페이지에 뿌려줄 수 있습니다.









- jsoup은 html 문서를 파싱할 수 있는 api이다.
- html을 읽어 특정 처리를 할 수 있다.
- 빅데티터를 처리하는데 많이 사용된다.








## Get Started

jsoup을 사용하기 위해서는 jsoup 라이브러리 (.jar파일) 를 추가해야한다.

- [jar 파일 다운로드](https://jsoup.org/download)
- 프로젝트 lib에 다운받은 .jar 파일을 추가한다.

<img src="https://i.imgur.com/c3zuxkK.png" width="500px" height="250px"/>





## How To Use

jsoup의 사용 순서는 다음과 같다.

1. ***웹 페이지의 소스를 전부 가져온다***
2. ***원하는 요소의 속성 및 태그를 확인한다.***
3. ***셀렉터를 사용하여 값을 가져온다***
4. ***끝!***



#### 1. 웹페이지의 소스를 전부 가져온다.

```java
Document doc = Jsoup.connect("http://www.cgv.co.kr/movies/?ft=0").get();
```

- Jsoup 객체를 통해 파싱하고 싶은 웹페이지와 연결한다.
- ```.get()``` 함수를 사용하여 html 코드를 전부 가져와 ```Document``` 타입으로 만든다.




#### 2. 원하는 요소의 속성 및 태그를 확인한다.

- cgv 홈페이지에 있는 영화 정보를 갖고 오고 싶다.



#### 3. 셀렉터를 사용하여 값을 가져온다.


```java
Elements title = doc.select("div.dox-contents strong.title");
```

- jsoup은 ```Element``` 객체를 선택(```select```)하기 위해 ***css selector*** 문법을 활용한다.
- 해당 html 소스에서 ***css selector*** 문법을 사용하여 원하는 ***element*** 를 가져온다.



#### 4. 끝!

```java
List<MovieDto> list = new ArrayList<>();

for(int i=0; i<7; i++) {
    Element titleElement = titleElements.get(i);
    Element likeElement = likeElements.get(i);

    String title = titleElement.text();
    // comma 를 삭제한다.
    int like = Integer.parseInt(likeElement.text().replace(",", ""));

    MovieDto mv = new MovieDto();
    mv.setLike(like);
    mv.setTitle(title);

    list.add(mv);
}
```

- 파싱하여 가져온 값을 잘 정제하여 ```list``` 로 리턴하면 JSP, Html 등 프론트 단에서 사용이 가능하다.
