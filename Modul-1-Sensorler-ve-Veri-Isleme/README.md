# ⚙️ Modül 1: Sensörler, Mikrodenetleyiciler ve Veri İşleme

Bu modül, Formula Student eğitim programının ilk aşamasıdır. Sistem mimarisini en temelden (donanım, analog/dijital sinyaller ve veri işleme) ele alır.

*Bu modül belgedeki **Görev 3 (Sensörler ve Mikrodenetleyiciler)** araştırma sunumu ve **Proje 1 (Sensör Okuma ve Veri İşleme)** uygulama çalışmasını kapsar.*

---

## 🎯 Vizyon ve Amaç
Formula Student yarış aracında onlarca sensör (pedal konum sensörleri, tekerlek hız sensörleri, sıcaklık/basınç sensörleri vb.) araç elektroniğine veri sağlar. Ancak gerçek dünyadan okunan sinyaller gürültülüdür ve doğrudan kullanılamaz. 

Bu modüldeki amacımız:
1. Mikrodenetleyicilerin çalışma prensibini ve ADC mekanizmasını derinlemesine anlamak.
2. Ham sensör verisini filtreleyerek kararlı ve anlamlı hale getirmek.
3. Sensör kopması veya arıza durumlarında sistemin güvenli davranmasını (fail-safe) sağlayacak algoritmalar geliştirmek.

---

## 📚 1. Sunum Görevi: Sensörler ve Mikrodenetleyiciler

Aşağıdaki araştırma başlıklarını detaylıca inceleyerek profesyonel bir sunum (PDF) hazırlayın. Sunumunuzda teorik tanımların yanı sıra blok diyagramlar, formüller ve Formula Student aracı senaryolarına yer verin:

1. **Gömülü Sistemler ve Takım Mimarisi:**
   * Gömülü sistemler nedir ve nerelerde kullanılır?
   * Bir Formula Student takımında *Embedded Systems* biriminin sorumlulukları ve araç elektroniğindeki kritik rolü nedir?
2. **Mikrodenetleyici Temelleri:**
   * Mikrodenetleyici (MCU) nedir? Mikroişlemciden farkı nedir?
   * Clock hızı, Register, Interrupt (kesme) kavramları ne işe yarar?
3. **ADC (Analog-to-Digital Converter) ve Analog Sensörler:**
   * ADC nedir ve nasıl çalışır?
   * ADC çözünürlüğü (ör. 10-bit, 12-bit), referans voltajı ($V_{ref}$) ve örnekleme frekansı (sampling rate) ne anlama gelir?
   * Ham analog voltaj mikrodenetleyicide sayısal değere nasıl dönüştürülür?
4. **Dijital Giriş ve Çıkışlar (GPIO):**
   * Dijital giriş/çıkış pinleri nasıl kullanılır?
   * Pull-up ve Pull-down dirençleri neden gereklidir, açıkta kalan (floating) pin neden risklidir?
   * PWM (Pulse Width Modulation) nedir ve nerelerde kullanılır?
5. **Gürültü ve Sinyal Filtreleme:**
   * Ham ADC verisi neden doğrudan kullanılamaz?
   * Elektriksel/çevresel gürültü kaynakları nelerdir?
   * Gürültü azaltma yöntemleri (Hareketli ortalama / Moving Average, Alçak Geçiren Filtre / LPF, Medyan filtre vb.) nasıl çalışır?
6. **Hata ve Güvenilirlik Yönetimi (Fail-Safe):**
   * Sensör bağlantısı koparsa (Open Circuit), kablo şaseye/beslemeye kısa devre olursa veya beklenmeyen bir değer gelirse sistem nasıl davranmalıdır?
   * Hata tespiti için donanımsal ve yazılımsal önlemler nelerdir?

---

## 🛠️ 2. Proje Çalışması: Sensör Okuma ve Veri İşleme

Sunumda araştırdığınız teorik bilgileri gerçek bir mikrodenetleyici veya simülasyon ortamında (Wokwi, Tinkercad, Proteus veya fiziksel Arduino/STM32/ESP32) uygulayın:

### Proje Adımları
1. **Sensör / Potansiyometre Bağlantısı:**
   * Bir potansiyometreyi (veya uygun bir analog sensörü) mikrodenetleyicinin analog giriş pinine bağlayın.
2. **Ham Veri Okuma ve Anlamlandırma:**
   * Ham ADC değerini okuyun ve bunu anlamlı bir fiziksel birime (ör. Voltaj `0.0V - 5.0V`, Pedal Yüzdesi `%0 - %100` veya Derece) haritalayın (`map()` formülü veya matematiksel denklem ile).
3. **Filtreleme / Gürültü Azaltma:**
   * Ham veri üzerine basit bir filtreleme algoritması (örneğin 10 örnekli Hareketli Ortalama - Moving Average veya Basit Üstel Filtre - EMA) uygulayın.
4. **Hata / Sınır Dışı Değer Tespiti (Out of Bounds):**
   * Sensörün normal çalışma aralığı dışındaki (ör. beklenmeyen ani sıçramalar, aşırı düşük/yüksek gerilim) durumları tespit edin.
   * Hata durumunda Serial Terminale net bir arıza uyarısı (`[ERROR] Sensor Out of Range!`) yazdırın.
5. **Gözlem ve Doğrulama:**
   * Seri port (Serial Monitor veya Serial Plotter) üzerinden ham veri ile filtrelenmiş veriyi eşzamanlı olarak çizdirin/gözlemleyin.

---

## 📦 Teslimat Yönergesi

Çalışmalarınızı Git üzerinden teslim ederken aşağıdaki standartlara **eksiksiz** uyun:

* **Hedef Klasör:** `Modul-1-Sensorler-ve-Veri-Isleme/submissions/[Ad]-[Soyad]/`
* **Klasör Örneği:** `Modul-1-Sensorler-ve-Veri-Isleme/submissions/Zuleyha-Nur-Gunes/`

### Beklenen Dosyalar
1. `[Ad]-[Soyad]-Sensorler-Sunum.pdf` (Sunum slaytları)
2. `Sensor-Okuma-Filtreleme.ino` (veya `.cpp` / `.c` kaynak kodu)
3. `Devre-Semasi.png` (Tinkercad / Fritzing / Wokwi devre şeması veya fotoğrafı)
4. `Test-Sonuclari-ve-Rapor.md` (veya `Serial-Plotter-Ciktisi.png` — ham ve filtrelenmiş verinin karşılaştırmalı ekran görüntüsü ve açıklaması)

> ⚠️ **Hatırlatma:** Klasör ve dosya isimlerinde **BOŞLUK YASAKTIR**. Her kelimenin ilk harfi büyük olmalıdır (`PascalCase-Tireli`).
