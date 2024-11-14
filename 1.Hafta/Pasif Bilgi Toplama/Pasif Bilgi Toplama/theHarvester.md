**theHarvester**, bir siber güvenlik aracıdır ve özellikle **açık kaynak istihbaratı (OSINT)** toplamak için kullanılır. Web siteleri, şirketler veya domainler hakkında e-posta adresleri, alt alan adları, IP adresleri ve URL gibi bilgileri toplar. Bu araç, genellikle sızma testleri (penetration testing) ve bilgi toplama aşamalarında kullanılır.

1. Temel Bilgi Toplama 
```
   theHarvester -d [domain] -b [source]/all
```

>**theHarvester** tarafından desteklenen kaynaklar arasında **Bing**, **DuckDuckGo**, **DNS Dumpster**, **LinkedIn**, **Shodan**, ve **Virustotal** gibi bilgi toplama platformları yer alır.

## Opsiyonel Parametreler

### -l (Limit Belirleme)

```
theharvester -d hedefsite.com -b bing -l 100
```

Bu komut, Bing arama sonuçlarını 100 ile sınırlar.
### -n (IP Adresi Çözümleme)

```
theharvester -d hedefsite.com -b bing -n

```
Hedef domainin IP adreslerini çözer ve sonuçları toplar.

### -e (Belirli DNS Sunucusunu Kullanma)

```
theharvester -d hedefsite.com -b bing -e 8.8.8.8
```

Bu komut, belirli bir DNS sunucusunu (örneğin Google DNS: `8.8.8.8`) kullanarak arama yapar.

### -S (Sonuçların Başlangıç Noktasını Belirleme)

```
theharvester -d hedefsite.com -b bing -S 50
```

Arama sonuçlarının 50. sıradan başlamasını sağlar (örneğin Bing'den gelen sonuçlar için).

### -f (Sonuçları Dosyaya Kaydetme)

```
theharvester -d hedefsite.com -b bing -f sonuc.html
```

Toplanan bilgileri belirli bir dosyaya (`sonuc.html`) kaydeder.

### --screenshot (Screenshot Alma)


```
theharvester -d hedefsite.com -b bing --screenshot /dosya_yolu/
```

Hedef domainin ekran görüntülerini belirttiğin dizine kaydeder (Shodan gibi kaynaklarla kullanılabilir).