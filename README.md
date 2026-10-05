# PuzzleCam — Yapboz Kamerası

Elle kontrol edilen, tamamen tarayıcıda çalışan bir fotomaton uygulaması. Kurulum, backend veya bağımlılık gerektirmez.

Ellerinle bir çerçeve oluşturup fotoğraf çek, fotoğraf siyah-beyaz fotomaton efektiyle 3x3 puzzle'a dönüşsün, pinch hareketiyle puzzle'ı tamamla ve fotoğraf şeridine kaydet.

## Gereksinimler

- Chrome veya Edge (önerilir)
- Web kamerası
- İnternet bağlantısı (MediaPipe modeli ilk açılışta yüklenir, ~10MB)
- Yerel sunucu (dosya doğrudan açılamaz)

## Kurulum

```bash
git clone https://github.com/ElifPasha/puzzle-cam.git
cd puzzle-cam
```

VS Code'da [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) eklentisini kur ve **Go Live**'a tıkla. Ardından tarayıcıda aç:

```
http://localhost:5500
```

Tarayıcı istediğinde kamera iznini ver.

## Proje Yapısı

```
puzzle-cam/
├── index.html        # Giriş noktası
├── app.js            # Tüm mantık (takip, puzzle, galeri)
└── css/
    └── styles.css    # Stiller
```

## Hareketler

| Hareket | Eylem |
|---|---|
| İki elle pinch | Alanı dondur ve geri sayımı başlat |
| Tek elle parça üzerinde pinch | Puzzle parçasını sürükle |
| Yumruk (basılı tut) | Tamamlanan puzzle'ı kaydet / tahtayı sıfırla |

## Nasıl Çalışır?

1. İki elini kameraya göster ve pinch yaparak çekim alanını belirle.
2. Geri sayım boyunca pinch'i koru, fotoğraf otomatik çekilir.
3. Fotoğraf, siyah-beyaz filtreyle 3x3 puzzle'a bölünür.
4. Parçaları pinch hareketiyle yerleştir.
5. Tamamlayınca yumruğunu kapat, puzzle parçalanma animasyonuyla şeride kaydedilir.
6. 3 puzzle biriktirince şeridi indir.

## Teknolojiler

- [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) `v0.10.14` — el landmark tespiti
- Canvas 2D API — render, puzzle parçaları, fotomaton efekti
- JavaScript (ES Modules), framework yok

Tüm bağımlılıklar CDN üzerinden yüklenir.
