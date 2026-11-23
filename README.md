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

👉 **[Erişilebilir_Ses_Değiştirici_installer.exe İndir (v1.0.0)](https://github.com/ali-ucel/erisilebilir-ses-degistirici/releases/latest/download/Erisilebilir_Ses_Degistirici_installer.exe)**  
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

1. **[Erişilebilir_Ses_Değiştirici_installer.exe](https://github.com/ali-ucel/erisilebilir-ses-degistirici/releases/latest/download/Erisilebilir_Ses_Degistirici_installer.exe)** dosyasını indirin.
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
*C: Evet, uygulama NVIDIA ekran kartı olmadığında otomatik olarak optimize edilmiş CPU moduna geçer.*

---

## 👤 Geliştirici & İletişim

* **Geliştirici:** Ali Ücel
* **E-Posta:** [aliucel2011@gmail.com](mailto:aliucel2011@gmail.com)
* **GitHub:** [@ali-ucel](https://github.com/ali-ucel)

*Bu yazılımın tüm dağıtım ve fikri hakları Ali Ücel'e aittir.*
