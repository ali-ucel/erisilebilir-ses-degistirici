# Değişiklik Günlüğü / Changelog

## v1.0.3 (2026-11-26)
- **Sunucu Bağlantısı & Kayıt/Giriş İyileştirmesi:** Bulut sunucusu uykudan uyanırken (`cold start`) yaşanan `3.5s`/`5s` zaman aşımı hatası giderildi; sunucu keşfi (`25s`), kayıt/giriş (`30s`) ve token doğrulama (`15s`) süreleri artırıldı.
- **Varsayılan Adres Temizliği:** Eski tünel varsayılanı kaldırılıp `https://voicechanger-server.onrender.com` doğrudan standart hale getirildi ve 7/24 uyanık kalma zamanlayıcısı (keep-alive) eklendi.

## v1.0.2 (2026-11-26)
- **25 Dil Desteği / 25 UI Languages:** `tr`, `en`, `de`, `fr`, `es`, `it`, `pt`, `ru`, `ar`, `ja`, `ko`, `zh-CN`, `zh-TW`, `sv`, `no`, `da`, `fi`, `hu`, `bg`, `el`, `hi`, `vi`, `az`, `kk`, `uz`.
- **Otomatik Dil Algılama:** İlk açılışta Windows arayüz dilini otomatik algılar; desteklenmeyen sistem dillerinde İngilizce ile açılır. Ayarlar menüsünden dil değiştirilebilir.
- **18 Dilli Kurulum Sihirbazı (Inno Setup):** Açılışta dil seçme ekranı, yerelleştirilmiş uyarılar, NVDA/SAPI sesli yönlendirme ve seçilen dilin `settings.json` dosyasına aktarılması.
- **Tam Yerelleştirilmiş Modüller:** Ana uygulama, Hakkında/Yardım, Tek & Toplu Model Eğitimi (en fazla 3 model), Metinden Sese (TTS) iletişim kutusu ve Şarkı/Ses Efekti Ayırıcı (Demucs AI).
- **Dokümantasyon & Web:** Ayrı [readme_türkçe.md](readme_türkçe.md) ve [readme_en.md](readme_en.md) dosyaları ile erişilebilir GitHub Pages tanıtım sayfası eklendi.

## v1.0.1 (2026-11-24)
- **Şarkı ve Ses Efekti Ayırıcı (Demucs AI):** Eğitim sihirbazında ve bağımsız pencere olarak temiz vokal ayrıştırma ile erişilebilir önizleme penceresi.
- **Güvenli Kurulum Temizliği:** Kullanıcı modellerini ve ayarlarını koruyarak eski sürüm dosyalarını temizleme onayı.
- **Sunucu & Oturum İyileştirmeleri:** Kayıt ve erişim kontrollerinin senkronizasyonu.

## v1.0.0 (2026-11-23)
- İlk kararlı sürüm: %100 NVDA uyumlu wxPython arayüzü, gerçek zamanlı RVC v2 ses dönüştürme, 690+ model havuzu, model eğitim sihirbazı ve erişilebilir Virtual Audio Cable kurulum yardımcısı.
