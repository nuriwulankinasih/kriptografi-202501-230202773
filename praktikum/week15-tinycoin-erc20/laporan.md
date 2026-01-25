# Laporan Praktikum Kriptografi
Minggu ke-: 15
Topik: Proyek Kelompok – TinyCoin ERC20

Nama: Nuri Wulan Kinasih   
NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Mengembangkan proyek sederhana berbasis algoritma kriptografi.
2. Mendokumentasikan proses implementasi proyek ke dalam repository Git.
3. Menyusun laporan teknis hasil proyek akhir.

---

## 2. Dasar Teori
TinyCoin (atau yang sering dikaitkan dengan simbol TINC) dalam ekosistem ERC-20 merujuk pada aset digital yang dibangun di atas blockchain Ethereum menggunakan standar teknis yang seragam. Sebagai token ERC-20, TinyCoin mengikuti sekumpulan aturan yang memungkinkan interaksi mulus dengan dompet digital, bursa kripto, dan aplikasi terdesentralisasi (dApps) lainnya di jaringan Ethereum. Standar ini memastikan bahwa setiap unit TinyCoin bersifat fungible, artinya satu token memiliki nilai yang identik dengan token lainnya, mirip dengan bagaimana mata uang konvensional bekerja dalam transaksi digital.

Secara fungsional, TinyCoin memanfaatkan infrastruktur Smart Contract untuk mengelola operasionalnya, mulai dari total pasokan hingga mekanisme transfer antar pengguna. Keunggulan utama dari penggunaan standar ERC-20 adalah keamanan yang diwariskan dari jaringan Ethereum yang sangat kuat serta kemudahan akses bagi para investor melalui platform populer seperti MetaMask atau Uniswap. Proyek ini sering kali ditujukan untuk ekosistem spesifik, seperti ekonomi dalam game berbasis blockchain atau sebagai aset utilitas dalam platform decentralized finance (DeFi) skala kecil yang mengutamakan efisiensi biaya gas.

Memasuki tahun 2026, eksistensi proyek-proyek seperti TinyCoin sangat bergantung pada kegunaan nyata (utility) dan kemampuan adaptasi terhadap teknologi Layer-2 seperti Polygon atau Arbitrum untuk menekan biaya transaksi. Meskipun memiliki potensi pertumbuhan yang menarik karena kapitalisasi pasarnya yang cenderung kecil, token jenis ini juga membawa risiko volatilitas yang tinggi dibandingkan aset kripto utama. Oleh karena itu, bagi pengguna yang ingin terlibat, pemahaman tentang kontrak pintar dan transparansi tim pengembang menjadi kunci utama dalam mengevaluasi keberlanjutan TinyCoin dalam ekosistem Web3 yang semakin kompetitif.

---

## 3. Alat dan Bahan
- Remix IDE  
- Git dan akun GitHub  
- Google Chrome
- Metamask

---

## 4. Langkah Percobaan
1. Membuat file `TinyCoin.sol` di folder `contracs` pada Remix.IDE
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan klik menu compile.
4. Melakukan Deploy & run transactions
5. Melakukan transfer pada kolom TRANSFER dibawah Deployed Contracts dengan memasukan alamat account wallet lain lalu transact.
6. Mengecek jumlah token TNC pada kolom BalanceOF dengan memasukan alamat account.

---

## 5. Source Code
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.0;
    
    contract TinyCoin {
    
        // =========================
        // Informasi Token
        // =========================
        string public name = "TinyCoin";
        string public symbol = "TNC";
        uint8 public decimals = 18;
        uint256 public totalSupply;
    
        // =========================
        // Penyimpanan Saldo
        // =========================
        mapping(address => uint256) public balanceOf;
    
        // =========================
        // Event (standar ERC20)
        // =========================
        event Transfer(address indexed from, address indexed to, uint256 value);
    
        // =========================
        // Constructor
        // =========================
        constructor(uint256 initialSupply) {
            totalSupply = initialSupply * 10 ** uint256(decimals);
            balanceOf[msg.sender] = totalSupply;
        }
    
        // =========================
        // Fungsi Transfer
        // =========================
        function transfer(address to, uint256 amount) public returns (bool) {
            require(balanceOf[msg.sender] >= amount, "Saldo tidak cukup");
            require(to != address(0), "Alamat tidak valid");
    
            balanceOf[msg.sender] -= amount;
            balanceOf[to] += amount;
    
            emit Transfer(msg.sender, to, amount);
            return true;
        }
    }

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program tinycoin.sol di REMIX.IDE :
<img width="1920" height="1080" alt="hasil tinycoin2" src="https://github.com/user-attachments/assets/8da04fa3-4f3a-4b4e-be9d-6cdffb1582f9" />
Hasil pada Remix menunjukkan bahwa smart contract TinyCoin telah berhasil di-deploy ke jaringan Sepolia Testnet melalui MetaMask, ditandai dengan transaksi constructor yang sukses dan munculnya alamat kontrak pada bagian Deployed Contracts; ini berarti seluruh total supply token TNC sudah dibuat dan otomatis masuk ke wallet MetaMask yang kamu gunakan saat deploy, sehingga kontrak siap dipakai untuk melakukan transfer token ke alamat wallet lain di jaringan Sepolia.

Hasil Deploy dan Transfer Smart Contract TinyCoin di Remix:
<img width="1920" height="1080" alt="hasil tinycoin2" src="https://github.com/user-attachments/assets/43026ad3-31c6-4580-b22a-6dc43bb3ec48" />
Tampilan tersebut menunjukkan bahwa fungsi transfer(address to, uint256 amount) pada smart contract TinyCoin sudah berhasil dikompilasi dan kontrak telah di-deploy di jaringan Sepolia Testnet, sehingga wallet MetaMask yang melakukan deploy kini memiliki seluruh saldo awal TNC dan siap menggunakan fungsi transfer di Remix untuk mengirim token ke alamat wallet lain dengan memasukkan alamat tujuan dan jumlah token (dalam satuan 10¹⁸).

Hasil Transfer akun 1 ke akun 2: 
<img width="959" height="539" alt="hasil tinycoin3" src="https://github.com/user-attachments/assets/258c36ac-61ea-4009-be14-04f99cc116d8" />
Hasil ini menunjukan transfer ke akun 2 (culan) berhasil, pada kolom TRANSFER masukan alamat walet akun 2 (culan) dan masukan jumlah yg ingin di transfer 1 TNC (1000000000000000000), dan pada metamask terlihat akun 2 sudah bertambah menjadi 2 (karena saya sudah transfer 1 sebelumnya).

Hasil cek token TNC pada remix:
<img width="967" height="539" alt="hasil tinycoin4" src="https://github.com/user-attachments/assets/4f6db82b-c815-4736-9d43-3a07fc26d820" />
Gambar ini menjukkan hasil cek token TNC akun 1 (nuri wulan) pada remix, dengan masukan alamat wallet akun 1 pada kolom BalanceOF dan setelah itu dibawahnya akan muncul keterangan jumlahnya yang sesuai dengan yang ada pada metamask.

Hasil transfer balik akun 2 ke akun 1:
<img width="959" height="539" alt="tinycoin transfer balik" src="https://github.com/user-attachments/assets/31c6621d-b7dc-4a81-a4af-0c764baf13b6" />
Pada gambar ini terlihat pengurangan token pada akun 2 karena sudah di transfer balik ke akun 1 sebesar 1 tinycoin. 

---

## 7. Jawaban Pertanyaan
1. Apa fungsi utama ERC20 dalam ekosistem blockchain?
2. Bagaimana mekanisme transfer token bekerja dalam kontrak ERC20?
3. Apa risiko utama dalam implementasi smart contract dan bagaimana cara mitigasinya?

Jawaban:
1. ERC20 berfungsi sebagai standar teknis untuk pembuatan dan pengelolaan token di blockchain Ethereum. Standar ini memastikan bahwa semua token memiliki fungsi dasar yang sama seperti transfer, balanceOf, dan approve, sehingga token dapat dengan mudah digunakan, ditukar, dan diintegrasikan ke berbagai aplikasi seperti wallet (MetaMask), exchange, dan aplikasi terdesentralisasi (dApp). Dengan adanya ERC20, interoperabilitas antar token dan platform menjadi lebih mudah dan konsisten.
   
2. Mekanisme transfer token dalam ERC20 bekerja dengan cara mengurangi saldo pengirim dan menambah saldo penerima di dalam smart contract. Ketika fungsi transfer(address to, uint256 amount) dipanggil, kontrak akan terlebih dahulu memeriksa apakah saldo pengirim mencukupi, kemudian memotong saldo tersebut dan menambahkannya ke alamat tujuan. Setelah itu, kontrak akan mencatat transaksi melalui event Transfer, sehingga aktivitas perpindahan token dapat dilacak di blockchain.

3. Risiko utama dalam smart contract meliputi bug pada kode, celah keamanan (seperti reentrancy), dan kesalahan logika, yang dapat menyebabkan kehilangan aset digital. Mitigasi risiko dilakukan dengan cara melakukan audit kode, menggunakan library standar yang telah teruji (seperti OpenZeppelin), melakukan pengujian menyeluruh di testnet, dan menerapkan mekanisme keamanan seperti require dan pembatasan akses. Dengan langkah-langkah ini, keamanan dan keandalan smart contract dapat lebih terjamin.
---

## 8. Kesimpulan
Berdasarkan hasil praktikum, proyek TinyCoin berbasis standar ERC-20 berhasil diimplementasikan dan diuji pada jaringan Sepolia Testnet menggunakan Remix dan MetaMask, mulai dari proses deploy smart contract hingga pengujian transfer token antar akun, yang membuktikan bahwa mekanisme pembuatan, penyimpanan saldo, dan pengiriman token berjalan sesuai dengan spesifikasi ERC-20; melalui kegiatan ini, mahasiswa tidak hanya memahami konsep kriptografi dan smart contract secara teoretis, tetapi juga memperoleh pengalaman praktis dalam membangun, memverifikasi, dan mengelola aset digital secara aman di lingkungan blockchain.

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week15-tinycoin-erc20
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2026-01-25

    week15-tinycoin-erc20: TinyCoin ERC20
```
