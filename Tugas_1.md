# Heading 1
## Heading 2
### Heading 3
... sampai
###### Heading 6

### Heading ini ada id nya
[Ini link menuju heading dengan custom id](#Heading-ini-ada-id-nya)

ini paragraph biasa

dibawah ini ada pembatasnya

---
<br> untuk enter gunakan `<br>`

:warning: Emoji diapit :

*ini italic* <br>
***BOLD and italic*** <br>
==Highlight== <br>
~~Strikethrough~~ <br>

Underlined, center dll kita pakai format HTML
<ins>underlined</ins> <br>
<p align="center">Centered Text</p> <br>
<p align="left">Left Text</p> <br>
<p align="right">Right Text</p> <br>
<p align="justify">Justified Text</p>

Dibawah ini ada hidden comment <br>

[hidden comment]: #
<br> if its works why not? jadi di atas itu fitur yang ditemuin orang, intinya dia mengubah syntax link dicampur dengan definisi dan syntax heading untuk menyembunyikan linknya.

Subscript formatnya H~2~0 diapit ~ <br>
Superscript formatnya X^2^ diapit ^ <br>
kalau tidak bisa pakai html H<sub>2</sub>O & X<sup>2</sup> 

> blockquotes
>> Nested blockquotes
Katanya
: definisinya

- ini unordered list
1. ini ordered list
- [x] ini tasklist
- [ ] tasklist yang belum

`ini font code biasa`

```python
print("Hello, world!")
for i in range(10):
    print(i)
```

<br> [ini format Link](https://www.google.co.id/) tapi link ini membuka di page yang sama.

<br> ![ini gambar ayam](https://github.com/Zorgons905/AdminJaringan2025/blob/main/PENS.png)

<br> jika ingin membenahi width dan heightnya kita pakai html
<br> <img src="https://th.bing.com/th/id/OIP.fJSlWKWeuR56aS3pdyG3LgHaEO?rs=1&pid=ImgDetMain" width="200" height="100">

<br> ini cara menambahkan video
<br> [![Less Than Jake — Scott Farcas Takes It On The Chin](https://img.youtube.com/vi/PYCxct2e0zI/0.jpg)](https://www.youtube.com/watch?v=PYCxct2e0zI)


Tabel biasa
| Jumlah | Jenis Ayam |
|--------|------------|
| 2 | Cemani |
| 3 | Horen<br><br>paragraph berikutnya namun masih satu baris |

ini kalimat footnote. [^1]
[^1]: footnotenya







<br>

---

<p align="right">
    SURABAYA <br> 04 DESEMBER 2024
</p> <br>

<h1 align="center"><ins>LAPORAN RESMI</ins></h1>
<h3 align="center"><em>"Tugas Workshop Administrasi Jaringan"</em></h3>
<h3 align="center">Mata Kuliah Workshop Administrasi Jaringan</h3>
<p align="center">
<img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/PENS.png" width="300" height="300"><br>
</p>

<p align="center">
Nama Dosen Pengampu : <br> 
Bapak Dr Ferry Astika Saputra ST, M.Sc <br>
<br>
Dikerjakan Oleh : <br>
</p>
<p>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Nama&emsp; : Nanda Ahmad Zidan <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;NRP&emsp;&emsp;: 3123600013 <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Kelas&emsp;&nbsp;&nbsp; : 2 D4 IT A <br>
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

D. [DAFTAR PUSTAKA..............................i](#d-daftar-pustaka)<br>


<p align="center">i</p>

---

## A. TUJUAN PEMBELAJARAN
1. Memahami bagaimana cara menjalankan wireshark
2. Memahami bagian-bagian dari datagram yang ada pada wireshark
3. Memahami layer OSI dalam internet secara mendalam
4. Memahami apa itu HTTP
5. Memahami apa itu tipe pengiriman data
6. Memahami apa itu three-way handshake

---

## B. DASAR TEORI
1. Mengenal Wireshark
<p>
&emsp;Wireshark adalah aplikasi untuk menampilkan hasil jejak rute / tracing route packet data dari router terdekat yang lalu ditangkap oleh komputer kita. Hasilnya lalu ditampilkan dalam rupa tabel berisi keterangan tertentu seperti no.packet, time / waktu respon packet, alamat source / sumber dan destination / destinasi packet, protocol yang digunakan, length / panjang data yang diterima maupun dikirim, dan info notifikasi dari program jaringan yang sedang kita jalankan maupun balasan dari destinasinya.
<br>
Pada Wireshark terdapat beberapa tampilan dan istilah yang perlu diketahui :
</p>

2. Mengenal Layer OSI
<p>
&emsp;OSI (Open Systems Interconnection) Model adalah kerangka jaringan yang dibuat oleh International Organization for Standardization (ISO, *bukan singkatan melainkan bahasa yunani artinya “sama”) pada tahun 1984. Model ini digunakan untuk memahami dan mengimplementasikan komunikasi dalam jaringan komputer. Adapun ISO bekerja sama dengan institusi lain guna menyatukan pemahaman terkait protokol atau aturan dalam pembuatan jaringan komputer ini. Di antara institusi tersebut adalah DARPA, IEEE, IETF, dll. 
<br>
Layer 1 : Physical layer<br>
&emsp;Adalah layer yang mengatur bagaimana data akan tersampaikan. Data elektronik dapat pertama-tama diubah menjadi bit data di dalam memori lalu disalurkan melalui bisa saja ethernet card maupun wifi, bila melalui ethernet maka data akan diubah menjadi sinyal listrik (gelombang sin) dan bila melalui wifi akan diubah menjadi gelombang elektromagnetik (gelombang radio) sedangkan bila kita mengirim data ke internet dengan kabel optik maka ia akan diubah menjadi sinyal cahaya.
<br>
Layer 2 : Datalink layer<br>
&emsp;Adalah layer yang berfungsi untuk transmisi data antar perangkat, berisi alamat mac dari komputer maupun router (ibarat seperti alamat rumah sumber dan tujuan pembeli dan penjual olshop). Sehingga mampu menghubungkan device ke server maupun ke device lain, karena mempunyai alamat sumber / source dan tujuan / destination. Contoh protocolnya adalah ARP, ATM, CDP, dll. Ditandai dengan rentetan angka heksadesimal (mac addressnya) sebesar 6 byte/48 bit. 
Contoh : 84-07-fb-2d-09-e8
<br>
Layer 3 : Network layer<br>
&emsp;Adalah layer yang berfungsi untuk menangani alamat logis dan pengiriman paket data antar jaringan (ibarat seperti no.seri/user yang diberikan oleh olshop untuk membedakan mana penjual dan pembeli). Yang paling terkenal dari Network layer adalah IP(versinya ada 2 yakni IPv4 dan IPv6) atau internet protocol ada juga protocol lain, seperti ICMP (ping request), RIP, IPsec, dll. 
IPv4 sendiri IP yang berbentuk desimal yang diberikan router pada device yang tersambung. Panjangnya 4 byte/32bit. Size header / tambahan file yang diberikan pada file masuk maupun keluar adalah 20-60 bytes. Jenis ip ini sering digunakan, sedangkan untuk IPv6 masih belum masif penggunaannya.
Contoh&emsp;: 192.168.1.1&emsp;&emsp;IPv4
&emsp;&emsp;&emsp; 2001:0db8:85a3::7334&emsp;&emsp;IPv6
<br>
Layer 4 : Transport layer
&emsp;Adalah layer yang menampilkan informasi mengenai bagaimana data ditransfer di aplikasi seperti no.port dan status koneksi dalam bentuk pemecahan data menjadi beberapa segmen dan nantinya di reassembly (ibarat kurir yang membawa paket bisa dalam bentuk paket terpisah maupun satu paket besar). Contoh protocolnya adalah TCP, dan UDP. 
Misalnya untuk TCP, hardware akan mengirimkan handshake / perkenalan kepada perangkat tertaut. Misal untuk wifi ke laptop. Maka akan terjadi 3 handshake berupa :
</p>
•	Laptop mengirim handshake [SYN] kepada wifi untuk mennyinkronisasi dengan wifi,
•	Lalu wifi mengirim handshake [SYN,ACK] untuk menyetujui laptop, 
•	Laptop lalu memberitahu ke wifi bahwa persetujuan diterima dengan handshake [ACK].
<p>
Sedangkan untuk UDP digunakan untuk broadcasting, biasanya dalam penampilan video online UDP digunakan tanpa kita harus mendownload semua data dan menyimpannya ke dalam device kita. UDP bekerja tanpa adanya handshake dan semua device bisa mengakses data tersebut asalkan sudah mendapat izin dari layer sebelumnya.
<br>
Layer 5 : Session layer <br>
&emsp;Adalah layer yang menjaga data agar aman dan sampai pada tujuan tanpa adanya data yang bocor atau masuk ke dalam perangkat lain di jaringan yang sama. Session sangat terikat dengan presentation layer dan application layer (ibarat kemasan dari paket olshop orang lain tidak boleh membukanya karena bukan miliknya dan alamat maupun data user yang berbeda). Ia bertugas untuk membuka, memelihara dan menutup sesi komunikasi antar dua aplikasi. Contoh protocolnya adalah NFS, RPC, SQL, SMB, CIFS dll.
Misalnya kita mengakses sebuah browser maka sesuai dengan OS yang digunakan maka akan dilakukan pembukaan sesi dengan router ataupun device lain (untuk Windows menggunakan SMB untuk browsing). Jadi jika ada file yang terbagikan oleh device / router lain. Device lain tidak akan bisa menginterupsi dan menggagalkan file sharing tersebut atau bahkan mengambil data dari pengunduhan file tersebut.

Layer 6 : Presentation layer
&emsp;Adalah layer yang menangani format data, enkripsi, dekripsi, dan kompresi serta menyiapkan data untuk aplikasi. Adapun untuk presentation layer ibarat isi dari paket yang kita pesan, ia tergolong apa, apakah gambar, puzel, instrument, ataukah alat lain. 
Yang pasti presentation layer berguna untuk menjaga data agar tidak diedit dan bisa diretas di internet. Contoh protocolnya adalah JPEG, SSL (encrypted data), MIDI, 

Layer 7 : Application layer
&emsp;Adalah layer untuk menangani interaksi antara aplikasi pengguna dan jaringan. Protokolnya seperti HTTP, HTTPs, FTP, SMTP, dll. 
Adapun untuk application layer ibarat penggunaan dari barang olshop yang kita beli dan merek dari barang tersebut. Misal saja untuk HTTPS karena ia memiliki SSL atau encryption. Maka data pada website akan lebih aman karena meskipun dua buah device membuka alamat website yang sama namun terdapat enkripsi data yang berbeda. Sehingga ia tidak akan mudah diedit oleh orang lain.
</p>
---

## C. PERCOBAAN
### 1. Pertanyaan
1. Analisa file http.cap dengan wireshark :
   - Versi HTTP yang digunakan,
   - IP address dari client maupun server,
   - Waktu dari client mengirimkan HTTP request,
   - Waktu dari server mengirinmkan server dan berapa durasinya
2. Deskripsi gambar pada slide (tipe pengiriman data)
3. Rangkuman tahapan komunikasi menggunakan TCP / three-way handshake

### 2. Jawaban
1. 


---

## D. DAFTAR PUSTAKA

---









