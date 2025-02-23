
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

## A. TUJUAN PEMBELAJARAN
1. Memahami bagaimana cara menjalankan wireshark
2. Memahami bagian-bagian dari datagram yang ada pada wireshark
3. Memahami layer OSI dalam internet secara mendalam
4. Memahami apa itu HTTP
5. Memahami apa itu tipe pengiriman data
6. Memahami apa itu three-way handshake

## B. DASAR TEORI
1. Mengenal Wireshark
<p>
&emsp;Wireshark adalah aplikasi untuk menampilkan hasil jejak rute / tracing route packet data dari router terdekat yang lalu ditangkap oleh komputer kita. Hasilnya lalu ditampilkan dalam rupa tabel berisi keterangan tertentu seperti no.packet, time / waktu respon packet, alamat source / sumber dan destination / destinasi packet, protocol yang digunakan, length / panjang data yang diterima maupun dikirim, dan info notifikasi dari program jaringan yang sedang kita jalankan maupun balasan dari destinasinya.<br>
<br>
Pada Wireshark terdapat beberapa tampilan dan istilah yang perlu diketahui :
</p>
<p align="center">
    <img src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/KenalWireshark.png"><br>
</p>

2. Mengenal Layer OSI
<p>
&emsp;OSI (Open Systems Interconnection) Model adalah kerangka jaringan yang dibuat oleh International Organization for Standardization (ISO, <sub>*bukan singkatan melainkan bahasa yunani artinya “sama”)</sub> pada tahun 1984. Model ini digunakan untuk memahami dan mengimplementasikan komunikasi dalam jaringan komputer. Adapun ISO bekerja sama dengan institusi lain guna menyatukan pemahaman terkait protokol atau aturan dalam pembuatan jaringan komputer ini. Di antara institusi tersebut adalah DARPA, IEEE, IETF, dll.
<br><br>
Layer 1 : Physical layer<br>
&emsp;Adalah layer yang mengatur bagaimana data akan tersampaikan. Data elektronik dapat pertama-tama diubah menjadi bit data di dalam memori lalu disalurkan melalui bisa saja ethernet card maupun wifi, bila melalui ethernet maka data akan diubah menjadi sinyal listrik (gelombang sin) dan bila melalui wifi akan diubah menjadi gelombang elektromagnetik (gelombang radio) sedangkan bila kita mengirim data ke internet dengan kabel optik maka ia akan diubah menjadi sinyal cahaya.
<br><br>

---

Layer 2 : Datalink layer<br>
&emsp;Adalah layer yang berfungsi untuk transmisi data antar perangkat, berisi alamat mac dari komputer maupun router (ibarat seperti alamat rumah sumber dan tujuan pembeli dan penjual olshop). Sehingga mampu menghubungkan device ke server maupun ke device lain, karena mempunyai alamat sumber / source dan tujuan / destination. Contoh protocolnya adalah ARP, ATM, CDP, dll. Ditandai dengan rentetan angka heksadesimal (mac addressnya) sebesar 6 byte/48 bit.<br>
Contoh : 84-07-fb-2d-09-e8
<br><br>
Layer 3 : Network layer<br>
&emsp;Adalah layer yang berfungsi untuk menangani alamat logis dan pengiriman paket data antar jaringan (ibarat seperti no.seri/user yang diberikan oleh olshop untuk membedakan mana penjual dan pembeli). Yang paling terkenal dari Network layer adalah IP(versinya ada 2 yakni IPv4 dan IPv6) atau internet protocol ada juga protocol lain, seperti ICMP (ping request), RIP, IPsec, dll.<br>
IPv4 sendiri IP yang berbentuk desimal yang diberikan router pada device yang tersambung. Panjangnya 4 byte/32bit. Size header / tambahan file yang diberikan pada file masuk maupun keluar adalah 20-60 bytes. Jenis ip ini sering digunakan, sedangkan untuk IPv6 masih belum masif penggunaannya.<br>
Contoh&emsp;: 192.168.1.1&emsp;&emsp;&emsp;&emsp;&emsp;IPv4<br>
&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;2001:0db8:85a3::7334&emsp;&emsp;IPv6
<br><br>
Layer 4 : Transport layer<br>
&emsp;Adalah layer yang menampilkan informasi mengenai bagaimana data ditransfer di aplikasi seperti no.port dan status koneksi dalam bentuk pemecahan data menjadi beberapa segmen dan nantinya di reassembly (ibarat kurir yang membawa paket bisa dalam bentuk paket terpisah maupun satu paket besar). Contoh protocolnya adalah TCP, dan UDP.<br>
Misalnya untuk TCP, hardware akan mengirimkan handshake / perkenalan kepada perangkat tertaut. Misal untuk wifi ke laptop. Maka akan terjadi 3 handshake berupa :
</p>

- Laptop mengirim handshake `[SYN]` kepada wifi untuk mennyinkronisasi dengan wifi,
- Lalu wifi mengirim handshake `[SYN,ACK]` untuk menyetujui laptop, 
- Laptop lalu memberitahu ke wifi bahwa persetujuan diterima dengan handshake `[ACK]`.

<p>
Sedangkan untuk UDP digunakan untuk broadcasting, biasanya dalam penampilan video online UDP digunakan tanpa kita harus mendownload semua data dan menyimpannya ke dalam device kita. UDP bekerja tanpa adanya handshake dan semua device bisa mengakses data tersebut asalkan sudah mendapat izin dari layer sebelumnya.
<br><br>

---

Layer 5 : Session layer <br>
&emsp;Adalah layer yang menjaga data agar aman dan sampai pada tujuan tanpa adanya data yang bocor atau masuk ke dalam perangkat lain di jaringan yang sama. Session sangat terikat dengan presentation layer dan application layer (ibarat kemasan dari paket olshop orang lain tidak boleh membukanya karena bukan miliknya dan alamat maupun data user yang berbeda). Ia bertugas untuk membuka, memelihara dan menutup sesi komunikasi antar dua aplikasi. Contoh protocolnya adalah NFS, RPC, SQL, SMB, CIFS dll.<br>
Misalnya kita mengakses sebuah browser maka sesuai dengan OS yang digunakan maka akan dilakukan pembukaan sesi dengan router ataupun device lain (untuk Windows menggunakan SMB untuk browsing). Jadi jika ada file yang terbagikan oleh device / router lain. Device lain tidak akan bisa menginterupsi dan menggagalkan file sharing tersebut atau bahkan mengambil data dari pengunduhan file tersebut.
<br><br>
Layer 6 : Presentation layer<br>
&emsp;Adalah layer yang menangani format data, enkripsi, dekripsi, dan kompresi serta menyiapkan data untuk aplikasi. Adapun untuk presentation layer ibarat isi dari paket yang kita pesan, ia tergolong apa, apakah gambar, puzel, instrument, ataukah alat lain. 
Yang pasti presentation layer berguna untuk menjaga data agar tidak diedit dan bisa diretas di internet. Contoh protocolnya adalah JPEG, SSL (encrypted data), MIDI, 
<br><br>
Layer 7 : Application layer<br>
&emsp;Adalah layer untuk menangani interaksi antara aplikasi pengguna dan jaringan. Protokolnya seperti HTTP, HTTPs, FTP, SMTP, dll.<br>
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
1. Pertama kita download dulu file dari https://wiki.wireshark.org/SampleCaptures, lalu kita buka isi file png tersebut menggunakan wireshark. Berikut adalah gambarnya :<br>
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram.png">
</p>
<br>
Tampak pada gambar terdapat runtutan proses yang terjadi antara client (komputer/laptop user) dengan server. Adapun yang sedang terjadi pada gambar tersebut seccara ringkas adalah user sedang meminta server untuk mengirimkan data file yang diminta user (proses download), di tengah proses download itu juga muncul pop up iklan yang kemudian dihilangkan oleh server itu sendiri / automated ads. Kemudian sewaktu pendownloadan terjadi tetiba sinyal paket ada yang terduplikasi biasanya hal tersebut terjadi karena kebocoran sinyal data sehingga data kembali dikirimkan padahal sudah ada. Dan terakhir pada packet details/datagram paling bawah terjadi pemutusan koneksi dengan server.

Di sisi lain mari menjawab pertanyaan yang diajukan berdasarkan materi wireshark yang sudah kita pelajari pada dasar teori :
- Versi HTTP yang digunakan,
  - Jika kita melihat pada waktu client mengirim perintah GET request maka akan dapat kita lihat pada datagramnya terdapat keterangan HTTP 1.1 sehingga itulah versi dari HTTP yang dimiliki.
<br>
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram4.png">
</p>

- IP address dari client maupun server,
  - Pertama dapat kita lihat sewaktu kita melakukan SYNCHRONIZATION dapat kita lihat ip source dan destination Nampak pada src dan dst pada datagram tertera bahwa ip source / ip client adalah 145.254.160.137 sedangkan pada ip destination / ip server adalah 65.208.228.223
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram.png">
</p>
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram2.png">
</p>
Sedangkan pada waktu muncul popup iklan ia memiliki ip yang berbeda 145.254.160.137 (milik client) dan 145.253.160.237(milik server ads)
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram6.png">
</p>
  
- Waktu dari client mengirimkan HTTP request,
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Datagram12.png">
</p>

Penjelasan :
Dapat dilihat pada tab time, nampak 0.911310 yang berarti client mengirimkan perintah itu pada waktu **0.911310 sekon** setelah membuat sinkronisasi dengan server

- Waktu server menerima HTTP request dari client
Penjelasan :
Dapat dilihat dalam tabel di atas nampak respon HTTP 200 OK terjadi pada waktu **4.846969 sekon** setelah dialog SYN dikirim. 

- Waktu yang dibutuhkan untuk transfer dan response dari client ke server
Penjelasan : 
Sehingga jika kita hitung perbedaan atau selisih dari waktu pengiriman adalah 4.846969 - 0.911310 = **3.935659 sekon.**

2. Berikut adalah gambar dari slide 23.1
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Tipe.png">
</p>
Penjelasan :
Pada pengiriman data akan ada perantara / komunikasi yang terjadi antara dua buah entitas entah itu antar device maupun antar proses. Nampak pada gambar tersebut terdapat 
- Node to Node : Data Link layer 
> yakni interaksi antara router dengan router yang menghantarkan paket data yang terkirim, adapun mereka (para router) akan berkenalan dengan router tetangga yang terdekat hingga paket sampai pada device tujuan. Dan interaksi ini diatur oleh protocol pada data link layer atau MAC address.

- Host to Host : Network Layer
> yakni interaksi antara host / pc / server / end device yang saling berkomunikasi. Host to host terjadi jika kedua device berada pada jaringan yang berbeda, sehingga memerlukan data berupa mac address dari device yang ingin terhubung. Adapun protokol yang bekerja pada pengiriman ini adalah network layer atau TCP
 
- Process to process : Transport layer
> yakni interaksi antara proses yang ada pada end device. Process to process terjadi ketika end device mengakses internet (artinya sebelumnya sudah ada router yang saling terkoneksi di radius, dan juga sudah ada koneksi ip yang terjalin antara 2 buah device yang berbeda jaringan). Protocol yang berlaku adalah transport layer karena port dari receiver dan sender akan berbeda tergantung proses apa yang terjadi.

3. Berikut adalah penjelasan mengenai tahapan komunikasi TCP / three-way handshake
Pada TCP terdapat aturan three way handshake yakni aturan untuk memulai suatu koneksi, menghantarkan data dan juga memutuskan koneksi.
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Establish.png">
</p>
Penjelasan :
Pada waktu memulai koneksi atau connection establisment akan dimulai dengan pengiriman dialog SYN dari client menuju server, kemudian server akan mengirimkan dialog SYN ACK yang berarti Synchronize dan Acknowledge yang berarti server juga meng-sinkronisasi / menghubungkan dengan client dan kemudian memberi dialog ACK atau acknowledge yakni mengetahui permintaan koneksi client. Kemudian client akan mengirimkan dialog ACK yang membalas permintaan koneksi dari server.
- Client minta koneksi (SYN) ke Server --> disebut juga active open, karena yang memulai client
- Server meminta koneksi, membalas client (SYN-ACK) --> disebut juga passive open, karena yang memulai adalah server langsung
- Client membalas server (ACK)
- Koneksi client dan server terhubung

<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Data-Transfer.png">
</p>
Penjelasan :
Pada waktu mengirim data atau data transfer terjadi juga perintah / dialog antar client dan server. Dialog dimulai dengan siapa yang memulai. Misal untuk http get request maka yang memberikan data adalah server sedangkan jika http post request maka yang memberikan data adalah client. Jadi jika "get" maka receivernya adalah client dan sendernya adalah server. Sedangkan untuk "post" sendernya adalah client dan receivernya adalah server. 

Data transfer dimulai dengan peristiwa berikut :

- Sender mengirimkan dialog ACK yang artinya ia siap mengirimkan data adapun ia berisi angka random, sedangkan untuk seq atau sequence adalah angka yang menunjukan mula mula/ permulaan jumlah data yang terkirim selalu dimulai dengan angka 1, 
misal biasanya akan ada dialog seperti ini :

    - **seq = 1, Ack = 80, dan len = 0** ➡ artinya data dimulai terkirim dari urutan ke 1, dengan nilai Ack random = 80 dan besaran file yang terkirim dimulai dari 0 (gunanya untuk mengecek apakah server merespon atau tidak / tes ombak, maka sender akan mengirimkan lanjutan perintah pengiriman paket data)
    - **seq = 1, Ack = 80, dan len = 1380** ➡ artinya data dimulai dari urutan ke 1, dengan nilai ack random, dan besaran data yang terkirim bernilai 1380 bytes.

- Receiver akan memberikan balasan kepada sender dengan format seq yang berisi nilai ack dari pengiriman paket yang diberikan oler server
Misal setelah tadi sender mengirimkan data maka receiver akan membalas :
    - **seq = 80, Ack = 1381, dan len = 0** ➡ artinya nilai ack dari sender dipindah ke seq, receiver mengharapkan data pada urutan ke 1381, karena data yang ia terima sebesar 1380 bytes.

- Begitu seterusnya hingga data habis. Adapun ketika data yang dikirimkan di komputer masih diproses misa thresholdnya 4140 bytes maka server akan mengirim balasan PSH, ACK. yang artinya data masih didorong dan sender akan mengirimkan data lagi.

<br>
<p align="center">
    <img  src="https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar/Terminate.png">
</p><br><br>
Penjelasan : 
Pada waktu memutus koneksi atau connection termination akan dimulai dengan pengiriman dialog FIN / finish dari client menuju server, kemudian server akan mengirimkan dialog FIN ACK yang berarti Finish dan Acknowledge yang berarti server juga mengakhiri / memutuskan dengan client dan kemudian memberi dialog ACK atau acknowledge yakni mengetahui permintaan koneksi client. Kemudian client akan mengirimkan dialog ACK yang membalas permintaan pemutusan koneksi dari server.
- Client minta memutus koneksi (FIN) ke Server --> disebut juga active close, karena yang memulai client
- Server menerima memutus koneksi, membalas client (FIN-ACK) --> disebut juga passive close, karena yang memulai adalah server langsung
- Client membalas server (ACK)
- Koneksi client dan server terputus








