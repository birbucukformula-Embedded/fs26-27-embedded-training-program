# 🏎️ Birbuçuk Formula (Adana Formula Student Team) — Gömülü Sistemler Eğitim Programı

Bu repo, **Birbuçuk Formula (Adana Formula Student Team)** bünyesindeki gömülü sistemler aday mühendislerimiz için hazırlanan **Eğitim, Proje ve Görev Takip** platformudur.

---

## 🎯 Vizyon ve Amaç

Embedded Systems birimine katılan yeni üyelerimizin gömülü sistemler alanında kendilerini geliştirmeleri, teknik araştırma yapmayı öğrenmeleri ve takımımızın araç elektroniği altyapısını tanımaları amacıyla bu eğitim sürecini hazırladık.

Bu süreçte sizlerden **yalnızca sunum hazırlamanızı değil, araştırdığınız konuları derinlemesine anlamanızı ve mutlaka uygulamaya dökmenizi** bekliyoruz. 

> 💡 **Önemli Not:** Bu konular hakkında daha önceden bilgi sahibi olmanız gerekmemektedir. Takımımızın asıl amacı, araştırma, deneme-yanılma ve uygulama sürecinde öğrenmeniz ve kendinizi gerçek bir yarış mühendisi vizyonuyla geliştirmenizdir.

---

## 🗺️ Eğitim Programı Mimarisi

Eğitim sürecimiz, teorik araştırma sunumları ile pratik donanım/yazılım projelerini doğrudan eşleştiren **4 ana modül** üzerine kurulmuştur:

| Modül | 📚 Sunum Görevi (Araştırma) | 🛠️ Proje Çalışması (Uygulama) | Anahtar Kavramlar |
| :--- | :--- | :--- | :--- |
| [**Modül 1: Sensörler ve Veri İşleme**](./Modul-1-Sensorler-ve-Veri-Isleme/) | Sensörler ve Mikrodenetleyiciler | Sensör Okuma ve Veri İşleme | MCU Mimarisi, ADC, GPIO, Gürültü Azaltma, Filtreleme, Fail-Safe |
| [**Modül 2: CAN Bus ve Haberleşme**](./Modul-2-CAN-Bus-ve-Haberlesme/) | Gömülü Sistemler ve CAN Bus | CAN Bus Haberleşmesi | CAN 2.0A/B, Arbitrasyon, Diferansiyel Hat, Çift Düğüm RX/TX, Timeout |
| [**Modül 3: FS Kuralları ve Güvenlik**](./Modul-3-FS-Kurallari-ve-Yazilim-Guvenligi/) | Formula Student Kuralları ve Yazılım Güvenliği | Araç Güvenliği Kontrol Simülasyonu | APPS, Plausibility (%10 / 100ms), SCS, BSPD, Fren-Gaz Çakışması |
| [**Modül 4: Dashboard ve Sürücü Arayüzü**](./Modul-4-Dashboard-ve-Surucu-Arayuzu/) | Dashboard ve Sürücü Arayüzü | Dashboard ve Telemetri | Kokpit Ergonomisi, CAN Telemetrisi, Kritik Alarmlar, Stale Data Koruması |

---

## 📁 Repo Yapısı

Repository modüler bir klasör hiyerarşisine sahiptir:

```text
fs26-27-embedded-training-program/
├── README.md
├── Modul-1-Sensorler-ve-Veri-Isleme/
│   ├── README.md
│   └── submissions/
│       └── [Ad]-[Soyad]/
├── Modul-2-CAN-Bus-ve-Haberlesme/
│   ├── README.md
│   └── submissions/
│       └── [Ad]-[Soyad]/
├── Modul-3-FS-Kurallari-ve-Yazilim-Guvenligi/
│   ├── README.md
│   └── submissions/
│       └── [Ad]-[Soyad]/
└── Modul-4-Dashboard-ve-Surucu-Arayuzu/
    ├── README.md
    └── submissions/
        └── [Ad]-[Soyad]/
```

* Her modül klasöründeki `README.md` dosyasında sunum soruları, proje adımları, teknik isterler ve test beklentileri yer alır.
* Her modülün içindeki `submissions` klasörü, ilgili modüle ait sunum ve proje ödevlerinizi yükleyeceğiniz havuzdur.

---

## 📏 İsimlendirme Standartları (ÇOK ÖNEMLİ)

Mühendislik disiplininin ilk kuralı standartlara uymaktır. Takımımızda **BOŞLUK (Space) KARAKTERİ KESİNLİKLE YASAKTIR.** Ayrıca her kelime **Büyük Harfle** başlamalıdır (`PascalCase-Tireli`).

### 1. Klasör İsmi Formatı
Ödev klasörünüz, ilgili modülün `submissions` klasörü altında **yalnızca adınız ve soyadınızdan** oluşmalıdır:
`[Ad]-[Soyad]`

* ✅ `Zuleyha-Nur-Gunes`
* ❌ `zuleyha-nur-gunes` *(Küçük harf yasak)*
* ❌ `Zuleyha Nur Gunes` *(Boşluk yasak)*
* ❌ `Zuleyha-Nur-Gunes-Modul-1` *(Ekstra ekler yasak, sadece isim-soyisim)*

### 2. Dosya İsmi Formatı
Ödev dosyalarınız da aynı disipline sahip olmalıdır:
* ✅ `Sensorler-Sunum.pdf`
* ✅ `Sensor-Okuma-Filtreleme.ino`
* ❌ `sunum.pdf` *(İsimsiz / küçük harf yasak)*
* ❌ `kod 1.c` *(Boşluklu dosya yasak)*

---

## 🛠️ Nasıl Ödev Teslim Ederim? (Git Workflow)

> ⛔ **DİKKAT:** GitHub web arayüzünden *"Upload files"* butonunu kullanmak kesinlikle yasaktır. Tüm adımlar terminal ve **Git** üzerinden yürütülmelidir:

1. **Fork:** Sağ üst köşedeki butondan bu repoyu kendi GitHub hesabınıza **Fork** edin.
2. **Clone:** Fork ettiğiniz repoyu bilgisayarınıza indirin:
   ```bash
   git clone https://github.com/<kullanici-adiniz>/fs26-27-embedded-training-program.git
   cd fs26-27-embedded-training-program
   ```
3. **Dizin Açma:** İlgili modülün `submissions` dizinine gidip kendi klasörünüzü oluşturun:
   ```bash
   cd Modul-1-Sensorler-ve-Veri-Isleme/submissions
   mkdir Ad-Soyad
   cd Ad-Soyad
   ```
4. **Dosyaları Ekleme:** Sunum PDF'inizi, kaynak kodlarınızı, devre şemalarınızı ve test çıktılarınızı bu klasöre ekleyin.
5. **Commit & Push:** Değişiklikleri kaydedin ve GitHub'a gönderin:
   ```bash
   git add .
   git commit -m "feat(modul-1): [Ad Soyad] sunum ve proje teslimi"
   git push origin main
   ```
6. **Pull Request (PR):** Kendi reponuzdan ana repoya bir **Pull Request (PR)** açın.

---

## 🎯 Değerlendirme Kriterleri

Çalışmalarınız değerlendirilirken aşağıdaki 7 temel kriter dikkate alınacaktır:

1. **Konunun Anlaşılması:** Konunun ne kadar içselleştirildiği ve temel mantığın kavranması.
2. **Araştırma Kaynaklarının Niteliği:** Kullanılan kaynakların doğruluğu, kural kitapçığı atıfları ve teknik güvenilirliği.
3. **Teknik Terminoloji:** Kavramların (Arbitrasyon, Plausibility, Fail-Safe, ADC vb.) doğru ve yerinde kullanılması.
4. **Uygulamaya Aktarım:** Öğrenilen teorik bilgilerin çalışan bir koda veya simülasyona dökülebilmesi.
5. **Hata Senaryoları ve Testler:** Kablo kopması, aşırı gürültü, sınır aşımı veya zaman aşımı gibi olumsuz senaryoların ele alınması.
6. **Kod ve Dokümantasyon Düzeni:** Temiz kod prensipleri, açıklayıcı şemalar ve düzenli dosya yapısı.
7. **Soru-Cevap:** Sunum esnasında takım liderleri ve üyelerden gelen sorulara verilen yanıtlar ve savunabilme yetkinliği.

---

## 📜 Takım Anayasası (Kurallar)

1. **Format Hatası = Ret:** İsimlendirme standardına uymayan (küçük harfle başlayan, boşluk içeren) PR'lar **incelenmeden doğrudan kapatılacaktır (Close PR).**
2. **Kopyala-Yapıştır Yasak:** Kodun veya devrenin çalışma mantığını bilmeden doğrudan kopyalayıp yapıştırmak takımdan ihraç sebebidir.
3. **Yapay Zeka Politikası:** LLM ve AI araçlarını (ChatGPT, Claude vb.) araştırma ve öğrenme amacıyla kullanabilirsiniz; ancak çıktıyı doğrulamadan, anlamadan ve açıklayamayacak şekilde teslim eden üye sorumlu tutulur.
4. **Profesyonel Commit Mesajları:** Commit mesajları açıklayıcı olmalıdır (Örn: `feat: APPS plausibility algoritmasi eklendi` ✅ | `dosya attim` ❌).

---

Bu eğitim sürecinin sonunda hepinizin gömülü sistemler, sensörler, haberleşme protokolleri ve Formula Student araç elektroniği hakkında sağlam bir temel kazanmasını hedefliyoruz.

Başarılar dileriz! Geleceğin yarış mühendisleri. 🏎️🏁