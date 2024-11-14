SQLi, web uygulamalarında veritabanı ile ilişkisini sağlamak için hazırlanmış SQL sorgularına, kullanıcı girdilerinin doğrulanmadığı durumlarda, var olmayan SQL komutları eklenerek veritabanı üzerinde işlem yapılmasıdır.

Örnek : 

```
SELECT * FROM users WHERE username = 'kullanıcı' AND password = 'parola';
```

"Username" ve "Password" bilgileri kullanıcıdan alındığını düşünelim. Eğer kullanıcı, "username" parametresine aşağıdaki gibi bir girdi gönderirse, `AND` operatörü boşa düşer ve "username" fark etmeksizin dönen SQL cevabının sıfırıncı indeksi ile işleme devam edilir.

```
' OR '1'='1
```


Ve sorgu sql motorunda aşağıda ki gibi değerlendirilir. 

```
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```


Kısaca SQLi türleri aşağıdakilerdir. 
- **Klasik (In-Band) SQL Injection**: Saldırgan, veritabanından doğrudan yanıt alır. En yaygın türleridir ve en hızlı sonuç verir.
    
- **Blind (Kör) SQL Injection**: Veritabanı hata veya yanıt döndürmez; saldırgan "doğru/yanlış" sorularla veri sızdırır. Boolean tabanlı veya zaman tabanlı olarak ayrılır.
    
- **Error-Based SQL Injection**: Veritabanı hatalarını kullanarak bilgi sızdırır. Hata mesajları, veritabanı yapısını açığa çıkarır.
    
- **Out-of-Band SQL Injection**: Veritabanı yanıtı doğrudan göndermez; e-posta veya DNS gibi alternatif kanallardan veri sızdırılır.