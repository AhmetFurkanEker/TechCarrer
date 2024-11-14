Recon-ng, siber güvenlik alanında kullanılan güçlü bir bilgi toplama aracıdır. Kullanıcıların hedeflere dair veri toplamasını kolaylaştıran modüler bir yapıya sahip olup, çeşitli API'ler ve eklentilerle genişletilebilir.

### Workspace Oluşturma 

```
workspace create <workspace_ismi>
```

### Workspace Silme 

```
workspace remove <workspace_ismi>
```

### Workspace Listeleme 

```
workspace list
```

### Workspace Değiştirme/Seçme 

```
workspace load <workspace_ismi>
```


### Recon-ng Modülleri

- exploitation  
- import  
- recon  
- reporting
- discovery 

### Recon-ng Modüllerinin Listelenmesi

```
marketplace search
```

### Recon-ng belirli bir modül hakkında info alma


```
marketplace info <modül_adı>
```
## Recon-ng Örnek 

### Adım 1 
```
marketplace search hackertarget
```

```
recon-ng][techcareer] > marketplace search hackertarget
[*] Searching module index for 'hackertarget'...

  +-----------------------------------------------------------------------------+
  |               Path               | Version |   Status  |  Updated   | D | K |
  +-----------------------------------------------------------------------------+
  | recon/domains-hosts/hackertarget | 1.1     | installed | 2020-05-17 |   |   |
  +-----------------------------------------------------------------------------+

  D = Has dependencies. See info for details.
  K = Requires keys. See info for details.
```

---
### Adım 2
```
marketplace info hackertarget
```

```
[recon-ng][techcareer] > marketplace info hackertarget
  +---------------------------------------------------------------------------------------------------------------+
  | path          | recon/domains-hosts/hackertarget                                                              |
  | name          | HackerTarget Lookup                                                                           |
  | author        | Michael Henriksen (@michenriksen)                                                             |
  | version       | 1.1                                                                                           |
  | last_updated  | 2020-05-17                                                                                    |
  | description   | Uses the HackerTarget.com API to find host names. Updates the 'hosts' table with the results. |
  | required_keys | []                                                                                            |
  | dependencies  | []                                                                                            |
  | files         | []                                                                                            |
  | status        | installed                                                                                     |
  +---------------------------------------------------------------------------------------------------------------+

```
---
### Adım 3 

```
marketplace install hackertarget
```

---
### Adım 4

```
modules load hackertarget
```

---
### Adım 5

```
opitons
```

---
### Adım 6

```
options set SOURCE techcareer.net
```

---
### Adım 7 

```
info/input
```

---
### Adım 8

```
run
```

```
[*] 23 total (23 new) hosts found.
[recon-ng][techcareer][hackertarget] > show hosts

  +--------------------------------------------------------------------------------------------------------------------------------+
  | rowid |                 host                 |   ip_address   | region | country | latitude | longitude | notes |    module    |
  +--------------------------------------------------------------------------------------------------------------------------------+
  | 1     | techcareer.net                       | 34.107.251.232 |        |         |          |           |       | hackertarget |
  | 2     | admin.gcp.techcareer.net             | 34.149.57.47   |        |         |          |           |       | hackertarget |
  | 3     | bffapi.gcp.techcareer.net            | 34.107.146.54  |        |         |          |           |       | hackertarget |
  | 4     | cdn.gcp.techcareer.net               | 34.117.173.31  |        |         |          |           |       | hackertarget |
  | 5     | cms.gcp.techcareer.net               | 34.111.149.145 |        |         |          |           |       | hackertarget |
  | 6     | cv.gcp.techcareer.net                | 34.160.25.137  |        |         |          |           |       | hackertarget |
  | 7     | bffapi.dev.gcp.techcareer.net        | 34.36.141.81   |        |         |          |           |       | hackertarget |
  | 8     | cdn.dev.gcp.techcareer.net           | 34.149.9.25    |        |         |          |           |       | hackertarget |
  | 9     | cms.dev.gcp.techcareer.net           | 34.110.227.242 |        |         |          |           |       | hackertarget |
  | 10    | cvparse.dev.gcp.techcareer.net       | 34.117.70.160  |        |         |          |           |       | hackertarget |
  | 11    | internalapi.dev.gcp.techcareer.net   | 34.117.130.190 |        |         |          |           |       | hackertarget |
  | 12    | publicapi.dev.gcp.techcareer.net     | 34.111.174.205 |        |         |          |           |       | hackertarget |
  | 13    | internalapi.gcp.techcareer.net       | 34.120.84.214  |        |         |          |           |       | hackertarget |
  | 14    | preprod.gcp.techcareer.net           | 35.227.211.84  |        |         |          |           |       | hackertarget |
  | 15    | publicapi.gcp.techcareer.net         | 34.110.149.23  |        |         |          |           |       | hackertarget |
  | 16    | rediscommander.gcp.techcareer.net    | 34.160.61.57   |        |         |          |           |       | hackertarget |
  | 17    | admin.stage.gcp.techcareer.net       | 34.95.89.247   |        |         |          |           |       | hackertarget |
  | 18    | bffapi.stage.gcp.techcareer.net      | 34.111.249.94  |        |         |          |           |       | hackertarget |
  | 19    | cdn.stage.gcp.techcareer.net         | 35.244.148.131 |        |         |          |           |       | hackertarget |
  | 20    | cms.stage.gcp.techcareer.net         | 34.111.156.150 |        |         |          |           |       | hackertarget |
  | 21    | cv.stage.gcp.techcareer.net          | 34.111.188.192 |        |         |          |           |       | hackertarget |
  | 22    | internalapi.stage.gcp.techcareer.net | 34.96.124.155  |        |         |          |           |       | hackertarget |
  | 23    | publicapi.stage.gcp.techcareer.net   | 34.117.135.105 |        |         |          |           |       | hackertarget |
  +--------------------------------------------------------------------------------------------------------------------------------+


```


