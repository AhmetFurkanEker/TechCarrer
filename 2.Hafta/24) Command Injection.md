Command Injection, bir web uygulamasının kullanıcıdan aldığı veriyi OS terminali aracılığıyla işlem yaparken düzgün şekilde filtrelememesi sonucunda, saldırganın bu veriyi manipüle ederek komut çalıştırmasına yol açan bir güvenlik açığıdır.

### 1. **Blind Command Injection (Kör Command Injection)**

Bu tür saldırıda saldırgan, komutun çalışıp çalışmadığına dair doğrudan bir çıktı alamaz, fakat komutun yan etkilerinden faydalanarak başarı durumunu anlar. Örneğin, saldırgan bir komut çalıştırdığında uygulamanın yanıt süresinde gecikme yaratabiliyorsa veya sunucu üzerinde dosya oluşturulup oluşturulmadığını kontrol edebiliyorsa, komutun başarıyla çalıştığını dolaylı yoldan öğrenebilir.

**Örnek:**

`127.0.0.1 && ping -c 10 127.0.0.1`

Bu komut, eğer çalışırsa uygulamanın yanıt vermesini geciktirir ve saldırgan bu gecikmeden komutun çalıştığını anlar.

### 2. **Error-Based Command Injection (Hata Tabanlı Command Injection)**

Bu saldırı türünde, saldırgan komutun çıktısını, sistemde meydana gelen hata mesajlarından öğrenebilir. Hatalar sayesinde komutun nasıl çalıştığı veya hangi verilere erişildiği hakkında bilgi sahibi olabilir. Hata mesajları bazen çok detaylı bilgiler verebilir, bu da saldırganın komutunu daha da iyileştirmesine olanak sağlar.

**Örnek:**


`127.0.0.1; ls /path

Bu komut, `/path` dizini bulunamadığında hata döndürür ve saldırgan bu hatayı kullanarak sistem hakkında bilgi sahibi olabilir.


### 4. **Output-Based Command Injection (Çıktı Tabanlı Command Injection)**

Bu saldırı türünde saldırgan, çalıştırdığı komutun çıktısını doğrudan alabilir. Komutun çıktısı doğrudan uygulamanın arayüzünde veya bir hata mesajında gösterildiğinde, saldırgan sistemdeki dosya içeriklerini okuyabilir veya diğer komut çıktıları hakkında bilgi sahibi olabilir.

**Örnek:**

`127.0.0.1; cat /etc/passwd`

Eğer bu komutun çıktısı doğrudan uygulamada gösteriliyorsa, saldırgan sistemdeki kullanıcı bilgilerini doğrudan görebilir.

### 5. **File-Based Command Injection (Dosya Tabanlı Command Injection)**

Bu tür saldırıda saldırgan, komut çıktısını bir dosyaya yönlendirir ve ardından bu dosyanın içeriğini başka bir yöntemle okuyabilir. Özellikle doğrudan komut çıktısı alamadığı durumlarda dosya sistemi üzerinden bu bilgilere ulaşabilir.

**Örnek:**

`127.0.0.1; ls > /tmp/output.txt`

Bu komut, `ls` komutunun çıktısını `/tmp/output.txt` dosyasına yazar. Saldırgan, başka bir yöntemle bu dosyanın içeriğini okuyabilir.