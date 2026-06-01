# ⚡ URL Media Scanner

Tool untuk scan URL video & gambar dari halaman web, langsung di Termux.
Hasil scan otomatis tersimpan ke file di `/sdcard/url-scanner/`.

---

## 📋 Fitur

- Deteksi video: `mp4`, `m3u8`, `ts`, `mkv`, `webm`, `flv`, dan lainnya
- Deteksi gambar: `jpg`, `png`, `webp`, `gif`, `svg`, `avif`, dan lainnya
- Deteksi audio: `mp3`, `aac`, `ogg`, `wav`, `flac`, `m4a`, dan lainnya
- Deteksi dokumen: `pdf`, `zip`, `rar`, `7z`, dan lainnya
- **Deep scan** — masuk ke embed/iframe/player otomatis sampai 4 layer
- Hasil scan tersimpan otomatis ke file `.txt` dengan nama dari URL halaman
- Tidak butuh root

---

## 📁 Struktur File

```
url-scanner/
├── setup.py          ← jalankan PERTAMA KALI untuk install otomatis
├── mediascan.py      ← logic utama (jangan dihapus)
├── ui.py             ← aplikasi utama (jalankan setiap pakai)
├── requirements.txt  ← daftar library (jangan dihapus)
├── uninstall.py      ← untuk hapus semua jika tidak dipakai lagi
└── README.md         ← panduan ini
```

---

## 🔧 Syarat Sebelum Mulai

1. Aplikasi **Termux** sudah terinstall
   - Download dari **F-Droid**, bukan Play Store
   - https://f-droid.org/packages/com.termux/

2. **Python** sudah terinstall di Termux
   ```
   pkg update && pkg install python -y
   ```

3. Semua **6 file** di atas sudah ada di folder `~/url-scanner/`

---

## 🚀 Instalasi

### Cara 1 — Git Clone (Direkomendasikan)

Install git dulu jika belum ada:
```
pkg install git -y
```

Lalu clone repo langsung ke Termux:
```
git clone https://github.com/pembri/url-scanner ~/url-scanner
cd ~/url-scanner
python setup.py
```

Selesai! Semua file otomatis ter-download sekaligus.

---

### Cara 2 — Manual (Download file satu per satu)

Setelah semua file ada di folder `~/url-scanner/`, cukup jalankan:

```
cd ~/url-scanner
python setup.py
```

`setup.py` akan otomatis mengurus semuanya — izin storage, install library, buat folder hasil scan.
Ikuti instruksi yang muncul di layar, tap **Izinkan** saat ada popup izin storage.

Setelah setup selesai, langsung jalankan:

```
python ui.py
```

---

## 📖 Cara Pakai

1. Jalankan tool:
   ```
   cd ~/url-scanner
   python ui.py
   ```

2. Masukkan URL halaman yang ingin di-scan, contoh:
   ```
   https://contohwebsite.com/halaman-video/
   ```

3. Tekan **Enter** dan tunggu proses scan selesai

4. Hasil tampil di terminal dikelompokkan per kategori (video, gambar, audio, dll)

5. Hasil juga otomatis tersimpan di `/sdcard/url-scanner/` dengan nama file dari URL, contoh:
   ```
   nama-halaman-video_04-15.txt
   ```

6. Ketik `q` lalu Enter untuk keluar

---

## 📂 Lokasi File Hasil Scan

```
/sdcard/url-scanner/
```

Buka dari **File Manager** HP — URL di dalam file sudah utuh, bisa langsung di-copy.

---

## 🗑 Uninstall

Jika ingin menghapus tool ini sepenuhnya:

```
cd ~/url-scanner
python uninstall.py
```

Ikuti instruksi — akan ada pilihan apakah file hasil scan ikut dihapus atau tidak.

---

## ❓ Catatan

- Tool ini membaca **HTML statis** — konten yang di-load via JavaScript tidak terdeteksi
- URL streaming dengan token/expired kemungkinan tidak terdeteksi

---

## 🛠 Troubleshooting

| Masalah | Solusi |
|--------|--------|
| `ModuleNotFoundError: No module named 'rich'` | Jalankan ulang `python setup.py` |
| Hasil scan selalu kosong | Website menggunakan JavaScript untuk load media |
| File tidak muncul di `/sdcard/url-scanner/` | Jalankan `termux-setup-storage`, tap Izinkan |

---

*URL Media Scanner — dibuat untuk Termux*
