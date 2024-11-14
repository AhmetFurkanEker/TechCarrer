
Günümüzde teknolojinin hızlı gelişimiyle internet kullanımı çok fazla artı. Bu gelişim web uygulamalarının dinamik ve kompleks yapılara dönmesine sebep oldu. Bu dinamizm de her kullanıcı için benzer türdeki verileri ve içerikleri ayrıştırarak sunma ihtiyacı gelişmiştir. Uygulamalar, kullanıcılarına içeriklerini daha verimli kullandırabilmek için “şablonlar (templates)” kullanmaya başlamıştır. Şablonlarda kullanılan özelliklerin manipülasyonu sonucunda Server Sıde Template Injection zafiyeti oluşmuştur.

Resim 1![[Pasted image 20241113010537.png]]

 Resim 1‘de görüldüğü gibi kullanıcı web uygulamasına ilk olarak HTTP Request  isteği gönderir web uygulaması dinamik verileri web sayfalarına yerleştiren sonuçların üretilmesi için şablonları bir veri modeliyle birleştirir. MVC ( Model View Controller) sisteminde 3 katman vardır bunlar : Model, View ve Controller. Her katmanın kendisine özgü görevleri vardır. Model, veri işleme ve depolama işlemlerini yönetir ve veri tabanıyla iletişim kurar verileri işler ve gerektiğinde Controller ile iletişim halinde olur. View, Kullanıcı arayüzünü oluşturur. HTML, CSS ve bazen de şablonlama dilini kullanarak sunum katmanını temsil eder. Verileri model ’den alır ve kullanıcıya gösterir. Controller, kullanıcının etkileşimlerini yönetir. Kullanıcının isteklerini alır, Model’e veri işleme taleplerinde bulunur ve sonuçları view’e ileterek kullanıcıya geri dönderir. Bu süreçler kullanıcı isteği ile başlar Controller à Model à Controller à View à Çıktı ile sonlanmaktadır.

Tüm bilgileri ele aldığımızda Server Sıde Template Injection zafiyetinin oluşumu için Server Sıde Rendering olması gerekmektedir. Web sayfasını görüntülemek isteyen kullanıcılar sunucuya bir istek gönderir. Bu isteğin sunucu tarafında işlendiği ve çıktının tarayıcıya iletildiği yönteme Server Sıde Rendering olarak adlandırılır. Tarayıcının yapacağı işlemin sunucu tarafında yapılması olarak da ifade edilebilir.

Günümüzde en çok kullanılan şablon motorları ;

1.    PHP : Smarty, Twigs

2.    Java : Velocity, Freemaker

3.    Python : JINJA, Mako, Tornado

4.    JavaScript : Jade, Rage

5.    Ruby : Liquid 

SSTI sonucu oluşan güvenlik açıkları genellikle kritiktir ve back-end sunucusunun tüm kontrolünü ele geçirerek uzaktan kod yürütülmesine neden olur. Kod yürütülmese de, saldırgan sunucuda bulunan hassas verileri elde edebilir. Kullanılan şablon motoruna göre ise barındırılan SSTI zafiyeti her zaman kritik olmayabilir ancak tüm zafiyeteler her zaman etkisi minimalize edilmesi güvenlik açısından önemlidir.

**Güvenlik Açığının Tespiti**

SSTI güvenlik açıklarını belirlemek için, şablonlarda sık sık tercih edilen özel karakterlerden oluşan Polyglot yükü kullanılır. Bir güvenlik zafiyeti durumunda, bir hata mesajı dönebilir veya sunucu tarafından istisna oluşturabilir.

Güvenlik zafiyetini belirlemek için:

1.    Şablon kaynağının (değişkenliğin) nerede olduğunun bulunması.
![[Pasted image 20241113010549.png]]

2.    Kullanılan şablon motorunun tanımlanması.

Kullanılan şablonun tespit edilebilmesi için Port Swigger tarafından yayınlan bir yol haritası vardır. Bu yol haritası sayesinde XSS ve SSTI zafiyetlerinin karışmasının önüne geçilebilir ancak XSS zafiyetini gördüğümüz yerler potansiyel template ınjection barındırmaktadır..

**İstismar**

Tespit ve tanımlama adımlarından sonra uygulamamız gereken işlem erişilebilen belgelerin okunmasıdır. Neye sahip olduğumuzu tam olarak öğrenmek için çevreyi keşfetmemiz gerekiyor. Şablon tarafından sağlanan varsayılan nesneleri ve geliştiricinin şablona aktardığı uygulamaya özgü nesneleri bulmaya çalışılmalıdır. Değişken adlarını bulmakta zorluk çekildiği takdirde FuzzDB, Burp Intruder’ın sözcük listesi, PHP projelerinde kullanılan GET/POST  değişken adlarını ve GitHub’ı tarayarak bu konu özelinde word listler bulunabilir.