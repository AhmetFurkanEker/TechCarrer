
Temel güvenlik sorunu, tüm kullanıcı girdilerinin güvenilmez olmasıdır. Birçok saldırı, beklenmeyen girdilerle uygulamanın beklenmedik davranışlar sergilemesine yol açar. Güvenlik savunmalarının temel gereksinimi, kullanıcı girdilerini güvenli bir şekilde işlemesidir. Girdiye dayalı güvenlik açıkları her tür teknolojiyle ilişkili olarak ortaya çıkabilir. "Girdi doğrulama" bu saldırılara karşı savunma olarak belirtilir, ancak evrensel bir koruyucu mekanizma yoktur ve kötü niyetli girdilere karşı savunma yapmak basit değildir.

![[Pasted image 20241112102208.png]]


Uygulamalar, kullanıcı girdilerini güvenli bir şekilde işlemek için katı doğrulama kontrolleri uygulamalıdır. Bazı girdiler, örneğin kullanıcı adı, sıkı kısıtlamalarla sınırlandırılabilirken, adres gibi diğer girdiler daha geniş bir karakter yelpazesini kabul edebilir, ancak makul uzunluk sınırları ve HTML işaretleme kısıtlamaları olabilir. Bazı durumlarda, rastgele girdiler kabul edilmelidir, örneğin blog gönderileri ve yorumlar. Tarayıcı arayüzü dışında, çerezler ve gizli form alanları gibi sunucuda başlayan ve istemci tarafından geri iletilen veriler de dikkatle doğrulanmalıdır. Bu tür verilerin doğrulanması, potansiyel saldırıları tespit etmek için önemlidir.

---

#### Approaches to Input Handling (Giriş İşleme Yaklaşımları) 

Kullanıcı girdilerini işleme sorununa yaygın olarak çeşitli geniş yaklaşımlar benimsenir. Farklı durumlar ve farklı girdi türleri için farklı yaklaşımlar genellikle daha uygundur ve bazen birden fazla yaklaşımın bir kombinasyonu tercih edilebilir.

1. Black List :Kara liste yaklaşımı, saldırılarda kullanılan belirli kelime veya desenleri engelleyerek diğer girdileri kabul eder. Ancak, bu yöntem genellikle etkisizdir. İlk olarak, güvenlik açıkları çeşitli şekillerde kodlanmış girdilerle istismar edilebilir ve kara listeler bu girdilerin bazılarını atlayabilir. İkinci olarak, istismar teknikleri sürekli olarak gelişir ve yeni yöntemler mevcut kara listeleri aşabilir. Sonuç olarak, kara liste tabanlı filtreler genellikle basit ayarlamalarla kolayca aşılabilir.

>select ==> Engellendi ==> SeLeCt
   'or 1=1-- ==> Engellendi ==> 'or 2=2--
   Alert("XSS") ==> Engellendi  ==> prompt("XSS")

Diğer durumlarda, belirli anahtar kelimeleri engellemek için tasarlanmış filtreler, uygulama tarafından gerçekleştirilen tokenleştirmeyi bozmak için ifadeler arasında standart olmayan karakterler kullanılarak atlanabilir.

![[Pasted image 20241112103040.png]]

Son olarak, özellikle web uygulama güvenlik duvarlarında (WAF) uygulanan birçok kara liste tabanlı filtre, NULL bayt saldırılarına karşı savunmasızdır. Yönetilen ve yönetilmeyen yürütme bağlamlarında dizelerin farklı şekilde işlenmesi nedeniyle, engellenen bir ifadenin öncesine bir NULL bayt eklemek, bazı filtrelerin girdiyi işlemeyi durdurmasına ve dolayısıyla ifadeyi tanımlayamamasına neden olabilir.

![[Pasted image 20241112103102.png]]

2. Whıte List
   
   Beyaz liste yaklaşımı, yalnızca zararsız olduğu bilinen girdileri kabul eden bir dizi kriter kullanır ve diğer her şeyi engeller. Örneğin, bir ürün kodunun sadece alfanümerik ve altı karakter uzunluğunda olması gibi. Bu yöntem, potansiyel olarak kötü niyetli girdileri önlemede en etkili yol olarak kabul edilir, çünkü dikkatli oluşturulan beyaz liste saldırganların girdilerini engeller. Ancak, her durumda uygulanabilir değildir, çünkü bazı girdiler (örneğin, kesme işareti veya tire içeren isimler) kabul edilmek zorunda kalınabilir. Dolayısıyla, beyaz listeleme genellikle etkili olmasına rağmen her zaman uygulanabilir bir çözüm sunmaz.


#### VERİ TEMİZLEME

Bu yaklaşım, güvenli olduğu garanti edilemeyen verileri reddetmek yerine temizlemeyi içerir. Potansiyel olarak kötü niyetli karakterler verilerden çıkarılır, güvenli olanlar bırakılır veya veriler uygun şekilde "encode" veya "escape" edilir. Veri temizleme, genellikle etkili bir yöntemdir ve kötü niyetli girdilere karşı genel bir çözüm sağlar. Örneğin, XSS saldırılarına karşı tehlikeli karakterlerin HTML ile encode edilmesi yaygındır. Ancak, bir girdide birden fazla türde kötü niyetli veri bulunması durumunda temizleme zor olabilir.

#### Güvenli Veri İşleme

Birçok web uygulaması güvenlik açığı, kullanıcı verilerinin güvensiz işlenmesinden kaynaklanır. Güvenlik açıkları, girdinin kendisini doğrulamak yerine, üzerinde yapılan işlemleri güvenli hale getirerek önlenebilir. Güvenli programlama yöntemleri, örneğin SQL enjeksiyon saldırılarını parametreli sorgular kullanarak engelleyebilir. Ayrıca, uygulamalar doğası gereği güvensiz işlemlerden kaçınacak şekilde tasarlanabilir. Bu yaklaşım her göreve uygulanamaz, ancak mümkün olduğunda, kötü niyetli girdileri işlemek için etkili bir yöntemdir.


#### Anlamsal Kontroller

Bazı güvenlik açıklarında, saldırganın sağladığı girdi, normal kullanıcıların gönderebileceği verilerle aynıdır; kötü niyetli yapan şey, bu girdinin sunulduğu koşullardır. Örneğin, bir saldırgan gizli bir form alanındaki hesap numarasını değiştirerek başka bir kullanıcının hesabına erişmeye çalışabilir. Sözdizimsel doğrulama bu tür girdiler arasında ayrım yapamaz. Yetkisiz erişimi önlemek için, uygulama gönderilen verinin doğru kullanıcıya ait olduğunu doğrulamalıdır.

#### Sınır Doğrulama 

Sınır Doğrulaması, web uygulamalarının kullanıcıdan alınan güvensiz verileri işleme sorununu ele alır. İstemci tarafı doğrulaması performansı artırabilir ancak verinin güvenliğini garanti etmez. Sunucu tarafı uygulamanın, kötü niyetli girdilere karşı sağlam savunmalar gerektirdiği kritik bir güven sınırıdır. Geleneksel girdi doğrulaması, güvensiz veriler ile güvenilir uygulama arasında bir sınır olarak düşünülür. Ancak, bu basit görüş gerçek dünya zayıflıklarını değerlendirmekte yetersiz kalabilir.

- Çeşitli Saldırı Yöntemleri: Web uygulamaları, benzersiz olarak oluşturulmuş veriler kullanan geniş bir girdi tabanlı saldırı yelpazesine karşı savunma yapmak zorundadır. Dış sınırdaki tek bir mekanizma, tüm olası saldırıları koruyabilecek şekilde uygulanamaz.
- Karmaşık İşlem Zincirleri: Birçok uygulama işlevi, kullanıcı girdisinin birden çok dönüşüm geçirdiği ardışık işlemleri içerir. Dönüştürülen veriler, başlangıçtaki girdi ile hiçbir benzerlik taşımayabilir, bu da başlangıçta tüm potansiyel saldırı senaryolarını tahmin etmeyi ve doğrulamayı zorlaştırır.
- Çakışan Doğrulama İhtiyaçları: Farklı türde saldırılar (örneğin XSS ve command ınjection) çelişen doğrulama kontrolleri gerektirir. Uygulamanın dış sınırında tüm saldırı kategorilerini aynı anda önlemeye çalışmak bazen pratik veya imkansız olabilir.
- Daha etkili bir yaklaşım, her bir bileşenin veya işlevsel birimin, sunucu tarafı uygulamanın içindeki girdileri potansiyel olarak kötü niyetli olarak ele almasıdır. Doğrulama, her güven sınırında gerçekleşir - hem dış (istemci-sunucu) hem de iç (uygulama bileşenleri arasında). Bu model, dış sınırdaki doğrulamanın eksikliklerini ele alır:

- Bileşenlere Özgü Savunma: Her bileşen, karşılaşabileceği belirli zayıflıklara karşı girdileri doğrular ve doğrulama kriterlerini bileşenin bağlamına ve işleme gereksinimlerine göre adapte eder.
- Sürekli Doğrulama: Veri farklı uygulama bileşenlerinden geçerken, mevcut dönüşümler sonrası veri durumuna göre ardışık doğrulama kontrolleri gerçekleştirilir. Bu, işlenmiş verilerin bile güvenliğini sağlar.
- Çatışma Azaltma: Farklı aşamalarda uygulanan doğrulama kontrolleri birbirleriyle çakışma olasılığı düşüktür, bu da uygulama işlevselliğini bozmadan kapsamlı koruma sağlar.

Pratikte, sınır doğrulaması kullanıcı girdilerinin her işleme aşamasında doğrulanmasını içerir:

- Giriş Alımı: Verinin bütünlüğünü sağlamak ve bilinen saldırı imzalarını içermemesini doğrulamak için başlangıç doğrulaması.
- Veritabanı Etkileşimi: SQL enjeksiyonunu önlemek için sorguları oluşturmadan önce veri içindeki potansiyel zararlı karakterleri kaçırma.
- Harici Servis Etkileşimi: SOAP gibi protokollere özgü enjeksiyon saldırılarını önlemek için veriyi kodlama.
- Tarayıcıya Çıktı: Kullanıcı tarafından sağlanan içeriğin web sayfalarında gösterilmesi sırasında XSS saldırılarını önlemek için veriyi kodlama.

![[Pasted image 20241112210439.png]]Bu yaklaşım, Şekil’de gösterildiği gibi, uygulama işleme aşamalarının çeşitli safhalarında kötü niyetli girdilere karşı güçlü bir savunma sunarak hem veri bütünlüğünü hem de kullanıcı güvenliğini sağlar.

Bu işlevsellikteki varyasyonların başka uygulama bileşenlerine veri aktarımını içermesi durumunda, ilgili güven sınırlarında benzer savunmaların uygulanması gerekecektir. Örneğin, başarısız bir oturum açma işlemi uygulamanın kullanıcıya bir uyarı e-postası göndermesine neden oluyorsa, e-postaya dahil edilen tüm kullanıcı verilerinin SMTP enjeksiyon saldırılarına karşı kontrol edilmesi gerekebilir.