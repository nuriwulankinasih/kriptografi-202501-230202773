# Laporan Praktikum Kriptografi
---
Minggu ke-: 3  
Topik: Modular Math (Aritmetika Modular, GCD, Bilangan Prima, Logaritma Diskrit)
Nama: Nuri Wulan Kinasih
NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Menyelesaikan operasi aritmetika modular.
2. Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
3. Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.

---

## 2. Dasar Teori
- Langkah 1 (Aritmetika Modular)

  def mod_add(a, b, n): return (a + b) % n
  def mod_sub(a, b, n): return (a - b) % n
  def mod_mul(a, b, n): return (a * b) % n
  def mod_exp(base, exp, n): return pow(base, exp, n)  # eksponensiasi modular
  
  print("7 + 5 mod 12 =", mod_add(7, 5, 12))
  print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
  print("7^128 mod 13 =", mod_exp(7, 128, 13))

  Hasilnya:

  7 + 5 mod 12 = 0
  7 * 5 mod 12 = 11
  7^128 mod 13 = 3

- Langkah 2 (GCD & Algoritma Euclidean)

  def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

  print("gcd(54, 24) =", gcd(54, 24))

  Hasilnya:

  gcd(54, 24) = 6

- Langkah 3 (Extended Euclidean Algorithm)

  def egcd(a, b):
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    return g, y1 - (b // a) * x1, x1

  def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None
    return x % n

  print("Invers 3 mod 11 =", modinv(3, 11))  # hasil: 4

  Hasilnya:

  Invers 3 mod 11 = 4

- Langkah 4 (Logaritma Diskrit)

  def discrete_log(a, b, n):
    for x in range(n):
        if pow(a, x, n) == b:
            return x
    return None

  print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))  # hasil: 4

  Hasilnya:

  3^x ≡ 4 (mod 7), x = 4
    
---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file dengan nama `aritmatika_modular.py` di folder praktikum/week3-modmath/src/.
2. Membuat file dengan nama `gcd-dan-algoritma euclidean.py` di folder praktikum/week3-modmath/src/.
3. Membuat file dengan nama `extended-euclidean-algorithm.py` di folder praktikum/week3-modmath/src/.
4. Membuat file dengan nama `logaritma-diskrit.py` di folder praktikum/week3-modmath/src/.
5. Menyalin kode program dari panduan praktikum.
6. Menjalankan program dengan perintah sesuai nama file.
---

## 5. Source Code
a. Langkah 1 (Aritmetika Modular)

  def mod_add(a, b, n): return (a + b) % n
  def mod_sub(a, b, n): return (a - b) % n
  def mod_mul(a, b, n): return (a * b) % n
  def mod_exp(base, exp, n): return pow(base, exp, n)  # eksponensiasi modular
  
  print("7 + 5 mod 12 =", mod_add(7, 5, 12))
  print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
  print("7^128 mod 13 =", mod_exp(7, 128, 13))

b. Langkah 2 (GCD & Algoritma Euclidean)

  def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

  print("gcd(54, 24) =", gcd(54, 24))

c. Langkah 3 (Extended Euclidean Algorithm)

  def egcd(a, b):
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    return g, y1 - (b // a) * x1, x1

  def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None
    return x % n

  print("Invers 3 mod 11 =", modinv(3, 11))  # hasil: 4

d. Langkah 4 (Logaritma Diskrit)

  def discrete_log(a, b, n):
    for x in range(n):
        if pow(a, x, n) == b:
            return x
    return None

  print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))  # hasil: 4

---

## 6. Hasil dan Pembahasan
Hasil eksekusi Langkah 1-Aritmetika Modular

<img width="1366" height="768" alt="langkah1_aritmetika_modular" src="https://github.com/user-attachments/assets/dfdda347-1731-4dba-8a11-b06bc5d1c6b2" />

Hasil eksekusi Langkah 2-GCD dan Algoritma Euclidean

<img width="1366" height="768" alt="langkah2_gcd algoritma uclidean" src="https://github.com/user-attachments/assets/59f05143-4b81-4b30-934e-e08dee83ecbc" />

Hasil eksekusi Langkah 3 — Extended Euclidean Algorithm

<img width="1366" height="768" alt="langkah3_Extended Euclidean Algorithm" src="https://github.com/user-attachments/assets/8252d9dd-e866-48b2-847c-0cb7f41ce67b" />

Hasil eksekusi Langkah 4 — Logaritma Diskrit (Discrete Log)

<img width="1366" height="768" alt="langkah4_logaritma diskrit" src="https://github.com/user-attachments/assets/ece9f869-8c5b-4a3a-b5b4-b1fc7ea9e5ec" />

Pembahasan: Semua langkah percobaan berhasil di eksekusi dengan benar tanpa eror. 

---

## 7. Jawaban Pertanyaan
1. Apa peran aritmetika modular dalam kriptografi modern?
   Jawaban: Peran aritmetika modular dalam kriptografi modern adalah memungkinkan operasi matematika dilakukan dalam ruang bilangan terbatas, sehingga                      mendukung proses enkripsi dan dekripsi yang aman tanpa menghasilkan nilai terlalu besar serta menjaga konsistensi hasil dalam sistem kunci publik               maupun simetris.
   
3. Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?
   Jawaban: Invers modular penting dalam algoritma kunci publik seperti RSA karena digunakan untuk membalik proses enkripsi, yaitu menemukan kunci privat yang              dapat mendekripsi pesan yang telah dienkripsi menggunakan kunci publik, sehingga menjamin keamanan komunikasi antara pengirim dan penerima.
  
4. Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?
   Jawaban: Tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar adalah kompleksitas komputasinya yang sangat tinggi, sebab belum ada                  algoritma efisien untuk menghitungnya dengan cepat, hal ini justru menjadi dasar keamanan sistem kriptografi seperti Diffie–Hellman dan ElGamal.
   
---

## 8. Kesimpulan
Dari percobaan ini dapat disimpulkan bahwa aritmetika modular merupakan dasar penting dalam kriptografi karena memungkinkan proses enkripsi dan dekripsi berjalan efisien dalam ruang bilangan terbatas. Konsep seperti GCD, invers modular, dan logaritma diskrit menunjukkan bahwa keamanan algoritma kriptografi modern bergantung pada kompleksitas perhitungan matematika dalam modulus besar.

---

## 9. Daftar Pustaka

---

## 10. Commit Log

```
commit week3-moodmath-gcd
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-10-19

    week3-moodmath-gcd: implementasi Modular Math (Aritmetika Modular, GCD, Bilangan Prima, Logaritma Diskrit) dan laporan.

```
