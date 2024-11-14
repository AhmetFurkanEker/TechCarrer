### Sızma Testi Nedir ? 

Sızma testi (penetrasyon testi), bir sistemin güvenlik açıklarını tespit etmek amacıyla yapılan kontrollü saldırı simülasyonudur. Bu test, bir saldırganın kullanabileceği zayıflıkları ortaya çıkararak sistemin savunma mekanizmalarını güçlendirmeyi hedefler.

**Sızma Testi Alanları Nelerdir ?**

1.        Ağ altyapıları
2.        Web Uygulamaları
3.        Mobil Uygulamalar
4.        Kablosuz Ağlar
5.        Sosyal Mühendislik
6.        Cloud

gibi bir çok alanda sızma testleri gerçekleştirilir.

### Sızma Testi Etiği Nedir?

Sızma testi, tıpkı bir evin kapılarını, pencerelerini kontrol ederek hırsız girebilir mi diye bakmak gibi. Ancak burada ev sahibinin izni var. Yani bir güvenlik uzmanı, bir şirketin sistemine izinsiz girip zarar vermek yerine, onların izin verdiği ölçüde güvenlik açıklarını bulmaya çalışır. Bu şekilde güvenlik açıkları keşfedilip düzeltilir.

Sızma testi yaparken dikkat edilmesi gereken **etik kurallar** şunlardır:

1. **İzin almak**: Bir sisteme veya ağa saldırmadan önce mutlaka sistem sahibinden yazılı izin alınır. Aksi takdirde bu, yasa dışı bir saldırı olur.
2. **Sadece izin verilen alanları test etmek**: Sadece sistem sahibinin izin verdiği bölümler üzerinde test yapılır. İzin verilen alanların dışına çıkmak, etik dışı ve yasadışıdır.
3. **Zarar vermemek**: Sistemi test ederken, istemeden bile olsa sisteme zarar vermemek için çok dikkatli olunur. Amaç sistemi korumak, ona zarar vermek değil.
4. **Gizlilik**: Sızma testi sırasında bulunan açıklar ve hassas bilgiler gizli tutulur. Testi yapan kişi, bulduğu bilgileri yalnızca sistem sahibine bildirir, üçüncü kişilerle paylaşmaz.
5. **Düzeltici adımlar önerme**: Sadece açıkları bulmakla kalmaz, aynı zamanda bu açıkları nasıl düzeltecekleri konusunda sistem sahiplerine yardımcı olunur.

Sonuç olarak, sızma testi yaparken güvenlik uzmanları, izin alarak, zarar vermeyerek ve dürüst bir şekilde çalışarak hem sistem sahiplerini korur hem de etik dışı davranışlardan kaçınmış olur.

### Sızma Testi Metodolojisi Nedir ?

Sızma testi metodolojisi, bir sistemdeki güvenlik açıklarını bulmak ve bu açıkları sömürerek sistemin ne kadar güvenli olduğunu test etmek için kullanılan adım adım süreçtir. Bu metodoloji, bir saldırganın nasıl düşündüğünü ve hareket ettiğini anlamaya dayanır, ancak etik çerçevede yapılır.

Genellikle sızma testi şu adımlarla gerçekleştirilir:

**1. Bilgi Toplama (Reconnaissance)**

Bu aşamada, hedef sistem hakkında mümkün olduğunca çok bilgi toplanır. Amaç, sistemin nasıl çalıştığını, kullanılan teknolojileri, ağ yapısını ve olası güvenlik açıklarını anlamaktır. Bilgi toplama iki şekilde yapılır:

- **Pasif Bilgi Toplama:** Sistemle doğrudan etkileşime girmeden, internet üzerindeki açık kaynaklardan bilgi toplama (örneğin, Google aramaları, sosyal medya, WHOIS sorgulamaları).
- **Aktif Bilgi Toplama:** Sisteme ping atmak, port taraması yapmak veya belirli hizmetlerle etkileşime girerek daha derinlemesine bilgi toplamak.

**2. Taramalar (Scanning)**

Bu aşamada, sistemdeki açıkları tespit etmek için farklı araçlar kullanılarak taramalar yapılır. Amaç, hedef sistemde hangi portların açık olduğunu, hangi hizmetlerin çalıştığını ve hangi versiyonların kullanıldığını bulmaktır. İki tür tarama yapılabilir:

- **Ağ Taraması:** Açık portlar ve çalışan hizmetler bulunur.
- **Zafiyet Taraması:** Sistem veya yazılımlar üzerinde bilinen güvenlik açıkları aranır.

**3. Zafiyet Analizi (Vulnerability Analysis)**

Bu aşamada, elde edilen bilgiler ışığında hangi zafiyetlerin gerçekten sömürülebilir olduğuna karar verilir. Yani hangi açıkların sistem için ciddi bir tehdit oluşturabileceği değerlendirilir. Tespit edilen zafiyetlerin önem derecesi, sistemin güvenliği üzerindeki etkileri incelenir.

**4. Sisteme Sızma (Exploitation)**

Bu aşama, bir siber saldırgan gibi davranarak sistemdeki güvenlik açıklarını kullanıp sisteme yetkisiz bir şekilde girmeye çalışmayı içerir. Amaç, sistemin nasıl ele geçirilebileceğini göstermek ve bu açıkları gerçek saldırganlar kullanmadan önce düzeltmektir. Bu adımda zarar vermemek çok önemlidir.

**5. Yetki Yükseltme (Privilege Escalation)**

Eğer sızma başarılı olursa, elde edilen yetkiler artırılmaya çalışılır. Bu, bir saldırganın sistemde en yüksek yetkileri elde ederek daha fazla zarar verebilmesine olanak sağlar. Test sırasında sızma testi uzmanı, bir kullanıcı olarak başladığı erişimle ne kadar ilerleyebileceğini ve ne tür verilere erişebileceğini gösterir.

**6. Erişimin Korunması (Maintaining Access)**

Bu adımda, sisteme giriş sağlandıktan sonra bu erişimin nasıl sürdürülebileceği üzerine çalışmalar yapılır. Saldırganların sistemde sürekli bir erişim sağlamak için kullanabileceği arka kapılar veya zararlı yazılımlar test edilir. Bu adım, güvenlik ekiplerine sistemde kalıcı bir tehdit oluşturabilecek yöntemleri anlatmak içindir.

**7. İzlerin Silinmesi (Covering Tracks)**

Bir saldırgan, sistemdeki izlerini silerek güvenlik ekiplerinin sızma girişimini fark etmesini zorlaştırabilir. Bu aşamada, sızma testi uzmanı, sisteme erişim sağladıktan sonra nasıl iz bırakılmadan çıkılabileceğini gösterir. Ancak etik kurallar gereği, sistem sahibi bu adımda bilgilendirilir.

**8. Raporlama**

Son aşamada, tüm test süreçleri ve sonuçları detaylı bir rapor halinde sistem sahibine sunulur. Bu raporda:

- Hangi açıkların bulunduğu,
- Bu açıkların sistem üzerindeki etkileri,
- Nasıl istismar edildikleri ve olası sonuçları,
- Bu açıkların nasıl kapatılabileceği detaylı bir şekilde açıklanır.

**9. Düzeltme ve Yeniden Test**

Test sırasında bulunan zafiyetlerin düzeltilmesinden sonra, aynı test süreçleri tekrar uygulanarak sistemin güvenlik durumunun iyileştirilip iyileştirilmediği kontrol edilir.

### Cyber Kill Chain 

![[cyberkillchain.png]]

**Cyber Kill Chain**, Lockheed Martin tarafından geliştirilen bir siber saldırı sürecini açıklayan bir modeldir. Bu model, saldırıların tipik aşamalarını ve her aşamada saldırganların ne yaptığını anlamaya yardımcı olur. Savunmacıların bu zinciri anlayarak, saldırıların hangi aşamasında müdahale edebileceklerini belirlemeleri mümkündür. Aşamalar şu şekildedir:

#### 1. **Keşif (Reconnaissance)**

**Bu aşamada saldırganlar, hedeflerini belirlemek ve saldırı için bilgi toplamak amacıyla araştırmalar yapar.**

- **Örnek:** Bir siber saldırgan, hedef şirketin web sitesini, sosyal medya hesaplarını ve diğer açık kaynak bilgilerini araştırır. Bu araştırma sırasında hedef şirkette hangi çalışanların IT yöneticisi olduğunu ve hangi sistemlerin kullanıldığını öğrenmeye çalışır.

#### 2. **Silahlanma (Weaponization)**

**Saldırganlar, topladıkları bilgileri kullanarak hedef sistemlere zarar verebilecek zararlı yazılımlar (malware) oluştururlar.**

- **Örnek:** Saldırgan, hedef şirketin PDF dosyalarını açtığını fark eder ve bir PDF dosyasına zararlı yazılım (malware) ekler. Bu yazılım, açıldığında saldırgana şirket ağına erişim sağlar.

#### 3. **Teslimat (Delivery)**

**Zararlı yazılım, hedefe iletilir. Bu aşama, saldırının başlamasıdır.**

- **Örnek:** Saldırgan, zararlı yazılım içeren PDF dosyasını hedef şirketteki bir çalışanına e-posta ile gönderir. E-posta, gerçek bir müşteriden geliyor gibi görünmektedir.

#### 4. **Sömürme (Exploitation)**

**Teslim edilen zararlı yazılım hedef sistemde çalıştırılır ve saldırgan, sistemdeki bir güvenlik açığını kullanarak sistemin kontrolünü ele geçirir.**

- **Örnek:** Çalışan, zararlı PDF dosyasını açar. Dosya açıldığında, bilgisayarda bulunan bir güvenlik açığı kullanılarak saldırganın bilgisayara erişimi sağlanır.

#### 5. **Yükleme (Installation)**

**Zararlı yazılım, hedef sisteme kalıcı olarak yerleştirilir. Saldırganlar, bu aşamada geri kapı (backdoor) veya uzaktan erişim araçları (RAT) gibi yazılımlar kullanarak sürekli erişim sağlamayı hedefler.**

- **Örnek:** Zararlı yazılım, çalışan bilgisayarına bir "backdoor" kurar ve saldırgan artık çalışan bilgisayarına istediği zaman uzaktan erişebilir hale gelir.

#### 6. **Komuta ve Kontrol (Command and Control - C2)**

**Saldırgan, hedef sistem üzerinde tam kontrol sağlayabilmek için uzaktan erişim yollarını etkinleştirir. Bu sayede, saldırgan sistemde kalıcı olarak kalabilir ve yönlendirmeler yapabilir.**

- **Örnek:** Saldırgan, çalışan bilgisayarına bağlanır ve ağa sızmak için komutlar gönderir. Artık bu bilgisayar üzerinden şirket ağına girebilir ve sistemde istediği işlemleri gerçekleştirebilir.

#### 7. **Hedefteki Amaç (Actions on Objectives)**

**Saldırının son aşaması, saldırganın hedeflediği asıl amacı gerçekleştirmesidir. Bu, veri hırsızlığı, sistemlere zarar verme ya da casusluk olabilir.**

- **Örnek:** Saldırgan, şirketteki önemli dosyaları çalar, kritik sistemleri sabote eder ya da fidye yazılımı ile sistemleri kilitler ve fidye talep eder.



### Sızma Testi Türleri Nelerdir ?

**Black Box, Gray Box ve White Box** sızma testleri, bir sistemin güvenlik açıklarını belirlemek için kullanılan farklı test türleridir. Bu testler, test sırasında güvenlik uzmanının sisteme ne kadar bilgiyle başladığına göre sınıflandırılır.

#### 1. Black Box Sızma Testi (Kara Kutu)

- **Tanım**: Black Box sızma testinde, test uzmanı sisteme dair hiçbir bilgiye sahip değildir. Bir dış saldırgan gibi davranarak, sisteme dışarıdan saldırılar düzenler.
- **Amaç**: Dışarıdan bir saldırganın sistem hakkında herhangi bir bilgiye sahip olmadan yapabileceği saldırıların simüle edilmesidir.
- **Bilgi Düzeyi**: Test yapan kişi, hedef sistem hakkında **sıfır bilgi** ile başlar. Kullanılan teknolojiler, ağ yapısı veya güvenlik önlemleri hakkında önceden bilgi yoktur.
- **Avantajlar**: Gerçek bir dış saldırganın yapacağı gibi, sistemin güvenlik açıklarını minimum bilgi ile bulmayı hedefler.
- **Dezavantajlar**: Daha fazla zaman alabilir ve bazı içsel zayıflıklar (örneğin, uygulama mantığı hataları) tespit edilemeyebilir.

#### 2.Gray Box Sızma Testi (Gri Kutu)

- **Tanım**: Gray Box sızma testinde, test uzmanı sisteme dair sınırlı bilgiye sahiptir. Örneğin, bazı dahili yapılandırma bilgileri, kullanıcı erişimleri veya ağ diyagramları gibi bilgilere erişebilir.
- **Amaç**: Hem dış hem de iç saldırganın ne tür tehditler oluşturabileceğini değerlendirmek ve daha hedefli bir test yapmak.
- **Bilgi Düzeyi**: Test yapan kişi, sisteme dair **sınırlı bilgi** ile başlar. Genellikle sistemdeki bazı kullanıcı rolleri veya dahili süreçler hakkında bilgiye sahiptir, ancak tüm sisteme dair tam bilgi yoktur.
- **Avantajlar**: Hem dış hem de iç tehditleri test edebilme imkanı verir. Testler daha hedefli olabilir ve daha fazla zafiyet tespit edilebilir.
- **Dezavantajlar**: Testin kapsamı sınırlı olabilir ve tüm sistemdeki açıkları ortaya çıkaramayabilir.

#### 3.White Box Sızma Testi (Beyaz Kutu)

- **Tanım**: White Box sızma testinde, test uzmanı sisteme dair tam bilgiye sahiptir. Kaynak kodu, ağ yapısı, kullanıcı erişimleri ve kullanılan güvenlik önlemleri gibi tüm detaylar test uzmanına sağlanır.
- **Amaç**: Sistemdeki en derin zafiyetleri bulmak, iç güvenliği test etmek ve en kapsamlı güvenlik incelemesini yapmaktır.
- **Bilgi Düzeyi**: Test yapan kişi, sistem hakkında **tam bilgi** ile başlar. Bu, hem kaynak kodu hem de sistem yapılandırmaları anlamına gelir.
- **Avantajlar**: En kapsamlı test türüdür, sistemdeki tüm potansiyel güvenlik açıklarını ortaya çıkarabilir.
- **Dezavantajlar**: Genellikle daha fazla zaman ve kaynak gerektirir, aynı zamanda sisteme dair daha fazla bilgi gerektiğinden daha karmaşık bir süreç olabilir.




