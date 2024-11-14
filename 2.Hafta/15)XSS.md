
#### Cross-Site Scripting Nedir ?

XSS zafiyetinde , web sitesi üzerinde JavaScript kullanılarak kullanıcının tarayıcısında çalışacak şekilde kötü niyetli scriptlerin enjekte edilmesine olanak tanır. XSS saldırıları, genellikle bir web uygulamasında kullanıcıların girdileriyle etkileşimli alanlarda gerçekleşir.  
  

XSS zafiyetinin temel amacı, kullanıcıların tarayıcısında kötü niyetli komutların çalışmasını sağlamaktadır. Bu sayede saldırgan, kullanıcıların oturum bilgilerini çalabilir, kimlik avı (phising) saldırıları gerçekleştirebilir, zararlı bağlantıları yayabilir veya kullanıcının tarayıcısını kontrol edilebilir.

##### XSS Türleri Nelerdir ?

XSS çeşitli şekillerde gerçekleştirebilir, ancak genellikle iki temel kategoriye ayrılır: Stored XSS ve Reflected XSS fakat bunların haricinde DOM Based XSS ve Blind XSS türleride vardır .

1.       **Reflected XSS** : Kötü niyetli scriptler, kullanıcının tarayıcısına özel bir URL veya form girişi gibi geçici verilerle birlikte gönderilir. Bu tür saldırılar, kullanıcının girdilerini doğrudan geri yansıtan uygulama alanlarını hedefler.

**Örnek Senaryo**

Bir e-ticaret sitesinde, kullanıcıların ürünleri aramak için bir arama kutusu bulunmaktadır. Arama sonuçları sayfasında, kullanıcı tarafından girilen arama terimi, sorguyu göstermek için geri yansıtılır. Ancak, site arama terimini filtrelemeden veya kaçış işlemi yapmadan doğrudan sayfaya dahil etmektedir.
![[Pasted image 20241113003818.png]]

2.      **Stored XSS** : Bu zafiyet türü , kötü niyetli scriptler, web uygulamasının veri tabanına veya depolama alanına kaydedilir ve sonrasında kullanıcıların tarayıcılarına aktarılır. Bu tür saldırılar, kullanıcıların etkileşime girdiği alanlarda depolanan verileri hedefler.

**Örnek Senaryo**

Bir forum sitesi kullanıcıların yorumlarını veri tabanında veya farklı bir depolamada kaynağına kayıt eder ancak yorumlar javascript veya kötü amaçlı kod var mı diye kontrol edilmez ise bu kod veri tabanına veya depolama alanına kayıt edilir. Böylelikle herhangi bir kullanıcı o sayfayı her gördüğünde kötü amaçlı kod çalışacak böylelikle Stored XSS zafiyeti gerçekleşmiş olur.

![[Pasted image 20241113003827.png]]

3.      **DOM Based XSS** : DOM , document object model kısaltılmasıdır. Dom Based XSS, yeni sayfaların yüklenmediği veya verilerin sunucu tarafı koduna gönderilmediği durumlarda Javascript’in doğrudan tarayıcıda çalıştığı bir saldırı türüdür. Kötü niyetli saldırgan, web uygulamasının JavaScript kodunun kullanıcıdan gelen verileri doğrudan işlediği yerellerde bir güvenlik açığı bulur ve bunu istismar eder. Saldırgan, kötü niyetli kodları kullanıcının tarayıcısında çalıştırmak için DOM’u manipüle eder.

Örneğin, bir web uygulaması kullanıcının girişini doğrudan bir HTML  elementine ekliyorsa ve bu verileri işlemek için JavaScript kullanıyorsa, saldırgan kötü niyetli bir girişle birlikte kötü niyetli bir Javascript kodunu enjekte edebilir. Kullanıcı sayfayı görüntülediğinde, saldırganın enjekte ettiği kod doğrudan tarayıcıda çalışır.

**Örnek Senaryo** 

Web sitesinin Javascript’i, içeriği windows.location.hash parametresinden içeriği alır ve ardından bunu sayfanın o anda görüntülenen bölümüne yazar. Saldırgan, hash parametresini kötü niyetli bir JavaScript koduyla değiştirerek web sayfasına zararlı kodu enjekte edebilir. Kullanıcılar sayfayı ziyaret ettiğinde, tarayıcı bu zararlı kodu çalıştırır ve saldırganının amaçladığı eylemleri gerçekleştirir.

DOM Tabanlı XXS’i test etmek zor olabilir ve kaynak kodunu okumak için belirli bir miktarda JavaScript bilgisi gerektirir “Windows.location.x” parametreleri gibi bir saldırganın kontrol edebileceği belirli değişkenlere erişen kod bölümlerini aramak gerekir.

Bu kod parçalarını bulduğunuzda, bunların nasıl ele alındığını ve değerlerin web sayfasının DOM’a yazılıp yazılmadığını veya eval() gibi güvenli olmayan JavaScript yöntemlerine aktarılıp aktarılmadığını görmek gerekebilir.

4.      **Blind XSS** : Saldırganın web uygulamasında bulunan bir güvenlik açığından yararlanarak kötü niyetli Javascript kodunu enjekte ettiği, ancak sonucun doğrudan kullanıcıya gösterilmediği bir Cross-Site Scripting saldırı türüdür.

Blind XSS saldırıları, saldırganın enjekte etiği kötü niyetli kodun sonucunu görmek veya doğrulamak için bir geri bildirim mekanizmasına sahip olmadığı durumlarda gerçekleşir. Bu durum, saldırganın saldırının etkinliğini doğrudan kullanıcı arayüzünden gözlemlemesini engeller.

Blind XSS genellikle şu senaryolarla ilişkilendirilir:

1.       Stored  XSS: Web uygulaması, kullanıcı girişlerini veri tabanında depoladığı veya kalıcı olarak sakladığı durumlarda saldırı gerçekleşebilir. Saldırgan, güvenlik açığı olan bir alan aracılığıyla kötü niyetli kodu enjekte eder, ancak bu kodun sonucu hedef kullanıcıya gösterilmez.

2.      Reflected  XSS: Web uygulaması, kullanıcı tarafından sağlanan verileri doğrudan URL veya form parametreleri gibi girişlerde yansıtıyorsa, saldırgan yoluyla kötü niyetli kodu enjekte edebilir. Ancak, saldırgan, enjekte ettiği kodun sonucunu doğrudan gözlemleyemez.

Örnek Senaryo

Bir web sitesinde yardım bölümünden çalışan personele ulaşabiliriz.  İleti içeriğine saldırganının istediği herhangi bir şeyi girmesine izin verilir ise bu mesajlar daha sonra personelin özel bir portalında görüntülenir ise saldırgan istediği veriye ulaşabilir.


Çözüm : HTML Escape