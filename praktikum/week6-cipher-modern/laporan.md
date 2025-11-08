# Laporan Praktikum Kriptografi
Minggu ke-: 6  
Topik: Cipher Modern (DES, AES, RSA)
Nama: Nuri Wulan Kinasih 
NIM: 230202773  
Kelas: 5IKRB  

---

## 1. Tujuan
1. Mengimplementasikan algoritma DES untuk blok data sederhana.
2. Menerapkan algoritma AES dengan panjang kunci 128 bit.
3. Menjelaskan proses pembangkitan kunci publik dan privat pada algoritma RSA.

---

## 2. Dasar Teori
Cipher modern merupakan bentuk kriptografi yang digunakan untuk menjaga keamanan data digital melalui proses enkripsi dan dekripsi menggunakan algoritma matematis yang kompleks. Tidak seperti cipher klasik yang hanya mengandalkan penggantian huruf atau pergeseran karakter, cipher modern bekerja pada level biner dan memanfaatkan operasi logika, substitusi, permutasi, serta penggunaan kunci yang panjang untuk mengamankan informasi. Tujuan utama dari cipher modern adalah memastikan kerahasiaan, integritas, dan autentikasi data dalam berbagai aplikasi, seperti komunikasi digital, transaksi keuangan, dan sistem keamanan jaringan.


Data Encryption Standard (DES) merupakan salah satu algoritma simetris pertama yang banyak digunakan secara luas sejak tahun 1977. DES menggunakan panjang kunci 56 bit dan bekerja dengan memecah data menjadi blok-blok berukuran 64 bit, kemudian melakukan proses enkripsi melalui 16 tahap substitusi dan permutasi menggunakan kunci yang berbeda di setiap tahap. Meskipun DES dianggap aman pada masanya, seiring perkembangan teknologi komputasi, kekuatannya menjadi lemah karena panjang kunci yang relatif pendek, sehingga mudah diserang dengan metode brute force. Akibatnya, DES kemudian digantikan oleh versi yang lebih aman yaitu Triple DES (3DES) dan kemudian AES.


Advanced Encryption Standard (AES) dan Rivest–Shamir–Adleman (RSA) merupakan algoritma yang lebih kuat dan banyak digunakan saat ini. AES adalah cipher blok simetris yang menggunakan panjang kunci 128, 192, atau 256 bit dengan proses enkripsi yang efisien dan cepat, sangat cocok untuk aplikasi keamanan data modern seperti Wi-Fi, VPN, dan penyimpanan cloud. Di sisi lain, RSA merupakan algoritma asimetris yang menggunakan sepasang kunci publik dan privat berbasis konsep matematika faktorisasi bilangan prima besar. RSA banyak digunakan untuk keamanan komunikasi, tanda tangan digital, dan distribusi kunci dalam sistem kriptografi hibrida. Gabungan penggunaan cipher simetris (AES) dan asimetris (RSA) saat ini menjadi fondasi utama sistem keamanan data modern.

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
### Langkah 1 — Implementasi DES (Opsional, Simulasi)

    from Crypto.Cipher import DES
    from Crypto.Random import get_random_bytes
    
    key = get_random_bytes(8)  # kunci 64 bit (8 byte)
    cipher = DES.new(key, DES.MODE_ECB)
    
    plaintext = b"ABCDEFGH"
    ciphertext = cipher.encrypt(plaintext)
    print("Ciphertext:", ciphertext)
    
    decipher = DES.new(key, DES.MODE_ECB)
    decrypted = decipher.decrypt(ciphertext)
    print("Decrypted:", decrypted)

Hasilnya: 



### Langkah 2 — Implementasi AES-128

    from Crypto.Cipher import AES
    from Crypto.Random import get_random_bytes
    
    key = get_random_bytes(16)  # 128 bit key
    cipher = AES.new(key, AES.MODE_EAX)
    
    plaintext = b"Modern Cipher AES Example"
    ciphertext, tag = cipher.encrypt_and_digest(plaintext)
    
    print("Ciphertext:", ciphertext)
    
    # Dekripsi
    cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
    decrypted = cipher_dec.decrypt(ciphertext)
    print("Decrypted:", decrypted.decode())

Hasilnya: 


### Langkah 3 — Implementasi RSA

    from Crypto.PublicKey import RSA
    from Crypto.Cipher import PKCS1_OAEP
    
    # Generate key pair
    key = RSA.generate(2048)
    private_key = key
    public_key = key.publickey()
    
    # Enkripsi dengan public key
    cipher_rsa = PKCS1_OAEP.new(public_key)
    plaintext = b"RSA Example"
    ciphertext = cipher_rsa.encrypt(plaintext)
    print("Ciphertext:", ciphertext)
    
    # Dekripsi dengan private key
    decipher_rsa = PKCS1_OAEP.new(private_key)
    decrypted = decipher_rsa.decrypt(ciphertext)
    print("Decrypted:", decrypted.decode())

Hasilnya: 


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
1. Apa perbedaan mendasar antara DES, AES, dan RSA dalam hal kunci dan keamanan?
2. Mengapa AES lebih banyak digunakan dibanding DES di era modern?
3. Mengapa RSA dikategorikan sebagai algoritma asimetris, dan bagaimana proses pembangkitan kuncinya?

Jawaban: 

1. Perbedaan mendasar antara DES, AES, dan RSA terletak pada jenis kunci dan tingkat keamanannya. DES dan AES sama-sama menggunakan kunci simetris (kunci enkripsi dan dekripsi sama), sedangkan RSA menggunakan kunci asimetris (kunci publik dan privat berbeda). DES memiliki panjang kunci 56 bit sehingga mudah ditembus, sementara AES lebih kuat dengan kunci 128–256 bit. RSA lebih aman untuk pertukaran kunci karena berbasis faktorisasi bilangan prima besar.

2. AES lebih banyak digunakan dibanding DES karena lebih aman dan efisien. DES kini dianggap lemah akibat panjang kunci yang pendek, sedangkan AES memiliki struktur dan panjang kunci yang lebih kompleks, menjadikannya tahan terhadap serangan brute force. Selain itu, AES juga lebih cepat diproses di perangkat modern, baik software maupun hardware.

3. RSA disebut algoritma asimetris karena menggunakan dua kunci berbeda: publik untuk enkripsi dan privat untuk dekripsi. Kuncinya dibangkitkan dengan memilih dua bilangan prima besar (p dan q), menghitung n = p × q, lalu menentukan nilai e dan d yang saling terkait secara matematis. Keamanannya bergantung pada sulitnya memfaktorkan n menjadi p dan q.

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
commit week6-cipher-modern
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-11-08

    week6-cipher-modern: Cipher Modern (DES, AES, RSA)
```
