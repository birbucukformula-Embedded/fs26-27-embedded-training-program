# 🛡️ Modül 3: Formula Student Kuralları ve Araç Güvenliği Simülasyonu

Bu modül, Formula Student kural kitapçığının (Formula Student Rules / FSAE) yazılım ve elektronik güvenliğini ilgilendiren maddelerini ve can güvenliği odaklı fail-safe yazılım mantığını inceler.

*Bu modül belgedeki **Görev 2 (Formula Student Kuralları ve Yazılım Güvenliği)** araştırma sunumu ve **Proje 3 (Araç Güvenliği Kontrol Simülasyonu)** uygulama çalışmasını kapsar.*

---

## 🎯 Vizyon ve Amaç
Formula Student yarışlarında hız kadar güvenlik de birincil önceliktir. Gaz pedalının takılı kalması, sensör kablosunun kopması veya donanım arızası gibi durumlarda aracın kontrolsüz hızlanmasını önlemek için kural kitapçığı çok katı yazılımsal ve donanımsal kurallar koyar. 

Bu modüldeki amacımız:
1. Formula Student Kural Kitapçığı'ndaki (özellikle T ve EV bölümleri) yazılım/sensör güvenliği maddelerini kural referanslarıyla öğrenmek.
2. Gaz pedalı (APPS) tutarsızlıkları ve fren-gaz çakışması (Brake Implausibility) gibi kritik güvenlik senaryolarını kavramak.
3. Arıza durumunda motor torkunu kesen ve güvenli duruma (Safe State) geçen bir durum makinesi (State Machine) algoritmasını simüle etmek.

---

## 📚 1. Sunum Görevi: Formula Student Kuralları ve Yazılım Güvenliği

Aşağıdaki konuları resmi Formula Student Kural Kitapçığı'ndan (FS Rules / FSG Rules) maddeleri doğrudan kaynak göstererek detaylıca araştırın ve profesyonel bir sunum (PDF) hazırlayın:

1. **APPS (Accelerator Pedal Position Sensor) ve Plausibility Kuralları:**
   * APPS nedir ve neden en az iki bağımsız sensör kullanılması zorunludur?
   * Sensörlerin farklı transfer fonksiyonlarına (ör. ters eğimli veya farklı voltaj aralığında çalışan iki potansiyometre) sahip olması kuralı neden vardır?
   * **APPS Plausibility Check:** İki sensör arasındaki sapma toleransı (örn. >%10 fark) ve izin verilen maksimum süre (örn. 100 ms) nedir? Kural ihlal edildiğinde yazılım ne yapmak zorundadır?
2. **System Critical Signals (SCS):**
   * SCS (Sistem Kritik Sinyalleri) tanımı nedir?
   * Bir sinyal hattında açık devre (Open Circuit), şaseye kısa devre veya beslemeye kısa devre durumunda sinyalin "aralık dışı" (Out of Range) kalması kuralı nasıl tasarlanır?
3. **BSPD (Brake System Plausibility Device):**
   * BSPD nedir ve hangi koşulda tetiklenir? (Fren basıncı varken gaz pedalına basılması durumu).
   * BSPD donanımsal mı olmalıdır, yazılımsal mı? Neden?
4. **Fren ve Gaz Çakışması (Brake Implausibility):**
   * Gaz pedalı basılıyken sert fren yapıldığında (veya tam tersi) yazılımın motor gücünü kesmesi kuralı nasıl işler?
   * Sistemin tekrar normale dönebilmesi için pedalın hangi konuma (örn. <%5) gelmesi şart koşulur?
5. **Kuralların Sistem ve Yazılım Tasarımına Etkileri:**
   * Bu kuralların Formula Student araç yazılım mimarisine etkileri nelerdir?
   * Güvenlik odaklı bir durum makinesi (State Machine) akışı nasıl kurgulanmalıdır?

> 📌 **Önemli:** Kuralların yalnızca ne söylediğini değil; **neden konulduklarını** (olası kaza senaryoları) ve **yazılım tarafında nasıl ele alınabileceğini** örneklerle açıklayın.

---

## 🛠️ 2. Proje Çalışması: Araç Güvenliği Kontrol Simülasyonu

Resmi kural mantığını simüle eden bir güvenlik kontrol yazılımı geliştirin:

> ⚠️ **Not:** Bu çalışma bir eğitim simülasyonudur; gerçek yarış aracında kullanılacak fiziksel güvenlik sistemlerinin yerine geçmez.

### Proje Adımları
1. **Çift Sensör Simülasyonu:**
   * İki potansiyometre veya yazılımsal girdi ile `APPS_1` ve `APPS_2` sinyallerini oluşturun.
   * Bir fren sinyali (`Brake_Pressure` veya fren butonu) tanımlayın.
2. **Plausibility (Tutarlılık) Kontrol Algoritması:**
   * İki pedal verisini normalize edin (%0 - %100 aralığına çevirin).
   * İki sensör arasındaki mutlak fark `%10`'dan büyükse bir zamanlayıcı (`millis()`) başlatın.
   * Tutarsızlık `100 ms`'den uzun sürerse tork talebini derhal `%0` yapın ve hata durumuna (`APPS_IMPLAUSIBILITY`) geçin.
3. **Fren ve Gaz Çakışması Mantığı:**
   * Fren sinyali aktifken APPS değeri belirli bir eşiğin üzerindeyse (ör. >%25) torku kesin.
   * Fren bırakılsa dahi gaz pedalı `%5`'in altına inene kadar tork talebini kilitli tutun.
4. **Görselleştirme ve Durum Çıktısı:**
   * Sistemin durumunu (`NORMAL`, `APPS_ERROR`, `BRAKE_OVERRIDE`) Serial Monitör'e net bir şekilde yazdırın.
5. **Akış Şeması (Flowchart):**
   * Geliştirdiğiniz kontrol mantığını, koşulları ve durum geçişlerini gösteren anlaşılır bir akış şeması hazırlayın.

---

## 📦 Teslimat Yönergesi

Çalışmalarınızı Git üzerinden teslim ederken aşağıdaki standartlara uyun:

* **Hedef Klasör:** `Modul-3-FS-Kurallari-ve-Yazilim-Guvenligi/submissions/[Ad]-[Soyad]/`
* **Klasör Örneği:** `Modul-3-FS-Kurallari-ve-Yazilim-Guvenligi/submissions/Zuleyha-Nur-Gunes/`

### Beklenen Dosyalar
1. `[Ad]-[Soyad]-FS-Kurallari-Sunum.pdf` (Sunum slaytları)
2. `Arac-Guvenligi-Simulasyonu.ino` (veya `.cpp` / `.py` kontrol mantığı kodu)
3. `Guvenlik-Akis-Semasi.png` (veya `.pdf` — Akış şeması / State machine diyagramı)
4. `Test-Senaryolari-ve-Rapor.md` (Normal, APPS sapması ve fren çakışması testlerinin adımları ve ekran görüntüleri)

> ⚠️ **Hatırlatma:** Klasör ve dosya isimlerinde **BOŞLUK YASAKTIR**. Her kelimenin ilk harfi büyük olmalıdır (`PascalCase-Tireli`).
