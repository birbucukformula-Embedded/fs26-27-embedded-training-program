# 📡 Modül 2: Gömülü Sistemler ve CAN Bus Haberleşmesi

Bu modül, Formula Student araç elektroniğinin kalbi olan endüstri standardı **Controller Area Network (CAN Bus)** mimarisini ve düğümler arası haberleşmeyi konu alır.

*Bu modül belgedeki **Görev 1 (Gömülü Sistemler ve CAN Bus)** araştırma sunumu ve **Proje 2 (CAN Bus Haberleşmesi)** uygulama çalışmasını kapsar.*

---

## 🎯 Vizyon ve Amaç
Modern bir Formula Student yarış aracında motor sürücüsü (Inverter), Batarya Yönetim Sistemi (BMS), Araç Kontrol Ünitesi (VCU) ve Dashboard gibi kritik birimler birbirleriyle yüksek gürültülü bir ortamda milisaniyeler mertebesinde haberleşmek zorundadır. Noktadan noktaya (Point-to-Point) kablolama aracı ağırlaştırır ve arıza riskini artırır. CAN Bus, diferansiyel hat yapısı ve hata toleransıyla bu zorluğun standart çözümüdür.

Bu modüldeki amacımız:
1. Otomotiv haberleşme protokollerini (UART, I2C, SPI ve CAN) karşılaştırmalı olarak kavramak.
2. CAN Bus'ın donanımsal ve mantıksal (katmanlı) mimarisini, arbitrasyon sürecini ve mesaj yapısını öğrenmek.
3. İki bağımsız düğüm arasında CAN mesajı gönderip alarak veri kaybı ve zaman aşımı (Timeout) senaryolarını yönetebilmek.

---

## 📚 1. Sunum Görevi: Haberleşme Protokolleri ve CAN Bus

Aşağıdaki başlıkları içeren profesyonel bir sunum (PDF) hazırlayın:

1. **Haberleşme Protokolleri Karşılaştırması:**
   * Seri haberleşme protokolleri (UART, I2C, SPI) nedir ve nasıl çalışır?
   * Hangi senaryolarda hangi protokol tercih edilir? Neden araç içi omurgada UART/I2C/SPI yerine CAN tercih edilir?
2. **CAN Bus Mimarisi ve Çalışma Prensibi:**
   * CAN Bus nedir? Tarihçesi ve otomotivdeki yeri.
   * Diferansiyel voltaj sinyalleşmesi (CAN_H, CAN_L) nasıl çalışır?
   * Bus topolojisi nedir? 120 Ω hat sonlandırma dirençleri (Termination Resistors) neden hattın iki ucunda bulunmak zorundadır?
3. **CAN Mesaj Formatı ve Katmanları:**
   * Standart (11-bit ID / CAN 2.0A) ve Genişletilmiş (29-bit ID / CAN 2.0B) çerçeve yapısı.
   * Çerçeve bileşenleri: SOF (Start of Frame), Identifier, RTR, Control (DLC), Data Field (0-8 byte), CRC, ACK, EOF.
   * Baud rate nedir? Formula Student araçlarında yaygın kullanılan hızlar (250 kbps, 500 kbps, 1 Mbps) ve kablo uzunluğu ilişkisi.
4. **Arbitrasyon (Önceliklendirme) Mekanizması:**
   * Bit seviyesinde tahkikat (Arbitration) nedir?
   * Dominant (0 mantıksal düzeyi) ve Resesif (1 mantıksal düzeyi) kavramları.
   * İki düğüm aynı anda mesaj göndermeye başladığında çarpışma (Collision) olmadan hattı kim kazanır? Neden düşük ID daha yüksek önceliğe sahiptir?
5. **Formula Student Araç Elektroniğinde CAN Bus:**
   * Araç içerisinde neden CAN Bus kullanıyoruz?
   * Telemetri, BMS, VCU ve Dashboard arasında akan tipik mesaj örnekleri (CAN ID ve sinyal içerikleri).

---

## 🛠️ 2. Proje Çalışması: CAN Bus Haberleşmesi

Araştırdığınız teorik yapıyı iki düğüm (örneğin iki mikrodenetleyici + MCP2515 CAN modülü veya simülatör / CAN kütüphanesi) üzerinde çalışır hale getirin:

### Proje Adımları
1. **Mesaj ID ve Sinyal Tanımlaması:**
   * Gönderilecek veri paketini belirleyin (Örn: `ID: 0x100`, Veri: Pedal konumu, Motor sıcaklığı veya Sayaç verisi).
   * 8 byte'lık veri alanında sinyalleri uygun biçimde paketleyin (Byte packing).
2. **Verici Düğüm (Transmitter / Node A):**
   * Periyodik olarak (örneğin 100 ms'de bir) CAN veri çerçevesini hatta basın.
3. **Alıcı Düğüm (Receiver / Node B):**
   * CAN hattını dinleyin, doğru ID'ye sahip mesaj geldiğinde veriyi çözümleyin (Byte unpacking).
   * Okunan değerleri Seri Port ekranına anlamlı şekilde yazdırın.
4. **Hata ve Zaman Aşımı (Timeout) Tespiti:**
   * CAN kablosu çıkarıldığında veya verici sustuğunda alıcı düğüm bunu nasıl anlar?
   * Belirli bir süre (örneğin 300 ms) boyunca yeni mesaj gelmezse `[WARNING] CAN Timeout: Node A Disconnected!` uyarısı üreten bir bekçi (Watchdog/Timeout) mantığı kurun.

---

## 📦 Teslimat Yönergesi

Çalışmalarınızı Git üzerinden teslim ederken aşağıdaki standartlara uyun:

* **Hedef Klasör:** `Modul-2-CAN-Bus-ve-Haberlesme/submissions/[Ad]-[Soyad]/`
* **Klasör Örneği:** `Modul-2-CAN-Bus-ve-Haberlesme/submissions/Zuleyha-Nur-Gunes/`

### Beklenen Dosyalar
1. `[Ad]-[Soyad]-CAN-Bus-Sunum.pdf` (Sunum slaytları)
2. `CAN-Transmitter-Node.ino` (Verici kaynak kodu)
3. `CAN-Receiver-Node.ino` (Alıcı kaynak kodu)
4. `CAN-Baglanti-Semasi.png` (İki düğümün ve CAN transceiver bağlantısının şeması)
5. `CAN-Test-Sonuclari.md` (veya `Terminal-Ciktisi.png` — Alınan mesajlar ve zaman aşımı uyarısının kanıtı)

> ⚠️ **Hatırlatma:** Klasör ve dosya isimlerinde **BOŞLUK YASAKTIR**. Her kelimenin ilk harfi büyük olmalıdır (`PascalCase-Tireli`).
