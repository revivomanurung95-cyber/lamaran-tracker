# Lamaran Tracker

Pelacak lamaran kerja berbasis web: dashboard, papan kanban, analisis, tindak lanjut, materi harian, modul karier, dan Belajar pajak (topik, glosarium, 16 kalkulator).

Situs ini **statis** dan berjalan di GitHub Pages. Tidak ada server dan tidak ada login. Data tiap pengguna tersimpan di **browser masing-masing**, jadi data orang yang membuka situs ini tidak tercampur.

## Pasang di GitHub Pages (±10 menit)

### 1. Buat akun dan repositori
1. Daftar di <https://github.com/signup> (gratis), lalu login.
2. Klik **+** di pojok kanan atas → **New repository**.
3. *Repository name*: `lamaran-tracker`. Pilih **Public**. Biarkan opsi lain kosong. Klik **Create repository**.

### 2. Unggah file
1. Ekstrak file ZIP dari paket ini. Di dalamnya ada `index.html`, `sw.js`, `manifest.webmanifest`, `README.md`, serta folder `css`, `js`, dan `assets`.
2. Di halaman repositori yang masih kosong, klik tautan **uploading an existing file**.
3. **Seret semua isi folder hasil ekstrak** (bukan folder pembungkusnya) ke area unggah. Seret folder `css`, `js`, `assets` sekaligus supaya struktur folder ikut terunggah.
4. Tunggu sampai semua file muncul di daftar, lalu klik **Commit changes**.
5. Pastikan di halaman repositori `index.html` terlihat langsung di daftar paling atas, bukan di dalam folder lain.

### 3. Aktifkan GitHub Pages
1. Buka tab **Settings** pada repositori → menu **Pages** di sisi kiri.
2. Di *Build and deployment* → *Source*: pilih **Deploy from a branch**.
3. *Branch*: pilih **main**, folder **/ (root)**, lalu klik **Save**.
4. Tunggu 1–2 menit lalu muat ulang halaman Pages. Akan muncul tulisan *Your site is live at* `https://USERNAME.github.io/lamaran-tracker/`.

Bagikan alamat itu ke siapa pun. Tiap orang yang membuka akan mulai dengan data kosong miliknya sendiri.

## Memindahkan data dari Google Sheets
1. Buka spreadsheet lamaranmu, pilih tab yang berisi tabel lamaran.
2. **File → Unduh → Nilai dipisahkan koma (.csv)**.
3. Buka situs → di layar sambutan klik **Pilih file…** (atau Pengaturan → **Impor / pulihkan file…**) dan pilih CSV itu.

Header dicari otomatis (butuh kolom `PERUSAHAAN` dan `POSISI`). Tanggal bergaya "Senin, 03 Agustus 2026" terbaca. Impor CSV menambah ke data yang sudah ada.

## Cadangan dan pindah perangkat
Karena data ada di browser, **unduh cadangan secara berkala**: Pengaturan → **Unduh cadangan (.json)**. Untuk pindah perangkat atau browser, pulihkan file itu lewat **Impor / pulihkan file…**. Aplikasi akan mengingatkan bila cadangan terakhir sudah lebih dari 14 hari.

Data hilang bila kamu menghapus data situs browser, memakai mode privat, atau berpindah alamat situs (misalnya dari alamat `github.io` ke domain sendiri). Cadangan melindungi dari semua itu.

## Memperbarui situs
- **Lewat web:** buka file di repositori → ikon pensil → ubah → **Commit changes**. Atau **Add file → Upload files** untuk menimpa file.
- Situs diperbarui dalam sekitar 1 menit. Bila masih tampil versi lama, tekan **Ctrl+F5**.
- **Lewat Git (opsional, bagus untuk belajar):**
  ```
  git clone https://github.com/USERNAME/lamaran-tracker.git
  cd lamaran-tracker
  # ubah file, lalu:
  git add .
  git commit -m "Ubah materi harian"
  git push
  ```

Mengunggah pertama kali lewat Git:
```
cd lamaran-tracker
git init
git add .
git commit -m "Versi pertama"
git branch -M main
git remote add origin https://github.com/USERNAME/lamaran-tracker.git
git push -u origin main
```

## Mencoba di komputer sendiri
Klik dua kali `index.html` untuk membukanya di browser. Semua fitur jalan, hanya tanpa mode aplikasi terpasang (service worker).

## Peta kode
| File | Fungsi |
|---|---|
| `index.html` | Kerangka halaman dan urutan pemuatan skrip |
| `css/style.css` | Warna (`--c1`…`--c8` di bagian atas), font, tata letak |
| `js/storage.js` | Penyimpanan di browser, impor CSV, cadangan |
| `js/app.js` | Inti: tracker, analisis, pengaturan |
| `js/belajar.js` | Tampilan materi harian, modul, belajar pajak |
| `js/data-harian.js` | 36 materi harian (tambah blok baru di array `DAILY`) |
| `js/data-modul.js` | 7 modul karier (array `MODULES`) |
| `js/data-pajak.js` | Topik, glosarium, tabel TER, kalkulator (`TAX_TOPICS`, `GLOSSARY`, `CALCS`) |
| `sw.js`, `manifest.webmanifest` | Agar bisa dipasang sebagai aplikasi dan dibuka tanpa internet |
| `assets/` | Chart.js, font, dan ikon (semuanya disimpan lokal, tanpa CDN) |

## Jika ada masalah
- **Halaman 404:** Pages belum selesai dibangun (tunggu 2 menit) atau `index.html` tidak berada di akar repositori.
- **Halaman putih:** nama folder atau file berbeda huruf besar/kecil dari yang di atas (GitHub peka huruf besar-kecil), atau ada file yang belum terunggah. Buka tab **Actions** atau konsol browser (F12) untuk melihat pesan error.
- **Data tidak muncul:** kamu membuka alamat atau browser yang berbeda. Data terpisah per browser dan per alamat. Pulihkan dari cadangan.
- **Versi lama tetap tampil:** tekan Ctrl+F5, atau naikkan angka `CACHE` di `sw.js` (`lt-v1` → `lt-v2`).

## Catatan
- Materi pajak bersifat edukatif dan disederhanakan. Aturan berubah, jadi cek pajak.go.id. Terakhir diverifikasi 12 Oktober 2026.
- Repositori publik aman karena datamu tidak ada di repositori, hanya di browsermu. Jangan mengunggah file berisi data pribadi ke repositori.
