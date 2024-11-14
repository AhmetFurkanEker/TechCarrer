Metasploit, sızma testlerinde mevcut uygulamalarda bulunan zafiyetlerin exploit edilebilmesi için geliştirilmiş bir araçtır. Exploitlerin yanı sıra birçok fonksiyonu da içinde barındırmaktadır. 
Bunlar ; 

1. **Exploitler**: Hedef sistemdeki güvenlik açıklarından faydalanarak içeri sızmamızı sağlar. Örneğin, eski bir yazılımın açığını kullanarak sisteme erişim sağlayabiliriz.
2. **Auxiliary Modülleri**: Sistemi ele geçirmez ama bilgi toplama gibi destek işler yapar. Örneğin, hangi portların açık olduğunu görmek veya şifre denemesi yapmak için kullanılır.
3. **Payloadlar**: Sisteme sızdıktan sonra çalıştırılacak kodlardır. Hedef sisteme komut gönderme veya dosya indirme işlemleri yapmamızı sağlar.
    - **Reverse Shell**: Hedef sistemi, saldırgana bağlanır ve komut gönderir.
    - **Meterpreter**: Daha gelişmiş komutlar çalıştırmamıza izin veren bir araçtır.
4. **Encoders (Kodlayıcılar)**: Payloadları antivirüslerden gizlemek için şifreler veya gizler, böylece payload’ların tespit edilmesi zorlaşır.
5. **Nops (NOP Sleds)**: Exploitlerin daha stabil çalışmasını sağlar. Kodun içine boş komutlar ekleyerek exploitin daha güvenilir olmasına yardımcı olur.
6. **Post-Exploitation Modülleri**: Sisteme sızdıktan sonra yapılacak işlemler için kullanılır. Örneğin, kullanıcı hesaplarını görmek veya ağ bağlantılarını kontrol etmek için işe yarar.
7. **Listener (Dinleyici)**: Payload sayesinde hedef sistemin bağlantı kurduğu yerdir. Hedefle bağlantı sağlandığında buradan komut gönderilebilir.
    
---

Metasploit’te yaygın olarak kullanılan bazı temel komutlar şunlardır:
1. **`msfconsole`**: Metasploit arayüzünü başlatır.
2. **`search <kelime>`**: Belirtilen kelime ile eşleşen modülleri arar. Örneğin, `search apache` komutu, Apache ile ilgili modülleri bulur.
3. **`use <modül_adı>`**: Kullanmak istediğiniz modülü seçer. Örneğin, `use exploit/windows/smb/ms17_010_eternalblue` komutu, EternalBlue exploit modülünü seçer.
4. **`show options`**: Seçilen modül için mevcut ayarları gösterir. Hedef IP adresi veya port gibi bilgileri buradan kontrol edebilirsiniz.
5. **`set <parametre> <değer>`**: Seçilen modülün parametrelerini ayarlamak için kullanılır. Örneğin, `set RHOST 192.168.1.10` komutu, hedef IP adresini ayarlar.
6. **`set payload <payload_adı>`**: Kullanılacak payload’ı ayarlamak için kullanılır. Örneğin, `set payload windows/meterpreter/reverse_tcp` komutu, Meterpreter reverse shell payload'ını seçer.
7. **`exploit` veya `run`**: Seçilen exploit’i çalıştırır.
8. **`sessions`**: Aktif oturumları gösterir. Sızma girişimi başarılı olursa, burada sistemdeki oturumları görebilirsiniz.
9. **`sessions -i <oturum_numarası>`**: Belirtilen oturuma bağlanmak için kullanılır. Örneğin, `sessions -i 1` komutu, 1 numaralı oturuma bağlanır.
10. **`exit` veya `quit`**: Metasploit konsolundan çıkmak için kullanılır.
11. **`show exploits`**: Kullanılabilir exploit modüllerinin listesini gösterir.
12. **`show payloads`**: Kullanılabilir payload modüllerinin listesini gösterir.

