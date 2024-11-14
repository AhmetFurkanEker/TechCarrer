#### Genel Tarama

`wpscan --url https://hedefsite.com`

Hedef siteyi tarayarak  güvenlik açıklarını raporlar.

#### Eklenti Taraması

`wpscan --url https://hedefsite.com --enumerate p`

#### Tema Taraması

Temalardaki güvenlik açıklarını taramak için:

`wpscan --url https://hedefsite.com --enumerate t`

#### Kullanıcı Adı Tespiti

Web sitesindeki kullanıcıları tespit etmek için:

`wpscan --url https://hedefsite.com --enumerate u`
##### Rastgele kullanıcı aracısı

Tarama yaparken  random user bilgileri ile istek gönderir.

`wpscan --url yourwebsite.com --random-user-agent`
##### Gizli tarama

Gizli modda tarama gerçekleştirirken user agent random ayarlanır,algılama yöntemi pasif olarak ayarlanır ve eklenti sürümleri pasif modda taranır.

`wpscan --url yourwebsite.com --stealthy`
##### Brute Force


`wpscan --url yourwebsite.com -passwords file/path/passwords.txt

