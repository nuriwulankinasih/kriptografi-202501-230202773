# Laporan Praktikum Kriptografi
Minggu ke-: 7
Topik: Diffie-Hellman Key Exchange

Nama: Nuri Wulan Kinasih
NIM: 230202773  
Kelas: 5IKRB  

---

## 1. Tujuan
1. Melakukan simulasi protokol Diffie-Hellman untuk pertukaran kunci publik.
2. Menjelaskan mekanisme pertukaran kunci rahasia menggunakan bilangan prima dan logaritma diskrit.
3. Menganalisis potensi serangan pada protokol Diffie-Hellman (termasuk serangan Man-in-the-Middle / MITM).

---

## 2. Dasar Teori

Diffie-Hellman Key Exchange merupakan salah satu algoritma kriptografi yang digunakan untuk melakukan pertukaran kunci secara aman melalui saluran komunikasi yang tidak aman. Algoritma ini diperkenalkan oleh Whitfield Diffie dan Martin Hellman pada tahun 1976 sebagai solusi untuk masalah distribusi kunci dalam sistem kriptografi simetris. Prinsip utamanya adalah memungkinkan dua pihak yang belum pernah bertemu sebelumnya untuk menghasilkan kunci rahasia bersama, tanpa harus mengirimkan kunci tersebut secara langsung melalui jaringan.

Dalam mekanisme Diffie-Hellman, kedua pihak menyepakati dua parameter publik yaitu bilangan prima besar (p) dan generator (g). Masing-masing pihak kemudian memilih kunci privat secara acak dan menghitung kunci publik dengan rumus tertentu menggunakan operasi perpangkatan dan modulo terhadap bilangan prima tersebut. Setelah saling bertukar kunci publik, masing-masing pihak dapat menghitung kunci rahasia yang sama dengan memanfaatkan kunci publik lawan dan kunci privat miliknya, tanpa mengungkapkan kunci privat kepada siapa pun.

Keamanan algoritma Diffie-Hellman bergantung pada kesulitan perhitungan discrete logarithm problem, yaitu mencari nilai eksponen dari hasil perpangkatan dalam modulo bilangan prima besar. Semakin besar nilai bilangan prima yang digunakan, semakin sulit bagi pihak ketiga untuk menebak atau menghitung kunci rahasia bersama. Oleh karena itu, meskipun algoritma ini tidak menyediakan autentikasi secara langsung, Diffie-Hellman tetap menjadi fondasi penting dalam banyak protokol keamanan modern seperti TLS, SSH, dan IPsec.

---

## 3. Alat dan Bahan
(- Python 3.14.0
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
### Langkah 1 — Simulasi Diffie-Hellman

    import random

    # parameter umum (disepakati publik)
    p = 23  # bilangan prima
    g = 5   # generator
    
    # private key masing-masing pihak
    a = random.randint(1, p-1)  # secret Alice
    b = random.randint(1, p-1)  # secret Bob
    
    # public key
    A = pow(g, a, p)
    B = pow(g, b, p)
    
    # exchange public key
    shared_secret_A = pow(B, a, p)
    shared_secret_B = pow(A, b, p)
    
    print("Kunci bersama Alice :", shared_secret_A)
    print("Kunci bersama Bob   :", shared_secret_B)

Hasilnya: 

    Kunci bersama Alice : 10
    Kunci bersama Bob   : 10

### Langkah 2 -- Analisis Serangan MITM (Man-in-the-Middle)

    import random

    # parameter publik
    p = 23
    g = 5
    
    # private key Alice dan Bob
    a = random.randint(1, p-1)
    b = random.randint(1, p-1)
    
    # ---- Eve melakukan MITM ----
    # Eve membuat private key sendiri
    e = random.randint(1, p-1)
    
    # Alice menghitung public key
    A = pow(g, a, p)
    
    # Bob menghitung public key
    B = pow(g, b, p)
    
    # Eve mencegat dan mengganti public key:
    # Alice menerima B_palsu, Bob menerima A_palsu
    A_fake = pow(g, e, p)   # public key Eve untuk Bob
    B_fake = pow(g, e, p)   # public key Eve untuk Alice
    
    # Alice menghitung shared secret (dengan kunci Eve)
    shared_A = pow(B_fake, a, p)
    
    # Bob menghitung shared secret (dengan kunci Eve)
    shared_B = pow(A_fake, b, p)
    
    # Eve menghitung dua kunci:
    # kunci dengan Alice
    shared_EA = pow(A, e, p)
    # kunci dengan Bob
    shared_EB = pow(B, e, p)
    
    print("=== Kunci yang Dihasilkan ===")
    print("Kunci bersama Alice (Alice–Eve):", shared_A)
    print("Kunci bersama Bob   (Bob–Eve): ", shared_B)
    print("Kunci Eve dengan Alice        :", shared_EA)
    print("Kunci Eve dengan Bob          :", shared_EB)

Hasilnya:

    Kunci bersama Alice (Alice–Eve): 4
    Kunci bersama Bob   (Bob–Eve):  2
    Kunci Eve dengan Alice        : 4
    Kunci Eve dengan Bob          : 2

Penjelasan simulasi:

1. Simulasi Diffie-Hellman (Langkah 1)
   
- Alice dan Bob memilih bilangan publik p=23 dan g=5.
- Keduanya membuat private key acak lalu menghitung public key masing-masing.
- Setelah bertukar public key, mereka menghitung shared secret dengan rumus modular eksponensial.
- Hasil akhirnya kunci Alice dan Bob sama (10) → protokol bekerja dengan benar.
  
2. Simulasi Serangan MITM (Langkah 2)
  
- Eve membuat private key sendiri lalu mencegat dan mengganti public key yang dikirim Alice dan Bob.
- Alice menghitung kunci dengan Eve, Bob juga menghitung kunci dengan Eve (bukan satu sama lain).
  Hasil:
  Kunci Alice–Eve = 4
  Kunci Bob–Eve = 2
  Ini menunjukkan bahwa Eve berhasil membuat dua kunci berbeda untuk memantau dan memodifikasi komunikasi.

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program simulasi diffie hellman:
<img width="1366" height="768" alt="Langkah1-simulasi diffie helman" src="https://github.com/user-attachments/assets/9318ca13-7691-4679-8d26-dfbd4fa9ffd7" />

Hasil Analisis Serangan MITM (Man-in-the-Middle): 
<img width="1366" height="768" alt="Langkah2-Analisis serangan MITM" src="https://github.com/user-attachments/assets/8dbb89b5-c290-462c-8815-b2e4b89f7d0c" />

Pembahasan: 

Pada simulasi Diffie-Hellman, Alice dan Bob berhasil menghasilkan shared key yang sama hanya dengan bertukar public key, menunjukkan bahwa proses pertukaran kunci bekerja dengan benar. Namun, pada analisis serangan MITM terlihat bahwa tanpa autentikasi, penyerang dapat memotong dan memalsukan pertukaran kunci, sehingga setiap pihak sebenarnya berbagi kunci dengan penyerang, bukan satu sama lain. Ini menunjukkan bahwa Diffie-Hellman aman secara matematis, tetapi rentan MITM jika tidak disertai autentikasi.

---

## 7. Jawaban Pertanyaan
1. Mengapa Diffie-Hellman memungkinkan pertukaran kunci di saluran publik?
2. Apa kelemahan utama protokol Diffie-Hellman murni?
3. Bagaimana cara mencegah serangan MITM pada protokol ini?

Jawaban: 

1. Karena keamanan Diffie-Hellman bergantung pada masalah logaritma diskrit, yaitu perhitungan yang sangat sulit dipecahkan. Meskipun nilai publik (p, g, dan public key) dapat dilihat semua orang, tidak ada yang dapat menghitung kunci rahasia tanpa mengetahui private key.
   
2. Kelemahan utamanya adalah tidak ada autentikasi, sehingga protokol ini rentan terhadap Man-in-the-Middle (MITM). Penyerang dapat memalsukan public key dan membuat dua kunci terpisah dengan masing-masing pihak tanpa terdeteksi.
   
3. Dengan menambahkan mekanisme autentikasi, seperti:
   - Menggunakan sertifikat digital (TSL/SSL).
   - Tanda tangan digital (RSA).
   - Menggabungkan Diffie-Hellman dengan autentikasi berbasis password.
     
---


## 8. Kesimpulan
Percobaan menunjukkan bahwa protokol Diffie-Hellman mampu menghasilkan kunci rahasia bersama secara aman meskipun pertukaran dilakukan melalui saluran publik. Namun, hasil simulasi MITM membuktikan bahwa tanpa mekanisme autentikasi, pertukaran kunci dapat disusupi dan dimanipulasi oleh pihak ketiga. Oleh karena itu, Diffie-Hellman perlu dikombinasikan dengan autentikasi agar komunikasi tetap aman dari serangan aktif.

---

## 9. Daftar Pustaka

## 10. Commit Log
```
commit week7-diffie-hellman
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-11-16

   week7-diffie-hellman: Diffie-Hellman Key Exchange

```
