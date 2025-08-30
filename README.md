Instant QRIS Generator
> Sebuah alat web modern untuk mengubah QRIS statis menjadi QRIS dinamis dengan nominal dan batas waktu tertentu. Aplikasi ini sepenuhnya berjalan di sisi klien (browser), memastikan privasi dan keamanan data pengguna.
> 
✨ Fitur Utama
 * Konversi QRIS Statis ke Dinamis: Unggah gambar QRIS statis, dan aplikasi akan secara cerdas memprosesnya.
 * Input Nominal Kustom: Masukkan jumlah pembayaran yang diinginkan untuk disematkan ke dalam QR code baru.
 * Ekstraksi Nama Merchant: Secara otomatis mendeteksi dan menampilkan nama merchant dari data QRIS asli.
 * Timer Kedaluwarsa 1 Jam: Setiap QRIS yang dihasilkan memiliki batas waktu 60 menit, meningkatkan keamanan transaksi.
 * Desain Modern: Antarmuka yang bersih, profesional, dan responsif dengan efek dinamis.
 * Unduh QRIS: Simpan QR code dinamis yang sudah jadi sebagai file gambar PNG.
 * Penanganan Error Cerdas: Otomatis menurunkan level koreksi error QR code jika data terlalu panjang, memastikan kompatibilitas maksimum.
🚀 Teknologi yang Digunakan
 * HTML5: Struktur dasar aplikasi web.
 * Tailwind CSS: Kerangka kerja CSS untuk membangun desain modern dengan cepat.
 * JavaScript (ES6): Logika inti aplikasi, termasuk pemrosesan gambar, manipulasi string QRIS, dan manajemen antarmuka.
 * Pustaka Eksternal:
   * jsQR: Untuk memindai dan membaca data dari gambar QR code yang diunggah.
   * QRCode.js: Untuk menghasilkan gambar QR code baru dari string data yang telah dimodifikasi.
🛠️ Cara Menggunakan
 * Unduh atau kloning repositori ini.
 * Buka file index.html di browser modern apa pun (Chrome, Firefox, Safari, dll.).
 * Ikuti tiga langkah mudah yang ditampilkan di layar:
   * Unggah gambar QRIS.
   * Masukkan nominal yang diinginkan.
   * Gunakan atau unduh QRIS dinamis yang dihasilkan.
📁 Struktur File
.
├── index.html     # File utama aplikasi generator QRIS
└── README.md      # Anda sedang membaca ini

⚙️ Bagaimana Cara Kerjanya?
Aplikasi ini bekerja melalui tiga tahap utama di sisi klien:
 * Membaca QRIS Statis:
   * Ketika pengguna mengunggah gambar, JavaScript menggunakan elemen <canvas> untuk menggambar ulang gambar tersebut.
   * Pustaka jsQR kemudian memindai data piksel dari canvas untuk menemukan dan mendekode QR code, mengekstraknya menjadi sebuah string panjang.
 * Memodifikasi String QRIS:
   * Ini adalah inti dari aplikasi. String QRIS memiliki format standar (EMVCo).
   * Aplikasi mencari dan menghapus tag nominal transaksi (54) yang mungkin sudah ada.
   * Kemudian, aplikasi menyisipkan tag nominal baru (54 + panjang_nominal + nominal).
   * Terakhir, aplikasi menghapus tag checksum lama (6304...) dan menghitung ulang nilai CRC-16-CCITT baru berdasarkan keseluruhan string yang telah dimodifikasi. Checksum baru ini kemudian ditambahkan di akhir string.
 * Menghasilkan QRIS Dinamis:
   * String QRIS yang sudah valid dan dimodifikasi kemudian diberikan kepada pustaka QRCode.js.
   * Pustaka ini merender string tersebut menjadi gambar QR code baru yang ditampilkan di layar dan siap untuk dipindai oleh aplikasi pembayaran.
📄 Lisensi
Proyek ini dilisensikan di bawah Lisensi MIT. Lihat file LICENSE untuk detail lebih lanjut.