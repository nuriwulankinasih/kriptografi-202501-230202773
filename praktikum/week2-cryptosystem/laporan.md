# Laporan Praktikum Kriptografi
Minggu ke-: 2
Topik: cryptosystem [komponen,enkripsi,dekripsi,simetris,asimetris]  
Nama: Nuri Wulan Kinasih 
NIM: 230202773 
Kelas: 5IKRB 

# 1. Tujuan
1. Mengidentifikasi komponen dasar kriptosistem (plaintext, ciphertext, kunci, algoritma).
2. Menggambarkan proses enkripsi dan dekripsi sederhana.
3. Mengklasifikasikan jenis kriptosistem (simetris dan asimetris).

# 2. Dasar Teori

## Membuat skema kriptosistem
<img width="511" height="51" alt="skema kriptosistem" src="https://github.com/user-attachments/assets/e91bcaef-f1c2-4ea5-86d7-95ae8a008193" /> 

## Implementasi program sederhana
Simulasi enkripsi & dekripsi menggunakan substitusi sederhana (misalnya Caesar Cipher).

      # file: praktikum/week2-cryptosystem/src/simple_crypto.py
      def encrypt(plaintext, key):
          result = ""
          for char in plaintext:
              if char.isalpha():
                  shift = 65 if char.isupper() else 97
                  result += chr((ord(char) - shift + key) % 26 + shift)
              else:
                  result += char
          return result
      
      def decrypt(ciphertext, key):
          result = ""
          for char in ciphertext:
              if char.isalpha():
                  shift = 65 if char.isupper() else 97
                  result += chr((ord(char) - shift - key) % 26 + shift)
              else:
                  result += char
          return result
      
      if __name__ == "__main__":
          message = "<230202773><Nuri Wulan Kinasih>"
          key = 5
      
          enc = encrypt(message, key)
          dec = decrypt(enc, key)
      
          print("Plaintext :", message)
          print("Ciphertext:", enc)
          print("Decrypted :", dec)

   Ekspektasi Keluaran

         Plaintext : <230202773><Nuri Wulan Kinasih>
         Ciphertext: <230202773><Szwn Bzqfs Pnsfxnm>
         Decrypted : <230202773><Nuri Wulan Kinasih>

## Klasifikasi Simetris & Asimetris
1. Simetris
   Kriptosistem simetris menggunakan satu kunci yang sama untuk mengenkripsi dan mendekripsi pesan. Keduanya (pengirim dan penerima)         harus memiliki kunci rahasia yang sama.
 
   Contoh Algoritma:
    - AES (Advanced Encryption Standard)
      Digunakan untuk mengamankan data pada aplikasi seperti WhatsApp dan Wi-Fi (WPA2/WPA3).
      Misalnya, pesan “HELLO” dienkripsi dengan kunci “KUNCI123” dan hanya bisa dibuka kembali menggunakan kunci yang sama.
    - DES (Data Encryption Standard)
      Dulu digunakan dalam sistem perbankan dan ATM untuk mengenkripsi PIN atau data transaksi, tetapi sekarang sudah jarang dipakai            karena keamanannya dianggap kurang kuat.
2. Asimetris
   Kriptosistem asimetris menggunakan dua kunci berbeda, yaitu kunci publik (untuk enkripsi) dan kunci privat (untuk dekripsi). Hanya        pemilik kunci privat yang bisa membuka pesan yang dikunci dengan kunci publiknya.

   Contoh Algoritma: 
    - RSA (Rivest–Shamir–Adleman)
      Digunakan dalam HTTPS, email terenkripsi (PGP), dan tanda tangan digital untuk mengamankan komunikasi di internet.
    - ECC (Elliptic Curve Cryptography)
      Banyak digunakan pada perangkat mobile dan dompet kripto (cryptocurrency wallets) karena tingkat keamanannya tinggi dengan ukuran         kunci yang lebih kecil.

## Komponen Kriptosistem
1. Plaintext
   Merupakan pesan atau data asli yang ingin diamankan sebelum dienkripsi. Plaintext masih dapat dibaca dan dipahami oleh siapa pun.
2. Ciphertext
   Adalah hasil dari proses enkripsi terhadap plaintext. Bentuknya berupa teks acak yang tidak dapat dibaca tanpa kunci yang benar.
3. Algoritma Enkripsi dan Dekripsi
   Algoritma enkripsi digunakan untuk mengubah plaintext menjadi ciphertext, sedangkan algoritma dekripsi digunakan untuk mengembalikan      ciphertext menjadi plaintext.
4. Kunci (Key)
   Nilai rahasia yang digunakan dalam proses enkripsi dan dekripsi. Pada sistem simetris digunakan satu kunci yang sama, sedangkan pada      sistem asimetris digunakan dua kunci, yaitu kunci publik dan kunci privat.

# 3. Alat dan Bahan
- Python 3.x
- Visual Studio Code
- Git dan akun GitHub
- Google chrome
- Google schollar.

# 4. Langkah Percobaan
1. Membuat file simple-cryptosystem.py di folder praktikum/week2-cryptosystem/src/.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah python simple-cryptosystem.py.
4. Membuat ringkasan perbedaan antara kriptosistem simetris dan asimetris.
5. Mengaploud hasil eksekusi di folder praktikum/week2-cryptosistem/screenshots/
6. Menjawab pertanyaan diskusi.

# 5. Source Code

      # file: praktikum/week2-cryptosystem/src/simple_crypto.py
      def encrypt(plaintext, key):
          result = ""
          for char in plaintext:
              if char.isalpha():
                  shift = 65 if char.isupper() else 97
                  result += chr((ord(char) - shift + key) % 26 + shift)
              else:
                  result += char
          return result
      
      def decrypt(ciphertext, key):
          result = ""
          for char in ciphertext:
              if char.isalpha():
                  shift = 65 if char.isupper() else 97
                  result += chr((ord(char) - shift - key) % 26 + shift)
              else:
                  result += char
          return result
      
      if __name__ == "__main__":
          message = "<230202773><Nuri Wulan Kinasih>"
          key = 5
      
          enc = encrypt(message, key)
          dec = decrypt(enc, key)
      
          print("Plaintext :", message)
          print("Ciphertext:", enc)
          print("Decrypted :", dec)

# 6. Hasil dan Pembahasan
Diagram Kriptosistem: 

<img width="511" height="51" alt="skema kriptosistem" src="https://github.com/user-attachments/assets/1788ec83-e53c-44d4-b511-cb3b17fbe3e2" />

Hasil eksekusi program Caesar Cipher:

<img width="1366" height="768" alt="hasil-eksekusi" src="https://github.com/user-attachments/assets/27c3c97f-7987-4a45-acc8-f13df9e8fec5" />

# 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: …  
- Pertanyaan 2: …  
)
---

# 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

# 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

# 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
