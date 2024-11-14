#### Server Side Request Forgery Nedir ?

Sunucu yanlış yapılandırılmış olduğunda, sunucunun iç ağ kaynaklarına doğrudan erişim sağlamasına ve kaynakların sömürülmesine izin veren güvenlik açığıdır. Bu saldırı türü, web uygulamalarının genellikle harici kaynaklara erişmesi için kullanılan özellikleri kötüye kullanır. HTTP sunucuları kendi aralarında istekler oluşturur. Bu istekler uzak kaynakları almak, meta verileri almak veya diğer web uygulamalarıyla iletişim kurmak için kullanılır. Tam olarak SSRF, saldırganın savunmasız bir web sunucusu aracılığıyla başka bir sisteme kötü amaçlı istekler göndermesine olanak sağlar.

##### Çalışma mantığı

1)Ürünlerini API aracılığıyla alan bir web sitemizin olduğunu varsayalım ;

``http://example.com/stock?url=http://example.com/api/stock/item?id=123``

Saldırgan, belli araçlar ile sunucunun başka bir uygulamaya yaptığı isteği belli araçlar ile sunucu-api arasına girebilir. Böylelikle isteği değiştirerek kötü amaçlı

olarak kullanabilir.

Saldırının gerçekleştirilmesi için kullanılan çeşitli yöntemler vardır. Bunlar arasında URL parametreleri, form verileri, kullanıcı tarafından kontrol edilen verilerin yanıtlarını içeren XML veya JSON belgeleri, içe aktarılan dosyalar veya diğer ağ istemleri gibi yöntemler alır.

URL adresimize baktığımızda ürünleri api.example.com aracılığıyla aldığını görüyoruz . Saldırgan bu isteği …/api/user olarak değiştirdiğinde eğer yapılandırma yoksa saldırgana user bilgileri döndürülecek.

2: Hava durumu web uygulamasının bilgileri bir api aracılığıyla aldığını düşünelim :

weatherApi =http://data.weatherapp.com:8080/meterology/forecasts/check%3FcurrentDateTime%3D6%26cityId%3D1

Saldırgan bunu aşağıdakilere değiştirebilir:

weatherApi = http://localhost/admin

POST isteğine baktığımızda web server ile api arasında bir iletişimin olduğunu görüyoruz. Saldırganımız bu iletişim arasına girerek :

http://data.weatherapp.com:8080/meterology/forecasts/check%3FcurrentDateTime%3D6%26cityId%3D1

Bu istek yolunu :

http://localhost/admin

Bu şekilde değiştiriyor ve yapılandırma yok ise saldırgana admin klasörünün görüntülenmesine neden olur .