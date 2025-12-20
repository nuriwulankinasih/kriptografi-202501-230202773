# Laporan Praktikum Kriptografi
Minggu ke-: 10  
Topik: Public Key Infrastructure (PKI & Certificate Authority)

Nama: Nuri Wulan Kinasih
NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Membuat sertifikat digital sederhana.
2. Menjelaskan peran Certificate Authority (CA) dalam sistem PKI.
3. Mengevaluasi fungsi PKI dalam komunikasi aman (contoh: HTTPS, TLS).
---

## 2. Dasar Teori
Public Key Infrastructure (PKI) adalah sistem yang digunakan untuk mengatur dan mengamankan penggunaan kunci publik dalam komunikasi digital. PKI membantu memastikan bahwa proses enkripsi, tanda tangan digital, dan pertukaran data dapat dilakukan dengan aman. Dengan adanya PKI, pengguna tidak hanya menggunakan kunci publik secara sembarangan, tetapi juga dapat memastikan bahwa kunci tersebut benar-benar milik pihak yang tepat, sehingga komunikasi menjadi lebih terpercaya.

Salah satu bagian terpenting dalam PKI adalah Certificate Authority (CA). CA berperan sebagai pihak yang dipercaya untuk menerbitkan sertifikat digital. Sertifikat digital ini berisi identitas pemilik dan kunci publiknya, yang telah diverifikasi dan ditandatangani oleh CA. Karena adanya tanda tangan dari CA, pengguna lain dapat yakin bahwa kunci publik tersebut asli dan tidak dipalsukan.

Selain CA, PKI juga memiliki komponen pendukung lainnya seperti Registration Authority (RA) dan mekanisme pencabutan sertifikat. RA bertugas mengecek identitas pemohon sebelum sertifikat diterbitkan, sedangkan pencabutan sertifikat digunakan jika kunci sudah tidak aman atau tidak berlaku lagi. Dengan sistem ini, PKI mampu menjaga keamanan dan kepercayaan dalam berbagai layanan digital seperti website aman (HTTPS), email, dan transaksi online.

---

## 3. Alat dan Bahan
- Python 3.x  
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
### Langkah 1 — Membuat Sertifikat Digital Sederhana

    from cryptography import x509
    from cryptography.x509.oid import NameOID
    from cryptography.hazmat.primitives import hashes, serialization
    from cryptography.hazmat.primitives.asymmetric import rsa
    from datetime import datetime, timedelta

    # Generate key pair
    key = rsa.generate_private_key(public_exponent=65537, key_size=2048)
    
    # Buat subject & issuer (CA sederhana = self-signed)
    subject = issuer = x509.Name([
        x509.NameAttribute(NameOID.COUNTRY_NAME, u"ID"),
        x509.NameAttribute(NameOID.ORGANIZATION_NAME, u"UPB Kriptografi"),
        x509.NameAttribute(NameOID.COMMON_NAME, u"example.com"),
    ])
    
    # Buat sertifikat
    cert = (
        x509.CertificateBuilder()
        .subject_name(subject)
        .issuer_name(issuer)
        .public_key(key.public_key())
        .serial_number(x509.random_serial_number())
        .not_valid_before(datetime.utcnow())
        .not_valid_after(datetime.utcnow() + timedelta(days=365))
        .sign(key, hashes.SHA256())
    )

    # Simpan sertifikat
    with open("cert.pem", "wb") as f:
        f.write(cert.public_bytes(serialization.Encoding.PEM))

    print("Sertifikat digital berhasil dibuat: cert.pem")



Hasilnya : Menghasilkan "cert.pem" yang berisi code
                -----BEGIN CERTIFICATE-----
    MIIDBjCCAe6gAwIBAgIUKYEIA5JvCumc9dyBiE1ucQbOwcUwDQYJKoZIhvcNAQEL
    BQAwPTELMAkGA1UEBhMCSUQxGDAWBgNVBAoMD1VQQiBLcmlwdG9ncmFmaTEUMBIG
    A1UEAwwLZXhhbXBsZS5jb20wHhcNMjUxMjEzMTUwNTIxWhcNMjYxMjEzMTUwNTIx
    WjA9MQswCQYDVQQGEwJJRDEYMBYGA1UECgwPVVBCIEtyaXB0b2dyYWZpMRQwEgYD
    VQQDDAtleGFtcGxlLmNvbTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEB
    AL9aaV3B5csHWZfsHCInnmCqaZDCCebO+q0sBaY8mcHQv4I5eSJJkrtOZgMouJ6d
    k7UW2OcEdZ14DudOmit25UcpBAwsPUQi0cWEf7rklxk9Y4w6/nWmnecPklVcdwoB
    MMJPusUHiAaO0AE2ZKK6EFqEoFXtrjNH23zx9t/DMyvemMuVadZo+h1eZHeYhZX4
    WrwsnvNP8zEpNQFWjZyfx+NGYGq0gS5eTWsx2g/esDXBOwcWgPNhM8pUQSrF0Rfy
    5yfRx6guEQ1bbKHQmpYH2HemZ3dHJiZHIsD5nWW0sSAkMSDlxkrMOFdVLnsPp15C
    U6uNWTa5fQcwE8enndaqvaECAwEAATANBgkqhkiG9w0BAQsFAAOCAQEAZNA9fKI7
    sUwZ3dnSQHMhb+G1k5YEPQpMjjYui0pYfYnCNQTl20vf38RihQuVfElAuJJ3JFjK
    tNW180Dm25bM+yKcTzT5isrF9KqFS/m84mnQ2/nEzIf2GarjfCz3FVyti1hVeqK3
    s8KiQiosFipNTmgPwYur0qPwjMW6VXzNIk/9RqBiyNMO4RKbZnM6YH96Cl0lDJGL
    Fy0rcOizYd7QTGfP0A/oBCoJGFTLtc0fRNVgjUZv1ctxCEBCVCwtBd/ucjTMgEZD
    DSsmwFOynyA2Y+eaPG2H4UJqFCEI84t7h5362hbBh21Bl0dsi2KaMo/kJULXl+WA
    YHv7c5cO/jMCpw==
    -----END CERTIFICATE-----


---

## 6. Hasil dan Pembahasan
<img width="1920" height="1080" alt="cert pem" src="https://github.com/user-attachments/assets/7285bfa9-61ed-4f5e-b6db-1721926966a0" />

<img width="1920" height="1080" alt="verifikasi sertifikat" src="https://github.com/user-attachments/assets/c3093a77-b880-468c-8171-b4a78c1b6ce4" />


---

## 7. Jawaban Pertanyaan
1. Apa fungsi utama Certificate Authority (CA)?
2. Mengapa self-signed certificate tidak cukup untuk sistem produksi?
3. Bagaimana PKI mencegah serangan MITM dalam komunikasi TLS/HTTPS?

Jawaban: 

1. Certificate Authority (CA) berfungsi sebagai pihak terpercaya yang menerbitkan dan memvalidasi sertifikat digital untuk mengikat identitas suatu entitas (seperti website, organisasi, atau individu) dengan kunci publiknya. CA melakukan proses verifikasi identitas sebelum menerbitkan sertifikat, sehingga pengguna dapat yakin bahwa kunci publik yang diterima benar-benar milik pihak yang sah. Dengan adanya CA, komunikasi digital dapat berlangsung secara aman karena keaslian identitas pihak yang berkomunikasi dapat dipercaya.
   
2. Self-signed certificate tidak cukup untuk sistem produksi karena sertifikat tersebut ditandatangani oleh pemiliknya sendiri tanpa verifikasi dari pihak tepercaya. Akibatnya, klien atau browser tidak memiliki cara untuk memastikan keaslian identitas server, sehingga rawan terhadap serangan pemalsuan identitas. Selain itu, self-signed certificate biasanya akan memunculkan peringatan keamanan pada browser, menurunkan tingkat kepercayaan pengguna, dan tidak cocok untuk lingkungan produksi yang membutuhkan jaminan keamanan dan kepercayaan tinggi.

3. Public Key Infrastructure (PKI) mencegah serangan Man-in-the-Middle (MITM) dengan memastikan bahwa kunci publik server yang digunakan dalam komunikasi TLS/HTTPS telah diverifikasi oleh CA tepercaya. Ketika klien mengakses sebuah website, browser akan memeriksa sertifikat digital server, termasuk tanda tangan CA dan kecocokan nama domain. Jika sertifikat valid, klien yakin bahwa kunci publik tersebut milik server yang benar, sehingga penyerang tidak dapat menggantikan kunci publik tanpa terdeteksi. Dengan demikian, proses pertukaran kunci dan enkripsi komunikasi menjadi aman dari penyadapan dan pemalsuan.

---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week10-pki
Author: Nuri Wulan kinasih <kinasihnuri60@gmail.com>
Date:   2025-12-19

    week10-pki: Public Key Infrastructure (PKI & Certificate Authority)
```
