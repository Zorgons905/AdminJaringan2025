
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
### Sistem Root dalam DNS
Domain Name System (DNS) adalah sistem yang digunakan untuk menerjemahkan nama domain (seperti example.com) menjadi alamat IP (seperti 192.0.2.1) yang dapat dikenali oleh komputer. DNS terdiri dari hierarki struktur, dimulai dari root DNS server yang menjadi pusat dari sistem ini.
Root DNS server bertugas untuk:
- Menyimpan informasi tentang domain-level tertinggi (Top-Level Domain/TLD) seperti .com, .org, .net, dll.
- Mengarahkan permintaan ke TLD server yang sesuai.

Struktur hierarki DNS dari atas ke bawah:
Root ( . )
 └── TLD (.com, .net, .org)
      └── Domain (example.com)
           └── Subdomain (www.example.com)

### Koneksi Antar Domain
Menghubungkan domain ke server dilakukan dengan menyetel DNS record pada penyedia domain. Beberapa record yang umum digunakan:
- A Record: Menghubungkan domain ke alamat IP (IPv4).
- AAAA Record: Menghubungkan ke alamat IP (IPv6).
- CNAME: Mengarahkan domain ke domain lain.
- NS Record: Menunjukkan server DNS mana yang berwenang untuk domain.
- MX Record: Mengatur layanan email untuk domain.
Contoh: jika domain mywebsite.com diarahkan ke IP 192.168.1.10, maka A record-nya akan seperti:
mywebsite.com   A   192.168.1.10

### Apa itu Web Hosting Lokal?
Web hosting lokal adalah cara untuk membuat situs web yang hanya dapat diakses oleh perangkat yang terhubung dalam jaringan yang sama. Ini biasanya digunakan untuk pengujian atau jaringan internal, di mana situs web atau aplikasi web hanya perlu diakses oleh pengguna atau perangkat yang berada dalam jaringan lokal (LAN).

### Peran Router dalam Web Hosting
Router berfungsi sebagai penghubung perangkat-perangkat dalam jaringan lokal. Router ini memberikan alamat IP lokal kepada perangkat yang terhubung dan menyaring lalu lintas data di dalam jaringan. Dalam konteks ini, hanya perangkat yang terhubung langsung ke router (baik melalui kabel atau Wi-Fi) yang bisa mengakses situs web yang di-hosting di server lokal.

### Apa itu BIND9?
BIND9 (Berkeley Internet Name Domain) adalah perangkat lunak DNS server (Domain Name System) yang digunakan untuk menerjemahkan nama domain menjadi alamat IP dan sebaliknya. BIND9 adalah versi terbaru dari BIND, yang merupakan salah satu perangkat lunak DNS server yang paling banyak digunakan di internet.
Fungsi Utama BIND9:
- Menjadi DNS Server: BIND9 menerima permintaan dari klien untuk menerjemahkan nama domain (misalnya, www.example.com) ke dalam alamat IP (misalnya, 192.168.1.1), sehingga perangkat bisa saling berkomunikasi melalui jaringan.
- Mengelola Zona DNS: BIND9 memungkinkan pengaturan dan pengelolaan zona DNS untuk domain tertentu. Ini termasuk A Record (untuk mengarahkan domain ke IP), MX Record (untuk mengarahkan email), dan CNAME Record (untuk alias domain).
- Mendukung DNS Resolving: BIND9 dapat berfungsi sebagai recursive resolver, yang berarti ia mencari informasi DNS dari server DNS lainnya jika ia tidak tahu jawabannya sendiri.

### Apa itu Apache2?
Apache2 (atau Apache HTTP Server) adalah perangkat lunak web server open-source yang paling banyak dipakai di dunia. Ia berjalan sebagai layanan (daemon) di sistem operasi (umumnya Linux/Unix) dan mendengarkan permintaan HTTP(S) dari klien (browser).
Fungsi Utama Apache2
- Melayani Konten Statis, yakni mengirimkan file HTML, CSS, JavaScript, gambar, video, dll., sesuai path di DocumentRoot (misalnya /var/www/html).
- Memproses Konten Dinamis, lewat modul seperti mod_php, mod_perl, mod_python, atau dengan proxy ke application server (misal Node.js, Gunicorn).
- Virtual Hosts (Multi-Site Hosting), Menjalankan banyak situs/domain di satu server fisik/IP yang sama, dengan konfigurasi terpisah (/etc/apache2/sites-available/…).
- Keamanan dan Authentication, Menyokong SSL/TLS (HTTPS), kontrol akses berbasis IP atau password, modul mod_security, mod_evasive untuk proteksi DDoS ringan.
- Logging & Monitoring, mencatat akses dan error dalam log (access.log, error.log) untuk debugging dan analisis performa.
- Extensibility, ratusan modul tersedia untuk caching (mod_cache), rewrite URL (mod_rewrite), proxy (mod_proxy), load‐balancing, dsb.

### Apa itu SSH?
SSH (Secure Shell) adalah protokol jaringan yang digunakan untuk mengakses dan mengelola perangkat secara remote dengan aman melalui jaringan. SSH menyediakan komunikasi yang terenkripsi antara klien dan server, yang memungkinkan pengelolaan server atau perangkat lain dengan aman tanpa takut data yang dikirimkan disadap oleh pihak ketiga.
Fungsi Utama SSH:
- Akses Remote Aman: SSH memungkinkan pengguna untuk mengakses server atau perangkat lain dari jarak jauh dengan cara yang aman. Ini sering digunakan untuk login ke server untuk mengelola sistem atau aplikasi.
- Enkripsi Komunikasi: Semua komunikasi yang terjadi melalui SSH dienkripsi, sehingga data yang dikirim (seperti password, file, atau perintah) terlindungi dari pemantauan atau manipulasi.
- Transfer File Aman: SSH juga memungkinkan transfer file antar server menggunakan protokol seperti SFTP (SSH File Transfer Protocol) atau SCP (Secure Copy Protocol).
- Tunneling dan Forwarding: SSH dapat digunakan untuk membuat tunnel aman untuk mengakses layanan di balik firewall, atau untuk melakukan port forwarding.

### Keterkaitan BIND9, APACHE dan SSL dengan Web Hosting
BIND9 memiliki fungsi untuk mengelola DNS, mengarahkan permintaan domain (misal mywebsite.com) ke IP server yang benar.
Apache2 memiliki fungsi untuk menangani permintaan HTTP/HTTPS dari browser, menyajikan konten situs web, dan mengelola pengaturan virtual host untuk berbagai domain.
SSH memiliki fungsi untuk memberi akses kontrol antar perangkat, mengedit dan mengelola file web, deploy / update website, memberi keamanan lokal.

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

Oleh karena itu langkah pertama kita ialah untuk menyetel BIND9 & BINDUTILS (BIND9 untuk aturannya, BINDUTILS untuk pengecek & alat kontrolnya). Jikalau belum diunduh maka lakukan perintah linux debian berikut :



---

# DAFTAR PUSTAKA
- ISC BIND9 Documentation
Internet Systems Consortium. (n.d.). BIND 9 Administrator Reference Manual.
Tersedia di: https://bind9.readthedocs.io/

- Apache HTTP Server Documentation
The Apache Software Foundation. (n.d.). Apache HTTP Server Version 2.4 Documentation.
Tersedia di: https://httpd.apache.org/docs/2.4/

- Let’s Encrypt and SSL/TLS Basics
Electronic Frontier Foundation. (n.d.). Certbot and HTTPS encryption.
Tersedia di: https://letsencrypt.org/

- SSH Protocol Description
OpenSSH Project. (n.d.). OpenSSH Manual Pages.
Tersedia di: https://www.openssh.com/manual.html

- DigitalOcean Tutorials
DigitalOcean. (n.d.). How To Set Up and Configure DNS with BIND9 on Ubuntu, How To Use SSH, dan How To Install the Apache Web Server on Ubuntu.
Tersedia di: https://www.digitalocean.com/community/tutorials

- Red Hat and Ubuntu Server Guides
Red Hat, Inc. dan Canonical Ltd. (n.d.). Server Administration Documentation.
Tersedia di:
> https://access.redhat.com/documentation
> https://ubuntu.com/server/docs
