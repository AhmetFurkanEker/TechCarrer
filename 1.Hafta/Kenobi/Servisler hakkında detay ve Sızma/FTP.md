[[Kenobi/Ağ Tarama/Nmap]] taramasında 21. porta ftp servisinin çalışıtğını tespit etmiştik. FTP servisinde   ProFTPD 1.3.5 çalışmaktadır. 


```
└──╼ #searchsploit ProFTPD 1.3.5
------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
 Exploit Title                                                                                                                                              |  Path
------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
ProFTPd 1.3.5 - 'mod_copy' Command Execution (Metasploit)                                                                                                   | linux/remote/37262.rb
ProFTPd 1.3.5 - 'mod_copy' Remote Command Execution                                                                                                         | linux/remote/36803.py
ProFTPd 1.3.5 - 'mod_copy' Remote Command Execution (2)                                                                                                     | linux/remote/49908.py
ProFTPd 1.3.5 - File Copy                                                                                                                                   | linux/remote/36742.txt
------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
Shellcodes: No Results
```

Mevcut sürüm ile alakalı 3 farklı exploiti getirdi . 

1. [ProFTPd 1.3.5 - 'mod_copy' Remote Command Execution (2)](https://www.exploit-db.com/exploits/49908)
2. [ProFTPd 1.3.5 - 'mod_copy' Command Execution (Metasploit)](https://www.exploit-db.com/exploits/37262)
3. [ProFTPd 1.3.5 - 'mod_copy' Remote Command Execution](https://www.exploit-db.com/exploits/36803)
4. [https://www.exploit-db.com/exploits/36742](# ProFTPd 1.3.5 - File Copy)


>Bu modül, ProFTPD 1.3.5'teki SITE CPFR/CPTO komutlarını istismar ederek, kimlik doğrulaması olmayan istemcilerin dosyaları sistemin her yerinden kopyalamasını sağlar. Kopyalama işlemleri 'nobody' kullanıcısının haklarıyla yapıldığından, bir PHP yükü web dizinine kopyalanarak uzaktan kod yürütme (RCE) sağlanabilir.


 **Exploitler test edilecek.**


![[kenobi_proftp.png]]


Zafiyetlerden yararlanarak id_rsa dosyasını dizine kopyaladık. Bu dosyanın yolunu [[Samba smbclient]] ile log.txt dosyasından ulaştık .

![[smclient_log.txt.png]]

id_rsa dosyamızı bizim ile paylaşılan /var/tmp klasörüne kopyalamış olduk. 