# Laporan Praktikum Kriptografi
Minggu ke-: 4
Topik: Entropy & Unicity Distance (Evaluasi Kekuatan Kunci dan Brute Force) 

Nama: Nuri Wulan Kinasih

NIM: 230202773

Kelas: 5IKRB

---

## 1. Tujuan
1. Menyelesaikan perhitungan sederhana terkait entropi kunci.
2. Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3. Menghitung unicity distance untuk ciphertext tertentu.
4. Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5. Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Entropy dalam konteks kriptografi menggambarkan tingkat ketidakpastian atau keacakan dalam sistem kunci. Semakin tinggi nilai entropi, semakin sulit bagi penyerang untuk menebak atau memprediksi kunci yang digunakan dalam proses enkripsi. Entropi biasanya diukur dalam bit. misalnya, sebuah kunci 128-bit dengan entropi penuh memiliki 2<sup>128</sup> kemungkinan kombinasi kunci. Dengan demikian, kunci dengan entropi tinggi dianggap lebih kuat karena memerlukan waktu dan sumber daya komputasi yang jauh lebih besar untuk dipecahkan menggunakan serangan brute force.

Unicity distance merupakan ukuran teoretis yang digunakan untuk menentukan berapa banyak ciphertext yang diperlukan untuk secara unik menentukan kunci yang digunakan. Nilai ini tergantung pada panjang kunci dan redundansi dari plaintext yang dienkripsi. Jika jumlah ciphertext yang tersedia melebihi unicity distance, maka secara teori penyerang dapat menemukan satu-satunya kunci yang benar dengan analisis kriptografi yang tepat. Oleh karena itu, semakin besar unicity distance, semakin sulit pula menemukan kunci melalui analisis statistik.

Dalam evaluasi kekuatan kunci, kombinasi antara entropi tinggi dan unicity distance yang besar menunjukkan sistem kriptografi yang kuat terhadap serangan brute force maupun analisis ciphertext. Brute force attack sendiri melibatkan percobaan semua kemungkinan kunci hingga menemukan yang sesuai, dan kompleksitas serangan ini meningkat secara eksponensial dengan panjang kunci. Oleh sebab itu, pemilihan ukuran kunci yang cukup besar dan sistem pengelolaan kunci yang aman sangat penting untuk menjaga integritas dan keamanan data dalam sistem kriptografi modern.

---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file `perhitungan-entropy.py` di folder `praktikum/week4-entropy-unicity/src/`.
2. Membuat file `menghitung-unicity distance.py` di folder `praktikum/week4-entropy-unicity/src/`.
3. Membuat file `analisis-brute force.py` di folder `praktikum/week4-entropy-unicity/src/`.
4. Menyalin kode program dari panduan praktikum.
5. Menjalankan program dengan perintah sesuai nama file

---

## 5. Source Code
a. Langkah 1 --Perhitungan Entropy

    import math

    def entropy(keyspace_size):
    return math.log2(keyspace_size)

    print("Entropy ruang kunci 26 =", entropy(26), "bit")
    print("Entropy ruang kunci 2^128 =", entropy(2**128), "bit")

Hasilnya:

    Entropy ruang kunci 26 = 4.700439718141092 bit
    Entropy ruang kunci 2^128 = 128.0 bit

b. Langkah 2 --Menghitung Unicity Distance

    import math
    def entropy(key_space):
    return math.log2(key_space)

    def unicity_distance(HK, R=0.75, A=26):
    return HK / (R * math.log2(A))

    HK = entropy(26)
    print("Unicity Distance untuk Caesar Cipher =", unicity_distance(HK))

Hasilnya:

    Unicity Distance untuk Caesar Cipher = 1.3333333333333333

c. Langkah 3 --Analisis Brute Force

    def brute_force_time(keyspace_size, attempts_per_second=1e6):
    seconds = keyspace_size / attempts_per_second
    days = seconds / (3600*24)
    return days

    print("Waktu brute force Caesar Cipher (26 kunci) =", brute_force_time(26), "hari")
    print("Waktu brute force AES-128 =", brute_force_time(2**128), "hari")

Hasilnya:

    Waktu brute force Caesar Cipher (26 kunci) = 3.0092592592592593e-10 hari
    Waktu brute force AES-128 = 3.938453320844195e+27 hari

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program perhitungan entropy:

<img width="1366" height="768" alt="langkah1-perhitungan entropy" src="https://github.com/user-attachments/assets/a44c3313-ab99-4394-aaef-74ffab09b491" />

Hasil eksekusi program unicity distance:

<img width="1366" height="768" alt="langkah2-unicity distance" src="https://github.com/user-attachments/assets/b1f16cbe-8439-4b64-9d13-5209c1c1a9c3" />

Hasil eksekusi program brute force:

<img width="1366" height="768" alt="langkah3-analisis brute force" src="https://github.com/user-attachments/assets/4016e46c-b238-4e57-b4d9-b4452312f495" />

Pembahasan: 

Dari hasil percobaan, dapat dilihat bahwa entropi menentukan seberapa besar ruang kemungkinan kunci yang tersedia. Caesar Cipher hanya memiliki entropi sekitar 4,7 bit, sedangkan AES-128 memiliki entropi 128 bit, menunjukkan perbedaan kekuatan kunci yang sangat besar.

Nilai unicity distance Caesar Cipher sebesar 1,33 menunjukkan bahwa hanya dengan sedikit ciphertext, kunci sudah dapat ditemukan secara unik. Ini menandakan cipher tersebut sangat lemah terhadap analisis kriptografi.

Hasil analisis brute force juga memperkuat bahwa Caesar Cipher bisa dipecahkan dalam waktu sangat singkat, sedangkan AES-128 membutuhkan waktu lebih lama dari usia alam semesta. Dengan demikian, dapat disimpulkan bahwa semakin besar entropi dan unicity distance, semakin kuat sistem kriptografi terhadap serangan brute force maupun analisis ciphertext.

---

## 7. Jawaban Pertanyaan
1. Apa arti dari nilai entropy dalam konteks kekuatan kunci?

   Jawaban:

   Entropy menunjukan tingkat keacakan dalam kunci. Semakin tinggi nilai entropi, semakin besar jumlah kemungkinan kunci yang harus ditebak, sehingga              sistem menjadi lebih sulit ditembus oleh penyerang.
   
2. Mengapa unicity distance penting dalam menentukan keamanan suatu cipher?

   Jawaban:

   Unicity distance penting karena menentukan jumlah ciphertext minimum yang diperlukan untuk menemukan kunci secara unik. Semakin besar nilainya, semakin         sulit cipher dipecahkan, dan jika nilai ini kecil, maka cipher lebih mudah dipecahkan melalui analisis statistik terhadap ciphertext.
   
3. Mengapa brute force masih menjadi ancaman meskipun algoritma sudah kuat?

   Jawaban:

   Brute Force masih menjadi ancaman karena kemajuan teknologi komputer terus meningkatkan kemampuan pemrosesan. Dengan kecepatan tinggi dan penggunaan sistem terdistribusi, penyerang tetap bisa mencoba jutaan kunci per detik meskipun algoritmanya tergolong kuat. 

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
commit week4-entropy-unicity

Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>

Date:   2025-10-25

    week4-entropy-unicity: Entropy & Unicity Distance (Evaluasi Kekuatan Kunci dan Brute Force) 

```
