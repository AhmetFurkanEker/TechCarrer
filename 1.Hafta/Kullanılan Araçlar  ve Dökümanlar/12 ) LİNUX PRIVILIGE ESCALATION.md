Linux sistemlere yetki yükseltme özet ile  , saldırganların sınırlı veya tam etkileşimli bir kabuk elde ettiği temel bir kullanıcı veya sistem hesabına sahip olduktan sonra, root kullanıcıya erişmek için yollar aramasıdır. Saldırgan sistem içerisinde root yetkisine sahip olursa tüm sistemi kontrol edebilir.

Gerçek dünyada ilk sisteme erişim noktasında root seviyesinde erişim elde etmek çok nadir bir durumdur. 

**Ayrıcalık Yükseltme İçin Linux Sistemlerinde Kullanılan Araçlar**

Keşif sürecinde zamandan tasarruf etmenizi sağlayacak çeşitli araçlar vardır. Bu araçların bazı ayrıcalık yükseltme yollarını kaçırabileceğini bilerek yalnızca zamanı verimli kullanmak için tercih edilmelidirler. Aşağıda, popüler Linux keşif araçlarının ve ilgili GitHub bağlantılarının bir listesi bulunmaktadır.

Hedef sistemin ortamı, kullanılacak aracı etkiler. Örneğin, hedef sistemde Python yüklü değilse, Python ile yazılmış bir aracı çalıştıramazsınız. Bu yüzden, yalnızca tek bir araca güvenmek yerine birkaç araca hakim olmak daha faydalı olacaktır.

- **LinPeas**: [https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)
- **LinEnum:** [https://github.com/rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)[](https://github.com/rebootuser/LinEnum)
- **LES (Linux Exploit Suggester):** [https://github.com/mzet-/linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester)
- **Linux Smart Enumeration:** [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)
- **Linux Priv Checker:** [https://github.com/linted/linuxprivchecker](https://github.com/linted/linuxprivchecker)
---
#### Enumeration

`Hostname`  komutu , hedef makinanın bilgisayar adını döndüreecektir. Bu dönen değer anlamsız bir string ifade olabilir fakat bazı durumlarda , hedef sistemin ağda bulunduğu durum hakkında bilgi verebilir. (SQL-PROD-01)
```
$ hostname
wade7363
```

---
`uname -a` komutu çekirdek hakkında bilgi sağlar. 

```
$ uname -a
Linux wade7363 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
---

`proc/version` komutu `proc` dosya sistemi, hedef sistemdeki süreçler hakkında bilgi sunar ve farklı Linux sürümlerinde yaygın olarak bulunur.

```
$ cat /proc/version 
Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014
```
---

`etc/issue` dosyası sistemleri tanımlamak için kullanılır .Sistemleri tanımlamak için bakalıabilir. İşletim sistemi hakkında bilgiler barındırır.
```
└──╼ #cat /etc/issue
Parrot Security 6.2 \n \l
```
---

`ps` komutu , Linux'ta çalışan işlemleri görüntülemek için kullanılır. 
Ps komutu ile çalışan işlemlerle alakalı şu verilere ulaşılır. 

1. PID : İşlem Id numarası her işlem idsi benzersizdir
2. TTY : Terminal türü 
3. Tıme : Cpu zamanı 
4. CMD : Çalışan komut veya yürütülebilir dosya. 

```
└──╼ #ps 
    PID TTY          TIME CMD
   3239 pts/5    00:00:00 sudo
   3240 pts/5    00:00:00 su
   3241 pts/5    00:00:00 bash
   3448 pts/5    00:00:00 ps
```
---

`ps` komutu seçenekleri şunlardır . 

1. ps -A : Tüm çalışan süreçleri görüntüler
2. ps axjf : Sürecin dallanmış yapısını görüntüler
3.  ps aux : Tüm kullanıcıların süreçlerini gösterir, süreci başlatan kullanıcıyı ve terminale bağlı olmayan süreçleri görüntüler. 
---

`env` komutu, çevresel değişkenleri gösterir. PATH değişkeni içinde bir derleyici veya betik dili bulunabilir. 

```
$ env
MAIL=/var/mail/karen
USER=karen
SSH_CLIENT=10.11.106.146 47748 22
HOME=/home/karen
SSH_TTY=/dev/pts/4
QT_QPA_PLATFORMTHEME=appmenu-qt5
LOGNAME=karen
TERM=xterm-256color
XDG_SESSION_ID=2
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
XDG_RUNTIME_DIR=/run/user/1001
LANG=en_US.UTF-8
SHELL=/bin/sh
PWD=/
SSH_CONNECTION=10.11.106.146 47748 10.10.124.203 22
```

---
`sudo -l` komutu kullanıcının sudo ile hangi komutları çalıştırabileceğini listelemeye yarar. 

---
`ls -la ` komutu ile ls veya ls -l komutları ile gözden kaçabilecek gizli dosyalar görülebilir. 

---
`id` komutu, kullanıcının ayrıcalık seviyesini ve grup üyeliklerini gösterir.

---
`etc/passwd` dosyasını okumak , sistemde bulunan kullanıcıları keşfetmek için kolay bir yoldur. ,

---
`history ` önceki komutları bakmaya yarar . Hedef sistem hakkında bilgi sağlayabilir . Bazen kullanıcı adı ve parolalar gibi bilgiler yer alabilir. 

---
`netstat` Ağ arayüzlerini ve mevcut bağlantıları kontrol ettikten sonra , emvcut iletişimleri incelemek faydalıdır. 
`netstat` komutunun kullanılabileceği seçenekler. 
1. `netstat -a ` : Dinlenilen portları ve bağlantıları listeler 
2. `netstat -at ` veya `netstat -au` : TCP veya UDP protokollerini listeler
3.  `netstat -l ` : Dinleme modundaki portları listeler 
4. `netstat -s ` : Protokol başına ağ kullanım istatistiklerini listeler . 
5. `netstat -tp` : Servis adı ve PID bilgisi ile bağlantıları listeler. 
---
"find" komutu, bir dosya sisteminde belirli dosya ve klasörleri aramak için kullanılan güçlü bir araçtır. Güvenlik araştırmalarında, özellikle ayrıcalık yükseltme (privilege escalation) vektörlerini bulmak için "find" komutu çok faydalıdır. Şimdi, bu komutun nasıl kullanılabileceğine dair bazı örnekler üzerinden açıklamalar yapalım.

##### 1. **Dosya Bulma**:

- `find . -name flag1.txt`: Bu komut, şu an bulunduğun dizinde (current directory) "flag1.txt" adlı dosyayı arar.
- `find /home -name flag1.txt`: "flag1.txt" adlı dosyayı, "/home" dizininde arar.
- `find / -type d -name config`: "/" kök dizini altında "config" adlı dizini arar. `-type d` burada yalnızca dizinleri aramak için kullanılır.
- `find / -type f -perm 0777`: Bu komut, tüm kullanıcılar tarafından okunabilir, yazılabilir ve çalıştırılabilir olan (yani 777 izinlerine sahip) dosyaları bulur.
- `find / -perm a=x`: Çalıştırılabilir olan dosyaları arar.
- `find /home -user frank`: "frank" kullanıcısına ait tüm dosyaları "/home" dizininde arar.
- `find / -mtime 10`: Son 10 gün içinde değiştirilmiş dosyaları bulur.
- `find / -atime 10`: Son 10 gün içinde erişilmiş dosyaları bulur.
- `find / -cmin -60`: Son 60 dakika içinde değiştirilmiş dosyaları bulur.
- `find / -amin -60`: Son 60 dakika içinde erişilmiş dosyaları bulur.
- `find / -size 50M`: Boyutu 50 MB olan dosyaları bulur.

##### 2. **Hata Mesajlarından Kurtulma**:

"find" komutu bazen hatalar verebilir, bu yüzden çıktıyı daha temiz hale getirmek için `2>/dev/null` ifadesini ekleyebiliriz. Bu ifade, hata mesajlarını (stderr) devnull'a yönlendirir, yani hiçbiri görüntülenmez.

Örneğin:

- `find / -writable -type d 2>/dev/null`: Bu komut, tüm dünyadan yazılabilir dizinleri arar, hata mesajlarını göstermez.
- `find / -perm -222 -type d 2>/dev/null`: Dünyadan yazılabilir dizinleri bulur.
- `find / -perm -o w -type d 2>/dev/null`: Dünyadan yazılabilir dizinleri arar.

##### 3. **Yazılabilir veya Çalıştırılabilir Dizinler**:

Yazılabilir veya çalıştırılabilir dosyaları bulmak için aşağıdaki komutları kullanabilirsiniz:

- `find / -perm -o x -type d 2>/dev/null`: Dünyadan çalıştırılabilir dizinleri bulur.

##### 4. **Geliştirme Araçlarını ve Dilleri Bulma**:

Yazılım geliştirme araçlarını ve desteklenen dilleri bulmak için:

- `find / -name perl*`: Perl ile ilgili dosyaları arar.
- `find / -name python*`: Python ile ilgili dosyaları arar.
- `find / -name gcc*`: GCC derleyicisi ile ilgili dosyaları arar.

##### 5. **Özel Dosya İzinlerini Bulma (SUID)**:

SUID (Set User ID) bitini bulmak, ayrıcalık yükseltme için oldukça önemlidir. Bu bit, dosyanın çalıştırılabilmesi için dosya sahibinin yetkilerini kullanmasına olanak tanır.

- `find / -perm -u=s -type f 2>/dev/null`: Bu komut, SUID bitine sahip dosyaları bulur. Bu dosyalar, daha yüksek yetkilere sahip olabileceğiniz potansiyel ayrıcalık yükseltme vektörleridir.
---
#### Kernel Exploıts Nedir ? 


Kernel Exploıts , işletim sistemi çekirdeğini hedef alarak o çekirdekte bulunan açıktan faydanılan saldırıdır.İşletim sistemi çekirdeği, donanımı yönetir,işlemciyi kontrol eder, bellek erişimini düzenler ve sistemdeki tüm işlemleri yönetir. Özetle kernel bilgisayarın beynidir. 

Kernel düzeyinde oluşan bir açıktan  faydalanabilmek için exploit kullanılır. Exploit kullanılarak sistem içerisinde yetki yükselerek en üst yetkili kullanıcıya ulaşılması sağlanır. Kernel düzeyinde ki bir açık çok kritiktir çünkü kernel düzeyinde yapılabilen bir manipülasyon sistemin tamamını etikileyebilir.


![[Kernel.png]]


Kernel bilgilerine ulaşabilmek için  aşağıda bulunan komut kullanılabilir .

```
uname -a 
```


Kernel versiyonu tespit edildikten sonra mevcut versiyon ile Exploit-db,searchspolit veya metasploit ile uygun exploit tespit edilip kullanılır. 

#### !!!!

1. Exploit kullanılmadan önce kodlarını inceleyerek nasıl çalıştığına dikkat edin. Kernel etkileneceğinden dolayı geri döndürülemez zararlar verilebilir. 
2. Bazı exploitler çalıştırıldıktan sonra tetiklenebilmesi için etkileşime geçilebilmesi gerekebilir bu yüzden exploitin kullanım talimatlarını ve kodlarını detaylıca okunulmalıdır. 
3. Exploit direkt olarak sisteme yükleme imkanı vermeyebilir . Sisteme yükleyebilmek adında Python modülü ile http sunucusu oluşturup hedef sisteme `wget` ile yüklenebilir. 


---
#### Sudo 
Linux veya benzeri işletim sistemlerinde "root" adlı bir kullanıcı vardır ve bu kullanıcı sistemin en üst düzey yetkilerine sahiptir. Yani, root kullanıcısı her türlü sistem değişikliği yapabilir, dosyalara sınırsız erişebilir ve programları yükleyip kaldırabilir. Normal kullanıcıların ise root kadar geniş yetkileri yoktur; güvenlik açısından onların yetkileri sınırlıdır.

Ancak, bazı durumlarda normal bir kullanıcının da bu yetkilere kısa süreliğine ihtiyaç duyabilir. İşte burada "sudo" komutu devreye girer. "Sudo" komutunu kullanarak, normal bir kullanıcı belirli komutları root yetkisiyle çalıştırabilir.

Herhangi bir kullanıcı, "sudo -l" komutunu kullanarak sahip olduğu root yetkilerini kontrol edebilir.

[GTFOBins](https://gtfobins.github.io/) ile mevcut uygulamlarla nası lroot yetkisi alınır bakılabilir. 

---
SUID