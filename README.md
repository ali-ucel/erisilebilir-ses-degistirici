# Erişilebilir Ses Değiştirici (Accessible Voice Changer)

![Sürüm](https://img.shields.io/badge/S%C3%BCr%C3%BCm-v1.0.0-blue.svg)
![NVDA](https://img.shields.io/badge/Eri%C5%9Fibillik-NVDA%20%25100-brightgreen.svg)
![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%2F%2011%20(64--bit)-lightgrey.svg)
![Lisans](https://img.shields.io/badge/Lisans-%C3%96zel%20(T%C3%BCm%20Haklar%C4%B1%20Sakl%C4%B1d%C4%B1r)-orange.svg)

**Erişilebilir Ses Değiştirici**, görme engelli bireyler başta olmak üzere tüm kullanıcılar için tasarlanmış, **%100 NVDA ve ekran okuyucu uyumlu**, yapay zeka (RVC v2) destekli gerçek zamanlı bir ses dönüştürme yazılımıdır.

Diğer karmaşık, ekran okuyucularla okunamayan ses değiştiricilerin aksine; tüm menüler, ses ayarları, model seçimleri ve eğitim araçları tamamen klavye ve ekran okuyucu dostu olarak geliştirilmiştir.

---

## 🚀 Doğrudan İndirme

Son sürüm kurulum paketini aşağıdaki bağlantıdan tek tıkla indirebilirsiniz:

👉 **[Erisilebilir_Ses_Degistirici_installer.exe İndir (v1.0.0)](https://github.com/ali-ucel/erisilebilir-ses-degistirici/releases/latest/download/Erisilebilir_Ses_Degistirici_installer.exe)**  
*(Dosya Boyutu: ~184 MB | 64-bit Windows Destekli)*

---

## ✨ Öne Çıkan Özellikler

* **♿ %100 NVDA ve Ekran Okuyucu Erişilebilirliği:**
  * wxPython altyapısıyla geliştirilmiş tam erişilebilir kullanıcı arayüzü.
  * NVDA Controller Client entegrasyonu ile anlık sesli durum ve işlem bildirimleri.
  * Klavyeden `Tab`, `Yön Tuşları`, `Boşluk` ve `Enter` ile eksiksiz kontrol.
  * İşlem adımları için sesli bip ve durum bildirimleri.

* **🎙️ Gerçek Zamanlı Yapay Zeka Ses Dönüşümü:**
  * RVC v2 (Retrieval-based Voice Conversion) mimarisi.
  * NVIDIA GPU (CUDA) donanım hızlandırması ile ultra düşük gecikme (~100-150ms).
  * CPU destekli yedek çalıştırma modu.

* **🎚️ Formant ve Perde (Pitch) İnce Ayarı:**
  * Ses tonunu milimetrik olarak kalınlaştırma veya inceltme imkanı.
  * Formant kaydırma özelliğiyle erkek sesini kadın veya çocuk sesine, kadın sesini tok erkek sesine dönüştürebilme.

* **🎓 Kendi Ses Modelinizi Eğitin (Fine-Tuning & Model Training):**
  * Uygulama içinden kendi ses veri setinizi (klasör veya tek ses dosyası) seçerek kendi RVC yapay zeka modelinizi eğitebilme.
  * Epoch ve adım ayarları için rehber bilgi kutuları.
  * Eğitilen modelleri otomatik olarak sisteme ekleme ve kullanıma sunma.

* **☁️ HuggingFace Model Kütüphanesi:**
  * Yüzlerce hazır Türkçe ve yabancı ses modelini uygulama içinden arama.
  * Tek tıkla indirip anında ses dönüştürmede kullanabilme.

* **🎮 Discord, Oyunlar ve Canlı Yayın Uyumu:**
  * Virtual Audio Cable (Line 1 / CABLE) desteğiyle Discord, Teamspeak, CS2, Valorant, GTA V, RDR2 ve tüm sesli sohbetlerde anında çalışır.
  * Kullanıcının kendi sesini kulaklıktan gecikmesiz monitör edebilmesi için çift çıkış desteği.

---

## 🧠 Retrieval-based Voice Conversion (RVC) Nedir ve Ne İçin Kullanılır?

### 1. RVC (Retrieval-based Voice Conversion) Nedir?
**Retrieval-based Voice Conversion (RVC)**, derin öğrenme temelli en gelişmiş yapay zeka ses dönüştürme mimarisidir. Konuşmacının ses tonunu, boğaz rezonansını ve akustik özelliklerini alıp hedef bir kişinin veya karakterin ses tınısına dönüştürür. En büyük gücü; söylenen kelimeleri, artikülasyonu, duyguyu, tonlamayı ve konuşma hızını birebir koruyarak yalnızca ses kimliğini (timbre) değiştirmesidir.

### 2. Neden "Retrieval-based" (Geri Getirme Tabanlı) Olarak Adlandırılır?
Geleneksel yapay zeka ses dönüştürme modelleri yalnızca sinir ağı ağırlıklarına (neural network weights) dayanır. Bu durum uzun konuşmalarda veya yüksek perdelerde sesin bozulmasına, metalikleşmesine ya da robotikleşmesine yol açabilir.

RVC'nin getirdiği devrimsel yenilik **Geri Getirme (Retrieval)** mekanizmasıdır:
* Model eğitilirken, hedef sesin tüm akustik vektörleri bir **FAISS (Facebook AI Similarity Search)** indeks dosyasında (`.index`) toplanır.
* Siz mikrofona konuştuğunuzda, sistem gerçek zamanlı olarak sesinizin fonetik özelliklerine en yakın hedef ses vektörlerini bu indeksten **"geri getirir" (retrieve eder)**.
* Bu sayede ses yapay olarak üretilmek yerine doğrudan hedef kişinin gerçek ses veri setindeki en uygun tonlarla harmanlanır. Sonuç; pürüzsüz, çatallanmayan, insan kulağına tamamen doğal gelen bir sestir.

### 3. RVC Nasıl Çalışır? (Teknik Mimari)
RVC mimarisi 4 temel aşamada gerçek zamanlı ses dönüşümü gerçekleştirir:
1. **İçerik Ayrıştırma (Feature Extraction):** `ContentVec` veya `HuBERT` modelleri kullanılarak mikrofondan gelen sesin tınısı silinir, sadece ne söylendiğini temsil eden saf fonetik içerik çıkarılır.
2. **Perde Algılama (Pitch Extraction / F0):** `RMVPE`, `FCPE` veya `Harvest` algoritmalarıyla sesinizin melodisi (iniş ve çıkışları) anlık olarak yakalanır.
3. **Vektör İndeks Eşleme (Feature Retrieval):** Çıkarılan fonetik özellikler `.index` dosyasındaki hedef konuşmacı vektörleriyle en yüksek benzerliğe göre eşleştirilir.
4. **Nöral Ses Sentezi (VITS / HiFi-GAN):** Hedef konuşmacının ağırlıkları ve geri getirilen indeks verileri birleştirilerek ultra düşük gecikmeyle (GPU desteğiyle ~100-150ms) hedef seste konuşma olarak dışarı aktarılır.

### 4. RVC Ne İçin ve Nerelerde Kullanılır?
* **Oyunlar ve Sesli Sohbet:** Discord, TeamSpeak, CS2, Valorant, GTA V / FiveM ve roleplay (RP) sunucularında dilediğiniz oyun karakteri veya kişi olarak gerçek zamanlı konuşmak için.
* **Canlı Yayınlar ve İçerik Üretimi:** Twitch, YouTube veya TikTok canlı yayınlarında izleyicilere eğlenceli ve interaktif ses performansları sunmak için.
* **Görme Engelliler İçin Erişilebilir İletişim:** Standart programların görsel karmaşasından bağımsız olarak, %100 NVDA desteğiyle görme engelli bireylerin kendi seslerini diledikleri gibi özelleştirebilmesi için.
* **Gizlilik ve Anonimlik:** Çevrim içi ortamlarda kendi gerçek sesini ve kimliğini paylaşmak istemeyen kullanıcılar için tam akustik koruma sağlamak amacıyla.
* **Müzik ve Şarkı Sentezi (AI Cover):** Herhangi bir ses kaydını veya vokali başka sanatçıların ses modelleriyle yeniden seslendirmek için.

### 5. Geleneksel Ses Değiştiricilerden (Clownfish, Voicemod vb.) Farkı Nedir?
* **Geleneksel Filtreler:** Ses dalgasının frekansını basitçe yukarı veya aşağı kaydırır (pitch shift). Sonuçta ortaya çıkan ses "sincap" (helyum gazı çekmiş gibi) veya mekanik "robot" sesinden öteye gidemez. Boğaz yapısını ve insan sesinin doğallığını taklit edemez.
* **RVC Yapay Zeka Dönüşümü:** Frekansı sadece kaydırmakla kalmaz; ses tellerinin titreşimini, ağız-boğaz rezonans boşluğunu (formant) ve konuşmacının kendine has tınısını baştan aşağı hedef sesin karakteristiğine göre yeniden modeller. Böylece karşınızdaki kişi bir filtre değil, gerçekten o kişinin konuştuğunu duyar.

---

## 💻 Sistem Gereksinimleri

| Bileşen | Minimum | Önerilen |
| :--- | :--- | :--- |
| **İşletim Sistemi** | Windows 10 (64-bit) | Windows 11 (64-bit) |
| **İşlemci (CPU)** | Intel Core i5 / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| **Ekran Kartı (GPU)** | CPU Modu Desteklenir | NVIDIA RTX 3060 veya üzeri (CUDA) |
| **Bellek (RAM)** | 8 GB RAM | 16 GB RAM veya üzeri |
| **Depolama** | 2 GB boş disk alanı | SSD (Hızlı model yükleme için) |
| **Ses Aygıtı** | Standart Mikrofon + Kulaklık | Line 1 (Virtual Audio Cable) |

---

## 🛠️ Kurulum ve Başlangıç

1. **[Erisilebilir_Ses_Degistirici_installer.exe](https://github.com/ali-ucel/erisilebilir-ses-degistirici/releases/latest/download/Erisilebilir_Ses_Degistirici_installer.exe)** dosyasını indirin.
2. Kurulum sihirbazını çalıştırın ve ekrandaki adımları takip edin.
3. Kurulum tamamlandığında masaüstünüzde oluşan **"Erişilebilir Ses Değiştirici"** kısayoluna basın.
4. Açılan arayüzde:
   * **Giriş Aygıtı:** Kendi mikrofonunuzu seçin.
   * **Çıkış Aygıtı:** `Line 1 (Virtual Audio Cable)` seçin.
   * **İzleme Çıkışı:** Kendi kulaklığınızı seçin.
   * **Ses Modeli:** Listeden konuşmak istediğiniz karakteri seçin.
5. **F5** tuşuna basarak ses dönüştürücüyü başlatın!

---

## ❓ Sıkça Sorulan Sorular (SSS)

**S: Discord'da sesimin değiştiğini arkadaşlarım nasıl duyar?**  
*C: Discord > Ayarlar > Ses ve Görüntü bölümünden Giriş Aygıtını `Line 1 (Virtual Audio Cable)` yapmanız yeterlidir.*

**S: Kendi sesimi de kulaklığımdan duyabilir miyim?**  
*C: Evet, arayüzdeki "Kendi Sesimi Duy" onay kutusunu işaretlediğinizde dönüştürülen ses anlık olarak kulaklığınıza da gelir.*

**S: Ekran kartım AMD veya Intel, programı kullanabilir miyim?**  
*C: Evet, uygulama NVIDIA ekran kartı (CUDA) tespit edemezse otomatik olarak optimize edilmiş CPU moduna geçer. Ancak beklentinizi çok yüksek tutmamanızda fayda var:*
* *RVC yapay zeka mimarisi gerçek zamanlı ses dönüştürürken saniyede binlerce yoğun tensör ve matris işlemi hesaplar. Ekran kartlarındaki binlerce özel Tensor/CUDA çekirdeği yerine işlemcinin (CPU) sınırlı çekirdekleri devreye girdiğinde hesaplama süresi doğal olarak uzar.*
* *Bu durum; ses gecikmesinin (latency) artmasına (500ms - 1 saniye veya üzeri), seste anlık takılmalara, çıtırtılara ya da robotik kırılmalara yol açabilir.*
* *Ayrıca işlemci kullanımınız tavan yapabilir; arka planda oyun veya ağır programlar açıksa sistemde belirgin kasılmalar yaşanabilir.*
* *Özetle: Çok çekirdekli güçlü bir işlemciniz varsa temel denemeler ve sohbet için kullanılabilir; ancak oyunlarda ve canlı yayınlarda sıfır gecikmeli, akıcı ve berrak bir deneyim için NVIDIA RTX/GTX ekran kartı kesinlikle tavsiye edilir.*

---

## 👤 Geliştirici & İletişim

* **Geliştirici:** Ali Ücel
* **E-Posta:** [aliucel2011@gmail.com](mailto:aliucel2011@gmail.com)
* **GitHub:** [@ali-ucel](https://github.com/ali-ucel)

*Bu yazılımın tüm dağıtım ve fikri hakları Ali Ücel'e aittir.*
