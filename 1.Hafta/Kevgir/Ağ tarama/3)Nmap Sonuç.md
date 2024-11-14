
`nmap -A 10.0.2.10`


```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-21 09:31 +03
Nmap scan report for 10.0.2.10
Host is up (0.0012s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
25/tcp   open  ftp         vsftpd 3.0.2
|_smtp-commands: SMTP: EHLO 530 Please login with USER and PASS.\x0D
80/tcp   open  http        Apache httpd 2.4.7 ((Ubuntu))
|_http-title: Kevgir VM
|_http-server-header: Apache/2.4.7 (Ubuntu)
111/tcp  open  rpcbind     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/tcp6  nfs
|   100003  2,3,4       2049/udp   nfs
|   100003  2,3,4       2049/udp6  nfs
|   100005  1,2,3      41209/tcp   mountd
|   100005  1,2,3      44472/udp6  mountd
|   100005  1,2,3      52283/udp   mountd
|   100005  1,2,3      54134/tcp6  mountd
|   100021  1,3,4      41951/tcp   nlockmgr
|   100021  1,3,4      43209/udp   nlockmgr
|   100021  1,3,4      45618/udp6  nlockmgr
|   100021  1,3,4      46744/tcp6  nlockmgr
|   100024  1          44003/udp6  status
|   100024  1          44063/tcp   status
|   100024  1          59208/udp   status
|   100024  1          59259/tcp6  status
|   100227  2,3         2049/tcp   nfs_acl
|   100227  2,3         2049/tcp6  nfs_acl
|   100227  2,3         2049/udp   nfs_acl
|_  100227  2,3         2049/udp6  nfs_acl
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 4.1.6-Ubuntu (workgroup: WORKGROUP)
1322/tcp open  ssh         OpenSSH 6.6.1p1 Ubuntu 2ubuntu2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 17:32:b4:85:06:20:b6:90:5b:75:1c:6e:fe:0f:f8:e2 (DSA)
|   2048 53:49:03:32:86:0b:15:b8:a5:f1:2b:8e:75:1b:5a:06 (RSA)
|   256 3b:03:cd:29:7b:5e:9f:3b:62:79:ed:dc:82:c7:48:8a (ECDSA)
|_  256 11:99:87:52:15:c8:ae:96:64:73:d6:49:8c:d7:d7:9f (ED25519)
2049/tcp open  nfs         2-4 (RPC #100003)
8080/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Potentially risky methods: PUT DELETE
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat
8081/tcp open  http        Apache httpd 2.4.7 ((Ubuntu))
|_http-generator: Joomla! 1.5 - Open Source Content Management
| http-robots.txt: 14 disallowed entries 
| /administrator/ /cache/ /components/ /images/ 
| /includes/ /installation/ /language/ /libraries/ /media/ 
|_/modules/ /plugins/ /templates/ /tmp/ /xmlrpc/
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: Welcome to the Frontpage
9000/tcp open  http        Jetty winstone-2.9
|_http-server-header: Jetty(winstone-2.9)
| http-robots.txt: 1 disallowed entry 
|_/
|_http-title: Dashboard [Jenkins]
MAC Address: 08:00:27:06:93:DA (Oracle VirtualBox virtual NIC)
```