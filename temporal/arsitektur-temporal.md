# Arsitektur Temporal

## Temporal Server

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Server Temporal terdiri dari layanan frontend, ditambah layanan backend yang bekerja sama untuk mengelola eksekusi kode pada aplikasi yang berjalan dan terintegrasi dengan Temporal. Semua layanan dapat dilaksanakan secara horizontal dan produksi environtment yang menjalankan beberapa instance dari masing-masing layanan yang diterapkan di beberapa perangkat untuk meningkatkan kinerja dan ketersediaan.

Klien berkomunikasi dengan Server Temporal dengan mengeluarkan permintaan ke Layanan Frontend ini. Layanan Frontend kemudian berkomunikasi dengan layanan backend, jika diperlukan untuk memenuhi permintaan, dan kemudian mengembalikan respons ke klien. Komunikasi ke dan di dalam Cluster dilakukan menggunakan gRPC, sebuah framework RPC open source berperforma tinggi populer yang awalnya dikembangkan di Google dan kini menjadi bagian dari ekosistem Cloud Native Computing Foundation. Pesan-pesan itu sendiri dikodekan menggunakan Protocol Buffer, sebuah mekanisme serialisasi sumber terbuka yang awalnya juga dikembangkan di Google.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Semua komunikasi ini dapat diamankan dengan TLS, yang mengenkripsi data saat dikirimkan melalui jaringan dan juga dapat memverifikasi identitas klien dan server dengan memvalidasi sertifikatnya.



## Temporal Cluster&#x20;

Server Temporal merupakan bagian penting dari keseluruhan sistem, namun memerlukan komponen tambahan untuk pengoperasiannya. Sistem yang lengkap dikenal sebagai **Temporal Cluster** , yang merupakan penerapan perangkat lunak Server Temporal pada sejumlah mesin, ditambah komponen tambahan yang digunakan dengannya.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Komponen yang diperlukan** hanyalah database, seperti Apache Cassandra, PostgreSQL, atau MySQL. Klaster Temporal melacak keadaan saat ini dari setiap eksekusi Alur Kerja Anda. Ia juga menyimpan riwayat semua Peristiwa yang terjadi selama eksekusinya, yang digunakannya untuk merekonstruksi keadaan saat ini jika terjadi kegagalan. Ini dan informasi lainnya, seperti detail terkait pengatur waktu dan antrean yang tahan lama, disimpan ke database.

Elasticsearch adalah komponen opsional, tetapi berguna ketika Anda menjalankan Alur Kerja jutaan kali dan perlu menemukan alur kerja tertentu; misalnya, berdasarkan kapan dimulainya, berapa lama waktu yang dibutuhkan untuk berjalan, atau status akhirnya.

Dua alat lainnya sering digunakan dengan Temporal. Prometheus digunakan untuk mengumpulkan metrik dari Temporal, sedangkan Grafana digunakan untuk membuat dasbor berdasarkan metrik tersebut. Bersama-sama, alat-alat ini membantu tim operasi memantau kesehatan klaster dan aplikasi.



## Worker

Meskipun platform menjamin eksekusi kode Anda yang tahan lama, platform ini mencapai hal ini melalui _orkestrasi_ . Eksekusi kode aplikasi Anda berada di luar klaster, dan dalam penerapan umum, terjadi pada kumpulan server terpisah, yang berpotensi berjalan di pusat data yang berbeda dari Klaster Temporal.

Entitas yang bertanggung jawab untuk mengeksekusi kode Anda dikenal sebagai Worker, dan merupakan hal yang umum untuk menjalankan Worker di beberapa server, karena hal ini meningkatkan skalabilitas dan ketersediaan aplikasi Anda. Worker, dapat berkomunikasi dengan Klaster Temporal untuk mengelola eksekusi Alur Kerja yang ada.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### Worker Connectivity <a href="#worker-connectivity" id="worker-connectivity"></a>

Karena Worker menggunakan Klien Temporal untuk berkomunikasi dengan Klaster Temporal, setiap mesin yang menjalankan Worker akan memerlukan konektivitas ke Layanan Frontend Klaster, yang mendengarkan pada port TCP 7233 secara default.
