
HTTP durum kodları, web sunucularının istemciye (örneğin, bir web tarayıcısına) verdiği yanıtı tanımlar ve isteğin nasıl işlendiğini gösterir. Her durum kodu üç rakamdan oluşur ve üç ana kategoriye ayrılır. Bu kategoriler, istemcinin yaptığı isteğe sunucunun nasıl bir yanıt verdiğini belirtir. Şimdi her kategoriye ve bazı yaygın durum kodlarına daha ayrıntılı göz atalım:

### 1. **1xx (Bilgi Kodları)**

Bu durum kodları, istemcinin yaptığı isteğin alındığını ve sunucunun işlemeye devam ettiğini bildirir. Bu tür yanıtlar genellikle kullanıcılar tarafından görünmez, çünkü bunlar istemciye süreç hakkında bilgi vermek için kullanılır.

- **100 Continue**: İstemciye, sunucunun isteğin ilk kısmını aldığını ve devam etmesi gerektiğini bildirir. Genellikle büyük isteklerde, ilk veri kısmı başarıyla alındığında kullanılır.
    
- **101 Switching Protocols**: İstemci, protokol değiştirme talebi göndermiştir ve sunucu bu isteği kabul etmiştir.
### 2. **2xx (Başarı Kodları)**

Bu kategori, istemcinin yaptığı isteğin başarılı bir şekilde sunucu tarafından işleme alındığını belirtir. Durum kodları genellikle başarılı işlemlerin bir sonucudur.

- **200 OK**: İstek başarıyla alındı, sunucu tarafından doğru şekilde işlendi ve istemciye yanıt gönderildi. Bu, en yaygın başarı kodudur.
    
- **201 Created**: İstek başarıyla işlendi ve bu işlem sonucunda yeni bir kaynak oluşturuldu. Genellikle POST istekleriyle birlikte kullanılır.
    
- **202 Accepted**: İstek alındı, ancak henüz işlenmedi. Sunucu isteği kabul etti, ancak işleme aşamasında olabilir.
    
- **204 No Content**: İstek başarıyla işlendi, ancak istemciye dönecek içerik yoktur. Genellikle bir kaynağın silinmesinden veya verilerin başarıyla güncellenmesinden sonra kullanılır.
    
- **205 Reset Content**: Sunucu, istemciyi içeriği sıfırlamaya yönlendiriyor. Örneğin, bir formun boşaltılmasını istemek için kullanılabilir.
    

### 3. **3xx (Yönlendirme Kodları)**

Bu durum kodları, istemcinin isteği için bir yönlendirme işlemi yapılması gerektiğini belirtir. İstemci, yeni bir URL'ye yönlendirilmelidir.

- **301 Moved Permanently**: Kaynak kalıcı olarak başka bir URL'ye taşındı. İstemciye eski URL yerine yeni URL'yi kullanması gerektiği bildirilir. SEO açısından önemli bir koddur.
    
- **302 Found**: Kaynak geçici olarak başka bir URL'de bulunmaktadır. İstemci, isteği geçici olarak başka bir yerde yapmalıdır. Bu kod, geçici yönlendirmeler için kullanılır.
    
- **303 See Other**: İstemci, isteği başka bir kaynak üzerinden almalıdır. Genellikle HTTP GET istekleri ile birlikte kullanılır.
    
- **304 Not Modified**: İstemcinin göndermiş olduğu istek, zaten sunucuda mevcut olan içerikle örtüşmektedir. İçeriğin değişmediğini belirtir ve istemciye yeni içerik gönderilmez.
    
- **307 Temporary Redirect**: Kaynak geçici olarak başka bir URL'ye taşındı, ancak istemci aynı HTTP yöntemini kullanarak isteği yeni URL'ye göndermelidir.
    

### 4. **4xx (İstemci Hatası Kodları)**

Bu kategori, istemcinin yaptığı istekte bir hata olduğunu belirtir. İstemci, hatalı bir istek yapmış olabilir veya erişim için gerekli izinlere sahip olmayabilir.

- **400 Bad Request**: Sunucu, istemciden gelen isteği anlamadı veya istekte bir hata var. Bu durum genellikle eksik veya hatalı parametreler nedeniyle ortaya çıkar.
    
- **401 Unauthorized**: İstemcinin isteği doğrulaması başarısız oldu. Kullanıcının kimliği doğrulanmamış veya geçerli bir oturum açılmamışsa bu kod döner.
    
- **403 Forbidden**: Sunucu, istemcinin isteğini anlamış, ancak istemcinin bu kaynağa erişmeye yetkisi yoktur. Bu, erişim yasaklarının olduğu durumlar için geçerlidir.
    
- **404 Not Found**: İstenilen kaynak sunucuda bulunamadı. En yaygın hata kodlarından biridir ve genellikle yanlış URL veya silinmiş içerik için kullanılır.
    
- **405 Method Not Allowed**: İstemci, sunucuda mevcut olmayan bir HTTP yöntemini kullanarak istekte bulundu. Örneğin, GET yerine POST kullanmak.
    
- **408 Request Timeout**: İstemci, sunucuya isteği zamanında gönderemedi. İstemcinin çok uzun süre yanıt vermemesi nedeniyle bu hata oluşur.
    

### 5. **5xx (Sunucu Hatası Kodları)**

Bu kategori, sunucu tarafında meydana gelen hataları belirtir. Sunucu, istemcinin geçerli bir isteğini işleyemez.

- **500 Internal Server Error**: Sunucu, isteği işleyemedi ve genel bir hata oluştu. Bu, sunucunun beklenmedik bir durumda olduğunu gösterir.
    
- **501 Not Implemented**: Sunucu, istemcinin kullandığı HTTP yöntemini desteklemiyor veya işleme kapasitesine sahip değil.
    
- **502 Bad Gateway**: Sunucu, başka bir sunucudan geçerli bir yanıt alamadı. Genellikle bir proxy veya ağ geçidi sunucusunda oluşan sorunlar nedeniyle ortaya çıkar.
    
- **503 Service Unavailable**: Sunucu, geçici bir arıza nedeniyle şu anda hizmet veremiyor. Genellikle aşırı yüklenme veya bakım nedeniyle bu kod döner.
    
- **504 Gateway Timeout**: Sunucu, isteği işlemek için gerekli olan diğer sunuculardan zamanında yanıt alamadı.
    
- **505 HTTP Version Not Supported**: Sunucu, istemcinin kullandığı HTTP sürümünü desteklemiyor.