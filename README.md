# Cardly

Aplikasi web responsif untuk memotret kartu nama, membaca teks dengan OCR, lalu menyimpan dan mencari kontak.

## Cara pakai

1. Buka aplikasi dari HP atau komputer.
2. Pilih **Tambah kartu nama**, lalu ambil foto dengan kamera atau pilih foto.
3. Periksa dan koreksi hasil OCR, kemudian tekan **Simpan**.

Tidak perlu login Google atau mengisi OAuth Client ID. Bahasa awal aplikasi adalah Jepang; tersedia juga Bahasa Indonesia dan English. OCR berjalan di browser dan hasilnya perlu diperiksa sebelum disimpan.

## Penyimpanan saat ini

Kartu tersimpan di penyimpanan browser pada perangkat yang digunakan. Data tidak tersinkron ke perangkat lain dan dapat hilang jika data situs/browser dihapus. Penyimpanan ke Google Drive perusahaan belum tersedia pada versi ini.

## Fitur

- Kamera HP dan unggah foto.
- OCR untuk bahasa Jepang, Inggris, dan Indonesia.
- Pencarian, favorit, dan pengurutan kartu.
- Antarmuka responsif untuk HP dan komputer.
- Designed & created by Wahyu.

## Pengembangan

Aplikasi ini berupa file statis dan dapat di-host di GitHub Pages. Agar kartu bisa tersimpan ke Drive perusahaan tanpa meminta setiap pengguna menyiapkan OAuth, diperlukan backend yang aman untuk mengelola akun dan folder Drive. Jangan menaruh kredensial rahasia di JavaScript publik.
