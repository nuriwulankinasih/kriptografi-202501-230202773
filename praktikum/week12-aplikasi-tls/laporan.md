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
- Python 3.14
- Visual Studio Code 
- GitHub  
- Google Chrome
---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```
)

---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: …  
- Pertanyaan 2: …  
)
---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
