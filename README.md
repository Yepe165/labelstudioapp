# Label Studio — PWA

Aplikasi desain & cetak label produk (parfum, kopi, makanan/minuman, dll).

## Struktur folder ini

```
├── index.html                     ← auto-redirect ke app (buat GitHub Pages)
├── label-studio-semua-produk.html ← aplikasi utama
├── manifest.json                  ← identitas PWA (nama, warna, icon)
├── sw.js                          ← service worker (mode offline)
└── icons/
    ├── icon-152.png
    └── icon-192.png
```

Semua path di dalam file sudah pakai **path relatif**, jadi folder ini bisa
langsung diupload apa adanya — tidak perlu diubah apa-apa lagi.

## Langkah 1 — Upload ke GitHub

1. Buat repository baru di GitHub (public), misal `label-studio-app`.
2. Upload **isi folder ini** (bukan file zip-nya) ke root repo:
   - drag semua file & folder (`index.html`, `label-studio-semua-produk.html`,
     `manifest.json`, `sw.js`, folder `icons/`) ke halaman "Add file → Upload files"
   - Commit.

## Langkah 2 — Aktifkan GitHub Pages

1. Buka repo → **Settings → Pages**.
2. Source: **Deploy from a branch**.
3. Branch: `main` (atau `master`), folder: `/ (root)`.
4. Save, tunggu ± 1 menit.
5. URL akan muncul, contohnya:
   `https://username.github.io/label-studio-app/`
6. Buka URL itu — harus langsung menampilkan aplikasi Label Studio.

## Langkah 3 — Convert ke APK

Pakai **PWABuilder** (gratis, tanpa install apa-apa):

1. Buka https://www.pwabuilder.com
2. Tempel URL GitHub Pages dari Langkah 2 → klik **Start**.
3. PWABuilder otomatis membaca `manifest.json` (icon 152 & 192 akan terbaca di sini).
4. Klik tab **Android** → **Generate Package**.
5. Download file `.apk` / `.aab` yang dihasilkan.
6. Install APK tersebut di HP Android (aktifkan "Install dari sumber tidak dikenal"
   jika diminta), atau upload `.aab` ke Google Play Console kalau mau publish resmi.

### Alternatif lain
- https://median.co — lebih banyak opsi kustomisasi (splash screen, nama app, dll)
- https://appilix.com — cukup masukin URL, langsung jadi APK

## Catatan

- Kalau nanti update isi HTML/manifest/sw.js dan upload ulang ke GitHub,
  naikkan angka versi di `sw.js` (`CACHE_NAME = "label-studio-cache-v3"` dst)
  supaya pengguna yang sudah install APK mendapat versi terbaru.
- Icon yang dipakai sengaja disederhanakan jadi hanya `icon-152.png` dan
  `icon-192.png` sesuai kebutuhan.
