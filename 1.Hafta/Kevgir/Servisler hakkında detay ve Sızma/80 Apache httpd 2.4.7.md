80 Portu http web için  kullanılan portur. 10.0.2.10 adresimize tarayıcı aracılığyla gittiğimizde varsayılan olarak ağ http üzerinden gider. 

![[Kevgir 80.png]]


Web uygulamaları üzerinden, sistem hakkında bilgi edinilebilir veya varsa zafiyetler tespit edilerek sömürülebilir. Fakat şu an bizi karşılayan sayfada bir web uygulaması gözükmemekte. 
Peki ya bu sürüm ile alakalı bir zafiyet mevcut olabilir mi ? 

Metasploit ile search yaptığımızda mevcut sürüm ile alakalı bir exploit bulunmadı . 

```
[msf](Jobs:0 Agents:0) >> search httpd 2.4.7
[-] No results from sear
```

Web sitesinin farklı dizinleri hakkında bilig toplamak için FFuf , Dirb,Gobuster veya FeroxBuster kullanılabilir. 


### Feroxbuster 

```
──╼ #./feroxbuster -u http://10.0.2.10/ -s 200,403,301,302
                                                                                                                                                                                              
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.10.4
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://10.0.2.10/
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
 👌  Status Codes          │ [200, 403, 301, 302]
 💥  Timeout (secs)        │ 7
 🦡  User-Agent            │ feroxbuster/2.10.4
 🔎  Extract Links         │ true
 🏁  HTTP methods          │ [GET]
 🔃  Recursion Depth       │ 4
 🎉  New Version Available │ https://github.com/epi052/feroxbuster/releases/latest
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Management Menu™
──────────────────────────────────────────────────
403      GET       10l       30w        -c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
200      GET        6l       46w     8690c http://10.0.2.10/kevgir.png
200      GET       20l      118w     8037c http://10.0.2.10/logo.png
200      GET       10l       25w      236c http://10.0.2.10/
301      GET        9l       28w      310c http://10.0.2.10/javascript => http://10.0.2.10/javascript/
301      GET        9l       28w      310c http://10.0.2.10/phpmyadmin => http://10.0.2.10/phpmyadmin/
301      GET        9l       28w      317c http://10.0.2.10/phpmyadmin/themes => http://10.0.2.10/phpmyadmin/themes/
301      GET        9l       28w      313c http://10.0.2.10/phpmyadmin/js => http://10.0.2.10/phpmyadmin/js/
301      GET        9l       28w      317c http://10.0.2.10/javascript/jquery => http://10.0.2.10/javascript/jquery/

```


### FFuf

```
└──╼ #./ffuf -u http://10.0.2.10/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.1.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.0.2.10/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
________________________________________________

javascript              [Status: 301, Size: 310, Words: 20, Lines: 10, Duration: 29ms]
phpmyadmin              [Status: 301, Size: 310, Words: 20, Lines: 10, Duration: 36ms]

```


### Gobuster 

```
└──╼ #gobuster dir -u http://10.0.2.10 -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.0.2.10
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/javascript           (Status: 301) [Size: 310] [--> http://10.0.2.10/javascript/]
/phpmyadmin           (Status: 301) [Size: 310] [--> http://10.0.2.10/phpmyadmin/]
```



/phpmyadmin dizinini tespit ettik  
![[Kevgir phphmyadmin.png]]


Kullanıcı adı-şifre varsayılan root-toor imiş. 

![[kevgirphpmyadmin user.png]]

Elde edilen hashli passwordleri hashcat ve john the ripper araçları ile kırıyoruz 

```
hashcat -a 0 -m 0 hash.txt /usr/share/wordlists/rockyou.txt
```

```
Dictionary cache built:
* Filename..: /usr/share/wordlists/rockyou.txt
* Passwords.: 14344392
* Bytes.....: 139921507
* Keyspace..: 14344385
* Runtime...: 1 sec

21232f297a57a5a743894a0e4a801fc3:admin                    
084e0343a0486ff05530df6c705c8bb4:guest 
```

```
└──╼ #john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt  
Using default input encoding: UTF-8
Loaded 2 password hashes with no different salts (Raw-MD5 [MD5 128/128 SSE2 4x3])
Warning: no OpenMP support for this hash type, consider --fork=5
Press 'q' or Ctrl-C to abort, almost any other key for status
admin            (?)     
guest            (?)     
2g 0:00:00:00 DONE (2024-10-21 13:45) 50.00g/s 3115Kp/s 3115Kc/s 3614KC/s hartwell..gangstaboy
Use the "--show --format=Raw-MD5" options to display all of the cracked passwords reliably
Session completed.
```