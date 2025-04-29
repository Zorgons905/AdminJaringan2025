
---

<p align="right">
    SURABAYA <br> 29 APRIL 2025
</p> <br>

<h1 align="center"><ins>LAPORAN PRAKTIKUM</ins></h1>
<h3 align="center"><em>"TOPOLOGI WEBSERVER DAN DNS"</em></h3>
<h3 align="center">Mata Kuliah Workshop Administrasi Jaringan</h3>

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/PENS.png" width="300" height="300"><br>
</p>

<p align="center">
Nama Dosen Pengampu : <br> 
Bapak Dr Ferry Astika Saputra ST, M.Sc <br>
<br>
Dikerjakan Oleh : <br>
< KELOMPOK 8 ><br>
Rifki Alaudin&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;[3123600007]<br>
Nanda Ahmad Zidan&emsp;&emsp;&emsp;[3123600013]<br>
Vemas Satria Edi Pratama&emsp;[3123600020]<br>
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
B. [DASAR TEORI](#b-dasar-teori)<br>
C. [PERCOBAAN](#c-percobaan)<br>
1. [Perintah](#1-pertanyaan)<br>
2. [Jawaban](#2-jawaban)<br>


<p align="center">i</p>

---

# A. TUJUAN PEMBELAJARAN
1. Memahami bagaimana sistem root dalam DNS
2. Memahami cara mengatur dan menghubungkan koneksi antar domain
3. Memahami cara menyetel apache2 pada DNS yang sudah dibuat
4. Memahami bagaimana web hosting bekerja (secara private)

---

# B. DASAR TEORI
Sistem Root dalam DNS
Domain Name System (DNS) adalah sistem yang digunakan untuk menerjemahkan nama domain (seperti example.com) menjadi alamat IP (seperti 192.0.2.1) yang dapat dikenali oleh komputer. DNS terdiri dari hierarki struktur, dimulai dari root DNS server yang menjadi pusat dari sistem ini.

Root DNS server bertugas untuk:
- Menyimpan informasi tentang domain-level tertinggi (Top-Level Domain/TLD) seperti .com, .org, .net, dll.
- Mengarahkan permintaan ke TLD server yang sesuai.

Struktur hierarki DNS dari atas ke bawah:
Root ( . )
 └── TLD (.com, .net, .org)
      └── Domain (example.com)
           └── Subdomain (www.example.com)

Koneksi Antar Domain
Menghubungkan domain ke server dilakukan dengan menyetel DNS record pada penyedia domain. Beberapa record yang umum digunakan:
- A Record: Menghubungkan domain ke alamat IP (IPv4).
- AAAA Record: Menghubungkan ke alamat IP (IPv6).
- CNAME: Mengarahkan domain ke domain lain.
- NS Record: Menunjukkan server DNS mana yang berwenang untuk domain.
- MX Record: Mengatur layanan email untuk domain.
Contoh: jika domain mywebsite.com diarahkan ke IP 192.168.1.10, maka A record-nya akan seperti:
mywebsite.com   A   192.168.1.10

Apa itu Web Hosting Lokal?
Web hosting lokal adalah cara untuk membuat situs web yang hanya dapat diakses oleh perangkat yang terhubung dalam jaringan yang sama. Ini biasanya digunakan untuk pengujian atau jaringan internal, di mana situs web atau aplikasi web hanya perlu diakses oleh pengguna atau perangkat yang berada dalam jaringan lokal (LAN).

Peran Router dalam Web Hosting
Router berfungsi sebagai penghubung perangkat-perangkat dalam jaringan lokal. Router ini memberikan alamat IP lokal kepada perangkat yang terhubung dan menyaring lalu lintas data di dalam jaringan. Dalam konteks ini, hanya perangkat yang terhubung langsung ke router (baik melalui kabel atau Wi-Fi) yang bisa mengakses situs web yang di-hosting di server lokal.

---

# PERCOBAAN
## 1. Perintah
Dalam satu kelompok gunakan 3 komputer yang tersedia, untuk melakukan tugas berikut :
- Komputer 1 menjadi host dari web
- Komputer 2 digunakan untuk menggambar topologi jaringan yang terjadi
- Komputer 3 sebagai pengecek apakah komputer 1 sudah bisa menghubungkan diri dengan domain kelompok lain.

Lakukan penerapan penyetelan BIND9 dan Apache2 serta pemahaman Anda soal bagaimana DNS bekerja lalu tuliskan dan sertakan screenshotnya. 

## 2. Jawaban
[1] Komputer 1
Ketika kita akan membuat suatu hosting dan koneksi dengan root adalah dengan menggunakan perantara router, sehingga kita memerlukan suatu aplikasi yang mampu menghubungkan kita dengan router dan mengenali domain lain yang juga terkoneksi melalui router tersebut. 

Oleh karena itu langkah pertama kita ialah untuk menyetel BIND9 & BINDUTILS (BIND9 untuk aturannya, BINDUTILS untuk pengecek & alat kontrolnya). Jika 



---

# DAFTAR PUSTAKA
- 
-
