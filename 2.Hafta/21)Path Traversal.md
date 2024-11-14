Web uygulamaları, sunucuda bir dizin içinde çalışır ve dosyalar belirli bir sistem içerisinde birbirleriyle uyumlu şekilde çalışır. `index.html` dosyası ana dizindedir; `src` dizininde bulunan `src.html` dosyasında iken `index.html` dosyasını görüntülemek istediğimizde   `../index.html` ile ana dizine ulaşabiliriz. Burada `../`, bir önceki dizine geçmeyi tanımlar. Böylece, dizin içinde bulunan web uygulaması dosyaları birbirleriyle etkileşime girer.


İşte tam olarak bu noktada, kullanıcı girişleri veya dosya getirme gibi işlemlerde bu dizin yönetim sistemi düzgün ayarlanmazsa, çeşitli denemeler ile sistem içerisinde ulaşılmaması gereken dosyalara erişim sağlanabilir.


`https://example.com/loadImage?filename=images.jpg` URL adresine istek yaptığımızda, `images.jpg` dosyasını getirir. Ancak, bu dosya yerine başka bir dosyayı getirmek istersem ve sistem düzgün bir şekilde düzenlenmemişse, istediğim dosyayı bana getirebilir.

`https://example.com/loadImage?filename=../../../etc/passwd` / `https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini` images.jpg yerine /etc/passwd veya windows\win.ini dosyasını getirecek dizin yolunu girerek  dosyaya erişim  sağlanabilir. 


```
<?php

$filename = $_GET['file'];


if (file_exists($filename)) {
    echo file_get_contents($filename);
} else {
    echo "Dosya bulunamadı!";
}
?>

```

Yukarıda verilen kaynak koda gösterildiği gibi GET isteği ile alınna file parametresi doğru şekilde işlenmeyerek direkt olarak getiriliyor.

