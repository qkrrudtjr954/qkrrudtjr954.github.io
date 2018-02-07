---
layout: post
title: '[jstl] 기본 설명'
categories:
  - jstl
tags:
  - jstl
---



jstl은 jsp 페이지에서 java 코드를 숨기기 위해 만들어진 ***확장 태그이다.***


# jstl 이란?

- jstl은 ***Java server page Standard Tag Lisbrary*** 의 약자로 ***JSP의 표준 태그 라이브러리*** 라는 의미를 갖는다.


# jstl 의 특징


- jstl은 간결화된 태그를 사용하여, ***JSP에서의 개발의 속도를 향상 시킬 수 있다.***
- 다양한 페이지에서 jstl을 사용하여 ***코드의 재사용성*** 을 향상시킬 수 있다.
- ***scriptlet 을 사용을 최소화*** 시켜 코드의 안정성을 올릴 수 있다.



# jstl 의 종류



|Tag Name	|Description|
|:-----:|:------:|
|Core tags|	The JSTL core tag provide variable support, URL management, flow control etc. The url for the core tag is http://java.sun.com/jsp/jstl/core . The prefix of core tag is c.|
Function tags	| The functions tags provide support for string manipulation and string length. The url for the functions tags is http://java.sun.com/jsp/jstl/functions and prefix is fn.|
Formatting tags |	The Formatting tags provide support for message formatting, number and date formatting etc. The url for the Formatting tags is http://java.sun.com/jsp/jstl/fmt and prefix is fmt.|
|XML tags  |	The xml sql tags provide flow control, transformation etc. The url for the xml tags is http://java.sun.com/jsp/jstl/xml and prefix is x.|
|SQL tags	| The JSTL sql tags provide SQL support. The url for the sql tags is http://java.sun.com/jsp/jstl/sql and prefix is sql.|


- [jtl의 종류 참조](https://www.javatpoint.com/jstl)

|Tag Name	|Description|
|:-----:|:------:|
|Core tags|	JSTL core tag 는 URL 관리, 흐름 제어 등 많은 기능을 지원한다. core tag의 url은 http://java.sun.com/jsp/jstl/core 이다. prefix는 c를 사용한다.|
Function tags	| The functions tags 는 문자열을 다루고 문자열의 길이를 구하는 등 다양한 기능을 제공한다.  The functions tags의 url은 http://java.sun.com/jsp/jstl/functions 이고 prefix는 fn를 사용한다.|
Formatting tags |	The Formatting tags 메세지 포맷, 날짜 또는 숫자 포맷등 다양한 포맷 기능을 제공한다. Formatting tags 의 url은 http://java.sun.com/jsp/jstl/fmt 이고, prefix 는 fmt를 사용한다.|
|XML tags  |	The xml sql tags 흐름 제어 및 변화의 기능을 제공한다. xml tags 의 url은 http://java.sun.com/jsp/jstl/xml 이고 prefix 는 x 이다|
|SQL tags	| The JSTL sql tags 는 SQL을 지원한다. sql tags 의 url은 http://java.sun.com/jsp/jstl/sql 이고 prefix 는 sql 이다.|
