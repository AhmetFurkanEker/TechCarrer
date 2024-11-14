FFUF aracı ile web uygulaması üzerinde dizin taraması gerçekleştiriyoruz.

```
└──╼ #./ffuf -u http://10.10.55.194/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.1.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.55.194/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
________________________________________________


sitemap                 [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 80ms]
rss                     [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 361ms]
login                   [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 635ms]
video                   [Status: 301, Size: 234, Words: 14, Lines: 8, Duration: 81ms]
0                       [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 712ms]
feed                    [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 686ms]
image                   [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 702ms]
atom                    [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 698ms]
wp-content              [Status: 301, Size: 239, Words: 14, Lines: 8, Duration: 81ms]
admin                   [Status: 301, Size: 234, Words: 14, Lines: 8, Duration: 79ms]
audio                   [Status: 301, Size: 234, Words: 14, Lines: 8, Duration: 81ms]
intro                   [Status: 200, Size: 516314, Words: 2076, Lines: 2028, Duration: 81ms]
wp-login                [Status: 200, Size: 2664, Words: 115, Lines: 53, Duration: 700ms]
css                     [Status: 301, Size: 232, Words: 14, Lines: 8, Duration: 79ms]
rss2                    [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 786ms]
license                 [Status: 200, Size: 309, Words: 25, Lines: 157, Duration: 82ms]
wp-includes             [Status: 301, Size: 240, Words: 14, Lines: 8, Duration: 80ms]
js                      [Status: 301, Size: 231, Words: 14, Lines: 8, Duration: 81ms]
Image                   [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 702ms]
rdf                     [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 684ms]
page1                   [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 677ms]
readme                  [Status: 200, Size: 64, Words: 14, Lines: 2, Duration: 85ms]
robots                  [Status: 200, Size: 41, Words: 2, Lines: 4, Duration: 80ms]
dashboard               [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 699ms]
```

Tespit edilen "robots" dizininde iki dosya ile karşılaşıyoruz . 

```
└──╼ #curl http://10.10.55.194/robots
User-agent: *
fsocity.dic
key-1-of-3.txt

```

Tespit edilen "/wp-login" dizini  ile birlikte web uygulamasında wordpress çalıştığını tespit ediyoruz . 

Tespit edilen "/license"  dizinin bir base64 ile encode edilmiş bir ifade ile karşılaşıyoruz. 

```
└──╼ #curl http://10.10.55.194/license

what you do just pull code from Rapid9 or some s@#% since when did you become a script kitty?

do you want a password or something?

ZWxsaW90OkVSMjgtMDY1Mgo=

```
Bu encode edilmiş veriyi decode ettiğimde kullanıcı adı ve şifre benzeri bir durumla karşılaşıyorum . 
```
└──╼ #echo "ZWxsaW90OkVSMjgtMDY1Mgo=" | base64 -d
elliot:ER28-0652

```


Bu bilgileri kullanarak Wordpress yönetim paneline giriş sağlandı . 


![[WordpressLogin.png]]