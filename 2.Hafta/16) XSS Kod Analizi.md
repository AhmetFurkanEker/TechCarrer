
```
<?php require_once '../header.php'; ?>
<html>
Hello 
<?php 
	echo $_GET["name"];
?>

<?php require_once '../footer.php'; ?>
```

Get isteğinde name parametresi direkt olarak echo ile sayfaya bastırılmakta. 

`<script>alert()</script>` payloadı ile direkt olarak xss tetiklenebilir. 

---
```
<?php require_once '../header.php'; ?>
Hello 
<?php
	 
	$name =  $_GET["name"];
	$name = preg_replace("/<script>/","", $name);
	$name = preg_replace("/<\/script>/","", $name);
echo $name;
?>
<?php require_once '../footer.php'; ?>
```

Temel savunma mekanizmalarında bahsetmiştik bu koda regex üzerinden `<script>` olup olmadığını kontrol ediyor. Bu doğru bir savunma bir şekli değildir. Yine aynı şekilde savunma mekanizmalarında `<script>` engeleniyorsa `<sCriPt>` şeklinde bir gönderim ile black list bypass edilebilir. 

---

```
<?php require_once '../header.php'; 

if (preg_match('/alert/i', $_GET["name"])) {
  die("error");
}
?>

Hello <?php  echo $_GET["name"]; ?>
<?php require_once '../footer.php'; ?>	
```

Bu kodda alert kelimesi küçük de büyük de yazılsa kullanılamaz. James Kettle "[alert() is dead, long live print()](https://portswigger.net/research/alert-is-dead-long-live-print)" yazısında bu konuyu ele alıyor fakat bakış açısı gereği alert kullanılmıyor olmak xss olmadığı anlamına gelmez farklı şeyler denenebilir. 
