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
- Python 3.x  
- Visual Studio Code 
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file `signature.py` di folder `praktikum/week9-digital-signature/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python signature.py`
4. Mencoba memodifikasi program.
5. Membuat folder screenshots di folder praktikum/week9-digital lalu mengupload hasil praktikum di dalam folder tersebut.

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
    Signature: 65ab56d6fa8f66cc6b28887fafeea3b16498cd18e0b607c2f85e61950a058bd2b1b484365ffe9b258d701efcf7c1f9b46a27069c9ca19d82820ca2685510e54eea3329a76ab76dc7d4f06dc78c20fa11ccea21c31e6b419092f32f0a60eb84ca6bd93f0686595bfa401735385380589d6ca937eed9fb2174bf1f0236b0936af24181a155ba025ca878767b87515d2394c49eb82180a7a6e434d06099e6566e95ef9379898a0469a60a0fa3959151a7f77c9f8458ef4d34d71bd1be24cd094684796def525e7bcb51523ab68285e1f2a7d8ff53e22737149f07ede036df496f45d9d87b87e4a9c511ac7dc2352ff8cbe32fcf526c8545ccced8b99f5497627a8c

### Langkah 2 — Verifikasi Tanda Tangan

    try:
        pkcs1_15.new(public_key).verify(h, signature)
        print("Verifikasi berhasil: tanda tangan valid.")
    except (ValueError, TypeError):
        print("Verifikasi gagal: tanda tangan tidak valid.")

Hasilnya: 

    Verifikasi berhasil: tanda tangan valid.

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

    Verifikasi gagal: tanda tangan tidak cocok dengan pesan.

### Signature 
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
    
    try:
        pkcs1_15.new(public_key).verify(h, signature)
        print("Verifikasi berhasil: tanda tangan valid.")
    except (ValueError, TypeError):
        print("Verifikasi gagal: tanda tangan tidak valid.")

Hasilnya :

    Signature: 164383e1bc19bf3c9454611553677a62ddd7e6e90f6ea042db8784674aec1c58128b6b0e7692bf30a16b76fdae069f6c132671bad4d12d9a5a67fdda970eb7560a742b78ce3ea7b725889fdcf399044df50cd2bf8a1ba2c18bc3ebcfb702d3cdce04229224cb960657a810b067dbdba0fe55519a0f1bc2d9df92ae56d716dba2191da69d3063fbd67ff7b0436a55e710809f2addfa1026251a42b8782427909b0ef13e84745a557d0985b8190b178a42516563cd89f3e06b5fbdf56df362d44cc1b496f2758bbb54280cd243f9b0e83daf3a7effd8db5b415cac385ff85461a324b396c2ddbb16e3a1b9eff490792d1c26144b06816254c76550f493c913679c
    Verifikasi berhasil: tanda tangan valid.

### Signature Modifikasi

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
    
    # Modifikasi pesan
    fake_message = b"Hello, ini pesan palsu."
    h_fake = SHA256.new(fake_message)
    
    try:
        pkcs1_15.new(public_key).verify(h_fake, signature)
        print("Verifikasi berhasil (seharusnya gagal).")
    except (ValueError, TypeError):
        print("Verifikasi gagal: tanda tangan tidak cocok dengan pesan.")

Hasilnya : 

    Signature: 5f8c113b56832fc25436336185e55c5cec4604dc9adac56f2493e5f84df5a9ce09f3031507a3a55edeb84bed3c28d1dcc9ddedf4ed22b00ccfbe36780c8e725426f6aa3a64b66021be776c598d02c626e28a635987e09acaf465206bf9fadddda48f366c80ecbf91ea45c77f63d68ec9b34afdfec17c6e19aa5705dde6f320338cb3edf5fe8556ad61b090cda054ae9b2a96021be776c598d02c626e28a635987e024c14fcb2931136aa117af19521851877a96036788ba2c5f6f16de2603bb0be2dfee58df87a66b8c16aa47d28c97fcee47b30f92d4d07edf6b1a0eacc4e9f7927952662c433f06f2c46a9ae7a96036788ba2c5f6f16de2603bb0be290aea055ef1323fc83cdb2a59f3cf9b44457cd4eafabdeb20ee96004f7d377464c9fd1                                                                                 4c9fd1
    Verifikasi gagal: tanda tangan tidak cocok dengan pesan.
    
---

## 6. Hasil dan Pembahasan
Hasil eksekusi program Digital Signature dengan RSA/ DSA:

<img width="1366" height="768" alt="Hasil Signature py" src="https://github.com/user-attachments/assets/183b4bb8-2324-4339-af70-ac955d27599e" />
<img width="1366" height="768" alt="Hasil Signature modifikasi" src="https://github.com/user-attachments/assets/2aab9609-0ac6-474c-b00d-68998424daeb" />

Penjelasan : 

Pada praktikum ini saya melakukan pembuatan dan pengujian tanda tangan digital menggunakan algoritma RSA. Awalnya, saya membuat sebuah tanda tangan dari pesan yang masih asli, kemudian langsung memverifikasinya tanpa melakukan perubahan apa pun pada isi pesan tersebut. Hasil verifikasi menunjukkan bahwa tanda tangan valid karena masih sesuai dengan pesan awal. Selanjutnya, saya mencoba mengubah isi pesan namun tetap menggunakan tanda tangan yang sama. Ketika dilakukan proses verifikasi, hasilnya menjadi gagal karena tanda tangan tidak lagi cocok dengan pesan yang telah dimodifikasi. Dari percobaan ini saya memahami bahwa tanda tangan digital hanya berlaku untuk pesan yang asli, sehingga perubahan sekecil apa pun pada pesan dapat terdeteksi dan menyebabkan verifikasi ditolak. Hal ini membuktikan bahwa digital signature berfungsi untuk menjaga keaslian dan integritas data.

---

## 7. Jawaban Pertanyaan
1. Apa perbedaan utama antara enkripsi RSA dan tanda tangan digital RSA?
2. Mengapa tanda tangan digital menjamin integritas dan otentikasi pesan?
3. Bagaimana peran Certificate Authority (CA) dalam sistem tanda tangan digital modern?

Jawaban : 
1. Perbedaan utama antara enkripsi RSA dan tanda tangan digital RSA terletak pada tujuan dan penggunaan kuncinya. Enkripsi RSA digunakan untuk menjaga kerahasiaan pesan, di mana pesan dienkripsi menggunakan public key penerima dan hanya dapat dibuka dengan private key penerima. Sebaliknya, tanda tangan digital RSA bertujuan untuk menjamin keaslian dan integritas pesan, di mana pesan ditandatangani menggunakan private key pengirim dan diverifikasi menggunakan public key pengirim.
   
2. Tanda tangan digital menjamin integritas dan otentikasi pesan karena tanda tangan dibuat dari hasil hash pesan yang dienkripsi dengan private key pengirim. Jika isi pesan diubah, nilai hash akan berubah sehingga tanda tangan tidak lagi valid. Selain itu, karena hanya pemilik private key yang dapat membuat tanda tangan tersebut, penerima dapat memastikan bahwa pesan benar-benar berasal dari pengirim yang sah.

3. Peran Certificate Authority (CA) dalam sistem tanda tangan digital modern adalah sebagai pihak tepercaya yang bertugas memverifikasi identitas pemilik kunci publik. CA menerbitkan sertifikat digital yang mengaitkan identitas seseorang atau organisasi dengan public key tertentu. Dengan adanya CA, pengguna dapat mempercayai bahwa kunci publik yang digunakan untuk verifikasi tanda tangan digital memang milik pihak yang benar, sehingga meningkatkan keamanan dan kepercayaan dalam komunikasi digital. 
---

## 8. Kesimpulan
Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa algoritma RSA berhasil diimplementasikan untuk membuat dan memverifikasi tanda tangan digital. Hasil pengujian menunjukkan bahwa tanda tangan digital hanya valid untuk pesan asli dan akan gagal diverifikasi apabila isi pesan mengalami perubahan. Hal ini membuktikan bahwa digital signature efektif dalam menjaga keaslian (otentikasi) dan integritas data pada proses pertukaran informasi digital.

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week9-digital-signature
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-12-13

    week9-digital-signature: Digital Signature (RSA/DSA)
```
