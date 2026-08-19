[README.md](https://github.com/user-attachments/files/31203575/README.md)
# Scan KTP → Excel (versi web)

Web app satu-file yang membaca banyak foto KTP (miring, buram, hitam-putih,
berwarna) dan menuliskan hasilnya ke Excel — semuanya jalan **di browser
pengguna**, tanpa server, tanpa upload data ke mana pun. Cocok untuk data
sensitif seperti KTP.

## Cara Deploy ke GitHub Pages (gratis, ~5 menit)

1. Buat repository baru di GitHub, misalnya `scan-ktp-excel`.
2. Upload file `index.html` ini ke repo tersebut (drag & drop lewat web GitHub
   juga bisa — tidak perlu command line):
   - Buka repo → tombol **"Add file" → "Upload files"** → pilih `index.html` → **Commit changes**.
3. Aktifkan GitHub Pages:
   - Buka tab **Settings** repo → menu **Pages** (di sidebar kiri) →
   - Pada **Source**, pilih branch `main` dan folder `/ (root)` → **Save**.
4. Tunggu ±1 menit, lalu buka:
   ```
   https://<username-kamu>.github.io/scan-ktp-excel/
   ```
   Web app-nya sudah live dan bisa diakses siapa saja lewat link itu.

## Cara Pakai
1. Buka link di atas.
2. Klik area unggah atau seret foto-foto KTP ke sana (bisa banyak sekaligus).
3. Klik **"Mulai scan semua"** — tunggu sampai semua kartu bertanda selesai/perlu cek.
4. Klik **"Unduh Excel"** — file `.xlsx` langsung ter-download ke perangkat.

## Kenapa aman untuk data KTP?
Semua pemrosesan (baca gambar, pelurusan gambar miring, OCR, penulisan Excel)
terjadi **di dalam browser pengguna** memakai JavaScript (Tesseract.js untuk
OCR, SheetJS untuk Excel). Tidak ada foto atau data yang dikirim ke server
manapun — bahkan setelah dihosting di GitHub Pages, GitHub hanya menyajikan
file HTML/JS-nya, bukan menerima data KTP.

## Kalau mau coba dulu tanpa GitHub
Buka langsung `index.html` ini dua kali klik di komputer kamu (jalan di
browser lokal) — hanya saja beberapa browser membatasi akses file lokal;
kalau ada masalah, cara paling gampang adalah tetap deploy ke GitHub Pages.

## Batasan
- Akurasi bergantung kualitas foto. Semakin miring/buram, makin besar
  kemungkinan ada karakter yang salah baca — makanya ada kolom
  **"Perlu Cek"** yang menandai baris untuk ditinjau ulang.
- OCR di browser (Tesseract.js) sedikit lebih lambat dibanding versi Python
  yang jalan di komputer biasa, tapi imbasnya: privasi data lebih terjaga
  karena tidak ada yang diunggah ke mana pun.
- Untuk volume sangat besar (ratusan KTP sekaligus), proses di browser bisa
  makan waktu — proses berjalan satu per satu (sequential) supaya tab
  browser tidak macet.
