
Searchsploit, Exploit Database (EDB) içinde yer alan exploitleri ve güvenlik zafiyetlerini hızlı bir şekilde aramak için kullanılan bir komut satırı aracıdır. 


1. **`searchsploit <app>`**: Belirtilen terimle eşleşen exploitleri arar.
    - Örnek: `searchsploit apache`
2. **`searchsploit --cve <CVE-ID>`**: Belirli bir CVE kimliğine göre arama yapar.
    - Örnek: `searchsploit --cve 2021-44228`
3. **`-j, --json`**: Sonuçları JSON formatında gösterir.
    - Örnek: `searchsploit -j apache`
4. **`-m, --mirror <EDB-ID>`**: Belirli bir exploit’i mevcut dizine kopyalar.
    - Örnek: `searchsploit -m 39446`
5. **`-x, --examine <EDB-ID>`**: Belirli bir exploit’i açar.
    - Örnek: `searchsploit -x 39446`
6. **`-u, --update`**: Exploit Database paket güncellemelerini kontrol eder ve yükler.
    - Örnek: `searchsploit -u`