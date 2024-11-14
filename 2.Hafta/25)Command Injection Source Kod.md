```
from flask import Flask, request, render_template_string
import os

app = Flask(__name__)

@app.route('/')
def index():
    return render_template_string("""
        <!DOCTYPE html>
        <html lang="tr">
        <head>
            <meta charset="UTF-8">
            <title>Ping Test</title>
        </head>
        <body>
            <h1>Ping Test</h1>
            <form action="/ping" method="post">
                <label for="ip">IP Adresi:</label>
                <input type="text" id="ip" name="ip" required>
                <button type="submit">Gönder</button>
            </form>
        </body>
        </html>
    """)

@app.route('/ping', methods=['POST'])
def ping():
    ip_address = request.form.get('ip')
    # OS command injection açığı
    command = f"ping -c 4 {ip_address}"
    result = os.popen(command).read()
    return f"<pre>{result}</pre>"

if __name__ == '__main__':
    app.run(debug=True)

```


```
<?php require_once("../header.php"); ?>

<pre>

<?php

  system("ping -c 2 ".$_GET['ip']);

?>

</pre>

<?php require_once("../footer.php"); ?>
```
