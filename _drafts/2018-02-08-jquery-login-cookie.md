```html
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script src="http://lab.alexcican.com/set_cookies/cookie.js" type="text/javascript" ></script>

<style type="text/css">
.center{
	margin: auto;
	width: 60%;
	border: 3px solid #ff0000;
	padding: 10px;
}
</style>

</head>
<body>

<div class="center">

	<form action="#" id="_form">
		<table border="1">
			<tr>
				<td>ID</td>
				<td>
					<input type="text" id="_id" name="id" size="20" data-msg="아이디를"/>
					<input type="checkbox" id="_check_save_id">remember this ID
				</td>
			</tr>
			<tr>
				<td>PWD</td>
				<td>
					<input type="password" id="_pwd" name="pwd" size="20" data-msg="암호를"/>
				</td>
			</tr>
			<tr>
				<td colspan="2" style="height:50px;width:100%;">
					<a href="#none" id="_btnLogin" title="Login">
						<img alt="Login img" src="login_btn.jpg">
					</a>
				</td>
			</tr>
		</table>
	</form>

</div>

<script type="text/javascript">
$('#_btnLogin').on('click', function () {
	if($('#_id').val() == ""){
		$('#_id').focus();

		alert($('#_id').attr('data-msg')+' 입력해주세요');
	}else if($('#_pwd').val()==""){
		$('#_pwd').focus();

		alert($('#_pwd').attr('data-msg')+' 입력해주세요');
	}else{
		$('#_form').attr("target", "_self").submit();
	}
});

var user_id = $.cookie("user_id");

if(user_id != null){
	$('#_id').val(user_id);
	$('#_check_save_id').attr('checked', 'checked');
}

$('#_check_save_id').on('click', function name() {
	if($('input:checkbox[id="_check_save_id"]').is(':checked')){
		alert('checked');
		if($('#_id').val()==""){
			alert('id를 입력해주세요.');
			$(this).attr('checked', false);
		}else{
			// 쿠키에 저장
			$.cookie('user_id', $('#_id').val(), {expires: 7, path: '/'});

		}
	}else{
		$.removeCookie("user_id");
	}
});
</script>
</body>
</html>
```
