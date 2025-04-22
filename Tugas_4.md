
---

<p align="right">
    SURABAYA <br> 04 DESEMBER 2024
</p> <br>

<h1 align="center"><ins>LAPORAN RESMI</ins></h1>
<h3 align="center"><em>"Tugas Workshop Administrasi Jaringan"</em></h3>
<h3 align="center">Mata Kuliah Workshop Administrasi Jaringan</h3>

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/PENS.png" width="300" height="300"><br>
</p>

<p align="center">
Nama Dosen Pengampu : <br> 
Bapak Dr Ferry Astika Saputra ST, M.Sc <br>
<br>
Dikerjakan Oleh : <br>
</p>

<p>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Nama&emsp;&nbsp; : Nanda Ahmad Zidan <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;NRP&emsp;&emsp;&nbsp;: 3123600013 <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Kelas&emsp;&emsp;: 2 D4 IT A <br>
<br>
</p>

<p align="center">
Tahun Pelajaran 2024/2025 <br>
<strong>POLITEKNIK ELEKTRONIKA NEGERI SURABAYA</strong>
</p>

---
<br>

<h2 align="center">DAFTAR ISI</h2>
<br>

[DAFTAR ISI........................................i](#daftar-isi)<br>
A. [TUJUAN PEMBELAJARAN............................1](#a-tujuan-pembelajaran)<br>
B. [DASAR TEORI.............................1](#b-dasar-teori)<br>
1. [Mengenal Wireshark......................1](#1-mengenal-wireshark)<br>
2. [Mengenal Layer OSI....................2](#2-mengenal-layer-osi)<br>

C. [PERCOBAAN..............................i](#c-percobaan)<br>
1. [Pertanyaan............................1](#1-pertanyaan)<br>
2. [Jawaban..............................1](#2-jawaban)<br>


<p align="center">i</p>

---

# A. TUJUAN PEMBELAJARAN
1. Memahami bagaimana cara DNS bekerja
2. Memahami bagian-bagian dari DNS
3. Memahami cara menghubungkan 2 VM yang saling terkoneksi
4. Memahami cara menyetel BIND9

---

# B. DASAR TEORI
## 1. Pengertian DNS

Domain Name System (DNS) adalah sistem yang berfungsi untuk menerjemahkan nama domain yang mudah dibaca manusia (seperti `www.google.com`) menjadi alamat IP numerik (seperti `142.250.190.4`) yang dapat dikenali oleh perangkat jaringan. DNS adalah fondasi penting dalam struktur internet karena memungkinkan komunikasi antarperangkat menggunakan nama yang mudah diingat.

## 2. Sejarah Singkat DNS

Sebelum DNS, jaringan komputer menggunakan file yang disebut `HOSTS.TXT` yang berisi daftar nama host dan alamat IP-nya. File ini dikelola secara terpusat oleh Stanford Research Institute. Namun, seiring pertumbuhan internet, pendekatan ini menjadi tidak efisien, sehingga pada tahun 1983, Paul Mockapetris mengembangkan sistem DNS seperti yang kita kenal sekarang.

## 3. Fungsi DNS

DNS memiliki beberapa fungsi penting, antara lain:

- **Resolusi Nama:** Menerjemahkan nama domain ke alamat IP.
- **Abstraksi:** Menyederhanakan identifikasi alamat-alamat IP yang kompleks.
- **Redundansi dan Ketersediaan Tinggi:** Menyediakan banyak server yang tersebar untuk menjamin ketersediaan.
- **Distribusi Beban:** Mengarahkan trafik ke server yang berbeda berdasarkan lokasi atau ketersediaan.
- **Manajemen Sistem Nama Domain Secara Terdistribusi:** Mengizinkan pengelolaan domain secara desentralisasi.

## 4. Cara Kerja DNS

1. **Permintaan DNS:** Saat pengguna mengetik `www.example.com` di browser, permintaan dikirim ke resolver lokal.
2. **Pencarian Cache:** Resolver memeriksa cache lokal.
3. **Root DNS Server:** Jika cache kosong, resolver meminta informasi ke root server.
4. **TLD Server:** Root server mengarahkan ke Top-Level Domain server (misal, `.com`).
5. **Authoritative DNS Server:** TLD server mengarahkan ke server yang memiliki informasi domain.
6. **Pengembalian IP:** Resolver mendapatkan alamat IP dan mengirimkannya ke browser.
7. **Koneksi ke Server Web:** Browser menggunakan IP tersebut untuk menghubungi server situs web.

## 5. Struktur Hirarki DNS

- **Root Level:** Representasi tertinggi (".") dalam hierarki.
- **Top-Level Domain (TLD):** Seperti `.com`, `.org`, `.id`.
- **Second-Level Domain:** Nama yang didaftarkan (misalnya `google` dalam `google.com`).
- **Subdomain:** Bagian opsional seperti `mail.google.com` atau `blog.example.com`.

Contoh:
mail.example.com 
├── Subdomain: mail 
├── Second-Level Domain: example 
└── Top-Level Domain: com

## 6. Jenis-Jenis DNS Record

| Tipe Record | Fungsi |
|-------------|--------|
| A           | Memetakan domain ke alamat IPv4 |
| AAAA        | Memetakan domain ke alamat IPv6 |
| CNAME       | Menunjukkan alias ke domain lain |
| MX          | Menentukan mail server untuk domain |
| NS          | Menunjukkan authoritative name server |
| PTR         | Reverse lookup dari IP ke domain |
| SOA         | Informasi otoritatif tentang domain |
| TXT         | Menyimpan teks, seperti verifikasi SPF, DKIM |

## 7. Komponen DNS

- **DNS Resolver (Recursive Resolver):** Bertanggung jawab menangani permintaan pengguna.
- **Root Server:** Titik awal pencarian domain di hirarki DNS.
- **TLD Server:** Menangani domain TLD seperti `.org`, `.net`, `.id`.
- **Authoritative DNS Server:** Menyediakan jawaban final untuk query DNS tertentu.

## 8. Keamanan DNS

- **DNS Spoofing/Cache Poisoning:** Serangan yang memanipulasi data DNS untuk mengarahkan pengguna ke situs palsu.
- **DNSSEC (DNS Security Extensions):** Fitur keamanan yang memastikan integritas dan keaslian data DNS.
- **DoH (DNS over HTTPS) / DoT (DNS over TLS):** Protokol untuk mengenkripsi permintaan DNS agar tidak dapat dilihat oleh pihak ketiga.

## 9. Proses Resolusi DNS (Diagram)
Browser --> DNS Resolver --> Root Server --> TLD Server --> Authoritative Server --> IP Address


## 10. Tools DNS

Beberapa tools untuk memeriksa dan menganalisis DNS:

- `nslookup`
- `dig`
- `host`
- DNS Checker (web-based tools)

---

# C. PERCOBAAN
## 1. Pertanyaan
> Buatlah konfigurasi DNS yang membuat 2 VM saling terhubung (ditandai dengan proses ping yang berhasil) pada salah satu dari kedua VM tersebut. Kemudian jalankan salah satu VM sebagai router agar nantinya bisa terhubung dengan internet. Satu sebagai client dan satunya sebagai server.

## 2. Jawaban
1. Instalasi
Pertama-tama kita download terlebih dahulu bind9 dan iptables baik pada VM1 dan VM2.

```bash
sudo apt install bind9 bind9utils
...
sudo apt install iptables iptables-persistent
...
```

contoh :
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/bind9.png" width="300" height="300"><br>
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/lanjutan_bind.png" width="300" height="300"><br>
</p>

bind9 utils berfungsi sebagai pengecek zona konfigurasi tempat dns akan dijalankan, ibaratnya kita membuat koneksi khusus dengan ip yang tertera dalam settingan bind9 dengan menggunakan alias / DNSnya.
iptables-persistent gunanya untuk menyimpan rules instalasi agar tetap ada meskipun VM dimatikan sehingga tak perlu konfigurasi ulang.

2. Setting IP address
Kemudian kita lanjut untuk mengedit file `/etc/network/interfaces`. Kita jalankan perintah ini :
```bash
sudo nano /etc/network/interfaces
```
lalu tambahkan beberapa settingan berikut :
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/setting_network" width="300" height="300"><br>
</p>

Di sini, enp0s3 adalah antarmuka jaringan utama yang terhubung ke bridge adapter/internet, sedangkan enp0s8 merupakan antarmuka sekunder yang terhubung ke jaringan internal, yang nantinya akan dikoneksikan ke VM 2.

Oleh karena itu, konfigurasi untuk enp0s3 akan dibiarkan dalam kondisi default agar menerima alamat IP secara otomatis sebagai klien DHCP, sedangkan enp0s8 akan dikonfigurasi secara statis dengan alamat IP 192.168.200.1 dan netmask 255.255.255.0 (atau /24).

setelah itu kita restart agar `/etc/network/interfaces` dapat berubah.
```bash
sudo systemctl restart networking
```
Lalu kita dapat mengecek apakah ip address sudah berubah melalui perintah ip a

4. DNS Config
Pertama kita masuk ke direktori `/etc/bind` kemudian kita lanjutkan dengan mengonfigurasi file `named.conf`

```bash
sudo nano named.conf
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/set_named.png" width="300" height="300"><br>
</p>

kita tambahkan line `include "/etc/bind/named.conf.external-zones"` untuk menambahkan zones yang nantinya akan kita buat. Selanjutnya kita setel `named.conf.options`

```bash
sudo nano named.conf.options
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/set_named_options.png" width="300" height="300"><br>
</p>

Tambahkan beberapa baris kode berikut

```
allow-query { any; };
allow-transfer { any; };
recursion yes;
```

Selanjutnya kita setel file `named.conf.external-zones`
```bash
sudo nano named.conf.external-zones
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/set_external.png" width="300" height="300"><br>
</p>

disini kita buat zones untuk DNS kita, kita membuat 2 zones dimana satu untuk nameserver yaitu kelompok2.com dan satu lagi untuk IP nya 1.200.168.192.in-addr.arpa pada line file berikan lokasi file untuk konfigurasi zone nantinya

Untuk konfigurasi zones, pertama saya akan mengonfigurasi file kelompok2.com
```bash
sudo nano kelompok2.com
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/kel_2.png" width="300" height="300"><br>
</p>

selanjutnya kita setting file 1.200.168.192.db
```bash
sudo nano 1.200.168.192.db
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/ipdb.png" width="300" height="300"><br>
</p>

setelah membuat konfigurasi untuk kedua zones tersebut, kita dapat mengecek apakah ada kesalahan dalam konfigurasi menggunakan perintah named-checkzone dari bind9utils
```bash
named-checkzone [nama_zone] [file_konfigurasi_zone]
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/checkzone.png" width="300" height="300"><br>
</p>

dan diatas sudah memampilkan OK untuk kedua zone yang berarti tidak ada masalah yang ditemukan

setelah semua konfigurasi di atas, restart named.service untuk menerapkan semua konfigurasi tersebut

```bash
sudo systemctl restart named
```


6. Setting IP forwarding
Pertama, ubah nilai ip_forward menjadi 1 agar VM 1 dapat meneruskan IP dengan perintah berikut:
```bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/ip_forward.png" width="300" height="300"><br>
</p>

jika file tersebut ditampilkan dengan perintah cat dan menampilkan nilai 1, maka ip_forward sudah diaktifkan

Selanjutnya adalah konfigurasi iptables, jalankan perintah berikut:
```bash
sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
```

Perintah tersebut digunakan untuk menambahkan tabel NAT pada iptables dan melakukan MASQUERADE ke ip yang diteruskan ke interface enp0s3 yang terhubung ke Internet Perintah ini berfungsi untuk mentranslasikan ip private ke ip public ke internet

Selanjutnya jalankan perintah berikut:
```
sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
sudo iptables -A FORWARD -i enp0s3 -o enp0s8 -j ACCEPT
```
Perintah ini akan menambahkan rules untuk meneruskan ip dari interface enp0s8 ke enp0s3 dan sebaliknya agar nantinya VM 2 bisa terhubung ke Internet

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/iptables.png" width="300" height="300"><br>
</p>

setelah menambahkan tabel NAT dan rules di atas, untuk menyimpan konfigurasi tersebut, jalankan perintah berikut:
```
sudo iptables-save
```
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/iptables-save.png" width="300" height="300"><br>
</p>


8. Setting VM2
Selanjutnya kita konfigurasi untuk VM 2 sebagai Client

KIta hanya perlu mengonfigurasi IP Static dari VM 2, dengan masuk Ke Wired Settings dan masuk Ke Tab IPv4 dan isikan address yang berada pada satu network dengan IP Address pada interface enp0s8 pada VM 1 sebelumnya, yaitu 192.168.200.x sebagai berikut:

<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/set_vm2.png" width="300" height="300"><br>
</p>

Masukkan juga IP Address 192.168.200.1 pada DNS agar kita dapat terhubung dengan DNS pada VM 1

Untuk mengonfigurasi IP pada VM 2 juga bisa dilakukan melalui CLI seperti pada VM 1 jika menggunakan OS tanpa GUI

9. Ping VM1
Disini akan dicoba untuk melakukan ping ke IP addresss dari VM 1 untuk mengecek koneksi antara VM 2 dan VM 1
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/check_ping.png" width="300" height="300"><br>
</p>
dan disini sudah ditampilkan bahwa VM 1 dan VM 2 sudah bisa saling berkomunikasi

10. check internet
Disini saya mencoba untuk membuka halaman web untuk mengecek apakah VM 2 sudah bisa terhubung dengan internet dan saya sudah bisa mengakses internet pada VM 2
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/yutub.png" width="300" height="300"><br>
</p>


12. check VM1 DNS
Disini saya mencoba DNS yang sudah dikonfigurasi pada VM 1 sebelumnya pada VM 2 dengan menggunakan dig / nslookup dan dapat kita lihat bahwa pada output dig sudah menampilkan ANSWER SECTION dan pada output nslookup juga sudah menampilkan nameserver dan ip addressnya
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/dig.png" width="300" height="300"><br>
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/dig2.png" width="300" height="300"><br>
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar3/nslookup.png" width="300" height="300"><br>
</p>
