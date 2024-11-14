
Web uygulamalarının güvenlik sorunları, kullanıcı girdilerinin güvenilmez olmasından kaynaklanır. Bu nedenle, uygulamalar saldırılara karşı çeşitli güvenlik mekanizmaları kullanır. Bu mekanizmalar, yetkisiz erişimi engeller, hatalı biçimlendirme ve istenmeyen girdileri filtreler, ve saldırganları engelleyici önlemler alır. Uygulamanın işlevselliğini ve güvenliğini korumak için kritik olan bu savunma mekanizmaları, uygulamaların büyük çoğunluğunu hedef alan saldırılara karşı koruma sağlar. Bir uygulamayı hacklemek için, bu mekanizmaları iyi anlamak ve zayıf noktalarını bulmak gerekir.


### Handling User Access (Kullanıcı Erişimini Yönetme) 

Uygulamaların temel güvenlik gereksinimi, kullanıcıların verilere ve işlevlere erişimini kontrol etmektir.Bu, farklı kullanıcı kategorileri (örneğin, anonim kullanıcılar, kayıtlı kullanıcılar, yöneticiler) ile sağlanır. Üç temel güvenlik mekanizması kullanılır: kimlik doğrulama, oturum yönetimi ve erişim kontrolü.Bu mekanizmalar birbirine bağımlıdır ve en zayıf halkaya kadar güçlüdürler. Herhangi bir bileşendeki kusur, saldırganların uygulamaya sınırsız erişim sağlamasına yol açabilir

#### Authentication

Kimlik doğrulama mekanizması, kullanıcının kimliğini doğrulama sürecini yönetir ve güvenlik açısından kritiktir.

Geleneksel olarak kullanıcı adı ve parola kullanılır, ancak ek kimlik bilgileri ve çok aşamalı oturum açma gibi yöntemlerle güvenlik artırılabilir. Ayrıca, hesap kurtarma ve parola değiştirme gibi işlevleri içerir. Ancak, tasarım ve uygulama hataları saldırganların bu mekanizmaları aşmasına olanak tanıyabilir. Bu nedenle, web uygulamalarına saldırırken kimlik doğrulama işlevlerine odaklanmak önemlidir.

#### Session management

Kullanıcı erişimi yönetimi, kimlik doğrulaması yapılan oturumların yönetimini içerir. Başarılı bir oturum açan kullanıcı, tarayıcısı aracılığıyla çeşitli sayfalara ve işlevlere istek gönderir. Uygulama, her kullanıcının isteklerini tanımlayıp işlemek için oturum belirteçlerini kullanır. Oturum, sunucuda kullanıcının durumunu takip eden bir veri yapısıdır ve belirteçler güvenli olmalıdır. Güvenlik açıkları, belirteçlerin oluşturulma ve ele alınma yöntemlerinden kaynaklanabilir. Saldırganlar, belirteçleri ele geçirerek diğer kullanıcıların oturumlarını kullanabilir. Bazı uygulamalar, her istek için ayrı kimlik doğrulaması yaparak kullanıcıları yeniden tanımlar.

#### Access Control

Erişim kontrolü, kullanıcıların izinlere göre verilere erişimini düzenler. Bu süreç, kullanıcı kimliğini doğrulayıp hangi izinlerin verileceğine karar vermeyi içerir. Kullanıcı rolleri, belirli ayrıcalıkları belirler ve sınırlı veri erişimi sağlar. Erişim kontrol hataları, güvenlik açıklarına neden olabilir. Geliştiriciler, hatalı varsayımlar yaparak veya dikkatsizlikle erişim kontrollerini atlayabilir. Bu nedenle, erişim kontrol testleri önemlidir ve güvenlik açıklarını tespit etmek için titiz bir test süreci gerektirir.