# Cardly — Kartu Nama Digital

Aplikasi statis responsif untuk menyimpan foto kartu nama dan detail kontak di Google Drive. Siap dipasang sebagai GitHub Pages, tanpa server atau database aplikasi.

## Pasang di GitHub Pages

1. Buat repository baru bernama `cardly` di akun GitHub, lalu unggah semua file di folder ini ke root branch `main`.
2. Buka **Settings → Pages**. Pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu simpan.
3. Di [Google Cloud Console](https://console.cloud.google.com/), buat/pilih project, aktifkan **Google Drive API**, lalu siapkan OAuth consent screen untuk akun Google yang akan dipakai.
4. Atur OAuth audience sebagai **Internal** di Google Workspace perusahaan, lalu buat **OAuth client ID** bertipe **Web application**. Isi **Authorized JavaScript origins** dengan alamat origin GitHub Pages, misalnya `https://namaakun.github.io` (tanpa path `/cardly`). Aplikasi juga memeriksa domain email `to-hatsu.info`; ubah `ALLOWED_DOMAIN` di `app.js` bila domain perusahaan berbeda.
5. Buka situs GitHub Pages di HP/komputer, pilih **Login Google Workspace**, masukkan Client ID, lalu setujui akses Drive. Saat login pertama, aplikasi otomatis membuat folder `Cardly` di Drive akun tersebut. Login berikutnya membuka koleksi yang sama. Ulangi login pada perangkat lain menggunakan akun perusahaan yang sama.

## Fitur

- OCR otomatis menggunakan Tesseract.js untuk kartu berbahasa Indonesia, Inggris, dan Jepang. Hasil pembacaan mengisi form untuk diperiksa dan dikoreksi sebelum disimpan. OCR berjalan di browser; koneksi internet dibutuhkan saat memuat library dan data bahasa pertama kali.
- Pilihan antarmuka Bahasa Indonesia, English, dan 日本語.
- Kredit aplikasi: **Designed & created by Wahyu**.

- Tampilan responsif dengan navigasi mobile.
- Foto kartu dapat diambil langsung dari kamera HP.
- Catatan kontak, perusahaan, email, nomor telepon, website, dan catatan pertemuan.
- Pencarian, favorit, urutkan nama/terbaru, dan ringkasan koleksi.
- Setiap akun Google Workspace memiliki folder `Cardly` dan koleksi kartu masing-masing di Drive pribadi pemilik akun. Folder bersama yang dikirim sebelumnya tidak digunakan untuk data personal karena metadata Drive menunjukkan akses “siapa pun dengan link dapat mengedit”.
- Cache lokal untuk melihat koleksi di perangkat yang sama.

## Privasi & catatan

Aplikasi meminta scope `drive.file`, yang membatasi akses pada file yang dibuat atau dipilih untuk Cardly. Tidak ada server Cardly; source dan halaman di-host GitHub, sedangkan data kontak dan fotonya berada di Drive pribadi tiap pemilik. Akun Workspace lain tidak mendapatkan folder atau file milik pengguna tersebut. OAuth Client ID hanya identifier publik; token akses sementara tidak ditulis ke source. Pengguna dapat mencabut izin melalui akun Google.

Untuk alasan keamanan, jangan commit OAuth client secret atau token ke repo. OCR membantu membaca kartu, tetapi hasilnya tetap perlu diperiksa sebelum disimpan karena kualitas foto dan jenis huruf memengaruhi ketepatannya.
