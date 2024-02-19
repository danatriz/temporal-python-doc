# Integrasi dengan Microservice

## Menerapkan Activity Method

Berkas `translate.py` berisi metode (greet\_in\_spanish) yang menggunakan layanan mikro untuk mendapatkan sapaan yang disesuaikan dalam bahasa Spanyol. Berkas ini juga berisi metode utilitas (`call_service`) yang Aktivitas gunakan untuk memanggil layanan mikro.

1. Buka berkas `translate.py` (berlokasi di subdirektori `practice`) di editor
2. Buatlah Aktivitas baru yang akan mendapatkan pesan perpisahan kustom dari layanan mikro.
   1. Salin metode `greet_in_spanish`
   2. Ganti nama metode baru (gunakan nama yang valid)
   3. Ubah `get-spanish-greeting` dalam metode baru ini menjadi `get-spanish-farewell`
   4. Simpan perubahan Anda ke berkas ini



## Registrasi Activity Method

1. Buka berkas `worker.py` (berlokasi di subdirektori `practice`) di editor
2. Modifikasi baris-baris yang mendaftarkan Aktivitas baru Anda dengan Pekerja (petunjuk: Anda akan menggunakan nama yang Anda gunakan untuk metode baru di langkah sebelumnya).
3. Simpan perubahan Anda ke berkas ini.

## Memodifikasi Workflow untuk mengeksekusi Activity Baru

1.Buka berkas `greeting.py` (berlokasi di subdirektori `practice`) di editor&#x20;

2\. Cari pesan TODO, buka komentar di bawahnya, dan kemudian ubah baris-baris tersebut untuk menjalankan metode Aktivitas yang Anda buat

&#x20;3\. Simpan perubahan Anda ke berkas ini



## Menjalankan Microservice dan Workflow

1. Mulai layanan mikro dengan menjalankan `python microservice.py` di terminal
2. Di terminal lain, mulai Pekerja Anda dengan menjalankan `python worker.py`
3. Di terminal ketiga, jalankan Alur Kerja Anda dengan menjalankan `python starter.py Donna` (ganti `Donna` dengan nama Anda sendiri).

Jika masih ada waktu, coba dengan kegagalan Aktivitas dan percobaan ulang dengan menghentikan layanan mikro (tekan Ctrl-C di terminalnya) dan menjalankan ulang Alur Kerja. Lihatlah antarmuka web untuk melihat status Alur Kerja dan Aktivitasnya. Setelah beberapa detik, mulai kembali layanan mikro dengan menjalankan perintah yang sama seperti yang digunakan untuk memulainya sebelumnya. Anda seharusnya menemukan bahwa Alur Kerja akan berhasil diselesaikan setelah percobaan ulang Aktivitas berikutnya
