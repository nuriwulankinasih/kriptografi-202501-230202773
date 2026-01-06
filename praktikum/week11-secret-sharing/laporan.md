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

1. Membuat file `shamir-secret-sharing.py` di folder `praktikum/week11-secret-sharing/src/`.
2. Menyalin lalu memodif kode program dari panduan praktikum.
3. Menjalankan program dengan perintah sesuai file
4. Membuat file `simulasi-manual.py` di folder `praktikum/week11-secret-sharing/src/`.
5. Memodif program
6. Menjalankan program
7. Membuat folder screenshot di folder praktikum/week11-secret_sharing/src/.
8. Menempel hasil eksekusi program ke folder screenshot.

---

## 5. Source Code
### Langkah 1 Implementasi Shamir Secret Sharing

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

### Langkah 2 Simulasi Manual (Tanpa Library)

    import random
    
    # Parameter
    p = 2089            # bilangan prima (harus > secret)
    secret = 1234       # rahasia (a0)
    k = 3               # threshold
    n = 5               # jumlah share
    
    # Bangun polinomial f(x) = a0 + a1*x + a2*x^2 mod p
    coefficients = [secret] + [random.randint(1, p-1) for _ in range(k-1)]
    
    def polynomial(x, coeffs, p):
        result = 0
        for i in range(len(coeffs)):
            result = (result + coeffs[i] * pow(x, i)) % p
        return result
    
    # Membuat shares (x, f(x))
    shares = []
    for x in range(1, n+1):
        y = polynomial(x, coefficients, p)
        shares.append((x, y))
    
    print("Shares:")
    for s in shares:
        print(s)
    
    # Lagrange Interpolation untuk rekonstruksi secret
    def lagrange_interpolation(x, shares, p):
        total = 0
        for i, (xi, yi) in enumerate(shares):
            prod = yi
            for j, (xj, _) in enumerate(shares):
                if i != j:
                    prod *= (x - xj) * pow(xi - xj, -1, p)
                    prod %= p
            total += prod
        return total % p
    
    # Rekonstruksi secret menggunakan k shares
    recovered_secret = lagrange_interpolation(0, shares[:k], p)
    print("\nRecovered Secret:", recovered_secret) 

Hasilnya: 
    (1, 1262)
    (2, 1482)
    (3, 1894)
    (4, 409)
    (5, 1205)
    
    Recovered Secret: 1234

### Langkah 3 Diskusi

1. Mengapa skema (k, n) aman meskipun sebagian share bocor?

Berdasarkan hasil Langkah 1 dan Langkah 2, terlihat bahwa setiap share yang dihasilkan berupa pasangan bilangan (x, y) yang tampak acak dan tidak memiliki arti apa pun jika berdiri sendiri. Keamanan skema (k, n) pada Shamir’s Secret Sharing terletak pada penggunaan polinomial berderajat (k−1). Secara matematis, untuk menentukan satu polinomial unik diperlukan minimal k titik. Jika hanya tersedia kurang dari k share, maka terdapat tak hingga kemungkinan polinomial yang dapat dibentuk, sehingga nilai rahasia (konstanta polinomial) tidak dapat ditentukan.

Pada Langkah 1, meskipun satu atau dua share bocor, nilai rahasia "KriptografiUPB2025" tetap tidak dapat direkonstruksi. Hal yang sama juga terlihat pada Langkah 2, di mana rahasia numerik 1234 baru dapat dipulihkan setelah tiga share digunakan. Dengan demikian, kebocoran sebagian share tidak mengurangi keamanan rahasia, selama jumlah share yang bocor masih di bawah nilai threshold k.

2. Apa risiko jika threshold k terlalu kecil atau terlalu besar?

Jika nilai threshold k terlalu kecil, maka tingkat keamanan sistem menjadi rendah. Sebagai contoh, apabila k = 2, maka hanya dua pihak saja yang sudah cukup untuk merekonstruksi rahasia. Kondisi ini meningkatkan risiko penyalahgunaan, karena rahasia dapat dengan mudah diakses jika dua share jatuh ke pihak yang tidak berwenang. Hal ini bertentangan dengan tujuan utama Shamir’s Secret Sharing yang ingin membatasi akses terhadap rahasia secara ketat.

Sebaliknya, jika threshold k terlalu besar, maka risiko operasional meningkat. Jika terlalu banyak pemegang share yang harus dikumpulkan, kemungkinan kehilangan satu atau lebih share menjadi lebih besar. Pada kondisi ini, rahasia bisa tidak dapat dipulihkan sama sekali, meskipun pemilik sah masih ada. Oleh karena itu, pemilihan nilai k harus seimbang antara keamanan dan ketersediaan, sebagaimana ditunjukkan dalam praktik Langkah 1 dan 2 dengan penggunaan k = 3 dari n = 5 yang terbukti efektif.

3. Bagaimana penerapan Shamir’s Secret Sharing di dunia nyata?

Shamir’s Secret Sharing banyak diterapkan dalam sistem keamanan modern. Salah satu contoh utama adalah manajemen kunci cryptocurrency, di mana private key dibagi ke beberapa pihak (misalnya pemilik, notaris, dan penyedia layanan). Private key hanya dapat dipulihkan jika jumlah share yang memenuhi threshold dikumpulkan, sehingga risiko kehilangan atau pencurian kunci dapat diminimalkan.

Selain itu, SSS juga digunakan pada sistem recovery password dan data penting, seperti kunci enkripsi perusahaan atau backup sistem cloud. Dalam kasus ini, tidak ada satu pihak pun yang memegang rahasia secara penuh. Hal ini meningkatkan keamanan organisasi dan mencegah single point of failure. Prinsip yang sama seperti yang ditunjukkan pada hasil Langkah 1 dan Langkah 2 diterapkan secara luas untuk memastikan bahwa data sensitif tetap aman namun tetap dapat dipulihkan saat diperlukan.

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program Shamir secret sharing:
<img width="1920" height="1080" alt="shamir_secretsharing" src="https://github.com/user-attachments/assets/94f28e13-5a82-458f-936d-266f0103a87a" />

Hasil eksekusi program simulasi manual
<img width="1920" height="1080" alt="simulasi manual secret sharing" src="https://github.com/user-attachments/assets/0fb7d408-5bfd-425c-a9e4-2194c8e3d283" />

Pembahasan:
Pada Langkah 1, Shamir’s Secret Sharing diimplementasikan menggunakan bilangan prima sangat besar untuk membagi rahasia berupa string “KriptografiUPB2025” menjadi lima share dengan ambang batas tiga. Setiap share dihasilkan dari evaluasi polinomial dan tidak dapat mengungkap rahasia secara mandiri. Proses rekonstruksi menggunakan tiga share berhasil mengembalikan rahasia asli, menunjukkan bahwa algoritma bekerja dengan benar.

Pada Langkah 2, dilakukan simulasi manual dengan bilangan prima kecil dan rahasia berupa angka. Polinomial dibentuk secara sederhana dan share dihitung secara langsung. Dengan interpolasi Lagrange menggunakan tiga share, rahasia berhasil direkonstruksi kembali. Hasil ini menegaskan bahwa baik implementasi realistis maupun simulasi sederhana mengikuti prinsip yang sama, yaitu rahasia hanya dapat diperoleh jika jumlah share memenuhi ambang batas minimum.

---

## 7. Jawaban Pertanyaan
1. Apa keuntungan utama Shamir Secret Sharing dibanding membagikan salinan kunci secara langsung?
2. Apa peran threshold (k) dalam keamanan secret sharing?
3. Berikan satu contoh skenario nyata di mana SSS sangat bermanfaat.

Jawaban:
1. Keuntungan utama shamir secret sharing adalah meningkatkan keamanan, karena rahasia tidak disimpan atau dibagikan secara utuh. Setiap pihak hanya memegang sebagian (share) yang secara individual tidak memiliki arti apapun. Berbeda dengan membagikan salinan kunci langsung yang berisiko bocor jika satu pihak disusupi, pada SSS rahasia hanya dapat direkontruksi jika jumlah share yang dikumpulkan memenuhi ambang batas tertentu.
   
2. Threshold (k) menentukan jumlah minimum share yang diperlukan untuk merekonstruksi rahasia. Jika jumlah share kurang dari k, rahasia sama sekali tidak dapat diketahui. Semakin besar nilai k, semakin tinggi tingkat keamanan karena dibutuhkan lebih banyak pihak untuk bekerja sama, namun konsekuensinya adalah fleksibilitas sistem menjadi lebih rendah.

3. Shamir’s Secret Sharing sangat bermanfaat dalam manajemen kunci kriptografi pada perusahaan atau lembaga keuangan, misalnya untuk menyimpan kunci utama server. Kunci dibagi ke beberapa administrator, dan hanya jika sejumlah administrator tertentu hadir bersama, kunci dapat digunakan, sehingga mencegah penyalahgunaan oleh satu pihak saja.

---

## 8. Kesimpulan
Berdasarkan praktikum yang telah dilakukan, Shamir’s Secret Sharing terbukti mampu membagi dan merekonstruksi rahasia secara aman menggunakan skema threshold (k, n). Hasil percobaan menunjukkan bahwa rahasia hanya dapat dipulihkan apabila jumlah share yang digunakan memenuhi nilai threshold, sedangkan sebagian share saja tidak memberikan informasi apa pun tentang rahasia. Dengan demikian, metode ini efektif untuk meningkatkan keamanan dan keandalan dalam pengelolaan data sensitif dan kunci kriptografi.

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week11-secret-sharing
Author:  Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-01-06

    week11-secret-sharing: Secret Sharing (Shamir’s Secret Sharing)
```
