---
layout: category
title: Spring
---

## Spring Framework

```java
@RequestMapping(value = "/spring", method = RequestMethod.GET)
public String home(Locale locale, Model model) {
  logger.info("안녕하세요 Spring Framework 입니다. {}", locale);

  Date date = new Date();
  DateFormat dateFormat = DateFormat.getDateTimeInstance(DateFormat.LONG, DateFormat.LONG, locale);

  String formattedDate = dateFormat.format(date);

  model.addAttribute("serverTime", formattedDate );

  return "spring";
}
```

Spring Framework의 대한 지식을 기술합니다.


<br>
<br>

### -- Post List --
