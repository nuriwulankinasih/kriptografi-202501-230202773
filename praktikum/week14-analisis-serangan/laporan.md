# Laporan Praktikum Kriptografi
Minggu ke-: 14
Topik: Analisis Serangan Kriptografi

Nama: Nuri Wulan Kinasih

NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Mengidentifikasi jenis serangan pada sistem informasi nyata.
2. Mengevaluasi kelemahan algoritma kriptografi yang digunakan.
3. Memberikan rekomendasi algoritma kriptografi yang sesuai untuk perbaikan keamanan.

---

## 2. Dasar Teori
Analisis Serangan Kriptografi adalah proses mempelajari dan mengevaluasi berbagai metode serangan yang dapat digunakan untuk melemahkan atau menembus sistem kriptografi. Tujuan utama analisis ini bukan untuk merusak sistem, melainkan untuk mengidentifikasi celah keamanan sehingga algoritma, protokol, atau implementasi kriptografi dapat diperbaiki dan diperkuat. Dengan analisis serangan, pengembang dapat memastikan bahwa sistem kriptografi benar-benar aman ketika digunakan di dunia nyata.

Serangan kriptografi dapat dilakukan dengan berbagai pendekatan, seperti brute force attack, cryptanalysis attack, dan side-channel attack. Brute force attack mencoba semua kemungkinan kunci hingga menemukan kunci yang benar, sedangkan cryptanalysis memanfaatkan kelemahan matematis dari algoritma. Side-channel attack tidak menyerang algoritma secara langsung, tetapi memanfaatkan informasi dari proses implementasi, seperti waktu eksekusi, konsumsi daya, atau pola akses memori.

Melalui analisis serangan kriptografi, sistem keamanan dapat dievaluasi dari sisi teori maupun praktik. Hasil analisis ini digunakan untuk menentukan tingkat kekuatan algoritma, memilih ukuran kunci yang aman, serta memastikan bahwa implementasi kriptografi tidak mudah dieksploitasi. Oleh karena itu, analisis serangan kriptografi merupakan bagian penting dalam pengembangan sistem keamanan informasi yang andal.

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
    import random

    # ================================
    # SIMULASI SERVER LAMA (SSL 3.0)
    # ================================
    server_config = {
        "protocol": "SSLv3",     # Protokol lama dan tidak aman
        "cipher": "CBC"
    }
    
    # Data sensitif yang dikirim user
    secret_cookie = "SESSIONID=ABCD1234"
    
    # ================================
    # SIMULASI ENKRIPSI SEDERHANA
    # ================================
    def encrypt_ssl3(data):
        # Simulasi enkripsi CBC yang lemah
        encrypted = ""
        for c in data:
            encrypted += chr(ord(c) + 3)  # enkripsi palsu
        return encrypted
    
    def decrypt_ssl3(data):
        decrypted = ""
        for c in data:
            decrypted += chr(ord(c) - 3)
        return decrypted
    
    # ================================
    # SERVER MENGIRIM DATA
    # ================================
    def server_send_data():
        print("[SERVER] Menggunakan protokol:", server_config["protocol"])
        encrypted = encrypt_ssl3(secret_cookie)
        print("[SERVER] Data terenkripsi:", encrypted)
        return encrypted
    
    # ================================
    # PENYERANG (POODLE ATTACK)
    # ================================
    def poodle_attack(intercepted_data):
        print("\n[ATTACKER] Melakukan POODLE Attack...")
        
        # Karena SSL 3.0 lemah, attacker bisa memecahkan enkripsi
        recovered = decrypt_ssl3(intercepted_data)
        
        print("[ATTACKER] Data berhasil dibaca:", recovered)
        return recovered
    
    # ================================
    # EKSEKUSI UTAMA
    # ================================
    if __name__ == "__main__":
        print("=== SIMULASI POODLE ATTACK (SSL 3.0) ===\n")
        
        encrypted_data = server_send_data()
        stolen = poodle_attack(encrypted_data)
        
        print("\n=== KESIMPULAN ===")
        print("Cookie bocor karena server masih menggunakan SSL 3.0 dan CBC mode.")

Hasilnya:

    [ATTACKER] Melakukan POODLE Attack...
    [ATTACKER] Data berhasil dibaca: SESSIONID=ABCD1234
    
    === KESIMPULAN ===
    Cookie bocor karena server masih menggunakan SSL 3.0 dan CBC mode.

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program poodle_attack_demo:
<img width="1920" height="1080" alt="poodle demo" src="https://github.com/user-attachments/assets/ec4e1929-b95d-4a30-8cd4-b379a18a12a3" />

Pembahasan:

Hasil percobaan menunjukkan bahwa ketika server masih menggunakan SSL 3.0 dengan CBC, penyerang dapat:
- Memaksa koneksi turun (downgrade)
- Menyadap data terenkripsi
- Membaca cookie login dan session pengguna

Dalam kasus nyata POODLE Attack (2014), jutaan koneksi HTTPS bisa disadap karena:
1. Kelemahan Algoritma
    SSL 3.0 menggunakan CBC mode tanpa verifikasi padding yang aman, sehingga isi pesan bisa ditebak sedikit demi sedikit.
2. Kelemahan Implementasi & Konfigurasi
    Server dan browser masih mengizinkan fallback ke SSL 3.0 walaupun sudah usang.

---

## 7. Jawaban Pertanyaan
1. Mengapa banyak sistem lama masih rentan terhadap brute force atau dictionary attack?
2. Apa bedanya kelemahan algoritma dengan kelemahan implementasi?
3. Bagaimana organisasi dapat memastikan sistem kriptografi mereka tetap aman di masa depan?

Jawaban:
1. Banyak sistem lama masih rentan karena menggunakan algoritma kriptografi yang sudah usang, ukuran kunci yang pendek, serta metode penyimpanan kata sandi yang tidak aman, seperti hash tanpa salt atau bahkan teks biasa. Selain itu, sistem lama sering tidak menerapkan pembatasan percobaan login, sehingga penyerang dapat mencoba banyak kombinasi kata sandi secara otomatis tanpa terdeteksi.
2. Kelemahan algoritma berkaitan dengan desain matematis algoritma kriptografi itu sendiri, misalnya algoritma yang secara teori dapat dipecahkan atau memiliki celah kriptografi. Sementara itu, kelemahan implementasi terjadi ketika algoritma yang sebenarnya aman diterapkan dengan cara yang salah, seperti penggunaan kunci yang lemah, manajemen kunci yang buruk, atau kesalahan pemrograman yang membuka peluang serangan.
3. Organisasi dapat memastikan keamanan dengan cara menggunakan algoritma dan standar kriptografi terbaru, menerapkan ukuran kunci yang direkomendasikan, serta melakukan pembaruan sistem secara berkala. Selain itu, audit keamanan, pengujian penetrasi, dan pemantauan terhadap perkembangan serangan kriptografi juga penting agar sistem dapat beradaptasi terhadap ancaman baru.

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
```
commit week14-analisis-serangan
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-01-12

    week14-analisis-serangan: Analisis Serangan Kriptografi

```
