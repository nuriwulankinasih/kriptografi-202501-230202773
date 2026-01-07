# Laporan Praktikum Kriptografi
Minggu ke-: 12
Topik: Aplikasi TLS & E-commerce 

Nama: Nuri Wulan Kinasih  

NIM: 230202773  
Kelas: 5IKRB  

---

## 1. Tujuan
1. Menganalisis penggunaan kriptografi pada email dan SSL/TLS.
2. Menjelaskan enkripsi dalam transaksi e-commerce.
3. Mengevaluasi isu etika & privasi dalam penggunaan kriptografi di kehidupan sehari-hari.
---

## 2. Dasar Teori
Transport Layer Security (TLS) merupakan protokol keamanan yang digunakan untuk melindungi komunikasi data antara klien dan server di jaringan internet. TLS berfungsi mengenkripsi data yang dikirim sehingga tidak dapat dibaca oleh pihak yang tidak berwenang. Dalam implementasinya, TLS memanfaatkan mekanisme kriptografi asimetris dan simetris serta sertifikat digital yang dikeluarkan oleh Certificate Authority (CA). Protokol ini menjadi standar utama dalam pengamanan website modern yang ditandai dengan penggunaan protokol HTTPS.

Dalam konteks e-commerce, TLS memiliki peran yang sangat penting untuk menjaga keamanan transaksi online. Data sensitif seperti informasi login, nomor kartu kredit, alamat pengiriman, dan detail pembayaran dienkripsi selama proses transmisi. Dengan adanya TLS, risiko serangan seperti penyadapan (sniffing), pencurian data, dan serangan Man-in-the-Middle (MITM) dapat diminimalkan. Selain itu, sertifikat digital yang digunakan pada TLS membantu pengguna memastikan bahwa mereka terhubung ke situs e-commerce yang sah dan bukan situs palsu.

Penerapan TLS juga meningkatkan kepercayaan pengguna terhadap platform e-commerce. Browser modern akan memberikan peringatan jika suatu situs tidak menggunakan TLS, sehingga dapat menurunkan kepercayaan pelanggan. Oleh karena itu, TLS tidak hanya berfungsi sebagai mekanisme keamanan teknis, tetapi juga sebagai komponen penting dalam membangun kredibilitas, keamanan transaksi, serta keberlangsungan bisnis digital di era modern.

---

## 3. Alat dan Bahan
- Python 3.11
- Visual Studio Code 
- GitHub  
- Google Chrome
---

## 4. Langkah Percobaan
### Langkah 1 - Analisis SSL/TLS pada Email & Web (Shopee)
Berdasarkan hasil pengecekan sertifikat digital pada website shopee.co.id menggunakan browser Google Chrome, dapat          diketahui bahwa Shopee telah menggunakan protokol HTTPS yang menandakan koneksi aman dan terenkripsi. Sertifikat            digital tersebut diterbitkan untuk domain *.shopee.co.id, yang berarti mencakup seluruh subdomain Shopee.
- Issuer Certificate Authority (CA):
  Sertifikat Shopee diterbitkan oleh GlobalSign GCC R6 AlphaSSL CA 2023, dengan organisasi penerbit GlobalSign nv-sa,          yang merupakan Certificate Authority terpercaya secara global.
- Masa berlaku sertifikat:
  Diterbitkan pada: 24 Maret 2025
  Kedaluwarsa pada: 25 April 2026
  Hal ini menunjukkan sertifikat masih valid dan aktif, sehingga aman digunakan.
- Algoritma enkripsi:
  a. Sertifikat menggunakan SHA-256 sebagai algoritma hash
  
  b. TLS pada website e-commerce umumnya menggunakan RSA atau ECDHE untuk pertukaran kunci dan AES untuk enkripsi data            sesi

Perbandingan HTTPS dan HTTP:
- Website HTTPS (Shopee): data terenkripsi, ada autentikasi server, aman dari penyadapan
- Website HTTP (tanpa HTTPS): data dikirim dalam teks biasa, mudah disadap, tidak aman untuk login dan transaksi

### Langkah 2 — Studi Kasus E-commerce (Shopee)
Pada website Shopee, enkripsi TLS digunakan untuk melindungi data sensitif pengguna, seperti username, password, informasi pembayaran, dan detail transaksi. Ketika pengguna melakukan login atau checkout, data akan dienkripsi sebelum dikirim ke server, sehingga pihak ketiga tidak dapat membaca atau memodifikasi isi data tersebut.

Jika TLS tidak digunakan, maka berbagai ancaman keamanan dapat terjadi, salah satunya adalah Man-in-the-Middle (MITM). Dalam serangan ini, penyerang dapat menyadap komunikasi antara pengguna dan server, mencuri kredensial login, atau memodifikasi transaksi tanpa sepengetahuan pengguna. Oleh karena itu, penggunaan TLS menjadi komponen wajib dalam sistem e-commerce modern untuk menjaga kepercayaan dan keamanan pengguna.

### Analisis Etika & Privasi
Dalam konteks komunikasi terenkripsi seperti email dengan PGP atau S/MIME, isu privasi menjadi sangat penting karena hanya pengirim dan penerima yang dapat membaca isi pesan. Hal ini melindungi data pribadi, tetapi juga menimbulkan dilema etika.

- Dilema etika perusahaan:
  Perusahaan berada di posisi sulit antara menjaga privasi karyawan dan kebutuhan audit keamanan. Secara etis, perusahaan       boleh melakukan dekripsi email karyawan hanya jika:
  1. Sudah tercantum dalam kebijakan resmi
  2. Digunakan untuk kepentingan hukum atau keamanan
  3. Dilakukan secara transparan

- Kebijakan pemerintah:
  Pemerintah di banyak negara menghadapi dilema antara keamanan nasional dan hak privasi warga. Di satu sisi, enkripsi          melindungi masyarakat, namun di sisi lain menyulitkan penegakan hukum. Oleh karena itu, kebijakan umumnya mengatur            pengawasan komunikasi terenkripsi melalui izin hukum dan proses pengadilan, bukan akses bebas terhadap data terenkripsi.
## 5. Source Code
---

## 6. Hasil dan Pembahasan
Hasil
<img width="1071" height="1911" alt="Screenshot 2026-01-07 225656" src="https://github.com/user-attachments/assets/13be7211-b034-4d2a-b346-bde0cc31b00e" />

Pembahasan:
Berdasarkan hasil pengecekan sertifikat SSL/TLS pada website shopee.co.id, diketahui bahwa Shopee menggunakan protokol HTTPS dengan sertifikat digital yang diterbitkan oleh GlobalSign GCC R6 AlphaSSL CA 2023. Sertifikat ini berlaku untuk domain *.shopee.co.id dan masih aktif dengan masa berlaku dari 24 Maret 2025 hingga 25 April 2026, sehingga koneksi antara pengguna dan server terjamin keamanannya.

Penggunaan algoritma kriptografi modern seperti SHA-256 pada sertifikat serta enkripsi TLS memastikan bahwa data sensitif pengguna, seperti informasi login dan transaksi pembayaran, terlindungi dari penyadapan. Hal ini menunjukkan bahwa penerapan SSL/TLS pada Shopee sangat penting untuk menjaga kerahasiaan, integritas, dan keaslian data dalam sistem e-commerce.

---
## 7. Pertanyaan Diskusi
1. Apa perbedaan utama antara HTTP dan HTTPS?
2. Mengapa sertifikat digital menjadi penting dalam komunikasi TLS?
3. Bagaimana kriptografi mendukung privasi dalam komunikasi digital, tetapi sekaligus menimbulkan tantangan hukum dan etika?

Jawaban:
1. HTTP mengirimkan data dalam bentuk teks biasa (plaintext) sehingga mudah disadap atau dimodifikasi oleh pihak tidak berwenang. Sebaliknya, HTTPS menggunakan protokol TLS/SSL untuk mengenkripsi data yang dikirim antara pengguna dan server. Dengan HTTPS, kerahasiaan, keaslian, dan integritas data lebih terjamin, sehingga aman digunakan untuk aktivitas sensitif seperti login dan transaksi online.
2. Sertifikat digital berfungsi untuk memverifikasi identitas server yang diakses dan memastikan bahwa pengguna benar-benar terhubung ke server yang sah, bukan server palsu. Sertifikat ini dikeluarkan oleh Certificate Authority (CA) tepercaya dan digunakan dalam proses TLS untuk membangun koneksi terenkripsi serta mencegah serangan seperti Man-in-the-Middle.
3. Kriptografi melindungi privasi dengan mengenkripsi komunikasi digital sehingga hanya pihak berwenang yang dapat mengakses isi pesan. Namun, hal ini juga menimbulkan tantangan hukum dan etika karena enkripsi dapat menghambat proses penegakan hukum, misalnya dalam penyelidikan kejahatan. Oleh karena itu, diperlukan keseimbangan antara perlindungan privasi individu dan kepentingan keamanan serta hukum.
---

## 8. Kesimpulan
Praktikum ini menunjukkan bahwa TLS/SSL berperan penting dalam mengamankan komunikasi dan transaksi pada e-commerce melalui enkripsi dan sertifikat digital. Penerapan HTTPS melindungi data pengguna dari penyadapan serta meningkatkan kepercayaan pengguna. Namun, penggunaan kriptografi juga menimbulkan tantangan etika dan privasi, sehingga diperlukan kebijakan yang seimbang antara keamanan dan perlindungan hak pengguna.

---

## 9. Daftar Pustaka
Katz, J., & Lindell, Y. Introduction to Modern Cryptography.
Stallings, W. Cryptography and Network Security.

---

## Commit Log
---
commit week12-aplikasi-tls 
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date: 2026-01-07

week12-apliaksi-tls: implementasi Aplikasi TLS & E-commerce Shopee
