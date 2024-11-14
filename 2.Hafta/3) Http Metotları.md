- HTTP (Hypertext Transfer Protocol) yöntemleri, web sunucuları ile istemciler arasında iletişimi sağlamak için kullanılır.
- HTTP yöntemleri, sunucudaki kaynaklara erişim ve bu kaynaklarla ilgili işlemler için kullanılan farklı türde istekleri belirtir.
---

### GET

###### **AMAÇ** 

Sunucudan veri almak için kullanılır.
##### **ÖZELLİKLER**

GET istekleri sadece veri almak için kullanılır, sunucuda herhangi bir değişiklik yapmaz.

##### **ÖRNEK** 

```
GET /users HTTP/1.1
Host: example.com
User-Agent: curl/8.6.0
Accept: */*
```

---

### POST

###### **AMAÇ** 

Sunucuya veri göndermek veya sunucuda yeni bir kaynak oluşturmak için kullanılır.
##### **ÖZELLİKLER**

POST istekleri genellikle veri eklemek veya sunucuda değişiklik yapmak için kullanılır.

##### **ÖRNEK** 

```
POST /users HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 31

username=value1&password=value2

```


---
### PUT

###### **AMAÇ** 

Sunucuda var olan bir kaynağı güncellemek veya sunucuda belirli bir konumda yeni bir kaynak oluşturmak için kullanılır.
##### **ÖZELLİKLER**

PUT istekleri genellikle idempotenttir, yani aynı isteğin tekrar tekrar yapılması aynı sonucu doğurur.(GET,PUT,DELETE)

##### **ÖRNEK** 

```
PUT /new.html HTTP/1.1
Host: example.com
Content-type: text/html
Content-length: 16

<p>New File</p>

```

```
HTTP/1.1 201 Created
Content-Location: /new.html
```


---
### DELETE

###### **AMAÇ** 

Sunucuda var olan bir kaynağı silmek için kullanılır.
##### **ÖZELLİKLER**

DELETE istekleri genellikle sunucudaki veriyi siler.

##### **ÖRNEK** 

```
DELETE /file.html HTTP/1.1
Host: example.com

```


---
### Patch

###### **AMAÇ** 

Sunucuda var olan bir kaynağın bir kısmını güncellemek için kullanılır.
##### **ÖZELLİKLER**

PATCH istekleri genellikle daha küçük güncellemeler için kullanılır ve sadece belirli alanları değiştirmek için uygundur.

##### **ÖRNEK** 

```
PATCH /users/123 HTTP/1.1
Host: example.com
Content-Type: application/json
Content-Length: 27
Authorization: Bearer ABC123

{
  "status": "suspended"
}

```




---
### OPTIONS

###### **AMAÇ** 

Sunucunun hangi HTTP yöntemlerini desteklediğini öğrenmek için kullanılır.
##### **ÖZELLİKLER**

Sunucunun yeteneklerini sorgular ve izin verilen yöntemleri döndürür.

##### **ÖRNEK** 

```
OPTIONS / HTTP/2
Host: example.org
User-Agent: curl/8.7.1
Accept: */*
```

```
HTTP/1.1 204 No Content
Allow: OPTIONS, GET, HEAD, POST
Cache-Control: max-age=604800
Date: Thu, 13 Oct 2016 11:45:00 GMT
Server: EOS (lax004/2813)

```

---
### CONNECT

###### **AMAÇ** 

İstemci ile sunucu arasında bir iletişim kanalı kurmak için kullanılır.
##### **ÖZELLİKLER**

Genellikle SSL tünelleme için kullanılır.

##### **ÖRNEK** 

```
CONNECT server.example.com:80 HTTP/1.1
Host: server.example.com:80
Proxy-Authorization: basic aGVsbG86d29ybGQ=

```



---
### TRACE

###### **AMAÇ** 

İstemci ve sunucu arasındaki iletişimin izlenmesi ve hata ayıklaması için kullanılır.
##### **ÖZELLİKLER**

Sunucuya gönderilen isteğin dökümünü döndürür.

##### **ÖRNEK** 

```
TRACE / HTTP/1.1
Host: example.com
User-Agent: curl/8.7.1
Accept: */*

```

```
HTTP/1.1 200 OK
Content-Length: 123
Date: Wed, 04 Sep 2024 11:50:24 GMT
Server: Apache/2.4.59 (Unix)
Content-Type: message/http

```

---
#### **GET VS POST**

![[Pasted image 20241112100626.png]]