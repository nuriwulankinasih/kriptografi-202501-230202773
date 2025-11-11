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
    
---

## 6. Hasil dan Pembahasan
Hasil eksekusi program simulasi diffie hellman:
<img width="1366" height="768" alt="Langkah1-simulasi diffie helman" src="https://github.com/user-attachments/assets/9318ca13-7691-4679-8d26-dfbd4fa9ffd7" />



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
