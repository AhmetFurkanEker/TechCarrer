
Ffuf , go dili ile yazılmış web uygulamalarında fuzzing yapmaya yarayan bir araçtır. 

#### Directory Fuzzing

`ffuf -w wordlist.txt:FUZZ -u http://example.com:PORT/FUZZ`

#### Uzantı (Extension) Fuzzing

`ffuf -w wordlist.txt:FUZZ -u http://example.com:PORT/indexFUZZ`

[Wordlist](https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/extensions-most-common.fuzz.txt)

#### Page Fuzzing 

`ffuf -w wordlist.txt:FUZZ -u http://example.com:PORT/blog/FUZZ.php`

#### Derinlemesine (Recursive ) Tarama 

`ffuf -w wordlist.txt:FUZZ -u http://example.com:PORT/FUZZ -recursion -recursion-depth 1 -e .php -v

#### Subdomain Fuzzing 

`ffuf -w wordlist.txt:FUZZ -u https://FUZZ.example.com/`

#### Vhost Fuzzing 

`ffuf -w wordlist.txt:FUZZ -u http://example.com:PORT/ -H 'Host: FUZZ.academy.htb' -fs xxx` 

#### Parametre Fuzzing - GET

`ffuf -w wordlist.txt:FUZZ -u http://admin.example.com:PORT/admin/admin.php?FUZZ=key -fs xxx`


#### Parametre Fuzzing - POST 

`ffuf -w wordlist.txt:FUZZ -u http://admin.example.com:PORT/admin/admin.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx`


####  Parametre Değeri Fuzzing 

`ffuf -w ids.txt:FUZZ -u http://admin.example.com:PORT/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx`



### Wordlist 

SecLists/Discovery/Web-Content/directory-list-2.3-small.txt	 => Dizin Sayfa Wordlist
SecLists/Discovery/Web-Content/web-extensions.txt => 	Uzantı Wordlist
SecLists/Discovery/DNS/subdomains-top1million-5000.txt => 	Domain Wordlist 
SecLists/Discovery/Web-Content/burp-parameter-names.txt => Parameters Wordlist