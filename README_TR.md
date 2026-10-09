# Sincan Durak Takip (Android)

Bu proje, telefondan GitHub Actions kullanarak debug APK üretmek için hazırlanmış bir başlangıç projesidir.

## Özellikler
- OpenStreetMap / Overpass verisinden yakın çevredeki `bus_stop` duraklarını arar.
- Yakındaki durakları mesafeye göre listeler.
- Seçilen durağa 300 metre kaldığında titreşim ve bildirim verir.
- Takip, Android konum ön plan hizmetiyle sürer; bildirim çubuğunda sürekli bildirim gösterir.

## Önemli sınırlar
- Durak verisi EGO'nun resmî canlı verisi değil, OpenStreetMap verisidir; eksik veya yanlış olabilir.
- Bu sürüm otobüsün gerçek konumunu veya hat bilgisini izlemez; telefonun GPS konumuna göre seçilen durağa yaklaşmayı algılar.
- GPS doğruluğu, kapalı alanlar ve Android pil yönetimi uyarıyı etkileyebilir.
- İlk çalıştırmada internet, konum ve bildirim izinleri gerekir. Takibi başlatınca uygulama görünür bir sürekli bildirim gösterir.

## Bilgisayarsız APK üretme (telefon üzerinden)
1. GitHub hesabınla yeni bir **public** depo aç (ör. `sincan-durak-takip`).
2. Bu ZIP'i telefonda çıkar. İçindeki dosya ve klasörleri depoya yükle. GitHub mobil web'de `Add file` → `Upload files` kullanılabilir.
3. `Actions` sekmesine gir. İzin istenirse workflow çalıştırılmasına izin ver.
4. `Android APK oluştur` workflow'unu çalıştır (ya da dosya yüklenince otomatik başlar).
5. Workflow tamamlanınca `Artifacts` bölümünden `sincan-durak-takip-debug-apk` dosyasını indir.
6. ZIP artifact'ini aç, içindeki `app-debug.apk` dosyasına dokun. Android sorarsa tarayıcı/GitHub için “Bilinmeyen uygulamaları yükle” izni ver ve kur.
7. Uygulamayı aç; konum ve bildirim izinlerini ver. Durakları yenile, bir durak seç, **Takibi başlat** düğmesine bas.
8. Xiaomi/Redmi cihazında Ayarlar → Uygulamalar → Sincan Durak Takip → Pil tasarrufu bölümünde **Kısıtlama yok** seçeneğini kullan. Gerekirse otomatik başlatmaya izin ver.

## Derleme
GitHub Actions workflow'u Android SDK ve Gradle kurarak `assembleDebug` çalıştırır.
