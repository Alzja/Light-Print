# 🚀 Cara Build APK via GitHub Actions (Tanpa Android Studio)

## Yang Kamu Butuhkan
- Akun GitHub (gratis) → github.com
- Semua file source code EpsonPrint

---

## LANGKAH 1 — Buat Repository di GitHub

1. Buka **github.com** → login
2. Klik tombol **"New"** (pojok kiri atas)
3. Isi nama repository: `EpsonPrint`
4. Pilih **Public** (gratis unlimited build)
5. Klik **"Create repository"**

---

## LANGKAH 2 — Upload Semua File

### Cara A: Lewat Web Browser (Paling Mudah)

1. Di halaman repository yang baru dibuat, klik **"uploading an existing file"**
2. Drag & drop seluruh folder `EpsonPrint-SourceCode`
3. Pastikan struktur file seperti ini:
   ```
   EpsonPrint/
   ├── .github/
   │   └── workflows/
   │       └── build.yml          ← FILE INI WAJIB ADA
   ├── app/
   │   ├── build.gradle
   │   └── src/main/
   │       ├── AndroidManifest.xml
   │       ├── res/
   │       │   ├── values/themes.xml
   │       │   └── xml/device_filter.xml
   │       └── java/com/epsonprint/
   │           ├── MainActivity.kt
   │           ├── file/FileRenderer.kt
   │           ├── printer/EscPRasterEncoder.kt
   │           ├── usb/UsbPrinterManager.kt
   │           └── ui/PrintViewModel.kt
   ├── build.gradle
   ├── settings.gradle
   └── gradle.properties
   ```
4. Scroll ke bawah → klik **"Commit changes"**

### Cara B: Lewat Git (Kalau Sudah Install Git)
```bash
git clone https://github.com/USERNAME/EpsonPrint.git
# Copy semua file ke folder tersebut
git add .
git commit -m "Initial commit"
git push origin main
```

---

## LANGKAH 3 — Cek Build Berjalan Otomatis

1. Setelah upload, buka tab **"Actions"** di repository
2. Kamu akan lihat workflow **"Build EpsonPrint APK"** sedang berjalan
3. Tunggu sekitar **3–7 menit**
4. Kalau berhasil → muncul tanda ✅ hijau

> Kalau merah ❌ → klik untuk lihat error, biasanya ada file yang kurang

---

## LANGKAH 4 — Download APK

1. Di tab **Actions**, klik workflow run yang ✅ hijau
2. Scroll ke bawah ke bagian **"Artifacts"**
3. Klik **"EpsonPrint-debug-1"** untuk download
4. Extract ZIP → dapat file `app-debug.apk`

---

## LANGKAH 5 — Install APK di HP

1. Pindahkan `app-debug.apk` ke HP (via kabel / Google Drive / WhatsApp)
2. Di HP: **Pengaturan → Keamanan → Izinkan sumber tidak dikenal**
3. Buka file manager → tap file APK → Install
4. Buka app **EpsonPrint** ✅

---

## 🔁 Update App ke Depannya

Setiap kali kamu edit kode dan push ke GitHub:
```
Edit file → Commit → Push → GitHub Actions otomatis build APK baru
```

---

## ❓ FAQ

**Q: Berapa lama build sekali?**
A: Pertama kali ~7 menit (download dependencies). Build berikutnya ~3 menit karena ada cache.

**Q: Berapa banyak build gratis?**
A: GitHub Actions gratis **2.000 menit/bulan** untuk repository public. Lebih dari cukup.

**Q: APK-nya aman diinstall?**
A: Ini debug APK — aman untuk testing. Untuk distribusi publik nanti perlu signing (release APK).

**Q: Bisa build langsung dari HP?**
A: Bisa! GitHub bisa diakses dari browser HP. Upload file, tunggu build, download APK — semua dari HP.
