## KEŞİF

### Nmap Nedir?

Bir ağda cihazları veya hizmetleri keşfetmek için kullanılan bir ağ tarama aracıdır. Nmap kullanarak ağ haritalandırma, port tarama, hizmet tanımlama, sürüm tespiti, işletim sistemi (OS) tespiti ve NSE kullanarak zafiyet tespiti gibi birçok işlem gerçekleştirilebilir.

Kevgir makinemizin ağda kullandığı IP adresinin tespiti için şu komut kullanılabilir:

`nmap 10.0.2.0/24`

>"/24" ifadesi, 10.0.2.0 ile 10.0.2.255 arasında 256 IP adresini kapsar. Bu sayede bu aralıktaki tüm IP adresleri taranmış olur.

Yapılan taramanın sonucunda ulaşılan çıktı da kevgir makinemizin ıp adresine ulaşmış olduk.

```
Nmap scan report for 10.0.2.10
Host is up (0.00050s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE SERVICE
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1322/tcp open  novation
2049/tcp open  nfs
8080/tcp open  http-proxy
8081/tcp open  blackice-icecap
9000/tcp open  cslistener
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
```



### Temel NMap Komutları 

**Temel Tarama**:
   
`nmap [IP_adresi]`
    
**Port Tarama** (Belirli bir port):

`nmap -p [port_numarası] [IP_adresi]`

```
└──╼ #nmap -p 80 10.0.2.10
Nmap scan report for 10.0.2.10
Host is up (0.0017s latency).

PORT   STATE SERVICE
80/tcp open  http
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtua
```

    
**Port Aralığı Tarama**:
    
`nmap -p [port_aralığı] [IP_adresi]`
    
```
└──╼ #nmap -p 80-300 10.0.2.10
PORT    STATE SERVICE
80/tcp  open  http
111/tcp open  rpcbind
139/tcp open  netbios-ssn
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC
```

    
**Tüm TCP Portlarını Tarama**:
    
`nmap -p- [IP_adresi]`

```
└──╼ #nmap -p- 10.0.2.10
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-20 18:37 +03
Nmap scan report for 10.0.2.10
Host is up (0.00031s latency).
Not shown: 65517 closed tcp ports (reset)
PORT      STATE SERVICE
25/tcp    open  smtp
80/tcp    open  http
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
1322/tcp  open  novation
2049/tcp  open  nfs
6379/tcp  open  redis
8080/tcp  open  http-proxy
8081/tcp  open  blackice-icecap
9000/tcp  open  cslistener
35928/tcp open  unknown
36398/tcp open  unknown
41315/tcp open  unknown
44226/tcp open  unknown
47506/tcp open  unknown
49539/tcp open  unknown
59423/tcp open  unknown
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC
```

    
 **SYN Tarama (Gizli Tarama)**:
    
`nmap -sS [IP_adresi]`

```
└──╼ #nmap -sS 10.0.2.10
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-20 18:36 +03
Nmap scan report for 10.0.2.10
Host is up (0.0011s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE SERVICE
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1322/tcp open  novation
2049/tcp open  nfs
8080/tcp open  http-proxy
8081/tcp open  blackice-icecap
9000/tcp open  cslistener
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
```
    
**UDP Tarama**:
    
`nmap -sU [IP_adresi]`
    
**Versiyon Tespiti**:
    
`nmap -sV [IP_adresi]`

```
└──╼ #nmap -sV 10.0.2.10
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-20 18:52 +03
Nmap scan report for 10.0.2.10
Host is up (0.00034s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
25/tcp   open  ftp         vsftpd 3.0.2
80/tcp   open  http        Apache httpd 2.4.7 ((Ubuntu))
111/tcp  open  rpcbind     2-4 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
1322/tcp open  ssh         OpenSSH 6.6.1p1 Ubuntu 2ubuntu2 (Ubuntu Linux; protocol 2.0)
2049/tcp open  nfs         2-4 (RPC #100003)
8080/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
8081/tcp open  http        Apache httpd 2.4.7 ((Ubuntu))
9000/tcp open  http        Jetty winstone-2.9
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
Service Info: Host: CANYOUPWNME; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kern
```

    
**OS  Tespiti**:
    
  `nmap -O [IP_adresi]`

```
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
```

 **Null Taraması (Host Keşfi)**:

`nmap -sN [IP_aralığı]`

```
└──╼ #nmap -sN 10.0.2.10
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-20 18:55 +03
Nmap scan report for 10.0.2.10
Host is up (0.00086s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE         SERVICE
25/tcp   open|filtered smtp
80/tcp   open|filtered http
111/tcp  open|filtered rpcbind
139/tcp  open|filtered netbios-ssn
445/tcp  open|filtered microsoft-ds
1322/tcp open|filtered novation
2049/tcp open|filtered nfs
8080/tcp open|filtered http-proxy
8081/tcp open|filtered blackice-icecap
9000/tcp open|filtered cslistener
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
```
**Çıktıyı Dosyaya Kaydetme**:
    
`nmap -oN [dosya_adı.txt] [IP_adresi]`

`nmap  [IP_adresi] > output.txt`


**Ping taraması**

```
nmap -Pn [ip]
```


**Hız Ayarlamaları**

```
nmap -T1/5
```

-T parametresi 1 ile 5 arasında değer alır . Değer büyüdükçe hız artar .

**Zafiyet Taraması**

```
nmap --script vuln <ip_adresi>
```

