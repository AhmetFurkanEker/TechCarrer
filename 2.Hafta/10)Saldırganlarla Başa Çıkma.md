
Uygulama tasarımında güvenliğin önemi vurgulanırken, uygulamanın doğrudan hedef alınabileceği ve bu tür saldırılara karşı hazırlıklı olunması gerektiği belirtilir. Güvenlik mekanizmaları, saldırıları kontrol altında tutmak ve uygun tepkiler vermek için tasarlanmıştır. Bu mekanizmalar, saldırganları engellemeyi ve saldırıların içeriği hakkında bilgi sağlamayı amaçlayan savunma ve saldırı önlemlerinin bir kombinasyonunu içerir. Genel olarak, saldırganları yönetmek için çeşitli görevler uygulanır.

- Hata Yönetimi (Handling errors): Bilgi sızdırmayı önlemek ve beklenmeyen davranışların güvenliği tehlikeye atmasını engellemek için etkili hata yönetimi mekanizmaları önemlidir.
- Denetim Kayıtlarını Sürdürme(Maintaining audit logs): Uygulama etkinlikleri ve güvenlik olaylarıyla ilgili detaylı kayıtlar tutmak, saldırıların doğası ve boyutunu anlamada ve yasal düzenlemelerle uyum sağlamada yardımcı olur.
- Yöneticilere Uyarı Gönderme(Alerting administrators): Şüpheli faaliyetler veya ihlaller hakkında yöneticilere veya güvenlik ekiplerine hızlı uyarılar göndermek, hızlı bir şekilde soruşturma yapılmasını ve önlem alınmasını sağlar.
- Saldırılara Tepki Verme(Reacting to attacks): IP adreslerini geçici olarak engelleme, oturumları sonlandırma veya olay yanıt prosedürlerini devreye sokma gibi saldırılara karşı proaktif önlemler, zararın en aza indirgenmesine ve normal işleyişin hızla yeniden sağlanmasına yardımcı olur.

#### Hata Yönetimi 

Uygulama geliştiricileri kullanıcı girişlerini doğrulamada dikkatli olsa da, beklenmedik hatalar kaçınılmaz olabilir. Bu hatalar genellikle işlevsellik ve kullanıcı kabul testleri sırasında tespit edilir ve üretim ortamına dağıtılmadan önce ele alınır. Ancak, kötü niyetli kullanıcıların uygulama ile etkileşimde bulunabileceği tüm yolları tahmin etmek zordur, bu nedenle saldırılar sırasında ek hatalar oluşabilir.

Bir ana savunma mekanizması, uygulamanın beklenmedik hataları düzgün şekilde ele almasını ve kullanıcıya uygun bir hata mesajı sunmasını sağlamaktır. Üretim ortamında, sistem mesajları veya hata ayıklama bilgileri kullanıcıya gösterilmemelidir çünkü bu bilgiler kötü niyetli kullanıcıların saldırılarını kolaylaştırabilir. Aşırı ayrıntılı hata mesajları, saldırganlara hassas bilgileri sağlamak ve veri çalmak için bir fırsat sunabilir.

![[Pasted image 20241112210946.png]]Çoğu web geliştirme dilinin, try-catch blokları ve kontrollü istisnalar aracılığıyla iyi bir hata işleme desteği sağladığını unutmamak gerekir. Uygulama kodu, belirli ve genel hataları yakalamak ve bunları uygun şekilde ele almak için bu yapıları yaygın bir şekilde kullanmalıdır. Ayrıca, çoğu uygulama sunucusunun uygulama tarafından ele alınmayan hataları özelleştirilmiş yollarla işlemek üzere yapılandırılabildiğini unutmamak gerekir, bu da belirsiz bir hata mesajı sunarak önlem alabilir.


Uygulama geliştiricileri kullanıcı girişlerini doğrulamada dikkatli olsa da, beklenmedik hatalar kaçınılmaz olabilir. Bu hatalar genellikle işlevsellik ve kullanıcı kabul testleri sırasında tespit edilir ve üretim ortamına dağıtılmadan önce ele alınır. Ancak, kötü niyetli kullanıcıların uygulama ile etkileşimde bulunabileceği tüm yolları tahmin etmek zordur, bu nedenle saldırılar sırasında ek hatalar oluşabilir.

Bir ana savunma mekanizması, uygulamanın beklenmedik hataları düzgün şekilde ele almasını ve kullanıcıya uygun bir hata mesajı sunmasını sağlamaktır. Üretim ortamında, sistem mesajları veya hata ayıklama bilgileri kullanıcıya gösterilmemelidir çünkü bu bilgiler kötü niyetli kullanıcıların saldırılarını kolaylaştırabilir. Aşırı ayrıntılı hata mesajları, saldırganlara hassas bilgileri sağlamak ve veri çalmak için bir fırsat sunabilir.


#### Denetim Kayıtlarını Sürdürme (Maintaining audit logs)

Uygulama geliştiricileri kullanıcı girişlerini doğrulamada dikkatli olsa da, beklenmedik hatalar kaçınılmaz olabilir. Bu hatalar genellikle işlevsellik ve kullanıcı kabul testleri sırasında tespit edilir ve üretim ortamına dağıtılmadan önce ele alınır. Ancak, kötü niyetli kullanıcıların uygulama ile etkileşimde bulunabileceği tüm yolları tahmin etmek zordur, bu nedenle saldırılar sırasında ek hatalar oluşabilir.

Etkili denetim günlükleri olayların zamanını, IP adresini ve kullanıcı bilgilerini kaydeder ve yetkisiz erişime karşı korunmalıdır. En iyi uygulama, denetim günlüklerini bağımsız bir sistemde saklamak ve bütünlüğü sağlamak için tek seferlik ortama atılmasını sağlamaktır. Kötü korunan denetim günlükleri, saldırganlar için hassas bilgilerin kaynağı olabilir ve oturum belirteçleri gibi bilgileri ifşa edebilir.

#### Yöneticilere Uyarı Gönderme (Alerting administrators):

Denetim günlükleri, saldırı girişimlerini geriye dönük olarak inceleme ve saldırgan hakkında yasal işlem başlatma imkanı tanır. Ancak, gerçek zamanlı yanıt vermek genellikle daha arzu edilir; yöneticiler saldırganın IP adresini veya kullanıcı hesabını engelleyebilir ve gerekirse uygulamayı çevrimdışı bırakabilir. Erken müdahale, başarılı sızmaların etkilerini hafifletebilir.

Uyarı mekanizmaları, gerçek saldırıları güvenilir bir şekilde rapor etmeli ve aşırı uyarı üretmeden bir denge sağlamalıdır. İyi bir uyarı mekanizması, çeşitli faktörleri kullanarak saldırıları teşhis edebilir ve ilgili olayları tek bir uyarıda toplayabilir. İzlenen anormal olaylar arasında IP adresinden gelen büyük sayıda istekler, olağandışı fon transferleri, bilinen saldırı dizeleri ve gizli verilerin değiştirildiği istekler yer alır.

Web uygulama güvenlik duvarları ve sızma tespit ürünleri, bu tür anormallikleri tanımlamada etkili olabilir, ancak genellikle genelleştirilmiş kurallarla sınırlıdır. Özellikle daha ince saldırı türlerini tespit etmek zor olabilir. En iyi sonuç için, gerçek zamanlı uyarı mekanizmalarının uygulamanın giriş doğrulama ve diğer kontrolleri ile entegre edilmesi önerilir. Bu entegrasyon, saldırıları tespit etmek ve etkili yanıt vermek için önemlidir.