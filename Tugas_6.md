
---

<p align="right">
    SURABAYA <br> 06 MEI 2025
</p> <br>

<h1 align="center"><ins>LAPORAN PRAKTIKUM</ins></h1>
<h3 align="center"><em>"Serba Serbi Email"</em></h3>
<h3 align="center">Mata Kuliah Workshop Administrasi Jaringan</h3>

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/PENS.png" width="300" height="300"><br>
</p>

<p align="center">
Nama Dosen Pengampu : <br> 
Bapak Dr Ferry Astika Saputra ST, M.Sc <br>
<br>
Dikerjakan Oleh : <br>
Nanda Ahmad Zidan&emsp;&emsp;&emsp;[3123600013]<br>
</p>

<p align="center">
Tahun Pelajaran 2024/2025 <br>
<strong>POLITEKNIK ELEKTRONIKA NEGERI SURABAYA</strong>
</p>

---
<br>

<h2 align="center">DAFTAR ISI</h2>
<br>

[DAFTAR ISI](#daftar-isi)<br>
A. [TUJUAN PEMBELAJARAN](#a-tujuan-pembelajaran)<br>
B. [SEJARAH](#b-sejarah)<br>
C. [PERTANYAAN](#c-pertanyaan)<br>
D. [RANGKUMAN](#d-rangkuman)<br>
[DAFTAR PUSTAKA](#daftar-pustaka)<br>

<p align="center">i</p>

---

# A. TUJUAN PEMBELAJARAN
1. Menjelaskan jenis-jenis protokol email yang umum digunakan, yaitu:
   - SMTP (Simple Mail Transfer Protocol),
   - POP3 (Post Office Protocol v3),
   - IMAP (Internet Message Access Protocol),
   - POP3S (POP3 Secure).
2. Membandingkan fungsi, cara kerja, dan karakteristik tiap protokol dalam pengiriman dan pengambilan email.
3. Mengidentifikasi cara kerja mail server dalam sebuah domain, termasuk:
   - Fungsi dan cara kerja MX record dalam DNS,
   - Proses pencarian server email menggunakan perintah nslookup atau dig.
4. Menganalisis arsitektur sistem email berdasarkan diagram dari sumber GeeksforGeeks, khususnya peran:
   - User Agent (UA),
   - Mail Transfer Agent (MTA),
   - Mail Box,
   - Spool File.
5. Menjelaskan alur pengiriman dan penerimaan email secara menyeluruh, dari sisi teknis dan logis, berdasarkan komponen dan protokol yang terlibat.

---
# B. SEJARAH
<p align="center"><strong>SEJARAH EMAIL & ASAL USUL ISTILAH SPAM<strong></p>

Email (electronic mail) merupakan salah satu bentuk komunikasi digital paling awal yang masih digunakan secara luas hingga saat ini. Konsep awal email muncul pada tahun 1960-an di lingkungan komputer besar (mainframe), namun bentuk email modern baru lahir pada tahun 1971 ketika seorang insinyur bernama Ray Tomlinson mengembangkan sistem yang memungkinkan pengiriman pesan antar komputer melalui jaringan ARPANET, cikal bakal internet. Ray Tomlinson juga memperkenalkan penggunaan simbol "@" untuk memisahkan nama pengguna dan alamat komputer, konvensi yang hingga kini menjadi standar dalam penulisan alamat email. Seiring perkembangan teknologi, pada tahun 1980-an email mulai digunakan secara luas di kalangan akademisi dan militer, terutama dengan diperkenalkannya protokol SMTP (Simple Mail Transfer Protocol) sebagai standar pengiriman email. Memasuki tahun 1990-an, layanan email mulai diakses publik secara luas seiring dengan pertumbuhan internet dan munculnya layanan seperti Yahoo Mail dan Hotmail. Hingga kini, email telah menjadi sarana komunikasi penting dalam bidang profesional maupun pribadi.

Sementara itu, istilah "spam" dalam konteks email memiliki asal-usul yang unik. Kata ini awalnya adalah nama produk daging kalengan asal Amerika, yaitu SPAM (Spiced Ham), yang diproduksi oleh perusahaan Hormel. Namun, penggunaannya dalam dunia teknologi terinspirasi dari sebuah sketsa komedi Monty Python pada tahun 1970, di mana tokoh-tokohnya terus-menerus menyebut kata "SPAM" dengan suara keras dan mengganggu dalam sebuah restoran. Adegan tersebut menggambarkan gangguan berulang yang tidak dapat dihindari, sehingga komunitas pengguna internet awal mulai menggunakan istilah "spam" untuk menyebut pesan digital yang bersifat mengganggu, berulang, dan tidak diinginkan. Dalam konteks email, spam merujuk pada email massal yang umumnya berisi iklan, penipuan, atau konten merugikan lainnya, dan hingga kini menjadi tantangan tersendiri dalam pengelolaan sistem email modern.

---

# C. PERTANYAAN
1. Buatlah Rangkuman mengenai materi berikut :
   - Penjelasan mengenai protokol mail (SMTP, POP3, IMAP dan POP3S)
   - Cara mengetahui informasi mail server dalam sebuah domain
   - Penjelasan mengenai gambar dari laman [materi alur pengiriman e-mail](https://www.geeksforgeeks.org/introduction-to-electronic-mail/)
2. Kerjakan dalam bentuk md
3. Kirim ke ethol dalam bentuk word berisi link githubnya

---

# D. RANGKUMAN
## 1. Protokol Pengiriman Email
Protokol pengiriman email adalah cara untuk menjaga agar pengiriman email sampai kepada penerima dengan selamat dan tidak kurang suatu apapun. Adapun protokol email itu adalah sebagai berikut :

| Protokol | Fungsi Utama | Port Default | Karakteristik |
|----------|--------------|--------------|---------------|
| SMTP (Simple Mail Transfer Protocol) | Mengirim email dari client ke server atau antar server | 25 (umum), 587 (secure), 465 (SSL) | Hanya untuk mengirim, bukan mengambil email. |
| POP3 | (Post Office Protocol v3) | Mengambil email dari server dan menghapusnya dari server (default) | 110 | Setelah email diunduh, biasanya dihapus dari server (kecuali diatur tetap di server). Cocok untuk penggunaan offline. |
| IMAP (Internet Message Access Protocol) | Mengambil dan menyinkronkan email tanpa menghapusnya dari server | 143 (non-secure), 993 (secure/IMAPS) | Bisa sinkron antar perangkat. Email tetap tersimpan di server. |
| POP3S | POP3 dengan SSL/TLS (versi aman dari POP3) | 995 | Sama seperti POP3, tetapi lebih aman karena terenkripsi. |

## 2. Cara Mencari Tahu Informasi Mail Server di Linux
Pada Linux terdapat perintah nslookup yang dapat digunakan untuk mengetahui mail server dari suatu domain website. Adapun kode yang diperlukan adalah :
```bash
user@hostname:~$ nslookup q=mx example.com
```
bisa juga dengan dig
```bash
user@hostname:~$ dig mx example.com
```

yang nantinya akan mengeluarkan output berupa domain/ip dari mail server yang menerima mail untuk domain tadi.
```bash
example.com.  3600  IN  MX  10 mail.example.com.
..
user@hostname:~$ 
```

## 3. Penjelasan Alur Pengiriman E-mail
![Simple Mail Transfer](https://media.geeksforgeeks.org/wp-content/uploads/20200731122504/Email1.png)
1. User Agent (UA)<br>
Bertugas sebagai antarmuka bagi pengguna untuk menulis, membaca, dan mengelola email.
Contoh: aplikasi email seperti Outlook, Gmail, dll.
2. Message Transfer Agent (MTA)<br>
Komponen yang bertugas mengirim email dari satu komputer ke komputer lain.
Menggunakan protokol seperti SMTP untuk mentransfer pesan.
Dapat mengirimkan email antar MTA dalam proses pengiriman ke tujuan akhir.
3. Mail Box<br>
Tempat penyimpanan email masuk untuk masing-masing pengguna. Email tetap di tempat ini sampai diambil oleh User Agent. Adapun Mail Box bisa diakses dengan protokol seperti POP3 atau IMAP (meskipun ini tidak dijelaskan detail di bagian ini).
5. Spool File<br>
Lokasi penyimpanan sementara untuk email yang menunggu untuk dikirim.
Spoolfile digunakan oleh MTA ketika email tidak bisa langsung dikirim ke tujuan (misalnya karena server tujuan sedang tidak aktif).

---

# DAFTAR PUSTAKA
1. GeeksforGeeks. (2021). *Introduction to Electronic Mail*. Diakses dari [https://www.geeksforgeeks.org/introduction-to-electronic-mail/](https://www.geeksforgeeks.org/introduction-to-electronic-mail/) pada 6 Mei 2025.

2. Kurose, J. F., & Ross, K. W. (2021). *Computer Networking: A Top-Down Approach* (7th ed.). Pearson Education.
   *(Referensi utama untuk penjelasan protokol email seperti SMTP, POP3, IMAP.)*

3. Tanenbaum, A. S., & Wetherall, D. J. (2011). *Computer Networks* (5th ed.). Prentice Hall.
   *(Digunakan untuk memahami arsitektur jaringan dan sistem pengiriman email.)*

4. Internet Engineering Task Force (IETF). (2008). *RFC 5321 - Simple Mail Transfer Protocol (SMTP)*. Diakses dari [https://tools.ietf.org/html/rfc5321](https://tools.ietf.org/html/rfc5321)

5. Hormel Foods Corporation. (n.d.). *Spam® Brand – A History*. Diakses dari [https://www.spam.com/about](https://www.spam.com/about)

6. BBC. (2007). *Monty Python sketch gave us spam*. Diakses dari [http://news.bbc.co.uk/2/hi/uk\_news/magazine/7090728.stm](http://news.bbc.co.uk/2/hi/uk_news/magazine/7090728.stm)

---
