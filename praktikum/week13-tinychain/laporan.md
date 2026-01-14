# Laporan Praktikum Kriptografi
Minggu ke-: 13
Topik: TinyChain – Proof of Work (PoW)

Nama: Nuri Wulan Kinasih

NIM: 230202773
Kelas: 5IKRB  

---

## 1. Tujuan
1. Menjelaskan peran hash function dalam blockchain.
2. Melakukan simulasi sederhana Proof of Work (PoW).
3. Menganalisis keamanan cryptocurrency berbasis kriptografi.

---

## 2. Dasar Teori
TinyChain merupakan contoh sederhana dari sistem blockchain yang digunakan untuk mempelajari konsep dasar blockchain, termasuk mekanisme konsensus Proof of Work (PoW). Dalam TinyChain, PoW digunakan untuk menentukan blok mana yang sah untuk ditambahkan ke dalam rantai. Proses ini dilakukan dengan mencari nilai nonce tertentu sehingga hasil fungsi hash dari data blok memenuhi tingkat kesulitan yang ditentukan, misalnya menghasilkan hash dengan awalan nol.

Setiap blok dalam TinyChain berisi data transaksi, hash blok sebelumnya, timestamp, dan nonce. Hash blok sebelumnya berfungsi untuk menghubungkan antarblok sehingga membentuk rantai yang saling bergantung. Jika terdapat perubahan data pada satu blok, maka hash akan berubah dan menyebabkan blok-blok setelahnya menjadi tidak valid. Hal ini menunjukkan bagaimana PoW dan fungsi hash bekerja bersama untuk menjaga integritas dan keamanan data.

Selain menjaga integritas data, Proof of Work pada TinyChain juga berperan dalam mencegah kecurangan seperti double spending. Karena proses penambahan blok memerlukan komputasi yang sulit dan memakan waktu, upaya untuk memanipulasi data atau menambahkan blok palsu menjadi sangat tidak efisien dan sulit dilakukan.

---

## 3. Alat dan Bahan
- Python 3.14
- Visual Studio Code 
- Git dan akun GitHub  
- Google Chrome

---

## 4. Langkah Percobaan
1. Membuat file `tinychain.py` di folder `praktikum/week13-tinychain/src/.`
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python tinychain.py`
4. Mengerjakan laporan.md
5. Membuat file hasil.png di folder praktikum/week13-tinychain/sreenshoot/

---

## 5. Source Code
### Langkah 1 dan 2 - Membuat Blokchain
    import hashlib
    import time
    
    class Block:
        def __init__(self, index, previous_hash, data, timestamp=None):
            self.index = index
            self.timestamp = timestamp or time.time()
            self.data = data
            self.previous_hash = previous_hash
            self.nonce = 0
            self.hash = self.calculate_hash()
    
        def calculate_hash(self):
            value = str(self.index) + str(self.timestamp) + str(self.data) + str(self.previous_hash) + str(self.nonce)
            return hashlib.sha256(value.encode()).hexdigest()
    
        def mine_block(self, difficulty):
            while self.hash[:difficulty] != "0" * difficulty:
                self.nonce += 1
                self.hash = self.calculate_hash()
            print(f"Block mined: {self.hash}")
            
    class Blockchain:
        def __init__(self):
            self.chain = [self.create_genesis_block()]
            self.difficulty = 4
    
        def create_genesis_block(self):
            return Block(0, "0", "Genesis Block")
    
        def get_latest_block(self):
            return self.chain[-1]
    
        def add_block(self, new_block):
            new_block.previous_hash = self.get_latest_block().hash
            new_block.mine_block(self.difficulty)
            self.chain.append(new_block)

Hasilnya:

    Mining block 1...
    Block mined: 00005b5ff03d03317662d2afaf2d297e517ec7a9ed746ec5a6580757145deff5
    Mining block 2...
    Block mined: 0000a5eda092731c49f7e28c278be4d3e8a4922c34493f76b770a2b1f84ef2ce

### Langkah 3 - Analisis Proof of Work
Berdasarkan hasil eksekusi program, terlihat bahwa setiap blok harus melalui proses mining sebelum dapat ditambahkan ke dalam blockchain. Proses mining ini dilakukan dengan mekanisme Proof of Work (PoW), yaitu mencari nilai nonce yang menghasilkan hash dengan awalan sejumlah nol sesuai tingkat difficulty yang ditentukan (pada program ini difficulty = 4).

Hasil output menunjukkan bahwa hash blok yang berhasil ditambang selalu diawali dengan “0000”. Hal ini menandakan bahwa sistem telah melakukan perhitungan hash berulang kali hingga menemukan hash yang memenuhi syarat. Semakin besar nilai difficulty, maka semakin sulit dan lama proses mining karena membutuhkan lebih banyak percobaan.

Dengan PoW, blockchain menjadi lebih aman karena perubahan data pada satu blok akan mengubah hash dan memaksa penambangan ulang seluruh blok berikutnya. Mekanisme ini mencegah manipulasi data dan memastikan integritas blockchain, sebagaimana ditunjukkan pada proses mining blok 1 dan blok 2 pada hasil percobaan.

---

## 6. Hasil dan Pembahasan
Hasil eksekusi program tinychain:
<img width="1920" height="1080" alt="tinychain" src="https://github.com/user-attachments/assets/19ebcf23-6432-497b-9981-ee63293426ab" />

Pembahasan:
Hasil eksekusi menunjukkan bahwa mekanisme Proof of Work (PoW) berjalan dengan baik. Setiap blok berhasil ditambang dengan menghasilkan hash yang diawali empat angka nol sesuai tingkat difficulty = 4, yang diperoleh melalui proses percobaan nilai nonce secara berulang.

Perbedaan hash pada setiap blok membuktikan bahwa setiap blok unik dan saling terhubung melalui previous_hash, sehingga perubahan data pada satu blok akan memengaruhi seluruh rantai. Ini menunjukkan fungsi PoW dalam menjaga keamanan dan integritas blockchain.

---

## 7. Jawaban Pertanyaan
1. Mengapa fungsi hash sangat penting dalam blockchain?
2. Bagaimana Proof of Work mencegah double spending?
3. Apa kelemahan dari PoW dalam hal efisiensi energi?

Jawaban:
1. Fungsi hash sangat penting karena digunakan untuk menjaga keamanan dan integritas data dalam blockchain. Setiap transaksi diubah menjadi nilai hash yang unik. Jika data diubah sedikit saja, nilai hash akan berubah total sehingga manipulasi data dapat langsung terdeteksi. Selain itu, hash juga digunakan untuk menghubungkan antarblok sehingga data bersifat tidak dapat diubah (immutable).
2. Proof of Work mencegah double spending dengan cara mewajibkan penambang melakukan perhitungan matematika yang kompleks sebelum sebuah transaksi dinyatakan valid. Hanya blok yang berhasil menyelesaikan perhitungan tersebut yang dapat ditambahkan ke blockchain. Setelah transaksi tercatat dalam blok yang sah, transaksi tersebut tidak dapat digunakan kembali, sehingga mencegah terjadinya pengeluaran ganda.
3. Kelemahan utama PoW adalah penggunaan energi yang sangat besar karena proses penambangan memerlukan perhitungan komputasi secara terus-menerus. Energi yang digunakan sebagian besar hanya untuk mencari hash yang sesuai, sehingga kurang efisien dan berdampak pada lingkungan. Oleh karena itu, PoW dianggap tidak ramah energi dibandingkan metode konsensus lainnya.

---

## 8. Kesimpulan
Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa mekanisme Proof of Work (PoW) pada TinyChain berhasil menunjukkan cara kerja blockchain dalam menjaga integritas dan keamanan data. Proses mining membuktikan bahwa setiap blok harus memenuhi tingkat kesulitan tertentu sebelum dapat ditambahkan ke dalam rantai, sehingga mencegah manipulasi data. Dengan demikian, fungsi hash dan PoW berperan penting dalam memastikan keandalan dan keamanan sistem blockchain, meskipun memiliki kelemahan dari sisi efisiensi energi.

---

## 9. Daftar Pustaka
---

## 10. Commit Log
```
commit week13-tinychain
Author: Nuri Wulan Kinasih <kinasihnuri60@gmail.com>
Date:   2025-01-12

    week13-tinychain: TinyChain – Proof of Work (PoW)
```
