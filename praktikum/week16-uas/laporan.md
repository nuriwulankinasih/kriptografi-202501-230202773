# Laporan Praktikum Kriptografi
Minggu ke-: 16

Topik: UAS KRIPTOGRAFI EDUTOKEN

Nama: Nuri Wulan Kinasih

NIM: 230202773   

Kelas: 5IKRB  

---

## 1. Tujuan
Projek EduToken dikembangkan dengan beberapa tujuan utama, yaitu:
1.	Mengimplementasikan konsep kriptografi dalam aplikasi pembelajaran berbasis web berbasis blockchain untuk memberikan pemahaman praktis kepada pengguna.
2.	Mengembangkan platform pembelajaran interaktif yang mengintegrasikan materi kriptografi, kuis, dan sistem reward token digital.
3.	Menerapkan teknologi blockchain Ethereum melalui smart contract ERC-20 serta penggunaan MetaMask pada jaringan Sepolia Testnet.
4.	Mendemonstrasikan penerapan protokol keamanan, termasuk hashing, autentikasi, integritas data, dan transaksi token digital.

---

## 2. Dasar Teori
Blockchain merupakan teknologi buku besar terdisentralisasi (distributed ledger) yang memungkinkan pencatatan transaksi secara transparan, aman, dan tidak dapat diubah. Setiap transaksi yang terjadi akan diverifikasi oleh jaringan dan disimpan dalam blok yang saling terhubung menggunakan teknik kriptografi. Karakteristik utama blockchain seperti transparansi, imutabilitas, dan desentralisasi menjadikannya sangat cocok digunakan dalam sistem yang membutuhkan kepercayaan tinggi, termasuk di bidang pendidikan. Dalam konteks pembelajaran, blockchain dapat digunakan untuk mencatat aktivitas, pencapaian, serta pemberian reward secara adil dan tidak dapat dimanipulasi.

Kriptografi merupakan fondasi utama dalam sistem blockchain yang berfungsi untuk menjaga keamanan, integritas, dan keaslian data. Beberapa konsep penting dalam kriptografi meliputi enkripsi untuk menjaga kerahasiaan data, hashing untuk menjamin integritas informasi, dan tanda tangan digital (digital signature) untuk memastikan keaslian pengirim. Dalam blockchain Ethereum, kriptografi digunakan untuk mengamankan transaksi, memverifikasi identitas pengguna, serta melindungi aset digital seperti token. Pemahaman terhadap kriptografi menjadi sangat penting bagi mahasiswa teknologi informasi agar mampu memahami cara kerja sistem keamanan digital modern.

Smart contract dan token digital merupakan implementasi nyata dari kriptografi dalam teknologi blockchain. Smart contract adalah program yang berjalan di blockchain dan mengeksekusi aturan secara otomatis tanpa perantara, sedangkan token ERC-20 adalah standar aset digital yang dapat ditransfer antar pengguna. Dengan menggunakan jaringan uji seperti Sepolia Testnet, pengembang dan pengguna dapat melakukan simulasi transaksi tanpa menggunakan uang asli. Dalam platform EduToken, smart contract digunakan untuk mengelola pemberian reward berupa token EDU kepada mahasiswa, sehingga mereka dapat belajar konsep kriptografi dan blockchain secara langsung melalui pengalaman praktik.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code
- Git dan akun GitHub  
- Visual Studio Code
- Remix IDE
- Akun Metamask
- Onrender
- Fron End menggunakan HTML, CSS, JavaScript
- Smart contract menggunakan solidity
- Network menggunakan Ethereum Sepolia
---

## 4. Langkah Percobaan
### Halaman Login Website EduToken
<img width="1920" height="1080" alt="halaman login" src="https://github.com/user-attachments/assets/07f8392a-5428-4e99-990d-1234908a2b69" />
Ini adalah tampilan halaman login pada website EduToken pada link https://edutoken-crypto.onrender.com 

### Tampilan Menu Dashboard Webiste EduToken
<img width="1920" height="1080" alt="Dashboard EduToken" src="https://github.com/user-attachments/assets/5c9fcb84-cb70-4c73-8c6a-77fe21d86724" />
Setelah berhasil login, selanjutnya akan masuk pada tampilan dashboard website EduToken.

### Tampilan Menu Materi dan Kuis
<img width="1920" height="1080" alt="Tampilan Materi Kuiz" src="https://github.com/user-attachments/assets/4975d06a-408b-464c-a067-6283babf74d2" />
Setelah masuk ke dashboard pilih menu materi dan kuis dan coba mengerjakan kuis dengan memilih mulai kuis 1, Kuiz 2 dan 3 bisa dibuka ketika jumlah token mencukupi.

### Tampilan Kuiz
<img width="1920" height="1080" alt="Tampilan Kuiz" src="https://github.com/user-attachments/assets/12c5831d-c29d-475c-9c0c-8b04940520c8" />
Setelah memilih mulai kuis terdapat 5 pertanyaan dengan durasi waktu 20 detik pengerjaan untuk masing-masing soal, setelah 20 detik soal akan otomatis lanjut ke soal berikutnya.

### Tampilan Klaim Token
<img width="1920" height="1080" alt="Tampilan Klaim Token" src="https://github.com/user-attachments/assets/1d81f36d-96e1-4c5d-bbdd-b47601b7b828" />
Setelah mengerjakan Kuiz, selanjutnya akan mendapatkan Token sebesar 1 benar (2 token), masing-masing pengguna harus menautkan akun metamask terlebih dahulu menggunakan smart contract EduToken. 

### Tampilan Konfirmasi Klaim Token Pada Metamask
<img width="1920" height="1080" alt="klaim ke metamask" src="https://github.com/user-attachments/assets/bb4cc5d3-c728-4280-9a2c-5fb9e10fad9c" />
Setelah klaim token, selanjutnya muncul pop up pada metamask dan klik "konfirmasikan" supaya token dapat diklaim

### Tampilan Notifikasi Berhasil Klaim Token
<img width="1920" height="1080" alt="tampilan berhasil klaim token" src="https://github.com/user-attachments/assets/71e11180-78c2-412a-8722-49737980bd58" />
Seteleh dikonfirmasi EduToken akan memberikan notifikasi bahwa token berhasil diklaim dan klik oke

### Tampilan Menu Info Token dan Transfer
<img width="1920" height="1080" alt="Tampilan Info Token" src="https://github.com/user-attachments/assets/8c2624e8-f0cb-4462-b494-f3d9bee6cb80" />
Pada menu ini terdapat informasi jumlah token dan menu transfer, Jika ingin melakukan transfer masukan alamat wallet teman dan masukan jumlah token yang akan di transfer lalu klik kirim token.

### Konfirmasi Metamask (coba transfer)
<img width="1920" height="1080" alt="transfer (konfir metamask)" src="https://github.com/user-attachments/assets/2076dc22-1328-48ac-a1a4-df909e06febb" />
Setelah memilih kirim token akan muncul pop up metamask untuk persetujuan dan klik "konfirmasikan" supaya transfer token berhasil dilakukan.

### Notifikasi Berhasil Transfer
<img width="1920" height="1080" alt="berhasil transfer" src="https://github.com/user-attachments/assets/60a7a34a-b557-419c-a45d-43a6f144aa60" />
Setelah melakukan konfirmasi EduToken akan memberikan notifikasi bahwa token berhasil di kirim.

### Tampilan Menu Profil
<img width="1920" height="1080" alt="Halaman Menu Profil" src="https://github.com/user-attachments/assets/014ba285-b961-49bb-aa4b-cde5c5b30ef5" />
Pada menu profil terdapat informasi tentang username pengguna, jumlah token dan riwayat aktivitas belajar.

---

## 5. Source Code
---

## 6. Hasil dan Pembahasan
Sistem EduToken berhasil diimplementasikan sebagai platform pembelajaran kriptografi berbasis web yang terintegrasi dengan blockchain Ethereum pada jaringan Sepolia Testnet. Seluruh fitur utama seperti login pengguna, koneksi MetaMask, pengerjaan kuis, klaim token, dan transfer token EDU berjalan sesuai dengan rancangan. Smart contract ERC-20 yang digunakan mampu mengelola saldo token, mendistribusikan reward, serta mencatat setiap transaksi secara transparan di blockchain.

Dari sisi keamanan, EduToken telah menerapkan konsep kriptografi secara nyata melalui penggunaan public–private key, fungsi hash, dan digital signature. Setiap transaksi klaim dan transfer token harus ditandatangani melalui MetaMask menggunakan private key pengguna, sehingga hanya pemilik sah yang dapat melakukan transaksi. Hash transaksi (TX Hash) yang dihasilkan juga menjamin integritas dan transparansi karena dapat diverifikasi langsung di jaringan blockchain.

Mekanisme reward berbasis token terbukti memberikan pengalaman belajar yang lebih interaktif. Pengguna tidak hanya mempelajari kriptografi secara teori, tetapi juga memahami praktik penggunaan blockchain, token, dan smart contract. Dengan adanya sistem kuis dan reward EDU, EduToken mampu meningkatkan keterlibatan dan motivasi belajar sekaligus menjadi media praktikum kriptografi berbasis Web3.

---

## 7. Jawaban Pertanyaan
---

## 8. Kesimpulan
Berdasarkan proses perancangan, pengembangan, dan pengujian, sistem EduToken berhasil diwujudkan sebagai platform pembelajaran berbasis blockchain Ethereum menggunakan token ERC-20. Sistem ini mampu mengintegrasikan pembelajaran kriptografi dengan mekanisme reward digital melalui jaringan Sepolia Testnet.

Penerapan kriptografi asimetris, hashing Keccak-256, dan tanda tangan digital ECDSA melalui MetaMask terbukti mampu menjaga keamanan, autentikasi, dan integritas setiap transaksi token EDU. Selain itu, penggunaan token sebagai insentif memberikan pendekatan pembelajaran yang lebih aplikatif dan menarik.

Dengan memanfaatkan sifat blockchain yang transparan dan immutable, seluruh aktivitas dan distribusi token dapat tercatat secara akurat serta aman, sehingga EduToken berhasil menjembatani konsep kriptografi teoritis dengan implementasi teknologi Web3 secara nyata.

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week16-UAS KRIPTOGRAFI EDUTOKEN
Author: Nama Mahasiswa <email>
Date:   2026-01-26

    week16-uas EDUTOKEN : UAS KRIPTOGRAFI EDUTOKEN
```
