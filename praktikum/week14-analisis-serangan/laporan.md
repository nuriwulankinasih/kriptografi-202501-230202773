# Laporan Praktikum Kriptografi
Minggu ke-: 14
Topik: Analisis Serangan Kriptografi

Nama: Nuri Wulan Kinasih

NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Mengidentifikasi jenis serangan pada sistem informasi nyata.
2. Mengevaluasi kelemahan algoritma kriptografi yang digunakan.
3. Memberikan rekomendasi algoritma kriptografi yang sesuai untuk perbaikan keamanan.

---

## 2. Dasar Teori
Analisis Serangan Kriptografi adalah proses mempelajari dan mengevaluasi berbagai metode serangan yang dapat digunakan untuk melemahkan atau menembus sistem kriptografi. Tujuan utama analisis ini bukan untuk merusak sistem, melainkan untuk mengidentifikasi celah keamanan sehingga algoritma, protokol, atau implementasi kriptografi dapat diperbaiki dan diperkuat. Dengan analisis serangan, pengembang dapat memastikan bahwa sistem kriptografi benar-benar aman ketika digunakan di dunia nyata.

Serangan kriptografi dapat dilakukan dengan berbagai pendekatan, seperti brute force attack, cryptanalysis attack, dan side-channel attack. Brute force attack mencoba semua kemungkinan kunci hingga menemukan kunci yang benar, sedangkan cryptanalysis memanfaatkan kelemahan matematis dari algoritma. Side-channel attack tidak menyerang algoritma secara langsung, tetapi memanfaatkan informasi dari proses implementasi, seperti waktu eksekusi, konsumsi daya, atau pola akses memori.

Melalui analisis serangan kriptografi, sistem keamanan dapat dievaluasi dari sisi teori maupun praktik. Hasil analisis ini digunakan untuk menentukan tingkat kekuatan algoritma, memilih ukuran kunci yang aman, serta memastikan bahwa implementasi kriptografi tidak mudah dieksploitasi. Oleh karena itu, analisis serangan kriptografi merupakan bagian penting dalam pengembangan sistem keamanan informasi yang andal.

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
1. Mengapa banyak sistem lama masih rentan terhadap brute force atau dictionary attack?
2. Apa bedanya kelemahan algoritma dengan kelemahan implementasi?
3. Bagaimana organisasi dapat memastikan sistem kriptografi mereka tetap aman di masa depan?

Jawaban:
1. Banyak sistem lama masih rentan karena menggunakan algoritma kriptografi yang sudah usang, ukuran kunci yang pendek, serta metode penyimpanan kata sandi yang tidak aman, seperti hash tanpa salt atau bahkan teks biasa. Selain itu, sistem lama sering tidak menerapkan pembatasan percobaan login, sehingga penyerang dapat mencoba banyak kombinasi kata sandi secara otomatis tanpa terdeteksi.
2. Kelemahan algoritma berkaitan dengan desain matematis algoritma kriptografi itu sendiri, misalnya algoritma yang secara teori dapat dipecahkan atau memiliki celah kriptografi. Sementara itu, kelemahan implementasi terjadi ketika algoritma yang sebenarnya aman diterapkan dengan cara yang salah, seperti penggunaan kunci yang lemah, manajemen kunci yang buruk, atau kesalahan pemrograman yang membuka peluang serangan.
3. Organisasi dapat memastikan keamanan dengan cara menggunakan algoritma dan standar kriptografi terbaru, menerapkan ukuran kunci yang direkomendasikan, serta melakukan pembaruan sistem secara berkala. Selain itu, audit keamanan, pengujian penetrasi, dan pemantauan terhadap perkembangan serangan kriptografi juga penting agar sistem dapat beradaptasi terhadap ancaman baru.

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
commit week14-analisis-serangan
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-01-12

    week14-analisis-serangan: Analisis Serangan Kriptografi

```
