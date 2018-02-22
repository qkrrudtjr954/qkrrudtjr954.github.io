---
layout: post
title: "[jsoup] cgv 영화 리스트 파싱"
categories:
  - jsoup
tags:
  - jsoup
  - parsing
  - parse
  - movie
---


<br>


jsoup을 사용하여 cgv 영화 순위에 대한 정보를 가져오는 웹페이지를 제작할 수 있습니다.

<br>

## 영화 제목, 좋아요 수 가져오기


<br>

#### 1. 영화 제목




```html
<div class="box-contents">
    <a href="/movies/detail-view/?midx=80489">
        <strong class="title">블랙 팬서</strong>
    </a>
</div>
```

- cgv 홈페이지 에서 ***영화 제목*** 에 대한 정보는 해당 태그 안에 들어있습니다.

  ​

```java
Elements titleElements = doc.select("div.box-contents strong.title");
```

- jsoup 을 사용하여 정보를 가져옵니다.


<br>


#### 2. 좋아요 수

```html
<div class="box-contents">
    <span class="like">
        <button class="btn-like" value="80489">영화 찜하기</button>
        <span class="count">
            <strong><i>23,791</i><span>명이 선택</span></strong>
            <i class="corner-RT"></i>
            <i class="corner-LT"></i>
            <i class="corner-LB"></i>
            <i class="corner-RB"></i>
            <i class="corner-arrow"></i>
        </span>
        <a class="link-reservation" href="/ticket/?MOVIE_CD=20015398&MOVIE_CD_GROUP=20015249">
            예매
        </a>
    </span>
    <div>
```

- cgv 홈페이지 에서 ***좋아요 수*** 에 대한 정보는 해당 태그 안에 들어있습니다.

  ​

```java
Elements likeElements = doc.select("div.box-contents span.like span.count strong i");
```

- jsoup 을 사용하여 정보를 가져옵니다.


<br>


#### MovieVO.java

- 영화에 대한 정보 ( 제목, 좋아요 ) 를 담는 객체

```java
public class MovieVO {
    private String title;
    private int like;

    public String getTitle() {
        return title;
    }
    public void setTitle(String title) {
        this.title = title;
    }
    public int getLike() {
        return like;
    }
    public void setLike(int like) {
        this.like = like;
    }
}

```


<br>


#### MovieManager.java

- 파싱 후 리스트를 리턴하는 클래스

```java
public class MovieManager {
    public static List<MovieVO> getCGVDate() throws IOException {
        List<MovieVO> list = new ArrayList<>();

        Document doc = Jsoup.connect("http://www.cgv.co.kr/movies").get();

        // jsoup의 elements
        Elements titleElements = doc.select("div.box-contents strong.title");

        // like count
        Elements likeElements = doc.select("div.box-contents span.like span.count strong i");

        for(int i=0; i<7; i++) {
            Element titleElement = titleElements.get(i);
            Element likeElement = likeElements.get(i);

            String title = titleElement.text();
            // comma 를 삭제한다.
            int like = Integer.parseInt(likeElement.text().replace(",", ""));

            MovieVO mv = new MovieVO();
            mv.setLike(like);
            mv.setTitle(title);

            list.add(mv);
        }

        return list;
    }
}

```


<br>



#### index.jsp



```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Movie chart</title>
        <script src="http://code.jquery.com/jquery-3.3.1.js" integrity="sha256-2Kok7MbOyxpgUVvAk/HJ2jigOSYS2auK4Pfzbm7uH60=" crossorigin="anonymous"></script>
        <script src="https://code.highcharts.com/highcharts.js"></script>
        <script src="https://code.highcharts.com/modules/exporting.js"></script>


    </head>
    <body>
        <%
        List<MovieVO> list = MovieManager.getCGVDate();

        // List to json
        String jsonLike = " [ ";

        for(MovieVO item : list){
            jsonLike += "{name: '"+item.getTitle()+"', y:"+item.getLike()+"},";
        }

        jsonLike = jsonLike.substring(0, jsonLike.lastIndexOf(","));
        jsonLike += "]";
        %>

        <c:set var="movieList" value="<%=jsonLike %>" />

        <div id="container" style="min-width: 310px; height: 400px; max-width: 600px; margin: 0 auto"></div>


        <script type="text/javascript">
            $(document).ready(function () {
                Highcharts.chart('container', {
                    chart: {
                        plotBackgroundColor: null,
                        plotBorderWidth: null,
                        plotShadow: false,
                        type: 'pie'
                    },
                    title: {
                        text: 'Movie Chart With CGV'
                    },
                    tooltip: {
                        pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
                    },
                    plotOptions: {
                        pie: {
                            allowPointSelect: true,
                            cursor: 'pointer',
                            dataLabels: {
                                enabled: true,
                                format: '<b>{point.name}</b>: {point.percentage:.1f} %',
                                style: {
                                    color: (Highcharts.theme && Highcharts.theme.contrastTextColor) || 'black'
                                }
                            }
                        }
                    },
                    series: [{
                        name: 'Movie Like',
                        colorByPoint: true,
                        data: ${movieList}
                             }]
                });
            })
        </script>
    </body>
</html>
```
