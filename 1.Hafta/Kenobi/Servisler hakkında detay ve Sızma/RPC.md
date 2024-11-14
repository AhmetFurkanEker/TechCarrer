
[[Kenobi/Ağ Tarama/Nmap]] taramasına 111. porta RPC çalıştığını tespit etmiştik . RPC, bir bilgisayarın başka bir bilgisayardaki bir programın işlevini çağırmasına yarayan bir yöntemdir. Yani, bir program, başka bir bilgisayardaki programı kullanmak istediğinde, RPC sayesinde bu çağrıyı yapabilir. Örneğin, bilgisayarındaki bir uygulama, bir sunucudaki veri tabanına erişmek istiyorsa, RPC ile bu sunucudaki programdan bir işlev (örneğin, bir veri almak) isteyebilir. Sunucu, bu isteği alır, işlemi yapar ve sonucu tekrar senin bilgisayarına gönderir. Böylece, farklı bilgisayarlar arasında iletişim kurulur ve bir program, başka bir programın özelliklerini kullanabilir. Kısacası, RPC, uzak bilgisayarlarla iletişim kurmayı kolaylaştırır.

```
└──╼ #nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.30.127
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-22 16:19 +03
Nmap scan report for 10.10.30.127
Host is up (0.073s latency).

PORT    STATE SERVICE
111/tcp open  rpcbind
| nfs-showmount: 
|_  /var *
| nfs-ls: Volume /var
|   access: Read Lookup NoModify NoExtend NoDelete NoExecute
| PERMISSION  UID  GID  SIZE  TIME                 FILENAME
| rwxr-xr-x   0    0    4096  2019-09-04T08:53:24  .
| rwxr-xr-x   0    0    4096  2019-09-04T12:27:33  ..
| rwxr-xr-x   0    0    4096  2024-10-22T11:25:01  backups
| rwxr-xr-x   0    0    4096  2019-09-04T10:37:44  cache
| rwxrwxrwx   0    0    4096  2019-09-04T08:43:56  crash
| rwxrwsr-x   0    50   4096  2016-04-12T20:14:23  local
| rwxrwxrwx   0    0    9     2019-09-04T08:41:33  lock
| rwxrwxr-x   0    108  4096  2019-09-04T10:37:44  log
| rwxr-xr-x   0    0    4096  2019-01-29T23:27:41  snap
| rwxr-xr-x   0    0    4096  2019-09-04T08:53:24  www
|_
| nfs-statfs: 
|   Filesystem  1K-blocks  Used       Available  Use%  Maxfilesize  Maxlink
|_  /var        9204224.0  1837640.0  6875988.0  22%   16.0T        32000

Nmap done: 1 IP address (1 host up) scanned in 8.11 seconds
```

Tarama sonucuna baktığımızda /var klasörü mount edilmiş.


>Dizinin (directory) mount edilmesi, bir klasörü başka bir yerden gelen dosya ve klasörlere bağlamak anlamına gelir. Örneğin, bilgisayarında "Belgeler" adında bir klasörün olduğunu düşün; bu klasörüne bir arkadaşın harici diskindeki "Resimler" klasörünü bağladığında, "Belgeler" klasörüne girdiğinde artık harici diskteki resimleri de görebilirsin. Bu işlem sayesinde, farklı yerlerde bulunan dosyaları tek bir yerde toplamak ve kullanmak daha kolay hale gelir; böylece dosyaları bulmak ve erişmek için fazla uğraşmak zorunda kalınmaz.