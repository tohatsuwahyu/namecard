# Cardly — Kartu Nama Digital

Aplikasi statis responsif untuk menyimpan foto kartu nama dan detail kontak di Google Drive. Siap dipasang sebagai GitHub Pages, tanpa server atau database aplikasi.

## Pasang di GitHub Pages

1. Buat repository baru bernama `cardly` di akun GitHub, lalu unggah semua file di folder ini ke root branch `main`.
2. Buka **Settings → Pages**. Pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu simpan.
3. Di [Google Cloud Console](https://console.cloud.google.com/), buat/pilih project dan aktifkan **Google Drive API**.
4. Siapkan Google Auth Platform dengan **Audience: External**. Buat satu OAuth Client ID bertipe **Web application** untuk aplikasi; pada **Authorized JavaScript origins**, masukkan `https://tohatsuwahyu.github.io` (tanpa `/namecard`). Jika status masih Testing, tambahkan akun pengguna sebagai test users.
5. Pemilik aplikasi memasang Client ID tersebut satu kali pada konfigurasi `GOOGLE_CLIENT_ID` di `app.js`. Pengguna tidak perlu membuat project Cloud atau memasukkan Client ID: mereka cukup menekan **Login dengan Google** dan menyetujui akses Drive. Kartu disimpan di folder `Cardly` pada Drive akun yang mereka pilih.

## Fitur

- OCR berjalan di browser. Bahasa antarmuka dan OCR default adalah Jepang (dengan Inggris); opsi Indonesia menggunakan model Indonesia + Inggris. Area kartu dipotong otomatis bila terdeteksi, dan teks mentah OCR bisa dibuka untuk pengecekan. Foto perlu cukup dekat, lurus, dan terang agar hasilnya baik. Koneksi internet dibutuhkan untuk memuat library dan model bahasa.
- Pilihan antarmuka Bahasa Indonesia, English, dan 日本語.
- Kredit aplikasi: **Designed & created by Wahyu**.

- Tampilan responsif dengan navigasi mobile.
- Foto kartu dapat diambil langsung dari kamera HP.
- Catatan kontak, perusahaan, email, nomor telepon, website, dan catatan pertemuan.
- Pencarian, favorit, urutkan nama/terbaru, dan ringkasan koleksi.
- Setiap akun Google memiliki folder `Cardly` dan koleksi kartu masing-masing di Drive pribadi pemilik akun. Folder bersama yang dikirim sebelumnya tidak digunakan untuk data personal karena metadata Drive menunjukkan akses “siapa pun dengan link dapat mengedit”.
- Cache lokal untuk melihat koleksi di perangkat yang sama.

## OCR berbasis API AI (opsional)

Aplikasi tidak memerlukan API AI untuk fungsi OCR dasar. Tesseract membaca karakter di perangkat; untuk lebih baik membedakan nama, jabatan, dan perusahaan, layanan vision/AI bisa ditambahkan sebagai tahap ekstraksi. API key tidak boleh ditaruh di JavaScript publik GitHub Pages. Integrasi seperti itu memerlukan backend yang menyimpan secret dan perlu mengirim foto kartu ke layanan tersebut.

## Privasi & catatan

Aplikasi meminta scope `drive.file`, yang membatasi akses pada file yang dibuat atau dipilih untuk Cardly. Tidak ada server Cardly; source dan halaman di-host GitHub, sedangkan data kontak dan fotonya berada di Drive pribadi tiap pemilik. Akun Workspace lain tidak mendapatkan folder atau file milik pengguna tersebut. OAuth Client ID hanya identifier publik; token akses sementara tidak ditulis ke source. Pengguna dapat mencabut izin melalui akun Google.

Untuk alasan keamanan, jangan commit OAuth client secret atau token ke repo. OCR membantu membaca kartu, tetapi hasilnya tetap perlu diperiksa sebelum disimpan karena kualitas foto dan jenis huruf memengaruhi ketepatannya.

