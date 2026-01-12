# Laporan Praktikum Kriptografi
Minggu ke-: 13
Topik: TinyChain – Proof of Work (PoW)

Nama: Nuri Wulan Kinasih

NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Menjelaskan peran hash function dalam blockchain.
2. Melakukan simulasi sederhana Proof of Work (PoW).
3. Menganalisis keamanan cryptocurrency berbasis kriptografi.

---

## 2. Dasar Teori
TinyChain merupakan contoh sederhana dari sistem blockchain yang digunakan untuk mempelajari konsep dasar blockchain, termasuk mekanisme konsensus Proof of Work (PoW). Dalam TinyChain, PoW digunakan untuk menentukan blok mana yang sah untuk ditambahkan ke dalam rantai. Proses ini dilakukan dengan mencari nilai nonce tertentu sehingga hasil fungsi hash dari data blok memenuhi tingkat kesulitan yang ditentukan, misalnya menghasilkan hash dengan awalan nol.

Setiap blok dalam TinyChain berisi data transaksi, hash blok sebelumnya, timestamp, dan nonce. Hash blok sebelumnya berfungsi untuk menghubungkan antarblok sehingga membentuk rantai yang saling bergantung. Jika terdapat perubahan data pada satu blok, maka hash akan berubah dan menyebabkan blok-blok setelahnya menjadi tidak valid. Hal ini menunjukkan bagaimana PoW dan fungsi hash bekerja bersama untuk menjaga integritas dan keamanan data.

Selain menjaga integritas data, Proof of Work pada TinyChain juga berperan dalam mencegah kecurangan seperti double spending. Karena proses penambahan blok memerlukan komputasi yang sulit dan memakan waktu, upaya untuk memanipulasi data atau menambahkan blok palsu menjadi sangat tidak efisien dan sulit dilakukan.

---

## 3. Alat dan Bahan
- Python 3.14
- Visual Studio Code 
- Git dan akun GitHub  
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
1. Mengapa fungsi hash sangat penting dalam blockchain?
2. Bagaimana Proof of Work mencegah double spending?
3. Apa kelemahan dari PoW dalam hal efisiensi energi?

Jawaban:
1. Fungsi hash sangat penting karena digunakan untuk menjaga keamanan dan integritas data dalam blockchain. Setiap transaksi diubah menjadi nilai hash yang unik. Jika data diubah sedikit saja, nilai hash akan berubah total sehingga manipulasi data dapat langsung terdeteksi. Selain itu, hash juga digunakan untuk menghubungkan antarblok sehingga data bersifat tidak dapat diubah (immutable).
2. Proof of Work mencegah double spending dengan cara mewajibkan penambang melakukan perhitungan matematika yang kompleks sebelum sebuah transaksi dinyatakan valid. Hanya blok yang berhasil menyelesaikan perhitungan tersebut yang dapat ditambahkan ke blockchain. Setelah transaksi tercatat dalam blok yang sah, transaksi tersebut tidak dapat digunakan kembali, sehingga mencegah terjadinya pengeluaran ganda.
3. Kelemahan utama PoW adalah penggunaan energi yang sangat besar karena proses penambangan memerlukan perhitungan komputasi secara terus-menerus. Energi yang digunakan sebagian besar hanya untuk mencari hash yang sesuai, sehingga kurang efisien dan berdampak pada lingkungan. Oleh karena itu, PoW dianggap tidak ramah energi dibandingkan metode konsensus lainnya.

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
```
commit week13-tinychain
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-01-12

    week13-tinychain: TinyChain – Proof of Work (PoW)
```
