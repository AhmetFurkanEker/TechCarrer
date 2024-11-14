Gobuster, bir hedefin dizin yapısını keşfetmek veya DNS çözümlemesi yapmak için kullanılan güçlü bir araçtır. Genellikle web uygulamaları için `dir` (dizin) keşfi ve DNS sunucularını test etmek için kullanılır.

### Genel komut düzeni 

```
gobuster [module] [options]
```

### **Modüller ve Parametrelerin Özeti**

| Modül     | Kullanım            | Ana Parametreler                                                                     |
| --------- | ------------------- | ------------------------------------------------------------------------------------ |
| **dir**   | Dizin keşfi         | `-u` (URL), `-w` (kelime listesi), `-t` (iş parçacığı sayısı)                        |
| **dns**   | DNS subdomain keşfi | `-d` (domain), `-w` (kelime listesi), `-s` (DNS sunucu), `-t` (paralel sorgu sayısı) |
| **vhost** | Virtual host keşfi  | `-u` (URL), `-w` (vhost listesi), `-t` (paralel istek sayısı)                        |
| **s3**    | AWS S3 bucket keşfi | `-b` (bucket adı), `-w` (bucket listesi), `-t` (iş parçacığı sayısı)                 |

#### Dizin Keşfi 

Web sunucularının dizin yapısını keşfetmek için kullanılır. 

```
gobuster dir -u http://hedefsite.com -w /path/to/wordlist.txt
```

##### Seçenekler 

1. -u : Hedef URL adresi belirtilir. 
2. -w : Kullanılacak kelime listesi belirtilir.
3. -t : Ne kadar thread ile isteklerin yapılacağı belirtilir. 
4. -s : Response status code filtrelemesini belirtmek için kullanılır. (200,301,403)
5. -x : Dosya uzantıları ekler. (.php,.html)
6. -e : URL Encode işlemi uygular.
7. -p : Proxy kullanımı için kullanılır . (-p http://127.0.0.1:8080)
8. -H : İstenilen http başlıklarını isteklere eklemek için kullanılır.
9. -d : İstekler arasındaki gecikme süresini belirtmek için kullanılır (ms cinsinden)
10. -o : Sonuçları bir dosyaya kaydetmek için kullanılır. 
#### DNS Subdomain Keşfi 

Bir hedefin alt alan adlarının tespiti için kullanılır. 


```
gobuster dns -d hedefsite.com -w /path/to/wordlist.txt
```

##### Seçenekler 

- `-d`: Hedef domain.
- `-w`: Subdomain listesi.
- `-s`: Kullanılacak DNS sunucu adresi (örneğin: `8.8.8.8`).
- `-t`: Paralel sorgu sayısı.
- `-o`: Sonuçları dosyaya kaydetmek.
- `-r`: Yalnızca bulunan subdomain'leri listeler.
- -i : Her subdomain'in karşılık geldiği IP adresini de verir. 

#### Vhost

Web sunucusunda sanal host (vhost) keşfi yapar. Hedef site üzerinde farklı subdomain'lerin çalışıp çalışmadığını kontrol eder.

```
gobuster vhost -u http://hedefsite.com -w /path/to/vhostlist.txt
```

##### Seçenekler 

- `-u`: Hedef URL.
- `-w`: Virtual host listesi.
- `-t`: Paralel istek sayısı.
- `-o`: Sonuçları dosyaya kaydetmek.

#### S3 

Amazon Web Services (AWS) üzerindeki S3 bucket'larını keşfeder. Belirtilen bucket ismiyle başlayarak public erişime açık dosyaları arar.

```
gobuster s3 -b my-bucket -w /path/to/bucketlist.txt
```

##### Seçenekler 

- `-b`: Hedef S3 bucket adı.
- `-w`: Bucket listesi.
- `-t`: Paralel istek sayısı.
- `-o`: Sonuçları dosyaya kaydetmek.

[Gobuster CheatSheet](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/)
