
```
import requests
from flask import Flask, request
app = Flask(__name__)
@app.route("/partial_ssrf")
def partial_ssrf():
    user_id = request.args["user_id"]
    resp = requests.get("https://api.example.com/user_info/" + user_id)

    if user_id.isalnum():
        resp = requests.get("https://api.example.com/user_info/" + user_id)
```


Bu zafiyet, kullanıcının sunucuya gönderdiği `user_id` gibi bir değerin, doğrulama yapılmadan bir URL'nin parçası olarak kullanılmasıyla ortaya çıkar. Kullanıcı, URL'nin yalnızca belirli bir kısmını kontrol edebileceği durumda bile, URL'nin yol (path) kısmını manipüle ederek sunucuyu istenmeyen yerlere yönlendirebilir. Örneğin, `user_id` değerine `../transfer-funds-to/123?amount=456` gibi bir değer ekleyen kötü niyetli bir kullanıcı, sunucunun `https://api.example.com/transfer-funds-to/123?amount=456` gibi farklı bir adrese istek yapmasını sağlayabilir. Bu sayede, saldırganın kontrolü dışında olan verilerle sunucu başka işlemler gerçekleştirebilir veya hassas kaynaklara erişim sağlanabilir. Bu zafiyeti önlemek için, kullanıcı girdileri alfanümerik karakterlerle sınırlandırılmalı ve yalnızca beklenen formatta verilere izin verilmelidir.


```
import requests
from flask import Flask, request, jsonify
app = Flask(__name__)
@app.route("/partial_ssrf")
def partial_ssrf():
    user_id = request.args.get("user_id")
    if user_id and user_id.isalnum():
        resp = requests.get("https://api.example.com/user_info/" + user_id)
        return jsonify({"status": resp.status_code, "data": resp.json()})
    else:
        return jsonify({"error": "Geçersiz kullanıcı ID"}), 400
```


user_id mevcut oalcak ve user_id alfanümerik karakterler olacak bu iki durumda gerçekleşirse eğer URL adresine istekte bulunacak. 