# Laporan Praktikum Kriptografi
Minggu ke-: 10  
Topik: Public Key Infrastructure (PKI & Certificate Authority)

Nama: Nuri Wulan Kinasih
NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Membuat sertifikat digital sederhana.
2. Menjelaskan peran Certificate Authority (CA) dalam sistem PKI.
3. Mengevaluasi fungsi PKI dalam komunikasi aman (contoh: HTTPS, TLS).
---

## 2. Dasar Teori
Public Key Infrastructure (PKI) adalah sistem yang digunakan untuk mengatur dan mengamankan penggunaan kunci publik dalam komunikasi digital. PKI membantu memastikan bahwa proses enkripsi, tanda tangan digital, dan pertukaran data dapat dilakukan dengan aman. Dengan adanya PKI, pengguna tidak hanya menggunakan kunci publik secara sembarangan, tetapi juga dapat memastikan bahwa kunci tersebut benar-benar milik pihak yang tepat, sehingga komunikasi menjadi lebih terpercaya.

Salah satu bagian terpenting dalam PKI adalah Certificate Authority (CA). CA berperan sebagai pihak yang dipercaya untuk menerbitkan sertifikat digital. Sertifikat digital ini berisi identitas pemilik dan kunci publiknya, yang telah diverifikasi dan ditandatangani oleh CA. Karena adanya tanda tangan dari CA, pengguna lain dapat yakin bahwa kunci publik tersebut asli dan tidak dipalsukan.

Selain CA, PKI juga memiliki komponen pendukung lainnya seperti Registration Authority (RA) dan mekanisme pencabutan sertifikat. RA bertugas mengecek identitas pemohon sebelum sertifikat diterbitkan, sedangkan pencabutan sertifikat digunakan jika kunci sudah tidak aman atau tidak berlaku lagi. Dengan sistem ini, PKI mampu menjaga keamanan dan kepercayaan dalam berbagai layanan digital seperti website aman (HTTPS), email, dan transaksi online.

---

## 3. Alat dan Bahan
- Python 3.x  
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
