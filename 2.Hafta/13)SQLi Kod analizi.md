
---
```
<?php

  require_once('../header.php');
  require_once('db.php');
	$sql = "SELECT * FROM users where name='";
	$sql .= $_GET["name"]."'";	
	$result = mysql_query($sql);
	if ($result) {
		?>
		<table class='table table-striped'>
      <tr><th>id</th><th>name</th><th>age</th></tr>
		<?php
		while ($row = mysql_fetch_assoc($result)) {
			echo "<tr>";
    			echo "<td>".$row['id']."</td>";
    			echo "<td>".$row['name']."</td>";
    			echo "<td>".$row['age']."</td>";
			echo "</tr>";
		}	
		echo "</table>";
	}
  require_once '../footer.php';
?>
```


Yukarıda bulunan kaynak kod içerisinde SQL sorgusuna GET ile gönderilen name parametresi hiç bir doğrulama olmaksızın direkt olarak eklenmiştir.

---

```
<?php
  require_once('../header.php');
  require_once('db.php');

	if (preg_match('/ /', $_GET["name"])) {
		die("ERROR NO SPACE");	
	}
	$sql = "SELECT * FROM users where name='";
	$sql .= $_GET["name"]."'";

	$result = mysql_query($sql);
	if ($result) {
		?>
		<table class='table table-striped'>
      <tr><th>id</th><th>name</th><th>age</th></tr>
		<?php
		while ($row = mysql_fetch_assoc($result)) {
			echo "<tr>";
    			echo "<td>".$row['id']."</td>";
    			echo "<td>".$row['name']."</td>";
    			echo "<td>".$row['age']."</td>";
			echo "</tr>";
		}	
		echo "</table>";
	}
  require '../footer.php';
?>

```

Yukarıda verilen kod örneğinde Get isteği ile alınan name parametresinde boşluk olmaması gerekmektedir. Bunu atlatmak için %09 kullanılabilir. 

---


```
<?php
    require_once('../header.php');
  require_once('db.php');
	if (preg_match('/\s+/', $_GET["name"])) {
		die("ERROR NO SPACE");	
	}
	$sql = "SELECT * FROM users where name='";
	$sql .= $_GET["name"]."'";

	$result = mysql_query($sql);
	if ($result) {
		?>
		<table class='table table-striped'>
      <tr><th>id</th><th>name</th><th>age</th></tr>
		<?php
		while ($row = mysql_fetch_assoc($result)) {
			echo "<tr>";
    			echo "<td>".$row['id']."</td>";
    			echo "<td>".$row['name']."</td>";
    			echo "<td>".$row['age']."</td>";
			echo "</tr>";
		}	
		echo "</table>";
	}
    require '../footer.php';
?>
```

Yukarıda verilen koda boşluk ve tab karakterleri bloklanmış durumdadır fakat sql yorum satırı şeklinde boşluk yerine gelebilecek olan `/**/`kullancağız. 

`'or/**/1/**/or`


---

```
<?php
  require_once('../header.php');
  require_once('db.php');
  $sql="SELECT * FROM users where id=";
	$sql.=mysql_real_escape_string($_GET["id"])." ";
	$result = mysql_query($sql);
	

	if ($result) {
		?>
		<table class='table table-striped'>
      <tr><th>id</th><th>name</th><th>age</th></tr>

		<?php
		while ($row = mysql_fetch_assoc($result)) {
			echo "<tr>";
    			echo "<td>".$row['id']."</td>";
    			echo "<td>".$row['name']."</td>";
    			echo "<td>".$row['age']."</td>";
			echo "</tr>";
		}	
		echo "</table>";
	}
    require '../footer.php';
?>
```


Yukarıda verilen kodlarda `mysql_real_escape_string()` fonksiyonu kullanılmış . SQL sorgusunda yinede kullanıcıdan alınan veri düzgün şekilde temizlenmemekte . 

`mysql_real_escape_string()` fonksiyonu, aşağıdaki karakterleri önüne ters eğik çizgi (`\`) ekleyerek etkisiz hale getirir:

- Tek tırnak (`'`)
- Çift tırnak (`"`)
- Ters eğik çizgi (`\`)
- NULL karakter (`\0`)

