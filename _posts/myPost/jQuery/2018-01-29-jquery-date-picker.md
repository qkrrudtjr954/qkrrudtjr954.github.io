---
layout: post
title: '[jQuery] datepicker'
categories:
  - jQuery
tags:
  - jQuery
  - datepicker
---

jquery-ui는 날짜를 선택할 수 있는 기능을 제공합니다.

[jquery datepicker](https://jqueryui.com/datepicker/)

## Get Started

- jquery-ui.js 파일을 추가해준다.
- jquery-latest.js 파일을 추가해준다.
- jquery-ui.css 파일을 추가해준다.



```html
<link rel="stylesheet" href="http://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css" type="text/css" />
<script src="http://code.jquery.com/jquery-latest.min.js"></script>
<script src="http://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
```

## 예제


<div class="example">
  <h1>JQuery 달력</h1>
  <h2>date Picker</h2>
  <p>
    선택일:<input type="text" id="date">
  </p>

  연도:
  <p id="myyear"></p>
  월:
  <p id="mymonth"></p>
  일:
  <p id="myday"></p>
  요일:
  <p id="mydate"></p>

  <script type="text/javascript">
  var weekday = new Array(7);
  weekday[0] =  "Sunday";
  weekday[1] = "Monday";
  weekday[2] = "Tuesday";
  weekday[3] = "Wednesday";
  weekday[4] = "Thursday";
  weekday[5] = "Friday";
  weekday[6] = "Saturday";

    $(function() {
      $("#date").datepicker(
          {
            dateFormat : "yy/mm/dd",
            dayNameMin : [ "일", "월", "화", "수", "목", "금", "토" ],
            monthName : [ "1월", "2월", "3월", "4월", "5월", "6월", "7월",
                "8월", "9월", "10월", "11월", "12월" ],
            onSelect : function(d) {
              var date = new Date(d);
              $('#myyear').html(date.getFullYear());
              $('#mymonth').html(date.getMonth()+1);
              $('#myday').html(date.getDate());
              $('#mydate').html(weekday[date.getDay()]);
            }
          });
    })
  </script>
</div>

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>jQuery Calendar</title>
<script	src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<link rel="stylesheet" href="http://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css" type="text/css" />
<script src="http://code.jquery.com/jquery-latest.min.js"></script>
<script src="http://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
</head>
<body>
	<h1>JQuery 달력</h1>
	<h2>date Picker</h2>
	<p>
		선택일:<input type="text" id="date">
	</p>

	연도:
	<p id="year"></p>
	월:
	<p id="month"></p>
	일:
	<p id="day"></p>
	요일:
	<p id="mydate"></p>

	<script type="text/javascript">
    var weekday = new Array(7);
    weekday[0] =  "Sunday";
    weekday[1] = "Monday";
    weekday[2] = "Tuesday";
    weekday[3] = "Wednesday";
    weekday[4] = "Thursday";
    weekday[5] = "Friday";
    weekday[6] = "Saturday";

		$(function() {
			$("#date").datepicker(
					{
						dateFormat : "yy/mm/dd",
						dayNameMin : [ "일", "월", "화", "수", "목", "금", "토" ],
						monthName : [ "1월", "2월", "3월", "4월", "5월", "6월", "7월",
								"8월", "9월", "10월", "11월", "12월" ],
						onSelect : function(d) {
							var date = new Date(d);
							$('#year').html(date.getFullYear());
							$('#month').html(date.getMonth()+1);
							$('#day').html(date.getDate());
              $('#mydate').html(weekday[date.getDay()]);
						}
					});
		})
	</script>
</body>
</html>
```

- ```dateFormat``` : 텍스트 필드에 데이터가 표현되는 포맷을 지정합니다.
- ```dayNameMin```, ```monthName``` 요일, 월의 표기를 정의합니다.
- ```onSelect``` 선택이 됐을때 행동을 정의할 수 있습니다.
