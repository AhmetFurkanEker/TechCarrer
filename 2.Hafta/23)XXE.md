XML NEDİR ? (eXtensible Markup Language)

Veri depolamak, iletmek ve taşımak için kullanılan, insan ve makine tarafından okunabilir, esnek ve genişletilebilir bir işaretleme dilidir.

XML Nerelerde Kullanılır
- Veri alışverişi
- Konfigürasyon Dosyaları
- Doküman Depolama
- Veri Tabanı İlişkileri
- Web İçeriği ve Veri Yayınlama(RSS VE ATOM)
- Grafik ve Multimedya

XML Neden Kullanılır?

- Platform Bağımsızlığı:
- İnsan ve Makine Okunabilirliği:
- Yapısal ve Hiyerarşik Veri Tanımı:
- Genişletilebilirlik
- Standartlaşma ve Uyumluluk:
- Metin Tabanlı Olması:

XXE NEDİR ?
Bir saldırganın bir uygulamanın XML verilerini işlemesine müdahale etmesine olanak tanıyan bir web güvenlik açığıdır. Bu açık, genellikle bir saldırganın uygulama sunucusunun dosya sistemindeki dosyaları görüntülemesine ve uygulamanın erişebildiği arka uç veya harici sistemlerle etkileşime girmesine izin verir.

XXE Nasıl Ortaya Çıktı ?

XML spesifikasyonunun çeşitli potansiyel olarak tehlikeli özellikler içermesi ve standart ayrıştırıcıların bu özellikleri desteklemesi nedeniyle ortaya çıkar.

Yetenekleri Neler ?

1. External Entites : XML, harici dosyalara veya URL'leri dahil etmeye izin veriyor. 
2. PArameter Entites : DTD(Docuemnt Type Definition) içinde tanımlanan parametreler de dış dosyalara referans verebiliyor, bu da saldırganlara kapı aralıyor. 
3. XML Inclusion : Başka bir XML belgesini mevcut belgenin içine ekleme imkanı veriyor.

DTD Nedir ?

Bir XML belgesinin yapısını, içerebileceği veri değerlerinin türlerini ve diğer öğeleri tanımlayabilecek bildirimleri içerir.XML belgesindeki belirli metin parçalarını yeniden kullanmak veya dinamik içerik sağlamak için kullanılır.


```
<!DOCTYPE foo [ <!ENTITY pentest "Selam"> ]>
<foo>

	<bar>

			&pentest;

	</bar>

</foo>
```


```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE note SYSTEM "Note.dtd">

<note>

<to>Tove</to>

<from>Jani</from>

<heading>Reminder</heading>

<body>Don't forget me this weekend!</body>

</note>
```

```
<!DOCTYPE note

[

<!ELEMENT note (to,from,heading,body)>

<!ELEMENT to (#PCDATA)>

<!ELEMENT from (#PCDATA)>

<!ELEMENT heading (#PCDATA)>

<!ELEMENT body (#PCDATA)>

]>
```

DTD'den dışarıda bulunduğu özel varlık türleridir. Dış varlıklar, genellikle SYSTEM anahtar kelimesi kullanılarak ve bir URL belirtilerek tanımlanır. URL, varlığın değerinin yükleneceği yerdir.

```
<!DOCTYPE foo [ <!ENTITY pentest SYSTEM "http://örnek.com"> ]>
<!DOCTYPE foo [ <!ENTITY pentest SYSTEM "file:///etc/passwd"> ]>
```