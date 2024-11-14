
Kanonikleştirme, bir şeyin en basit, standart veya genel biçime getirilmesi anlamına gelir. Matematikte ve bilgisayar bilimlerinde, genellikle verilerin, ifadelerin veya yapıların belirli bir kurala göre basitleştirilmesi anlamında kullanılır. Örneğin, matematiksel ifadelerin standart bir forma getirilmesi veya veritabanlarındaki verilerin belirli bir formatta düzenlenmesi gibi. Bu süreç, karmaşıklığı azaltır ve işlemleri daha verimli hale getirir.

#### Çok Adımlı Doğrulama ve Kanonikleştirme

Kullanıcı tarafından sağlanan girdilerin doğrulama mantığı parçası olarak birkaç adımda manipüle edilmesi sırasında sıkça karşılaşılan bir sorun, bu sürecin dikkatlice yönetilmediği durumlarda saldırganın, doğrulama mekanizması aracılığıyla kötü niyetli verileri geçirmeyi başarabilmesidir. Bu problem türlerinden biri, bir uygulamanın belirli karakterleri veya ifadeleri kaldırarak veya kodlayarak kullanıcı girdisini temizlemeye çalışmasıyla ortaya çıkar.

Örneğin, bir uygulama bazı cross-site scripting saldırılarına karşı korunmaya çalışırken şu ifadeyi filtrelemeye çalışabilir:

```
<script> ==> Kaldırıldı

<scr<script>ipt> ==> <script>
```


Benzer şekilde, kullanıcı girdisine birden fazla doğrulama adımı uygulandığında, saldırgan bu adımların sıralanmasını kullanarak filtreyi atlayabilir. Örneğin, uygulama önce "../" işaretlerini rekürsif olarak kaldırır ve sonra ".." işaretlerini kaldırırsa, aşağıdaki girdi doğrulamayı geçmek için kullanılabilir

```
....\/
```


Veri kanonikleştirme, çeşitli kodlama şekillerindeki girdileri ortak bir karakter kümesine dönüştürme işlemidir. Kullanıcı tarayıcısından gönderilen veriler farklı kodlama şemalarında olabilir. Eğer girdi filtreleri uygulandıktan sonra kanonikleştirme yapılırsa, saldırgan uygun kodlama şeması kullanarak doğrulama mekanizmasını atlayabilir.


Örneğin, bir uygulama bazı SQL enjeksiyon saldırılarına karşı tek tırnak karakterini engellemeye çalışırken, girdi sonradan kanonikleştirilirse, saldırgan aşağıdaki gibi çift URL kodlamayı kullanarak filtreyi atlayabilir:

```
%2527
```


Bu girdi alındığında, uygulama sunucusu normal URL çözümlemesini yapar, böylece girdi şu hale gelir:

```
%27
```


Bu durumlardaki birden fazla doğrulama ve kanonikleştirme adımları sadece sunucu tarafında gerçekleşmek zorunda değildir. Örneğin, aşağıdaki girdide birkaç karakter HTML kodlaması yapılmıştır:

```
<iframe src=j&#x61;vasc&#x72ipt&#x3a;alert&#x28;1&#x29;>
```
Eğer sunucu tarafı uygulama, belirli JavaScript ifadelerini ve karakterleri engellemek için bir girdi filtresi kullanıyorsa, kodlanmış girdi filtreyi atlamakta başarılı olabilir. Ancak girdi daha sonra uygulamanın yanıtına kopyalanırsa, bazı tarayıcılar src parametre değerini HTML çözümleme işlemine tabi tutar ve stored xss çalıştırılır.


Kanonikleştirme sorunları, uygulamanın bir karakter setini başka bir setle dönüştürdüğü durumlarda ortaya çıkabilir. Örneğin, bazı teknolojiler benzer karakterleri "en iyi eşleşme" ile dönüştürebilir, bu da saldırganların engellenmiş karakterleri geçirmesine yol açabilir. Bu tür saldırılar genellikle girdi tabanlı zayıflıklara karşı etkili olabilir. Kanonikleştirme ve çok adımlı doğrulama sorunlarını önlemek zor olabilir ve tek bir çözümü yoktur. Bir yaklaşım, temizleme adımlarını rekürsif olarak uygulamaktır, ancak bu bazen sonsuz döngülere neden olabilir. Kötü girdilerin tamamen reddedilmesi, temizleme yerine tercih edilebilir.