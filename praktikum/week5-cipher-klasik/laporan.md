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
1. Membuat file `implementasi-caesar cipher.py` di folder `praktikum/week5-cipher-klasik/src/`.
2. Membuat file `implementasi-vignere cipher.py` di folder `praktikum/week5-cipher-klasik/src/`.
3. Membuat file `implementasi-transposisi sederhana.py` di folder `praktikum/week5-cipher-klasik/src/`.
4. Menjalankan program dengan perintah sesuai pada file

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

### Langkah 3 -- Implementasi Transposisi Sederhana

    def transpose_encrypt(plaintext, key=5):
        ciphertext = [''] * key
        for col in range(key):
            pointer = col
            while pointer < len(plaintext):
                ciphertext[col] += plaintext[pointer]
                pointer += key
        return ''.join(ciphertext)
    
    def transpose_decrypt(ciphertext, key=5):
        num_of_cols = int(len(ciphertext) / key + 0.9999)
        num_of_rows = key
        num_of_shaded_boxes = (num_of_cols * num_of_rows) - len(ciphertext)
        plaintext = [''] * num_of_cols
        col = 0
        row = 0
        for symbol in ciphertext:
            plaintext[col] += symbol
            col += 1
            if (col == num_of_cols) or (col == num_of_cols - 1 and row >= num_of_rows - num_of_shaded_boxes):
                col = 0
                row += 1
        return ''.join(plaintext)
    
    # Contoh uji
    msg = "TRANSPOSITIONCIPHER"
    enc = transpose_encrypt(msg, key=5)
    dec = transpose_decrypt(enc, key=5)
    print("Plaintext :", msg)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)


Hasilnya:

    Plaintext : TRANSPOSITIONCIPHER
    Ciphertext: TPIPROOHASNENICRSTI
    Decrypted : TRANSPOSITIONCIPHER
    

---

## 6. Hasil dan Pembahasan

Hasil eksekusi program Implementasi Caesar Cipher:

<img width="1366" height="768" alt="langkah1-implementasi caesar cipher" src="https://github.com/user-attachments/assets/accd5a56-f0ca-4d09-a19f-5822394bc565" />

Hasil eksekusi program Implementasi Vignere Cipher:

<img width="1366" height="768" alt="Langkah2-implementasi vignere cipher" src="https://github.com/user-attachments/assets/8d97604c-a7d4-4ce0-b5ce-16a84dc468d0" />

Hasil eksekusi program Implementasi Transposisi Sederhana:

<img width="1366" height="768" alt="Langkah3-implementasi transposisi sederhana" src="https://github.com/user-attachments/assets/1cd08a9a-671a-43f4-b857-2734c945fa4f" />


Pembahasan:

Berdasarkan hasil eksekusi program, ketiga algoritma cipher klasik Caesar Cipher, Vigenère Cipher, dan Transposisi Sederhana berhasil melakukan proses enkripsi dan dekripsi dengan benar. Caesar Cipher menggeser huruf berdasarkan nilai kunci tertentu, Vigenère Cipher menggunakan kata kunci untuk menghasilkan pola enkripsi yang lebih kompleks, sedangkan Transposisi Cipher mengacak urutan huruf tanpa mengubah karakter aslinya. Hasil yang diperoleh menunjukkan bahwa algoritma dapat mengubah teks asli menjadi ciphertext dan mengembalikannya lagi ke bentuk semula, menandakan implementasi program berjalan sesuai dengan teori kriptografi klasik.


---

## 7. Jawaban Pertanyaan
1. Apa kelemahan utama algoritma Caesar Cipher dan Vigenère Cipher?
2. Mengapa cipher klasik mudah diserang dengan analisis frekuensi?
3. Bandingkan kelebihan dan kelemahan cipher substitusi vs transposisi.

Jawaban:

1. Kelemahan Caesar Cipher adalah jumlah kuncinya yang sangat terbatas, yaitu hanya 25 kemungkinan pergeseran. Hal ini membuatnya mudah dipecahkan menggunakan     metode brute force atau dengan analisis frekuensi, karena pola huruf pada ciphertext masih mengikuti pola bahasa aslinya. Selain itu, algoritma ini tidak       cukup aman untuk digunakan pada sistem modern karena tidak melibatkan variasi kunci yang kompleks.

    Kelemahan Vigenère Cipher terletak pada penggunaan kata kunci yang dapat menjadi titik lemah. Jika panjang kata kunci pendek atau berulang, pola enkripsi       dapat terdeteksi dan dianalisis menggunakan metode Kasiski examination atau Friedman test. Meskipun lebih kuat dibanding Caesar Cipher, Vigenère Cipher         tetap rentan terhadap serangan analisis pola jika kunci tidak dijaga kerahasiaannya.

2. Cipher klasik mudah diserang dengan analisis frekuensi karena setiap huruf dalam ciphertext masih mempertahankan pola kemunculan yang mirip dengan bahasa       aslinya. Misalnya, dalam bahasa Indonesia huruf “A” atau “E” muncul lebih sering dibandingkan huruf lain. Dengan menganalisis frekuensi huruf dalam             ciphertext, penyerang dapat menebak huruf-huruf asli dan memecahkan pesan dengan cukup mudah.

3. Cipher substitusi mengganti setiap huruf dengan huruf lain berdasarkan aturan tertentu, sedangkan cipher transposisi hanya menukar posisi huruf tanpa           mengganti karakter itu sendiri. Kelebihan cipher substitusi adalah sederhana dan cepat diterapkan, tetapi mudah diretas melalui analisis frekuensi.             Sementara itu, cipher transposisi lebih sulit dipecahkan dengan analisis frekuensi karena huruf tidak berubah, namun tetap dapat diserang jika pola             penukarannya terdeteksi.

---

## 8. Kesimpulan
Berdasarkan percobaan yang telah dilakukan, dapat disimpulkan bahwa algoritma cipher klasik seperti Caesar Cipher, Vigenère Cipher, dan Transposisi Sederhana berhasil diimplementasikan dengan baik untuk melakukan proses enkripsi dan dekripsi teks. Ketiganya menunjukkan prinsip dasar kriptografi, yaitu mengubah pesan asli menjadi bentuk yang sulit dibaca tanpa kunci. Namun, meskipun efektif untuk memahami konsep dasar enkripsi, cipher klasik masih memiliki kelemahan keamanan dan tidak cocok digunakan dalam sistem modern karena mudah dipecahkan melalui analisis pola dan frekuensi huruf.

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
```
commit week5-cipher-klasik
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>

Date:   2025-10-25

    week5-cipher-klasik: Cipher Klasik (Caesar, Vigenère, Transposisi)

```
