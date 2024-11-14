
Hydra, şifre kırma ve zayıf parola tespiti için kullanılan güçlü bir araçtır. Özellikle çevrimiçi hizmetlerde (“ssh, telnet, ftp, http, pop3 smtp, xmpp, nntp, mysgl, cisco vb.”) kullanıcı adı ve şifre kombinasyonlarını denemek için kullanılır.

- **Temel Kullanım**:
    
    `hydra -l <kullanıcı_adı> -P <parola_listesi.txt> <hizmet>://<hedef_ip>`
    
    `hydra -l admin -P passwords.txt ssh://192.168.1.10`
    
- **Birden Fazla Kullanıcı Adı ile Deneme**:
    
    
    `hydra -L <kullanıcı_listesi.txt> -P <parola_listesi.txt> <hizmet>://<hedef_ip>`
    
    `hydra -L users.txt -P passwords.txt ftp://192.168.1.10`
    
- **Hedef Servis Belirleme**:
    
    `hydra -s <port> -l <kullanıcı_adı> -P <parola_listesi.txt> <hizmet>://<hedef_ip>`
    
    `hydra -s 2222 -l admin -P passwords.txt ssh://192.168.1.10`
    
- **Hız Ayarlama**:
    
    `hydra -t <eşzamanlı_istek_sayısı>`
    
    `hydra -l admin -P passwords.txt -t 4 ssh://192.168.1.10`
    
- **Sonuçları Kaydetme**:
    
    `hydra -l <kullanıcı_adı> -P <parola_listesi.txt> <hizmet>://<hedef_ip> -o <sonuç_dosyası.txt>`
    
    `hydra -l admin -P passwords.txt ssh://192.168.1.10 -o results.txt`
    
