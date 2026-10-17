# 🖥️ Modül 4: Dashboard, Telemetri ve Sürücü Arayüzü

Bu modül, Formula Student yarış pilotunun kokpitte ihtiyaç duyduğu kritik telemetri bilgilerini gecikmesiz, ergonomik ve güvenli bir şekilde sunan sürücü arayüzü mimarisini kapsar.

*Bu modül belgedeki **Görev 4 (Dashboard ve Sürücü Arayüzü)** araştırma sunumu ve **Proje 4 (Dashboard ve Telemetri)** uygulama çalışmasını kapsar.*

---

## 🎯 Vizyon ve Amaç
Yarış esnasında pilot yüzlerce beygirlik bir gücü kontrol ederken karmaşık veya yanıltıcı bilgilerle boğuşamaz. Gösterge panelinin (Dashboard) tasarımı pilot ergonomisini doğrudan etkiler. Ayrıca bir kablo koptuğunda göstergenin eski hız veya sıcaklık değerini "donmuş" şekilde göstermesi hayati tehlike yaratır.

Bu modüldeki amacımız:
1. Kokpit ergonomisi ve sürücü arayüzü (Driver Interface) prensiplerini kavramak.
2. CAN Bus üzerinden gelen telemetri verilerini filtreleyerek ekrana aktarmak.
3. Kritik hata uyarılarını görsel/işitsel olarak önceliklendirmek ve veri kesintisinde eski bilginin donup kalmasını engelleyen bekçi mekanizmaları kurmak.

---

## 📚 1. Sunum Görevi: Dashboard ve Sürücü Arayüzü

Aşağıdaki başlıkları araştırarak profesyonel bir sunum (PDF) hazırlayın:

1. **Dashboard'un Araç İçerisindeki Amacı ve Önemi:**
   * Bir Formula Student kokpitinde sürücü arayüzünün temel işlevi nedir?
   * Hangi bilgiler pilota doğrudan gösterilmeli, hangi bilgiler yalnızca arka planda kaydedilmelidir (Data Logging)?
2. **Görüntülenecek Veriler ve Düzen:**
   * Hız, Motor/Inverter devri (RPM), Batarya Şarj Seviyesi (SoC), Motor/Batarya Sıcaklıkları, Lap Time ve Sistem Durumu (Ready-to-Drive, Precharge vb.) nasıl konumlandırılmalıdır?
   * Veri hiyerarşisi nasıl kurulmalıdır?
3. **Kritik Hata ve Uyarı Yönetimi:**
   * Kritik alarmlar (Aşırı sıcaklık, yalıtım hatası - IMD, BMS hatası, düşük voltaj) pilota nasıl iletilmelidir?
   * Renk kodları, ikaz ışıkları ve sesli uyarılar nasıl tasarlanmalıdır?
4. **CAN Bus Entegrasyonu:**
   * Dashboard ihtiyaç duyduğu verileri CAN Bus üzerinden nasıl dinler?
   * CAN ID filtreleme (Mask & Filter) neden önemlidir?
5. **Haberleşme Kesintisi ve Geçersiz Veri Durumu (Stale Data):**
   * CAN hattı koptuğunda veya bir sensör sustuğunda arayüz nasıl davranmalıdır?
   * Eski verinin güncelmiş gibi gösterilmesi nasıl önlenir?
6. **Örnek Dashboard Tasarımı:**
   * Takımımızın aracı için hayali veya prototip bir dashboard ekran tasarımı (UI Mockup) hazırlayın. Hangi veriyi neden nereye koyduğunuzu gerekçeleriyle savunun.

---

## 🛠️ 2. Proje Çalışması: Dashboard ve Telemetri

Basit ama kurallara uygun çalışan bir gösterge paneli prototipi geliştirin (Fiziksel OLED / LCD / Nextion ekran veya bilgisayarda Python/Processing/Web/Serial GUI):

### Proje Adımları
1. **Veri Akışı Oluşturma:**
   * Araç verilerini (Hız, Gaz/Fren pedalları, Batarya sıcaklığı, Sistem durumu) simüle eden veya CAN/Seri port üzerinden alan bir veri kaynağı kurun.
2. **Dashboard Arayüzü Geliştirme:**
   * Ekran üzerinde en az şu parametreleri dinamik olarak görselleştirin:
     * Hız (km/h) veya Motor RPM
     * Pedal Konumu (%)
     * Araç Durumu (`OFF`, `PRECHARGE`, `READY_TO_DRIVE`, `ERROR`)
3. **Kritik Hata Uyarı Mekanizması:**
   * Kritik bir hata sinyali geldiğinde ekranda belirgin bir görsel uyarı (renk değişimi, yanıp sönen ikaz, büyük uyarı kutusu vb.) tetikleyin.
4. **Eski Veri Koruması (Stale Data Prevention):**
   * Veri akışı kesildiğinde (Timeout), ekranın son değeri göstermeye devam etmesini engelleyin. Belirli bir süre (ör. 500 ms) veri gelmezse ilgili parametreyi tire (`--`), soru işareti (`??`) veya `DISCONNECTED` durumuna getirin.
5. **(Opsiyonel / Tercihen):**
   * Dashboard'u Modül 2'de yaptığınız CAN alıcı düğümüne bağlayarak gerçek CAN mesajlarıyla çalıştırın.

---

## 📦 Teslimat Yönergesi

Çalışmalarınızı Git üzerinden teslim ederken aşağıdaki standartlara uyun:

* **Hedef Klasör:** `Modul-4-Dashboard-ve-Surucu-Arayuzu/submissions/[Ad]-[Soyad]/`
* **Klasör Örneği:** `Modul-4-Dashboard-ve-Surucu-Arayuzu/submissions/Zuleyha-Nur-Gunes/`

### Beklenen Dosyalar
1. `[Ad]-[Soyad]-Dashboard-Sunum.pdf` (Sunum slaytları)
2. `Dashboard-Yazilimi.ino` (veya `.py`, `.cpp`, `.js` GUI kodu)
3. `Dashboard-UI-Tasarimi.png` (Ekran tasarımı / arayüz görüntüsü)
4. `Calisma-Kaniti.png` (veya kısa test raporu `Rapor.md` / ekran kaydı bağlantısı)

> ⚠️ **Hatırlatma:** Klasör ve dosya isimlerinde **BOŞLUK YASAKTIR**. Her kelimenin ilk harfi büyük olmalıdır (`PascalCase-Tireli`).
