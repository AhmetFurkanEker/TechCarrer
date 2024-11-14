
```
from flask import Flask, request, render_template_string
app = Flask(__name__)
@app.route("/")
def home():
    if request.args.get('c'):
        return render_template_string(request.args.get('c'))
    else:
        return "Hello, send someting inside the param 'c'!"
if __name__ == "__main__":
    app.run()
```

`http://127.0.0.1:5000/?c={{7*7}}``

Çıktı ==> 49

```
from flask import Flask, request
app = Flask(__name__)
@app.route("/")

def home():
    user_input = request.args.get('c')
    if user_input:
        return f"Kullanıcı Girdisi: {user_input}"
    else:
        return "Hello, send something inside the param 'c'!"
if __name__ == "__main__":
app.run()
```



İki kod arasında ki fark alınan c parametresi birinde return işleminde render_tempalte_string() metotuyla çağırılırken diğerinde direkt olarak string  döndürülmekte.