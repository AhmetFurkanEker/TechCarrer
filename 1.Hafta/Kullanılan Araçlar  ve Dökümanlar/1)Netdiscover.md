### Netdiscover nedir ? 

Yerel ağ üzerinde Ip adreslerini ve MAC adreslerini keşfetmek için kullanılan ağ keşif aracıdır. Ağı toplu taramak ve DHCP ile atanan IP adreslerini bulmada iyidir.


### Temel Kullanım 

`netdiscover [options]`

### Temel Seçenekeler 

-i <interface> : Kullanılcak ağ arayüzü belirtilir. Örnek : eth0 vs..
-r <subnet> : Belirli bir alt ağı tarma
-p Pasif modda çalışır. ARP yoluyla mevcut IP adreslerini gösterir. 


```
netdiscover -r <ip_range>
```
