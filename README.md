# NetScanner

Yerel ağdaki cihazları bulan ve seçilen cihazda açık portları listeleyen küçük bir masaüstü uygulaması. 2021'de Python öğrenirken yazdım.

![NetScanner arayüzü](screenshots/netscanner-main.png)

## Ne yapıyor

Uygulama açıldığında arka planda ağı tarıyor ve bulduğu cihazları bir listeye ekliyor. Listeden bir IP seçip "PORT TARAMAYI BAŞLAT" butonuna basınca, o cihazda hangi portların açık olduğunu gösteriyor.

İki dosyadan oluşuyor:

- `iplib.py` — ağ tarama ve port tarama işlemlerini yapan kısım (nmap kütüphanesini kullanıyor)
- `testqt1.py` — PyQt5 ile yapılmış arayüz kısmı

## Kurulum

```bash
brew install nmap
pip install PyQt5 python-nmap
python testqt1.py
```


## Bugün tekrar çalıştırdım

Bu projeyi uzun zamandır açmamıştım, bu repoyu düzenlerken tekrar çalıştırıp test ettim. Genel olarak çalışıyor — yukarıdaki görüntü gerçek bir çalıştırmadan.

Fark ettiğim birkaç şey oldu:

- Yönetici izni olmadan çalıştırınca ağdaki bazı cihazları bulamayabiliyor. Bunun sebebini tam çözemedim ama muhtemelen nmap'in bazı tarama yöntemleri için ekstra yetki gerektirmesiyle ilgili.
- Port taraması, özellikle yanıt vermeyen ya da yavaş cevap veren cihazlarda beklenenden çok daha uzun sürebiliyor. Taramada bir bekleme süresi (timeout) tanımlanmadığı için her port için biraz zaman kaybediliyor.

Kodu şu an değiştirmedim, o zamanki halini koruyor. Zamanla bu tür şeyleri (timeout eklemek, izin gerektiren kısımları daha anlaşılır hale getirmek gibi) düzeltmeyi düşünüyorum.
