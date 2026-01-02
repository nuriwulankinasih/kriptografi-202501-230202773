# Laporan Praktikum Kriptografi
Minggu ke-: 11
Topik: Secret Sharing (Shamir’s Secret Sharing)

Nama: Nuri Wulan Kinasih  

NIM: 230202773        

Kelas: 5IKRB

---

## 1. Tujuan
1. Menjelaskan konsep Shamir Secret Sharing (SSS).
2. Melakukan simulasi pembagian rahasia ke beberapa pihak menggunakan skema SSS.
3. Menganalisis keamanan skema distribusi rahasia.
---

## 2. Dasar Teori
Shamir’s Secret Sharing merupakan salah satu metode kriptografi yang digunakan untuk membagi sebuah rahasia (secret) menjadi beberapa bagian yang disebut shares. Metode ini dirancang oleh Adi Shamir pada tahun 1979 dengan tujuan meningkatkan keamanan penyimpanan dan pengelolaan informasi sensitif. Dalam skema ini, sebuah rahasia tidak disimpan secara utuh pada satu pihak, melainkan dibagi ke beberapa pihak sehingga tidak ada satu pihak pun yang dapat mengetahui rahasia tersebut secara sendiri.

Prinsip utama Shamir’s Secret Sharing adalah konsep threshold scheme (k, n), di mana sebuah rahasia dibagi menjadi n bagian dan hanya dapat direkonstruksi jika minimal k bagian digabungkan kembali. Skema ini memanfaatkan konsep matematika polinomial, di mana rahasia disimpan sebagai nilai konstanta dari sebuah polinomial berderajat k−1. Selama jumlah share yang dikumpulkan kurang dari k, maka rahasia tidak dapat diketahui, sehingga menjamin kerahasiaan informasi meskipun sebagian share bocor.

Shamir’s Secret Sharing banyak digunakan dalam sistem keamanan modern, seperti manajemen kunci kriptografi, penyimpanan cadangan data penting, dan sistem otorisasi terdistribusi. Dengan membagi rahasia ke beberapa pihak, risiko kehilangan data akibat kegagalan satu pihak dapat diminimalkan, sekaligus meningkatkan ketahanan terhadap serangan. Oleh karena itu, skema ini menjadi solusi yang efektif untuk menjaga keamanan dan ketersediaan informasi dalam lingkungan yang membutuhkan tingkat kepercayaan dan keamanan tinggi.

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
    
    # PRIME besar (harus lebih besar dari secret)
    PRIME = 2**521 - 1
    
    def string_to_int(text):
        return int.from_bytes(text.encode("utf-8"), "big")
    
    def int_to_string(number):
        length = (number.bit_length() + 7) // 8
        return number.to_bytes(length, "big").decode("utf-8")
    
    def split_secret(secret, k, n):
        secret_int = string_to_int(secret)
    
        coeffs = [secret_int] + [random.randrange(1, PRIME) for _ in range(k - 1)]
    
        def polynomial(x):
            return sum(coeffs[i] * pow(x, i, PRIME) for i in range(k)) % PRIME
    
        return [(i, polynomial(i)) for i in range(1, n + 1)]
    
    def recover_secret(shares):
        def lagrange(x, points):
            total = 0
            for i, (xi, yi) in enumerate(points):
                term = yi
                for j, (xj, _) in enumerate(points):
                    if i != j:
                        term *= (x - xj) * pow(xi - xj, -1, PRIME)
                        term %= PRIME
                total += term
            return total % PRIME
    
        secret_int = lagrange(0, shares)
        return int_to_string(secret_int)
    
    # ============================
    # MAIN
    # ============================
    secret = "KriptografiUPB2025"
    
    shares = split_secret(secret, 3, 5)
    print("Shares:")
    for s in shares:
        print(s)
    
    recovered = recover_secret(shares[:3])
    print("\nRecovered secret:", recovered)

Hasilnya :

    (1, 3059922323003560657135166065444894582706920526301386073747359322319028860617287486376724589230610771490126594550604396025864744552930183268166717761925746784)
    (2, 1935247417478662038012349328445708941638015299926968651373159720233295119925955100274761030704549852767072791886384192867393903656518266784405139142633411187)
    (3, 3490772943555913857613450588083836294062719621020053142271864652928341961323658893816668965083271798808134903398826820915497014707391589518604441958082476141)
    (4, 861701241104706400956569045277883422711598189437334137049010661218626201412742814879888751705322054636016617696451422133052089705833507658190597917157884495)
    (5, 912829970255649383023605499109243544854086305322117045099061204289691023590862915586980031232155175228014246170738854557181116651560665015737635310974693400)

Recovered secret: KriptografiUPB2025

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
