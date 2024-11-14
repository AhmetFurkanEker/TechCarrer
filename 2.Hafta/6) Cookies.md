
Çerezler, HTTP protokolünün önemli bir parçası olup web uygulamalarının güvenliği ve işlevselliği için kullanılır. Çerez mekanizması, sunucunun istemciye veri göndermesine ve bu verilerin istemci tarafından depolanıp sunucuya tekrar iletilmesine olanak tanır. Çerezler, her bir sonraki istekte otomatik olarak gönderilir ve bu nedenle güvenlik açıkları için bir hedef olabilir.

### 1. **SameSite Flag**

SameSite, çerezlerin yalnızca belirli koşullar altında, belirli sitelere gönderilmesini kontrol eden bir güvenlik önlemidir. Bu flag, genellikle **cross-site request** saldırılarını (örneğin, **Cross-Site Request Forgery - CSRF**) engellemek amacıyla kullanılır. Çerezler üzerinde `SameSite` değeri belirtilmezse, çerez varsayılan olarak herhangi bir şekilde gönderilebilir.

- **SameSite=Strict**:
    
    - **Tam koruma sağlar**, çerez yalnızca **aynı site** üzerinden yapılan taleplere gönderilir.
    - Örneğin, bir kullanıcı başka bir siteden linke tıkladığında veya bir formu dış bir siteden gönderdiğinde, bu çerez o talep ile gönderilmez.
    - Bu, kullanıcı güvenliğini artırır ancak bazen kullanıcı deneyimini kısıtlayabilir çünkü kullanıcılar farklı sitelere geçerken oturumları kaybedebilirler.
- **SameSite=Lax**:
    
    - Çerez, **yalnızca bazı cross-site taleplerinde** gönderilir. Bu, güvenlik sağlarken kullanıcı deneyimini bozmadan çalışır.
    - Örneğin, bir kullanıcı başka bir siteye gidip geri dönerse (bir bağlantıya tıklanarak), çerez hala geçerli olur, ancak form gönderimleri gibi daha "gizli" işlemler cross-site isteklerle yapılmaz.
    - Bu, genellikle **login** süreçlerinde ve **3rd-party analytics**'lerde tercih edilir.
- **SameSite=None**:
    
    - **Herhangi bir cross-site isteğiyle** çerez gönderilir. Bu, çerezin herhangi bir siteden gelen isteklere dahil edilebileceği anlamına gelir.
    - **Güvenlik riski taşıyabilir**, bu yüzden yalnızca HTTPS üzerinden yapılacak isteklerle gönderilmesine izin verilmek için `Secure` flag'inin de kullanılması gerekir.
    - Genellikle, **üçüncü taraf içerik** (örneğin, reklamlar) ve **cross-site talepler** için gereklidir.

---

### 2. **HttpOnly Flag**

`HttpOnly` flag'i, çerezi yalnızca HTTP(S) istekleri ile sunucuya göndermek için kullanılır. Bu, çerezin **JavaScript** tarafından erişilmesini engeller.

- **Amacı**: XSS (Cross-Site Scripting) saldırılarına karşı koruma sağlamaktır. Bir XSS saldırısı gerçekleştiğinde, kötü niyetli bir JavaScript kodu sayfanın DOM'undan çerezlere erişebilir. Ancak, `HttpOnly` flag'i olan bir çerez, bu tür bir saldırıya karşı dayanıklıdır çünkü JavaScript ile erişilemez.
    
    **Örnek:**
    
    `Set-Cookie: sessionid=abc123; HttpOnly; Secure; SameSite=Strict`
    
    Bu çerez, yalnızca HTTP(S) isteklerinde kullanılabilir ve JavaScript tarafından erişilemez.
    

---

### 3. **Secure Flag**

`Secure` flag'i, çerezin yalnızca güvenli bağlantılar üzerinden gönderilmesini sağlar. Yani, çerez yalnızca **HTTPS** protokolü kullanılarak gönderilir, **HTTP** ile gönderilemez.

- **Amacı**: Güvenli olmayan bağlantılar üzerinden (örneğin, HTTP) çerezlerin çalınmasını engellemektir. Çünkü HTTP üzerinden çerezlerin iletilmesi sırasında çerezler **şifrelenmez**, bu da bir saldırganın trafiği dinlemesi halinde çerezi elde etmesine yol açabilir.
    
    **Örnek:**
    
    `Set-Cookie: sessionid=abc123; Secure; HttpOnly; SameSite=Strict`
    
    Bu durumda, çerez yalnızca HTTPS istekleriyle iletilecektir.