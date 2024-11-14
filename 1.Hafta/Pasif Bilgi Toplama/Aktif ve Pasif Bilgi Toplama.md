**Bilgi Toplama Süreçleri Nelerdir ?**

**_Bilgi toplama süreci, sızma testi veya güvenlik değerlendirmesi için en kritik adımlardan biridir._** Bu aşamada, hedef sistem hakkında mümkün olduğunca fazla bilgi toplamak, güvenlik açıklarını keşfetmek ve daha sonraki adımları planlamak için gereken temel verileri elde etmek amacıyla çeşitli yöntemler kullanılır. Bilgi toplama süreçleri genel olarak iki ana başlık altında toplanabilir:

**1. Pasif Bilgi Toplama**

**_Pasif bilgi toplama, hedef sistemle doğrudan etkileşime girmeden gerçekleştirilen bilgi toplama yöntemlerini ifade eder._** Bu yöntemler, hedef hakkında dışarıdan toplanan verileri içerir. Genellikle daha az risklidir çünkü hedef sistemin farkına varılmadan bilgi edinilir.

**Pasif bilgi toplama yöntemleri:**

- **Açık Kaynak Araştırması (OSINT):** İnternet üzerindeki açık kaynaklardan bilgi toplamak. Bu, web siteleri, sosyal medya, forumlar, bloglar ve veri tabanları gibi kaynaklardan bilgi edinmeyi içerir.
- **WHOIS Sorgulamaları:** Hedefin alan adı kaydı hakkında bilgi toplamak için WHOIS veritabanlarını kullanmak. Bu, alan adının sahibi, iletişim bilgileri ve kayıt tarihi gibi bilgileri sağlar.
- **Google Dorking:** Hedef sistemle ilgili özel arama terimleri kullanarak, hedefin web sayfalarında yer alan bilgileri bulmak için Google aramalarını kullanmak.
- **Sosyal Mühendislik:** Hedef sistemin çalışanları hakkında bilgi toplamak için sosyal mühendislik teknikleri kullanmak. Örneğin, LinkedIn üzerinden çalışanların profillerini incelemek.
- **Hedefin Web Sitesi İncelemesi:** Hedefin web sitesi üzerinde gezinerek, kullanılan teknolojiler, uygulama yapısı ve sunucu bilgileri gibi detayları incelemek.

**2. Aktif Bilgi Toplama**

**_Aktif bilgi toplama, hedef sistemle doğrudan etkileşime girerek bilgi edinme sürecidir_**. Bu yöntemler, **_genellikle daha fazla risk taşır_** çünkü hedef sistem, yapılan sorguları ve taramaları fark edebilir.

**Aktif bilgi toplama yöntemleri:**

- **Port Taraması:** Hedef sistemde açık olan portları tespit etmek için araçlar (örneğin Nmap) kullanmak. Bu, hangi hizmetlerin çalıştığını ve hangi protokollerin kullanıldığını anlamaya yardımcı olur.
- **Hizmet Taraması:** Açık portlarda hangi hizmetlerin çalıştığını ve hangi versiyonlarının kullanıldığını belirlemek için tarama yapmak. Bu, zafiyet taramasında önemli bir adımdır.
- **Ağ Taraması:** Hedef ağın yapısını anlamak için IP adresleri, alt ağlar ve yönlendirme bilgileri gibi verileri toplamak.
- **Web Uygulama Taraması:** Hedef web uygulamasındaki potansiyel güvenlik açıklarını (örneğin SQL injection, XSS) belirlemek için araçlar (örneğin Burp Suite, OWASP ZAP) kullanmak.
- **DNS Sorgulamaları:** Hedefin DNS kayıtlarını inceleyerek IP adresleri, subdomainler ve diğer bilgileri toplamak. Bu, özellikle subdomain keşfi için önemlidir.

**Bilgi Toplama Sürecinin Önemi**

- **Hedefi Anlamak:** Bilgi toplama, hedef sistemin mimarisi, teknolojileri ve olası zayıflıkları hakkında derinlemesine bir anlayış kazandırır. Bu bilgi, testin sonraki aşamaları için strateji geliştirmede kritik öneme sahiptir.
- **Risk Analizi:** Toplanan bilgiler, hedef sistemdeki potansiyel güvenlik açıklarını belirlemek için kullanılır. Bu, güvenlik ekiplerine daha hedefli bir değerlendirme yapma imkanı tanır.
- **Sızma Testi Planlaması:** Bilgi toplama sürecinde elde edilen veriler, sızma testinin nasıl gerçekleştirileceğine dair bir plan oluşturmak için temel oluşturur. Hangi araçların ve tekniklerin kullanılacağı bu aşamada belirlenir.