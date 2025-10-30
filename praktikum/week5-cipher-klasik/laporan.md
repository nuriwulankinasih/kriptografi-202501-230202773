# Laporan Praktikum Kriptografi
Minggu ke-: 5
Topik: Cipher Klasik (Caesar, Vigenère, Transposisi)

Nama: Nuri Wulan Kinasih  

NIM: 230202773

Kelas: 5IKRB

---

## 1. Tujuan
1. Menerapkan algoritma Caesar Cipher untuk enkripsi dan dekripsi teks.
2. Menerapkan algoritma Vigenère Cipher dengan variasi kunci.
3. Mengimplementasikan algoritma transposisi sederhana.
4. Menjelaskan kelemahan algoritma kriptografi klasik.

---

## 2. Dasar Teori
Cipher klasik merupakan dasar dari perkembangan ilmu kriptografi modern. Jenis cipher ini digunakan pada masa sebelum komputer ditemukan, dengan prinsip utama melakukan substitusi (penggantian huruf) atau transposisi (penukaran posisi huruf) untuk menyembunyikan pesan asli. Meskipun tekniknya sederhana, cipher klasik memiliki peran penting dalam sejarah keamanan informasi karena memperkenalkan konsep enkripsi dan dekripsi yang masih digunakan hingga kini dalam bentuk yang lebih kompleks.
Salah satu cipher klasik paling terkenal adalah Caesar Cipher, yang digunakan oleh Julius Caesar untuk mengirim pesan rahasia kepada pasukannya. Cipher ini bekerja dengan cara menggeser setiap huruf dalam plaintext sebanyak beberapa posisi di alfabet. Misalnya, jika pergeserannya tiga huruf, maka huruf A menjadi D, B menjadi E, dan seterusnya. Walaupun mudah dipahami dan diterapkan, Caesar Cipher mudah dipecahkan menggunakan analisis frekuensi atau brute force karena jumlah kuncinya yang sangat terbatas.
Cipher klasik lain yang lebih kompleks adalah Vigenère Cipher dan Transposisi Cipher. Vigenère Cipher merupakan bentuk pengembangan dari Caesar Cipher dengan menggunakan kata kunci untuk menentukan jumlah pergeseran tiap huruf, sehingga hasil enkripsi menjadi lebih sulit diprediksi. Sementara itu, Transposisi Cipher bekerja dengan menukar posisi huruf dalam pesan tanpa mengubah huruf itu sendiri. Teknik ini mengandalkan pola tertentu dalam penukaran posisi huruf, misalnya dengan menulis pesan dalam bentuk tabel dan membaca urutannya secara vertikal atau zig-zag. Meskipun teknik-teknik ini kini tidak lagi aman untuk penggunaan modern, konsep dasarnya tetap menjadi fondasi dalam memahami prinsip kerja algoritma kriptografi masa kini.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
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
### Langkah 1 --Implementasi Caesar Cipher

    def caesar_encrypt(plaintext, key):
        result = ""
        for char in plaintext:
            if char.isalpha():
                shift = 65 if char.isupper() else 97
                result += chr((ord(char) - shift + key) % 26 + shift)
            else:
                result += char
        return result
    
    def caesar_decrypt(ciphertext, key):
        return caesar_encrypt(ciphertext, -key)
    
    # Contoh uji
    msg = "CLASSIC CIPHER"
    key = 3
    enc = caesar_encrypt(msg, key)
    dec = caesar_decrypt(enc, key)
    print("Plaintext :", msg)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)

    Hasilnya:

    Plaintext : CLASSIC CIPHER
    Ciphertext: FODVVLF FLSKHU
    Decrypted : CLASSIC CIPHER

### Langkah 2 --Implementasi Vigenère Cipher

    def vigenere_encrypt(plaintext, key):
        result = []
        key = key.lower()
        key_index = 0
        for char in plaintext:
            if char.isalpha():
                shift = ord(key[key_index % len(key)]) - 97
                base = 65 if char.isupper() else 97
                result.append(chr((ord(char) - base + shift) % 26 + base))
                key_index += 1
            else:
                result.append(char)
        return "".join(result)
    
    def vigenere_decrypt(ciphertext, key):
        result = []
        key = key.lower()
        key_index = 0
        for char in ciphertext:
            if char.isalpha():
                shift = ord(key[key_index % len(key)]) - 97
                base = 65 if char.isupper() else 97
                result.append(chr((ord(char) - base - shift) % 26 + base))
                key_index += 1
            else:
                result.append(char)
        return "".join(result)
    
    # Contoh uji
    msg = "KRIPTOGRAFI"
    key = "KEY"
    enc = vigenere_encrypt(msg, key)
    dec = vigenere_decrypt(enc, key)
    print("Plaintext :", msg)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)

    Hasilnya:

    Plaintext : KRIPTOGRAFI
    Ciphertext: UVGZXMQVYPM
    Decrypted : KRIPTOGRAFI

    

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
