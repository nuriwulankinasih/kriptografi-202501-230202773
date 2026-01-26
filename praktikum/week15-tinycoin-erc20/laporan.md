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
4. Memasukkan argumen initialSupply sebesar 1000.
5. Melakukan Deploy & run transactions.
6. Pengujian Fungsi: Menguji fungsi balanceOf dan transfer.
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
<img width="1920" height="1080" alt="ERC-20" src="https://github.com/user-attachments/assets/925fd63d-f866-493c-8e63-e337d5008219" />
Hasil pada Remix menunjukkan bahwa smart contract TinyCoin (TNC) telah berhasil dikompilasi dan dideploy ke blockchain, yang dibuktikan dengan munculnya alamat contract 0xD4Fc541236927E2EAf8F27606bD7309C1Fc2cbee pada bagian Deployed Contracts; hal ini menandakan bahwa token ERC-20 telah aktif dan siap digunakan untuk menyimpan serta mengelola saldo token pengguna, menjalankan proses transfer, dan menjadi dasar sistem reward berbasis blockchain seperti pada proyek kuis kriptografi, sehingga setiap transaksi token yang terjadi akan tercatat secara transparan dan aman di jaringan blockchain.

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
Implementasi smart contract TinyCoin (TNC) telah berhasil dilakukan dengan baik, di mana token ERC-20 berhasil dideploy ke blockchain dan dapat berfungsi sebagai media pertukaran dan reward digital dalam sistem yang dibangun, sehingga mendukung penerapan konsep kriptografi dan blockchain secara nyata melalui transaksi yang aman, transparan, dan terdesentralisasi untuk meningkatkan interaksi dan motivasi pengguna dalam aplikasi kuis berbasis token.

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
