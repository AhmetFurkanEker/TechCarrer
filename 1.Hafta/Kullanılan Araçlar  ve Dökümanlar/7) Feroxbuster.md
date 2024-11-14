**Feroxbuster**, web uygulamalarını taramak ve hedef URL'lerdeki gizli veya korumasız dosyaları bulmak için kullanılan açık kaynaklı bir dizin keşif aracıdır. Hızlı ve etkili bir şekilde dizinleri, dosyaları ve endpoint'leri keşfetmek için kullanılır.


### Temel Kullanım:

`feroxbuster -u <url>`
### Wordlist belirtme:

`feroxbuster -u <url> -w <kelime_listesi>`
### Threat belirtme:

`feroxbuster -u <url> -t <eşzamanlı_bağlantı_sayısı>`
### Header belirtme:

`feroxbuster -u <url> -H "User-Agent: <kullanıcı_ajanı>"`
### Çerez kullanma:

`feroxbuster -u <url> -C <çerez>`
### Yönlendirmeleri takip etme:

`feroxbuster -u <url> -r`

### HTTP  Durum Kodu Filtresi:

`feroxbuster -u <url> --filter-status <durum_kodu>`
### Ayrıntılı çıktı:

`feroxbuster -u <url> -v`

### SSL doğrulaması kullanma:

`feroxbuster -u <url> --insecure`
### Zaman aşımı ayarlama:

`feroxbuster -u <url> --timeout <zaman_aşımı_saniye>`

