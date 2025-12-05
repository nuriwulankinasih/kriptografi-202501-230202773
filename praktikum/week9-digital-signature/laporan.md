# Laporan Praktikum Kriptografi
Minggu ke-: 9
Topik: Digital Signature (RSA/DSA)

Nama: Nuri Wulan Kinasih 
NIM: 230202773 
Kelas: 5IKRB 

---

## 1. Tujuan
1. Mengimplementasikan tanda tangan digital menggunakan algoritma RSA/DSA.
2. Memverifikasi keaslian tanda tangan digital.
3. Menjelaskan manfaat tanda tangan digital dalam otentikasi pesan dan integritas data.
---

## 2. Dasar Teori
Digital signature atau tanda tangan digital adalah mekanisme kriptografi yang memastikan keaslian, keutuhan, dan penolakan kembali suatu pesan atau dokumen digital. Tanda tangan digital dibuat dengan menghitung nilai hash dari dokumen, kemudian mengenkripsinya menggunakan kunci privat milik pengirim. Hasil enkripsi tersebut menjadi tanda tangan digital yang dapat diverifikasi oleh penerima menggunakan kunci publik, sehingga bisa dipastikan bahwa dokumen tidak berubah dan benar berasal dari pengirim yang sah.

Pada algoritma RSA, tanda tangan digital dibuat dengan mengenkripsi hash dokumen menggunakan kunci privat. Penerima kemudian menggunakan kunci publik pengirim untuk memverifikasi tanda tangan tersebut. RSA sering digunakan karena konsepnya sederhana dan dapat dipakai baik untuk enkripsi maupun digital signature. Namun, performanya relatif lebih lambat dan membutuhkan ukuran kunci yang besar untuk mempertahankan keamanan di era modern.

Sementara itu, Digital Signature Algorithm (DSA) dibuat khusus untuk keperluan tanda tangan digital dan tidak digunakan untuk enkripsi. DSA bekerja berdasarkan konsep logaritma diskrit dan menghasilkan tanda tangan yang lebih efisien serta proses penandatanganan yang lebih cepat. Meski demikian, DSA sangat bergantung pada bilangan acak yang kuat; jika nilai acaknya lemah atau bocor, kunci privat dapat diketahui oleh pihak lain sehingga mengancam keamanan tanda tangan digital.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code 
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )
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
### Langkah 1 — Generate Key dan Buat Tanda Tangan

    from Crypto.PublicKey import RSA
    from Crypto.Signature import pkcs1_15
    from Crypto.Hash import SHA256
    
    # Generate pasangan kunci RSA
    key = RSA.generate(2048)
    private_key = key
    public_key = key.publickey()
    
    # Pesan yang akan ditandatangani
    message = b"Hello, ini pesan penting."
    h = SHA256.new(message)
    
    # Buat tanda tangan dengan private key
    signature = pkcs1_15.new(private_key).sign(h)
    print("Signature:", signature.hex())
Hasilnya: 





### Langkah 2 — Verifikasi Tanda Tangan

    try:
        pkcs1_15.new(public_key).verify(h, signature)
        print("Verifikasi berhasil: tanda tangan valid.")
    except (ValueError, TypeError):
        print("Verifikasi gagal: tanda tangan tidak valid.")

Hasilnya: 



### Langkah 3 — Uji Modifikasi Pesan

    # Modifikasi pesan
    fake_message = b"Hello, ini pesan palsu."
    h_fake = SHA256.new(fake_message)

    try:
        pkcs1_15.new(public_key).verify(h_fake, signature)
        print("Verifikasi berhasil (seharusnya gagal).")
    except (ValueError, TypeError):
        print("Verifikasi gagal: tanda tangan tidak cocok dengan pesan.")

Hasilnya: 



---

## 6. Hasil dan Pembahasan
### Hasil eksekusi program Generate Key dan Buat Tanda Tangan:


### Hasil eksekusi program Verifikasi Tanda Tangan:


### Hasil eksekusi program Uji Modifikasi Pesan: 


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
