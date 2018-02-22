---
layout: category
title: jsoup
---

jsoup 은 외부에 있는 홈페이지에서 원하는 정보를 파싱하여 데이터로 만들어 주는 ***html 파싱 api*** 입니다.

jsoup을 활용하면 외부 사이트의 많은 정보를 가져와 사용할 수 있습니다.


```java
Document doc = Jsoup.connect("https://qkrrudtjr954.github.io").get();
Elements hello = doc.select("div#hello");
```



<br>
<br>

### -- Post List --
