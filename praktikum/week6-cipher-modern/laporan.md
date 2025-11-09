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
(- Python 3.14.0 
- Visual Studio Code
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file `implementasi-DES.py` di folder `praktikum/week6-cipher-modern/src/`.
2. Membuat file `implementasi-AES128.py` di folder `praktikum/week6-cipher-modern/src/`.
3. Membuat file `implementasi-RSA.py` di folder `praktikum/week6-cipher-modern/src/`.
4. Menyalin kode program dari panduan praktikum.
5. Menjalankan program dengan perintah yg sesuai pada file

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

    Ciphertext: b'\xe3}\xf2\x97+\x13\x07%'
    Decrypted: b'ABCDEFGH'


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

    Ciphertext: b'4\xd8\tZ\xe8\xa2\xdfbr\xea\xc7\x97\x94Bs\xd4t\x11\xbb\x06\xdc4X\x7f\x9a'
    Decrypted: Modern Cipher AES Example

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

    Ciphertext: b'W\xae\xd9Sa\xae\xe3f\xd1\xcc\xab\x1a\xf4D\xbckx\x8a\x14\xc0\x16K\xdb\x92\x0e\xd7y\xdb\x08\xc6\xfaa~?\x17!KAb\xa6\xb7\xe2\xae\xb4\xd4#}\xe2ic\xa7\x155W\xe1hP+B\xeb\x80"\xc9S\xe7\xe6>\xc54\x10\x83Y\x8f\xe67\r+\xeb\xf2\x88\x8d\xa4\x8cNY\xaf_\xd5\x04`}M\xc6\x9a\x8fV!ts5\xeaM\xb24\x87\xf8\xd8Rs\xf0\x12#\xac\x82\xd6\xb8m\xb2\xb7\x00\xbb\xf0\xa7\xb2\xdf6E\xf9\x19\x10\x92\xcc\xdb\x129\x99v\x8c\x9f\xd1\x05\x08\xe38\xfd\x8f\xe8FJ\xaa\x9a\x1e\xee\xc9\\\xc4/\xb1s\xf2\xf2\x1e\xffm\xfe\xe3Bfy\x94j\xd9\xad&Pi\xda]\x07U)\x8cF\xf9\x17\xad`\xd2\xa9\x1f-bH\xa82\xdd\x87\xb9\xa5\x91zm\xac\x02\xbd\xb9\x8d\x0cB\xd4\x93\xd2\x8a\xee\x9aC\xaf\xf0#\'\x0b\xf2\xf2\xd47*\xfb\xcbDS~\xfc\xe2\x12\xed\xdc\xce|VI[H\xf0k\xa3\xb7\xbc<\xd0\xce\xa6h\xcaO\xb8\x1a'
    Decrypted: RSA Example
    
---

## 6. Hasil dan Pembahasan
Hasil eksekusi program Implementasi DES:
<img width="1366" height="768" alt="Langkah1-Implementasi DES" src="https://github.com/user-attachments/assets/531cba41-25b3-4dd3-8441-6f3fe1cc9801" />

Hasil eksekusi program Implementasi AES-128:
<img width="1366" height="768" alt="Langkah2-Implementasi AES128" src="https://github.com/user-attachments/assets/ea5088bf-7e49-4c72-93fe-53e9861eea86" />

Hasil eksekusi program Implementasi RSA:
<img width="1366" height="768" alt="Langkah3-Implementasi RSA" src="https://github.com/user-attachments/assets/bf95586b-f17d-40b9-98cd-9e75a1039412" />

Pembahasan: Hasil eksekusi menunjukkan bahwa ketiga algoritma bekerja sesuai konsepnya.
- DES berhasil mengenkripsi dan mendekripsi teks dengan benar, namun keamanannya lemah karena panjang kuncinya pendek.
- AES menghasilkan ciphertext acak dan mampu mengembalikan plaintext dengan tepat, menunjukkan keamanan dan efisiensi yang tinggi.
- RSA juga berjalan baik, menggunakan kunci publik untuk enkripsi dan kunci privat untuk dekripsi, membuktikan konsep asimetrisnya.

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
Dari percobaan yang telah dilakukan, dapat disimpulkan bahwa ketiga algoritma cipher modern (DES, AES, dan RSA) berhasil diimplementasikan dengan baik untuk proses enkripsi dan dekripsi data. DES menggunakan kunci simetris 56 bit dan bekerja pada blok 64 bit, namun keamanannya kini sudah lemah terhadap brute force. AES merupakan pengganti DES yang lebih kuat dan efisien karena mendukung panjang kunci hingga 256 bit serta memiliki kecepatan tinggi dalam proses enkripsi. Sementara itu, RSA menggunakan sistem kunci asimetris yang lebih aman untuk pertukaran kunci dan autentikasi data. Secara keseluruhan, AES dan RSA menjadi standar utama dalam sistem keamanan modern karena kombinasi kekuatan, efisiensi, dan fleksibilitasnya dalam berbagai aplikasi digital.

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
```
commit week6-cipher-modern

Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>

Date:   2025-10-30

    week6-cipher-modern: Cipher Modern (DES, AES, RSA)

```
