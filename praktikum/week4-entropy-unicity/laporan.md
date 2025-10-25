# Laporan Praktikum Kriptografi
Minggu ke-: 4
Topik: Entropy & Unicity Distance (Evaluasi Kekuatan Kunci dan Brute Force) 

Nama: Nuri Wulan Kinasih

NIM: 230202773

Kelas: 5IKRB

---

## 1. Tujuan
1. Menyelesaikan perhitungan sederhana terkait entropi kunci.
2. Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3. Menghitung unicity distance untuk ciphertext tertentu.
4. Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5. Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Entropy dalam konteks kriptografi menggambarkan tingkat ketidakpastian atau keacakan dalam sistem kunci. Semakin tinggi nilai entropi, semakin sulit bagi penyerang untuk menebak atau memprediksi kunci yang digunakan dalam proses enkripsi. Entropi biasanya diukur dalam bit. misalnya, sebuah kunci 128-bit dengan entropi penuh memiliki 2<sup>128</sup> kemungkinan kombinasi kunci. Dengan demikian, kunci dengan entropi tinggi dianggap lebih kuat karena memerlukan waktu dan sumber daya komputasi yang jauh lebih besar untuk dipecahkan menggunakan serangan brute force.

Unicity distance merupakan ukuran teoretis yang digunakan untuk menentukan berapa banyak ciphertext yang diperlukan untuk secara unik menentukan kunci yang digunakan. Nilai ini tergantung pada panjang kunci dan redundansi dari plaintext yang dienkripsi. Jika jumlah ciphertext yang tersedia melebihi unicity distance, maka secara teori penyerang dapat menemukan satu-satunya kunci yang benar dengan analisis kriptografi yang tepat. Oleh karena itu, semakin besar unicity distance, semakin sulit pula menemukan kunci melalui analisis statistik.

Dalam evaluasi kekuatan kunci, kombinasi antara entropi tinggi dan unicity distance yang besar menunjukkan sistem kriptografi yang kuat terhadap serangan brute force maupun analisis ciphertext. Brute force attack sendiri melibatkan percobaan semua kemungkinan kunci hingga menemukan yang sesuai, dan kompleksitas serangan ini meningkat secara eksponensial dengan panjang kunci. Oleh sebab itu, pemilihan ukuran kunci yang cukup besar dan sistem pengelolaan kunci yang aman sangat penting untuk menjaga integritas dan keamanan data dalam sistem kriptografi modern.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file `perhitungan-entropy.py` di folder `praktikum/week4-entropy-unicity/src/`.
2. Membuat file `menghitung-unicity distance.py` di folder `praktikum/week4-entropy-unicity/src/`.
3. Membuat file `analisis-brute force.py` di folder `praktikum/week4-entropy-unicity/src/`.
4. Menyalin kode program dari panduan praktikum.
5. Menjalankan program dengan perintah `python caesar_cipher.py`.)

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
