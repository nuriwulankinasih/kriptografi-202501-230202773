# Laporan Praktikum Kriptografi
Minggu ke-: 11
Topik: Secret Sharing (Shamir’s Secret Sharing)

Nama: Nuri Wulan Kinasih  

NIM: 230202773        

Kelas: 5IKRB

---

## 1. Tujuan
1. Menjelaskan konsep Shamir Secret Sharing (SSS).
2. Melakukan simulasi pembagian rahasia ke beberapa pihak menggunakan skema SSS.
3. Menganalisis keamanan skema distribusi rahasia.
---

## 2. Dasar Teori
Shamir’s Secret Sharing merupakan salah satu metode kriptografi yang digunakan untuk membagi sebuah rahasia (secret) menjadi beberapa bagian yang disebut shares. Metode ini dirancang oleh Adi Shamir pada tahun 1979 dengan tujuan meningkatkan keamanan penyimpanan dan pengelolaan informasi sensitif. Dalam skema ini, sebuah rahasia tidak disimpan secara utuh pada satu pihak, melainkan dibagi ke beberapa pihak sehingga tidak ada satu pihak pun yang dapat mengetahui rahasia tersebut secara sendiri.

Prinsip utama Shamir’s Secret Sharing adalah konsep threshold scheme (k, n), di mana sebuah rahasia dibagi menjadi n bagian dan hanya dapat direkonstruksi jika minimal k bagian digabungkan kembali. Skema ini memanfaatkan konsep matematika polinomial, di mana rahasia disimpan sebagai nilai konstanta dari sebuah polinomial berderajat k−1. Selama jumlah share yang dikumpulkan kurang dari k, maka rahasia tidak dapat diketahui, sehingga menjamin kerahasiaan informasi meskipun sebagian share bocor.

Shamir’s Secret Sharing banyak digunakan dalam sistem keamanan modern, seperti manajemen kunci kriptografi, penyimpanan cadangan data penting, dan sistem otorisasi terdistribusi. Dengan membagi rahasia ke beberapa pihak, risiko kehilangan data akibat kegagalan satu pihak dapat diminimalkan, sekaligus meningkatkan ketahanan terhadap serangan. Oleh karena itu, skema ini menjadi solusi yang efektif untuk menjaga keamanan dan ketersediaan informasi dalam lingkungan yang membutuhkan tingkat kepercayaan dan keamanan tinggi.

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
