
Chunked encoding, HTTP protokolünde dinamik içeriklerin veya büyük veri boyutlarının parçalara bölünerek ve her bir parça (chunk) olarak iletilmesini sağlayan bir tekniktir. Bu yöntem, içeriğin boyutunun önceden bilinmediği veya içerik değişken olduğu durumlarda kullanılır. Özellikle, içerik verisinin tamamı bir anda hazır olmadığında veya çok büyük olduğunda veri iletiminin devam etmesini sağlar.

### Nasıl çalışır?

1. **Veri Parçalara Ayrılır**: Veri, belirli boyutlarda parçalara bölünür. Bu parçalara "chunk" denir. Her bir chunk, boyutu ile birlikte gönderilir.
    
2. **Boyut Bilgisi**: Her bir chunk, önceden belirlenmiş bir boyutla gönderilir ve bu boyut hexadecimal (16'lık) olarak belirtilir. Boyutun kendisi de bir chunk olduğu için her parça, boyut bilgisini içerir.
    
3. **Veri Gönderimi**: Her bir chunk, boyutuyla birlikte, sırasıyla gönderilir. Son chunk, boyut değeri "0" (sıfır) olarak gönderildiğinde, içerik bitmiş olarak kabul edilir.
    
4. **Sonlandırma**: Son chunk'tan sonra, veri aktarımı sona erer. "0" uzunluğunda bir chunk ve ardından iki adet `\r\n` ile sonlanır.
    

### Chunked Encoding Yanıtı Örneği

Aşağıda, bir HTTP yanıtının chunked encoding ile gönderilmesini gösteren bir örnek verilmiştir:


```
HTTP/1.1 200 OK\r\n Transfer-Encoding: chunked\r\n \r\n 7\r\n Mozilla\r\n 9\r\n Developer\r\n 4\r\n Network\r\n 0\r\n \r\n
```
#### Açıklama:

- **HTTP/1.1 200 OK**: Bu, başarılı bir yanıtı belirtir.
- **Transfer-Encoding: chunked**: Yanıtın chunked encoding yöntemiyle gönderildiğini belirtir.
- **7\r\n**: İlk chunk'ın uzunluğu 7 byte (hexadecimal değer). Bu, "Mozilla" verisini gösterir.
- **Mozilla\r\n**: İlk chunk'ın içeriği.
- **9\r\n**: İkinci chunk'ın uzunluğu 9 byte (hexadecimal değer). Bu, "Developer" verisini gösterir.
- **Developer\r\n**: İkinci chunk'ın içeriği.
- **4\r\n**: Üçüncü chunk'ın uzunluğu 4 byte (hexadecimal değer). Bu, "Network" verisini gösterir.
- **Network\r\n**: Üçüncü chunk'ın içeriği.
- **0\r\n**: Bu, verinin sonlandığını belirtir ve chunked encoding yönteminin sona erdiğini gösterir.

### Chunked Encoding Özellikleri

- **Dinamik İçerik**: Sunucu, içerik üretimi bitmeden veriyi istemciye gönderebilir. Yani, içerik tamamlandıkça, istemci her yeni chunk'ı alır.
- **Veri Büyüklüğü Bilinmediğinde Kullanılır**: İçeriğin boyutu önceden belirlenemediği için, sunucu içerik üretmeye devam ederken istemciye veri iletmeye başlayabilir.
- **İstemci ve Sunucu Performansı**: Bu yöntem, özellikle sürekli veri iletimi veya uzun süren veri işlemleri için kullanışlıdır.

### Kullanım Alanları

- **Stream edilen veri**: Video, ses, canlı yayın gibi içerikler için idealdir.
- **Dinamik içerikler**: İçeriğin boyutu veya uzunluğu değişken olan veri (örneğin, büyük dosya yüklemeleri veya kullanıcı tarafından oluşturulan içerikler).
- **Büyük veri iletimi**: İçeriğin tamamı gönderilmeden önce verilerin taşınması gerekirse.

Chunked encoding, HTTP protokolünün bir parçası olduğu için istemci ve sunucu arasındaki veri iletiminin daha verimli ve esnek olmasına olanak tanır.