**Medusa**, şifre kırma ve zayıf parola tespiti için kullanılan açık kaynaklı bir araçtır. Çok sayıda protokolü destekler ve kullanıcı adı ile şifre kombinasyonlarını denemek için hızlı bir şekilde çalışır.


**Medusa**, desteklediği  protokoller :

1. **SSH** - Güvenli uzak bağlantılar.
2. **FTP** - Dosya transferi.
3. **HTTP/HTTPS** - Web sunucuları.
4. **IMAP/POP3** - E-posta sunucuları.
5. **SMTP** - E-posta gönderimi.
6. **RDP** - Uzak masaüstü bağlantısı.
7. **MySQL** - Veritabanı bağlantıları.
8. **VNC** - Uzak masaüstü kontrolü.
9. **SIP** - Sesli ve görüntülü arama oturumları.


`medusa -h <hedef_ip> -u <kullanıcı_adı> -P <parola_listesi.txt> -M <protokol> -s <port>`


`medusa -h <hedef_ip> -U <kullanıcı_adı_listesi.txt> -P <parola_listesi.txt> -M <protokol> -s <port>`