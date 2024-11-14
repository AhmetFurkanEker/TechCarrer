
#### HTTP Nedir ? 

HTTP (Hypertext Transfer Protocol), web üzerinden veri iletmek için kullanılan bir protokoldür. Tarayıcı ile sunucu arasında gerçekleşen veri alışverişini düzenleyen bir dizi kuraldır. İstemci (client) ve sunucu (server) arasındaki iletişimi sağlar. İstemci, sunucudan bir web sayfası veya veri talep ettiğinde HTTP istekleri kullanılır ve sunucu bu isteklere yanıt verir.

HTTP, "request-response" modeline dayanır. Örneğin, bir kullanıcı bir web sitesine girdiğinde tarayıcısı bir HTTP isteği gönderir, sunucu bu isteği alır ve gerekli içeriği HTTP yanıtı olarak geri gönderir. Bu protokol, HTTP başlıkları, yanıt kodları (200, 404, 500 gibi) ve veri içerikleriyle çalışır.

**HTTP'nin bazı temel özellikleri:**

1. **Stateless (Durumsuz):** Her isteğin önceki isteklere bağlı olmadan yapılmasıdır; yani her istek bağımsızdır.
    
2. **Port Numarası:** HTTP varsayılan olarak 80 numaralı portu kullanır.
    
3. **HTTP Metodları:** GET, POST, PUT, DELETE gibi metodlarla istek türleri belirlenir.
    
4. **Şifrelenmemiş Veri:** HTTP'de veriler düz metin olarak gönderildiği için güvenlik sorunlarına açıktır. Bu nedenle HTTPS (HTTP Secure) tercih edilir.
    
![[Pasted image 20241111235350.png]]


---
### HTTP Request Headers

HTTP isteği (request) başlıkları, istemci tarafından sunucuya gönderilen ek bilgiler sağlar. Bu başlıklar, istemcinin talepleri hakkında sunucuya bilgi verir ve sunucunun yanıtını özelleştirebilir. İşte en önemli HTTP request başlıkları:
### 1. **Host**
- **Açıklama:** Sunucunun hangi alan adına (domain) hizmet verdiğini belirtir. HTTP/1.1'de zorunludur. Bir hosting içerisinde birden fazla domain bulunabilir. Host header sayesinde hangi domaine ulaşacağı anlaşılır.
- **Örnek:** `Host: www.example.com`
### 2. **User-Agent**
- **Açıklama:** İstemcinin (tarayıcı, uygulama vb.) türünü belirtir. Bu başlık, tarayıcının veya cihazın hangi sürümde olduğunu belirlemek için kullanılır.
- **Örnek:** `User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36`
### 3. **Accept**
- **Açıklama:** Sunucudan alınmak istenen içerik türünü belirtir. Bu başlık, istemcinin hangi türde veri kabul ettiğini belirtir (örneğin, JSON, HTML, vb.).
- **Örnek:** `Accept: text/html, application/xhtml+xml, application/xml;q=0.9, image/webp, */*;q=0.8`
### 4. **Accept-Encoding**
- **Açıklama:** İstemcinin, hangi veri sıkıştırma yöntemlerini desteklediğini belirtir. Genellikle, verilerin daha hızlı aktarılabilmesi için kullanılır.
- **Örnek:** `Accept-Encoding: gzip, deflate, br`
### 5. **Authorization**
- **Açıklama:** Sunucuya yapılacak istekte kimlik doğrulaması için kullanılan başlık. Kullanıcı adı ve şifreyi base64 olarak kodlayarak içerir.
- **Örnek:** `Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=`
### 6. **Content-Type**
- **Açıklama:** İstemcinin sunucuya gönderdiği verinin türünü belirtir. Bu başlık, özellikle POST ve PUT isteklerinde kullanılır.
- **Örnek:** `Content-Type: application/json`
### 7. **Content-Length**
- **Açıklama:** İstemcinin gönderdiği verinin (body) uzunluğunu belirtir. Veri uzunluğu byte cinsinden ifade edilir.
- **Örnek:** `Content-Length: 348`
### 8. **Cookie**
- **Açıklama:** Tarayıcı tarafından sunucudan alınan ve kaydedilen çerezleri (cookies) gönderir. Web uygulamaları genellikle kullanıcı bilgilerini burada saklar.
- **Örnek:** `Cookie: sessionId=abc123; userId=xyz789`
### 9. **Referer**
- **Açıklama:** İstemcinin geldiği önceki sayfanın URL'sini belirtir. Bu, sunucuların yönlendirme bilgisi almasına yardımcı olur.
- **Örnek:** `Referer: https://www.example.com/previous-page`
### 10. **X-Requested-With**
- **Açıklama:** JavaScript AJAX isteklerini tanımak için kullanılır. Genellikle, `XMLHttpRequest` veya `fetch` ile yapılan isteklerde bulunur.
- **Örnek:** `X-Requested-With: XMLHttpRequest`
### 11. **Connection**
- **Açıklama:** Bağlantının yönetimi hakkında bilgi verir. `keep-alive` değeri, bağlantının açık kalmasını sağlar.
- **Örnek:** `Connection: keep-alive`
### 12. **Cache-Control**
- **Açıklama:** Sunucunun yanıtını önbellekleme ile ilgili talimatları belirtir. Bu, özellikle dinamik içerik için önemlidir.
- **Örnek:** `Cache-Control: no-cache, no-store, must-revalidate`
---
### HTTP Response  Headers
### 1. **Status Code**
- **Açıklama:** Yanıtın durumunu belirtir (örneğin, başarılı, hata vb.). Bu başlık, yanıtın başarı durumunu anlamamıza yardımcı olur.
- **Örnek:** `200 OK`, `404 Not Found`, `500 Internal Server Error`
### 2. **Content-Type**
- **Açıklama:** Sunucunun yanıtında gönderdiği verinin türünü belirtir. Bu başlık, istemcinin nasıl işlem yapması gerektiğini belirler.
- **Örnek:** `Content-Type: text/html; charset=UTF-8`, `Content-Type: application/json`
### 3. **Content-Length**
- **Açıklama:** Yanıtın içeriğinin uzunluğunu belirtir. Bu, sunucudan gelen verinin byte cinsinden boyutudur.
- **Örnek:** `Content-Length: 1234`
### 4. **Cache-Control**
- **Açıklama:** Sunucunun yanıtını nasıl önbelleğe alması gerektiğiyle ilgili talimatları belirtir. Önbellekleme politikasını düzenler.
- **Örnek:** `Cache-Control: no-store`, `Cache-Control: max-age=3600`
### 5. **Date**
- **Açıklama:** Yanıtın sunucudan gönderildiği zamanı belirtir.
- **Örnek:** `Date: Mon, 11 Nov 2024 12:00:00 GMT`
### 6. **Server**
- **Açıklama:** Yanıtı gönderen sunucunun yazılım bilgilerini belirtir. Web sunucusunun türünü öğrenmek için kullanılır.
- **Örnek:** `Server: Apache/2.4.29 (Ubuntu)`
### 7. **Location**
- **Açıklama:** Yönlendirme (redirect) yanıtlarında, istemciyi gitmesi gereken yeni bir URL'ye yönlendirir.
- **Örnek:** `Location: https://www.example.com/newpage`
### 8. **Set-Cookie**
- **Açıklama:** Tarayıcıya gönderilen çerezi (cookie) belirtir. Kullanıcı bilgilerini ve oturumları saklamak için kullanılır.
- **Örnek:** `Set-Cookie: sessionId=abc123; path=/; secure; HttpOnly`
### 9. **Content-Encoding**
- **Açıklama:** Sunucunun yanıtını hangi sıkıştırma algoritması ile sıkıştırdığını belirtir. Verilerin daha hızlı aktarılmasını sağlar.
- **Örnek:** `Content-Encoding: gzip`, `Content-Encoding: br`
### 10. **Vary**

- **Açıklama:** Yanıtın hangi başlıklara göre değişebileceğini belirtir. Bu, önbelleklerin içeriği nasıl saklayacağına dair bilgi verir.
- **Örnek:** `Vary: Accept-Encoding`, `Vary: User-Agent`
### 11. **X-Content-Type-Options**
- **Açıklama:** Tarayıcıların içerik türü doğrulamasını zorlamak için kullanılır. Bu, MIME tipini değiştirmeye çalışan saldırılara karşı koruma sağlar.
- **Örnek:** `X-Content-Type-Options: nosniff`
### 12. **Strict-Transport-Security (HSTS)**
- **Açıklama:** Tarayıcılara, yalnızca HTTPS protokolü üzerinden bağlanmalarını söyleyen bir güvenlik başlığıdır. Bu başlık, HTTPS'e yönlendirilmek için kullanılır. Yani bağlantı yalnızca HTTPS ile gerçekleşir böylece downgrade salıdırıları ve ssl stripping saldırılarına karşı korunmuş olunur. 
- **Örnek:** `Strict-Transport-Security: max-age=31536000; includeSubDomains`
### 13. **Access-Control-Allow-Origin**
- **Açıklama:** CORS (Cross-Origin Resource Sharing) politikalarını belirtir. Bir kaynağın hangi domainlerden erişilebileceğini belirler.
- **Örnek:** `Access-Control-Allow-Origin: *`
### 15. **ETag**
- **Açıklama:** Yanıtın içerik versiyonunu belirtir. Bu, istemcilerin içeriğin değişip değişmediğini anlamalarını sağlar.
- **Örnek:** `ETag: "12345"`


```
GET / HTTP/2
Host: www.techcareer.net
Cookie: _gcl_au=1.1.1667933108.1731359477; _ga=GA1.1.76344871.1731359477; _tt_enable_cookie=1; _ttp=rlSPRmeYKlmlMZLwXf5ufQdjNDj; FPID=FPID2.2.iQqdVFng4uDb5ifYalRWVydI9ElICiDDVbJR9lX0ArA%3D.1731359477; FPLC=8iZgUAQPez875XszpiSwgJWh32iZb%2FUSo5pTP%2BGzyNcKt2aQ%2FSVZnZN1ouQ6BdxoQxTl%2FM83Miyzrck8PCr7OQc9k1Q9oDxLMR%2FwO8yWD9aVRncUSk4oIJFAvjzYzA%3D%3D; _hjSession_2664841=eyJpZCI6ImVhOTcxMWI3LTA4MmItNDkzYi1hNTJlLTVmOTQ0NWE3MTAwYyIsImMiOjE3MzEzNTk0Nzc4OTAsInMiOjAsInIiOjAsInNiIjowLCJzciI6MCwic2UiOjAsImZzIjoxLCJzcCI6MH0=; _dn_sid=28582547-c329-46c0-a41a-7b5c63f56d91; _gcl_aw=GCL.1731359491.EAIaIQobChMIla2oy5jViQMVgaloCR3poRYmEAAYASAAEgK3-PD_BwE; _gcl_gs=2.1.k1$i1731359486$u111329409; _ga_E0FGSHPKVP=GS1.1.1731359477.1.1.1731359491.46.0.0; _ga_1234=GS1.1.1731359477.1.1.1731359491.0.0.1994089258; _hjSessionUser_2664841=eyJpZCI6IjAyNzcyNjUwLTljYTUtNWFhMi05ZDczLWZjMTFmZTA1MWYyNCIsImNyZWF0ZWQiOjE3MzEzNTk0Nzc4ODksImV4aXN0aW5nIjp0cnVlfQ==
Sec-Ch-Ua: "Not?A_Brand";v="99", "Chromium";v="130"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.6723.70 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

```

```
HTTP/2 200 OK
Referrer-Policy: unsafe-url
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
Cache-Control: public,max-age=300,no-store
Etag: "16zfggk4cokc0qh"
Content-Type: text/html; charset=utf-8
Vary: Accept-Encoding
Date: Mon, 11 Nov 2024 21:13:26 GMT
Server: Google Frontend
Via: 1.1 google
X-Hit-Type: LIST
X-Hit-Cache: miss
Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
```

---
### OWASP Secure Headers Project

✅ **Active**

- [Strict-Transport-Security](https://owasp.org/www-project-secure-headers/#strict-transport-security)
- [X-Frame-Options](https://owasp.org/www-project-secure-headers/#x-frame-options)
- [X-Content-Type-Options](https://owasp.org/www-project-secure-headers/#x-content-type-options)
- [Content-Security-Policy](https://owasp.org/www-project-secure-headers/#content-security-policy)
- [X-Permitted-Cross-Domain-Policies](https://owasp.org/www-project-secure-headers/#x-permitted-cross-domain-policies)
- [Referrer-Policy](https://owasp.org/www-project-secure-headers/#referrer-policy)
- [Clear-Site-Data](https://owasp.org/www-project-secure-headers/#clear-site-data)
- [Cross-Origin-Embedder-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-embedder-policy)
- [Cross-Origin-Opener-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-opener-policy)
- [Cross-Origin-Resource-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-resource-policy)
- [Cache-Control](https://owasp.org/www-project-secure-headers/#cache-control)


---
#### [Strict-Transport-Security](https://owasp.org/www-project-secure-headers/#strict-transport-security)


Tarayıcılara, yalnızca HTTPS protokolü üzerinden bağlanmalarını söyleyen bir güvenlik başlığıdır. Bu başlık, HTTPS'e yönlendirilmek için kullanılır. Yani bağlantı yalnızca HTTPS ile gerçekleşir böylece downgrade salıdırıları ve ssl stripping saldırılarına karşı korunmuş olunur.

Özellikleri:
1. **HTTPS Bağlantısı Zorunluluğu:** HSTS aktif olduğunda, siteye yalnızca HTTPS üzerinden erişilir.
2. **Yönlendirme Koruması:** HTTP isteklerini otomatik olarak HTTPS'ye yönlendirir.
3. **Cache Süresi:** Tarayıcı, HSTS başlığındaki `max-age` parametresiyle belirlenen süre boyunca siteye yalnızca HTTPS üzerinden erişir.
4. **Subdomain Kapsamı:** `includeSubDomains` parametresiyle tüm alt alan adlarını HTTPS üzerinden zorunlu hale getirir.

`Strict-Transport-Security: max-age=31536000; includeSubDomains; preload`

- `max-age=31536000`: 1 yıl boyunca geçerli olacak şekilde süreyi belirtir.
- `includeSubDomains`: Alt alan adlarını da kapsar.
- `preload`: Siteyi tarayıcıların HSTS ön yükleme listelerine eklemek için kullanılır.

HSTS, güvenliği artırmak için HTTPS kullanımını zorunlu kılarak güvenli olmayan HTTP bağlantılarını tamamen engeller.

---

#### [X-Frame-Options](https://owasp.org/www-project-secure-headers/#x-frame-options)

`X-Frame-Options`, web sayfalarının iframe içinde yüklenip yüklenemeyeceğini belirleyen bir HTTP başlık güvenlik önlemidir. Bu başlık, clickjacking saldırılarına karşı koruma sağlar. Clickjacking, saldırganların kurbanları gizli bir iframe içinde bir butona veya bağlantıya tıklatmasını sağlayarak güvenlik açıklarından faydalanmasını içerir.

1. **DENY:** Sayfanın hiçbir koşulda iframe içinde yüklenmesine izin vermez.
    
    `X-Frame-Options: DENY`
    
2. **SAMEORIGIN:** Sayfanın yalnızca kendi domain'inden gelen iframe'lerde yüklenmesine izin verir. Böylece, farklı bir domain’den yüklenmesi engellenmiş olur.
    
    `X-Frame-Options: SAMEORIGIN`
    
3. **ALLOW-FROM uri:** Sayfanın yalnızca belirli bir kaynaktan gelen iframe'lerde yüklenmesine izin verir. Ancak, bu değer tüm tarayıcılar tarafından tam olarak desteklenmemektedir.
    
    `X-Frame-Options: ALLOW-FROM https://example.com`
    
Bir site yalnızca kendi domain’i üzerinden iframe içinde yüklenmek istiyorsa, HTTP yanıt başlığına `X-Frame-Options: SAMEORIGIN` ekleyebilir. Bu sayede site, farklı domain’lerdeki potansiyel clickjacking saldırılarından korunmuş olur.

---
#### [X-Content-Type-Options](https://owasp.org/www-project-secure-headers/#x-content-type-options)

MIME type (veya içerik türü), web tarayıcılarına bir dosyanın ne tür bir içeriğe sahip olduğunu anlatmak için kullanılan bir etikettir. Tarayıcı, bu etiket sayesinde bir dosyanın HTML, resim, video, ses veya başka bir tür olup olmadığını anlar ve dosyayı ona göre işler. Böylece tarayıcı, dosyayı doğru şekilde görüntüler veya çalıştırır.

Örneğin:

- Bir web sayfası dosyası ise, `text/html` türü ile gelir ve tarayıcı bu dosyayı bir sayfa olarak açar.
- Bir resim dosyası ise, `image/png` veya `image/jpeg` türü ile gelir, böylece tarayıcı onu resim olarak gösterir.
- Bir müzik dosyası ise, `audio/mpeg` türü ile gelir ve tarayıcı bu dosyayı çalmak için müzik oynatıcı açabilir.

**X-Content-Type-Options: nosniff** başlığı ise, tarayıcının dosyayı gelen bu etiketin dışındaki bir türde çalıştırmamasını sağlar. Bu güvenlik önlemiyle, örneğin bir JavaScript dosyasının HTML gibi çalıştırılması veya resim dosyası gibi gösterilmesi engellenmiş olur.


[Mıme Sniffing](https://www.youtube.com/watch?v=XSUVIRgroXo)

---
#### [Content-Security-Policy](https://owasp.org/www-project-secure-headers/#content-security-policy)


`Content-Security-Policy` (CSP), web sayfalarında güvenliği artırmak için kullanılan bir güvenlik başlığıdır. Bu başlık, tarayıcıya hangi içerik kaynaklarının (JavaScript, CSS, resim, iframe vb.) güvenli olduğunu ve yüklenmesine izin verildiğini belirterek çeşitli saldırı türlerine karşı koruma sağlar. Özellikle sitelerdeki XSS (Cross-Site Scripting) ve veri enjeksiyonu saldırılarına karşı güçlü bir savunma sağlar.

CSP ile bir web sayfası, belirli içeriklerin sadece güvenilir kaynaklardan yüklenmesini zorunlu kılarak zararlı kodların çalıştırılmasını engeller. Örneğin, sayfada yalnızca kendi sunucusundan gelen JavaScript kodlarının çalıştırılmasını sağlayabilir veya dış sitelerden yüklenebilecek içerikleri kısıtlayabilir.

### CSP'nin Sıklıkla Kullanılan Direktifleri

1. **default-src**: Genel olarak tüm içerik türleri için güvenilir kaynakları belirtir.
    
    `Content-Security-Policy: default-src 'self'`
    
2. **script-src**: JavaScript dosyalarının yalnızca güvenli kaynaklardan yüklenmesine izin verir.
    
    `Content-Security-Policy: script-src 'self' https://trusted-source.com`
    
3. **style-src**: CSS dosyaları için izin verilen kaynakları belirtir.
    
    `Content-Security-Policy: style-src 'self' https://trusted-styles.com`
    
4. **img-src**: Görsellerin hangi kaynaklardan yüklenebileceğini belirler.
    
    `Content-Security-Policy: img-src 'self' https://images.example.com`
    
5. **frame-ancestors**: Sayfanın hangi siteler tarafından iframe içinde gösterilebileceğini belirtir.
    
    `Content-Security-Policy: frame-ancestors 'self'`
    
6. **object-src**: Flash veya diğer embed edilmiş medya gibi içeriklerin nereden yükleneceğini kısıtlar.
    
    `Content-Security-Policy: object-src 'none'`
    

### CSP Örneği:

Aşağıdaki örnek, yalnızca kendi domain’inden (self) gelen JavaScript, CSS ve resimlerin yüklenmesine izin verir:

`Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self'; img-src 'self'`

Bu sayede, dış kaynaklardan gelen potansiyel zararlı içeriklerin yüklenmesi engellenmiş olur. CSP, web uygulamalarını güvenli hale getirerek saldırı yüzeyini büyük oranda daraltır ve kötü niyetli kodların çalışmasını zorlaştırır.


---
#### [X-Permitted-Cross-Domain-Policies](https://owasp.org/www-project-secure-headers/#x-permitted-cross-domain-policies)


`X-Permitted-Cross-Domain-Policies`, bir web sitesinin başka sitelere veya uygulamalara kendi içeriklerine erişim izni verip vermeyeceğini belirleyen bir güvenlik ayarıdır. Örneğin, bir web sitesi bir başka sitenin, kendisindeki bazı dosyaları (görseller, ses dosyaları, videolar veya Flash içerikler gibi) kullanmasını istemeyebilir.

Normalde, bazı tarayıcı eklentileri (örneğin Flash oynatıcılar veya PDF görüntüleyiciler), bir sitedeki içeriklere başka bir siteden erişmeye çalışabilir. Bu, eğer kontrol edilmezse veri hırsızlığı gibi güvenlik risklerine yol açabilir. `X-Permitted-Cross-Domain-Policies`, web sitesinin bu tür erişimlere izin verip vermeyeceğini veya hangi koşullarda izin vereceğini tanımlar.


1. **none**: Hiçbir site bu sunucudaki içeriklere erişemez. Bu, dış erişimi tamamen engeller ve en güvenli seçenektir.
    
    `X-Permitted-Cross-Domain-Policies: none`
    
2. **master-only**: Sunucunun kök dizininde özel bir `crossdomain.xml` dosyası varsa, yalnızca o dosyada belirtilen sitelere erişim izni verilir.
    
    `X-Permitted-Cross-Domain-Policies: master-only`
    
3. **all**: Herkes bu sunucudaki içeriklere erişebilir. Bu ayar genellikle önerilmez, çünkü güvenlik açığı yaratabilir.
    
    `X-Permitted-Cross-Domain-Policies: all`
### Örnek Senaryo:

Bir bankanın web sitesi düşünelim. Bu bankanın web sitesindeki içeriklere sadece kendi çalışanları ya da belirli güvenilir kaynaklardan erişim sağlanması istenebilir. Bu durumda, bankanın sunucusu `X-Permitted-Cross-Domain-Policies: none` başlığını kullanarak dışardan erişimi tamamen engeller. Bu başlık, istem dışı veri erişimlerine karşı önemli bir koruma sağlar ve genellikle güvenlik için `none` olarak ayarlanması tercih edilir.

---
#### [Referrer-Policy](https://owasp.org/www-project-secure-headers/#referrer-policy)

`Referrer-Policy`, bir web sayfasının bağlantıya tıklayan kullanıcının geldiği URL bilgisini (referrer) diğer sayfalara nasıl ileteceğini belirleyen bir güvenlik başlığıdır. Bu başlık, bir sayfadan başka bir sayfaya geçerken gönderilen referrer bilgisinin miktarını kısıtlayarak kullanıcı gizliliğini artırmak için kullanılır. Özellikle, sayfanın hangi kısmından veya hangi parametrelerle yönlendirme yapıldığını gizleyerek hassas bilgilerin üçüncü taraflara sızmasını önler.

Bir web sayfası başka bir sayfaya yönlendirme yaptığında, bu yönlendirme sırasında referrer bilgisi alıcıya iletilir. Bu bilgi, kullanıcıyı yönlendiren URL’yi içerir ve bazı durumlarda bu URL gizli ya da kişisel bilgileri barındırabilir. `Referrer-Policy`, referrer bilgisinin paylaşımını denetleyerek bu tür hassas bilgilerin korunmasını sağlar.

1. **no-referrer**: Referrer bilgisi hiçbir durumda iletilmez. Yani, hedef sayfa kullanıcıyı yönlendiren sayfanın URL’sini göremez.
    
    `Referrer-Policy: no-referrer`
    
2. **no-referrer-when-downgrade**: HTTPS’den HTTP’ye geçerken referrer bilgisi gönderilmez, ancak HTTPS’den HTTPS’ye veya HTTP’den HTTP’ye geçişlerde referrer bilgisi iletilir. Bu varsayılan güvenlik ayarıdır.
    
    `Referrer-Policy: no-referrer-when-downgrade`
    
3. **same-origin**: Referrer bilgisi sadece aynı domain içindeki sayfalara geçişlerde gönderilir. Farklı domain’lere yönlendirme yapılırken referrer bilgisi gizlenir.
    
    `Referrer-Policy: same-origin`
    
4. **origin**: Referrer bilgisi sadece yönlendiren sitenin ana domain’ini içerir. Örneğin, `https://example.com/page?user=123` URL’sinden yönlendirme yapılırken yalnızca `https://example.com` bilgisi paylaşılır.
    
    `Referrer-Policy: origin`
    
5. **strict-origin**: HTTPS’den HTTPS’ye geçişlerde ana domain bilgisi paylaşılır, ancak HTTPS’den HTTP’ye geçerken hiçbir referrer bilgisi gönderilmez.
    
    `Referrer-Policy: strict-origin`
    
6. **origin-when-cross-origin**: Aynı domain’de tam referrer bilgisi gönderilirken, farklı bir domain’e geçişte yalnızca ana domain bilgisi paylaşılır.
    
    `Referrer-Policy: origin-when-cross-origin`
    
7. **strict-origin-when-cross-origin**: HTTPS’den HTTPS’ye geçişlerde tam referrer bilgisi paylaşılır, farklı bir domain’e geçerken yalnızca ana domain bilgisi gönderilir. HTTPS’den HTTP’ye geçişlerde ise referrer bilgisi gönderilmez.
    
    `Referrer-Policy: strict-origin-when-cross-origin`
    
8. **unsafe-url**: Referrer bilgisi her durumda tam URL olarak paylaşılır. Bu en riskli seçenektir, çünkü tam URL her durumda görünür olur.
    
    `Referrer-Policy: unsafe-url`
### Örnek Senaryo:

Eğer bir alışveriş sitesinde kullanıcı işlemleri yapılıyorsa, `Referrer-Policy: no-referrer` veya `strict-origin-when-cross-origin` gibi değerlerle referrer bilgisi gizlenebilir. Bu şekilde, kullanıcıların işlemleri sırasında URL'de yer alabilecek sipariş detayları gibi hassas bilgiler, üçüncü taraflara sızdırılmadan korunur.


---

#### [Clear-Site-Data](https://owasp.org/www-project-secure-headers/#clear-site-data)

`Clear-Site-Data` başlığı, bir web sitesi kullanıcılarının tarayıcılarında saklanan verileri (örneğin çerezler, önbellek, yerel depolama verileri) temizlemek için kullanılan bir güvenlik başlığıdır. Bu başlık sayesinde, sitenin eski veya güvenli olmayan verileri silinerek, kullanıcıların güncel ve güvenli bir deneyim yaşaması sağlanır. Özellikle oturum kapatma, hesap silme, veya site güncelleme gibi durumlarda kullanışlıdır.

Bir kullanıcı bir sayfaya eriştiğinde, `Clear-Site-Data` başlığı tarayıcıya hangi tür verilerin temizlenmesi gerektiğini bildirir. Böylece, istem dışı veri sızıntıları veya eski verilerin kullanılması gibi güvenlik riskleri azaltılmış olur.


1. **"cache"**: Tarayıcı önbelleğini temizler. Bu, sitenin dosyalarının (ör. CSS, JavaScript, görseller) güncel sürümlerinin indirilmesini sağlar.
    
    `Clear-Site-Data: "cache"`
    
2. **"cookies"**: Sitede ayarlanmış tüm çerezleri temizler. Kullanıcıların oturumları kapatılmış olur, bu yüzden oturum kapatma işlemi sırasında sıklıkla kullanılır.
    
    `Clear-Site-Data: "cookies"`
    
3. **"storage"**: Tarayıcıda saklanan tüm verileri temizler (ör. yerel depolama, oturum depolama gibi veriler). Bu, sitede kullanıcıya özel veri saklanmasını sona erdirir.
    
    `Clear-Site-Data: "storage"`
    
4. **"executionContexts"**: Tarayıcıdaki tüm çalışan iş parçacıklarını ve servis çalışanlarını (service workers) temizler. Bu, sitenin çalışan eski veya güvenli olmayan komut dosyalarının durdurulmasını sağlar.
    
    `Clear-Site-Data: "executionContexts"`
    
5. **Birden Çok Değerin Kombinasyonu**: Birden fazla değeri aynı anda kullanarak tüm veriler temizlenebilir.
    
    `Clear-Site-Data: "cookies", "storage", "cache", "executionContexts"`
    

### Kullanım Örneği

Bir kullanıcı siteye giriş yaptıktan sonra oturumunu kapatmak istediğinde, `Clear-Site-Data: "cookies", "storage"` başlığı kullanılarak tüm oturum verileri temizlenebilir. Bu, kullanıcıyı tamamen çıkış yapmış ve tarayıcıda kalan hiçbir verinin saklanmadığından emin olmuş olur. Bu sayede, kullanıcının özel bilgileri korunmuş olur ve eski verilere dayalı hatalı bir deneyim yaşanması önlenir.


---
#### [Cross-Origin-Embedder-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-embedder-policy)


**COEP** (Cross-Origin-Embedder-Policy), bir web sayfasının **başka sitelerden gelen içerikleri** nasıl yükleyeceğini kontrol eden bir güvenlik başlığıdır. Bu başlık, sayfanın yalnızca **güvenli ve onaylı kaynaklardan** içerik almasını sağlar. Örneğin, bir web sayfası başka bir domain'den (farklı bir siteden) resim, video veya başka bir içerik alırken, **COEP**, bu dış içeriklerin güvenli olup olmadığını kontrol eder.

1. **`unsafe-none`**:
    
    - Bu, COEP'in **devre dışı** olduğu anlamına gelir. Yani, sayfa dış kaynaklardan içerik alırken herhangi bir güvenlik kısıtlaması yoktur. Başka bir deyişle, sayfa dışarıdan gelen her türlü içeriği yükleyebilir.
    
    `Cross-Origin-Embedder-Policy: unsafe-none`
    
2. **`require-corp`**:
    
    - Bu seçenek, sayfanın yalnızca **güvenilir ve onaylı kaynaklardan** içerik almasına izin verir. Yani, dışarıdan gelen içeriklerin güvenli olup olmadığını kontrol etmek için **CORP (Cross-Origin Resource Policy)** başlığı kullanılır. Eğer dış kaynak, güvenli değilse veya uygun başlıkları (CORP) eklememişse, içerik yüklenmez.
    
    `Cross-Origin-Embedder-Policy: require-corp`
### Neden Kullanılır?

**COEP**, sayfanın güvenliğini artırmak için kullanılır. Web sayfası başka bir siteden içerik alırken, COEP, yalnızca güvenli ve onaylı içeriklerin yüklenmesini sağlar. Bu, özellikle aşağıdaki gibi durumlar için önemlidir:

- **WebAssembly** veya **SharedArrayBuffer** gibi özelliklerin çalışabilmesi için güvenli bir ortam gereklidir.
- Sayfanın kötü niyetli dış kaynaklardan gelen içeriklerle yüklenmesi engellenir.

### Örnek Senaryo:

Diyelim ki bir e-ticaret sitesindesiniz ve bu site başka bir domain'den (örneğin, `ads.com`) reklam resimleri yüklüyor. Eğer **COEP** başlığı `require-corp` olarak ayarlanmışsa, `ads.com` sitesinin bu resimlere **CORP başlığı** eklemesi gerekir. Eğer `ads.com` bu başlığı eklemezse, resimler yüklenmez.

---

#### [Cross-Origin-Opener-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-opener-policy)

**Cross-Origin-Opener-Policy (COOP)**, web güvenliğiyle ilgili bir HTTP başlığıdır ve tarayıcılara, bir sayfanın başka bir kaynağı (örneğin, bir iframe veya pop-up) ile nasıl etkileşime gireceğini belirler. COOP, özellikle **cross-origin** (farklı kökenlerden gelen) içeriğin güvenliğini sağlamaya yardımcı olur.

Bu başlık, sayfanın hangi kaynaklardan gelen içeriklerle etkileşimde bulunabileceğini ve bu içeriklerin sayfanın başlatıcı ortamını (parent environment) nasıl etkileyebileceğini kontrol eder. Amaç, sayfanın gizliliğini ve güvenliğini artırmaktır. Özellikle, sayfanın başka bir kaynağa (örneğin, kötü niyetli bir pop-up'a) etkileşimle maruz kalmasını engellemeye yönelik bir mekanizma sağlar.

**COOP** başlığına sahip sayfalar, başlık aşağıdaki değerlere sahip olabilir:

1. **`same-origin`**: Sayfa sadece aynı kökenden (same-origin) gelen içeriklerle etkileşime girebilir.
2. **`same-origin-allow-popups`**: Sayfa, aynı kökenden gelen içeriklerle etkileşime girebilir, ancak pop-up pencereleri açıldığında farklı bir kaynağa da izin verilebilir.
3. **`unsafe-none`**: Sayfa, herhangi bir kısıtlama olmadan herhangi bir kaynaktan gelen içerikle etkileşime girebilir.

Özetle, **COOP** başlığı, güvenlik ve gizliliği artırmak amacıyla, bir sayfanın başka bir kaynağa nasıl erişebileceğini denetler ve kötüye kullanım risklerini azaltmaya yardımcı olur.

---
#### [Cross-Origin-Resource-Policy](https://owasp.org/www-project-secure-headers/#cross-origin-resource-policy)


**Cross-Origin-Resource-Policy (CORP)**, web güvenliği ile ilgili bir HTTP başlığıdır ve web sayfalarının, farklı kökenlerden (cross-origin) gelen kaynaklara nasıl erişim sağlayacağını belirler. Bu başlık, özellikle sayfanın dışarıdan (cross-origin) yüklediği kaynakların güvenliğini kontrol eder ve tarayıcıya, kaynakların yalnızca belirli koşullarda yüklenmesine izin verir.

**CORP**, temel olarak **cross-origin** isteklerini kontrol eder ve sayfa içeriğinin yalnızca belirli türdeki dış kaynaklarla (örneğin, scriptler, stil dosyaları veya görüntüler) etkileşime girmesini sağlar. Bu başlık, özellikle **cross-origin** kaynaklardan (diğer domainlerden veya kökenlerden) veri çekerken, bu kaynakların güvenliğinin sağlanması amacıyla kullanılır.

CORP başlığı üç farklı değere sahip olabilir:

1. **`same-origin`**: Yalnızca aynı kökenden (same-origin) gelen kaynaklara izin verir. Bu, sayfanın yalnızca kendi kökeninden (domain'inden) kaynakları yüklemesine ve kullanmasına olanak tanır.
    
2. **`same-origin-allow-popups`**: Sayfa, kendi kökeninden gelen kaynakları kullanabilir, ancak pop-up'lar veya yeni pencere açılması durumunda, farklı kökenlerden gelen kaynaklara izin verir. Yani, sayfa içeriği sadece aynı kökenden yüklenebilir, ancak pop-up'lar farklı bir kökenden yüklenebilir.
    
3. **`cross-origin`**: Sayfa, başka bir kökenden (cross-origin) gelen kaynaklara erişebilir. Bu, sayfanın başka bir domain'den gelen içerikleri yüklemesine izin verir.
    

CORP başlığı, sayfanın dışarıdan gelen kaynaklarla etkileşimi hakkında daha fazla kontrol sağlar ve özellikle **cross-site scripting (XSS)** gibi saldırılara karşı koruma sağlar. Bu başlık sayesinde, bir sayfa yalnızca güvenilir kaynaklardan içerik alabilir, kötü niyetli kaynakların sayfa içinde çalışmasını engelleyebilir.

---
#### [Cache-Control](https://owasp.org/www-project-secure-headers/#cache-control)


**Cache-Control** HTTP başlığı, web tarayıcılarının ve ara sunucuların (proxy'ler gibi) bir kaynağı (örneğin bir web sayfası, resim veya başka bir dosya) nasıl önbelleğe alacağını kontrol etmek için kullanılır. Bu başlık, hem sunucu hem de istemci tarafında önbellek yönetimi yaparak, web içeriğinin ne zaman ve nasıl saklanacağını, yenileneceğini veya tekrar kullanılacağını belirtir.

**Cache-Control** başlığı, çeşitli direktiflerle yapılandırılabilir ve her direktif farklı bir önbellekleme stratejisini ifade eder. İşte en yaygın kullanılan Cache-Control direktifleri:

1. **`public`**: Kaynak, herhangi bir ara sunucu veya istemci tarafından önbelleğe alınabilir. Bu, kaynak herkese açık olduğunda, yani doğrulama gerektirmeyen ve genel olarak herkese açık olan içerikler için kullanılır.
    
2. **`private`**: Kaynak yalnızca kullanıcıya ait tarayıcıda önbelleğe alınabilir. Bu, kişisel verilere veya kullanıcıya özgü içeriğe sahip sayfalar için uygundur. Örneğin, bir kullanıcı profil sayfası.
    
3. **`no-cache`**: Kaynak, istemcide veya ara sunucularda önbelleğe alınabilir, ancak her erişimde sunucuya gidilip doğrulama yapılmalıdır. Sunucudan gelen yanıt her seferinde kontrol edilmelidir. Bu, içeriğin her zaman güncel olmasını sağlamak için kullanılır.
    
4. **`no-store`**: Kaynak hiçbir şekilde önbelleğe alınamaz. Her istekte sunucuya gidilmesi gerekir ve veri asla önbelleğe kaydedilmez. Bu, güvenlik gereksinimlerinin yüksek olduğu, örneğin finansal bilgiler veya şifreli sayfalar için kullanılır.
    
5. **`max-age=<seconds>`**: Kaynağın önbellekte ne kadar süreyle saklanabileceğini belirler. `<seconds>` parametresi, önbelleğin geçerlilik süresini saniye cinsinden belirtir. Örneğin, `max-age=3600` ifadesi, kaynağın bir saat boyunca geçerli olduğunu belirtir.
    
6. **`s-maxage=<seconds>`**: Bu direktif, yalnızca ortak önbelleklerde (örneğin, proxy sunucuları) geçerlidir. `max-age` ile birlikte kullanılabilir, ancak yalnızca proxy'ler için geçerlidir.
    
7. **`must-revalidate`**: Eğer bir kaynağın geçerliliği sona erdiyse, istemci kaynakla ilgili işlemi tekrar doğrulamak zorundadır. Yani, bir kaynak önbellekten çıkarıldıysa, istemci sunucuya doğrulama yapmak için başvurmalıdır.
    
8. **`proxy-revalidate`**: `must-revalidate` ile aynıdır, ancak yalnızca proxy sunucuları için geçerlidir.
    
9. **`immutable`**: Kaynağın değişmeyeceği belirtilir, yani bir kere alındığında, istemcinin kaynağı tekrar doğrulamasına gerek yoktur. Bu, genellikle sabit içerik (örneğin, resimler) için kullanılır.
    

### Örnekler:

- **`Cache-Control: public, max-age=86400`**  
    Kaynak 24 saat (86400 saniye) boyunca her yerde (tarayıcılar ve ara sunucular) önbelleğe alınabilir.
    
- **`Cache-Control: private, no-store`**  
    Kaynak yalnızca istemcinin tarayıcısında saklanabilir, ancak hiçbir zaman önbelleğe alınmaz.
    
- **`Cache-Control: no-cache, must-revalidate`**  
    Kaynak her zaman sunucudan doğrulanarak alınmalıdır, yani önbellekte saklanabilir ancak her erişimde geçerliliği kontrol edilmelidir.
    
