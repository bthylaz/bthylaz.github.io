---
title: php实现留言板功能
date: 2020-03-03 17:06:15
cover: ../img/c7.jpg
tags:
---
03html
```
<!DOCTYPE html>
<html>
<head>
	<title>新建网页</title>
	<meta charset="utf-8">
</head>
<body>
<form action="04.php"method="post">
		<p>留言标题：<input type="text" name="title"></p>
		<p>留言内容：<textarea name="content" id=""cols="30"rows="10"></textarea></p>
		<p><input type="submit" value="提交"></p>
	</form>
</body>
</html>

```
04.php
```php
<?php 

// print_r($_POST);

//php打开文件
// $fh = fopen('./msg.txt','a');//打开文件

// //往文件写东西，
// fwrite($fh,'from php into txt');

// fclose($fh);
// echo 'ok';
//开始留言
$str = $_POST['title'].",".$_POST['content']."\n";

$fh = fopen('./msg.txt','a');

fwrite($fh,$str);
fclose($fh);

echo 'ok';

 ?>
```
msg.php
```php
<?php 

// $tid = $_GET['tid'];

// echo '你想看第' ,$tid,'行留言';

// $tid = $_GET['tid'];

// echo '你想看第' ,$tid,'行留言';



// 全打印

// $fh = fopen('./msg.txt','r');

// while(($row=fgetcsv($fh)) != false){
// 		print_r($row);
// 	}



$fh = fopen('./msg.txt','r');

$i=1;

while(($row=fgetcsv($fh)) != false){

	echo '<li><a href="readmsg.php?tid=',$i ,'">',$row[0],'</li>';

    $i = $i + 1;
}

?>
```
创建msg.txt，存储内容



readmsg.php
```php
<?php 

$tid = $_GET['tid'];

// echo '你想看第' ,$tid,'行留言';

//打开得到的文件
$fh = fopen('./msg.txt','r');

$i=1;

while(($row=fgetcsv($fh)) != false){
	if($i == $tid){
		echo '<h1>',$row[0],'</h1>';
 		echo '<p>',$row[1],'</p>';
 	}
 	
   $i = $i + 1;
}

?>

<a href="msg.php">首页</a>
<a href="03.html">留言</a>
```
