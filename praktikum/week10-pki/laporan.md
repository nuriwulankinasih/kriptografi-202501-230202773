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
1. Apa fungsi utama Certificate Authority (CA)?
2. Mengapa self-signed certificate tidak cukup untuk sistem produksi?
3. Bagaimana PKI mencegah serangan MITM dalam komunikasi TLS/HTTPS?

Jawaban: 

1. Certificate Authority (CA) berfungsi sebagai pihak terpercaya yang menerbitkan dan memvalidasi sertifikat digital untuk mengikat identitas suatu entitas (seperti website, organisasi, atau individu) dengan kunci publiknya. CA melakukan proses verifikasi identitas sebelum menerbitkan sertifikat, sehingga pengguna dapat yakin bahwa kunci publik yang diterima benar-benar milik pihak yang sah. Dengan adanya CA, komunikasi digital dapat berlangsung secara aman karena keaslian identitas pihak yang berkomunikasi dapat dipercaya.
   
2. Self-signed certificate tidak cukup untuk sistem produksi karena sertifikat tersebut ditandatangani oleh pemiliknya sendiri tanpa verifikasi dari pihak tepercaya. Akibatnya, klien atau browser tidak memiliki cara untuk memastikan keaslian identitas server, sehingga rawan terhadap serangan pemalsuan identitas. Selain itu, self-signed certificate biasanya akan memunculkan peringatan keamanan pada browser, menurunkan tingkat kepercayaan pengguna, dan tidak cocok untuk lingkungan produksi yang membutuhkan jaminan keamanan dan kepercayaan tinggi.

3. Public Key Infrastructure (PKI) mencegah serangan Man-in-the-Middle (MITM) dengan memastikan bahwa kunci publik server yang digunakan dalam komunikasi TLS/HTTPS telah diverifikasi oleh CA tepercaya. Ketika klien mengakses sebuah website, browser akan memeriksa sertifikat digital server, termasuk tanda tangan CA dan kecocokan nama domain. Jika sertifikat valid, klien yakin bahwa kunci publik tersebut milik server yang benar, sehingga penyerang tidak dapat menggantikan kunci publik tanpa terdeteksi. Dengan demikian, proses pertukaran kunci dan enkripsi komunikasi menjadi aman dari penyadapan dan pemalsuan.

---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week10-pki
Author: Nuri Wulan kinasih <kinasihnuri60@gmail.com>
Date:   2025-12-19

    week10-pki: Public Key Infrastructure (PKI & Certificate Authority)
```
