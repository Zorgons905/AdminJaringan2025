

---

<p align="right">
    SURABAYA <br> 02 JUNI 2025
</p><br>
<h1 align="center"><ins>LAPORAN PRAKTIKUM</ins></h1>
<h3 align="center"><em>"Projek 2"</em></h3>
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
</p><br>

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
1. Menjelaskan cara kerja docker
2. Mengubah data axon dari file drive menjadi file image dan meng-container-isasikannya
3. Menghubungkan Power BI dengan Container docker yang dinyalakan



---

# B. DASAR TEORI

PENGENALAN SINGKAT DOCKER

Docker pertama kali dikembangkan oleh Solomon Hykes sebagai bagian dari proyek internal di perusahaan dotCloud (platform-as-a-service). Proyek ini diumumkan secara resmi pada Maret 2013 dalam konferensi Python di Amerika Serikat (PyCon).

Beberapa tonggak penting:
2013: Docker dirilis sebagai open source. Awalnya menggunakan teknologi LXC (Linux Containers).
2014: Docker menjadi perusahaan independen dan mulai menarik perhatian besar dari komunitas open source dan perusahaan besar.
2015–2017: Docker menggantikan LXC dengan pustaka container-nya sendiri bernama libcontainer.
2020: Docker Inc. memfokuskan diri pada alat pengembang (developer tools) dan menyerahkan Docker Enterprise ke Mirantis.

Hubungan antara Image dan Container

Apa itu Docker Image?
Image adalah template read-only (hanya-baca) yang berisi semua hal yang dibutuhkan untuk menjalankan sebuah aplikasi: kode program, runtime, library, variabel lingkungan, dan konfigurasi lainnya.
Sederhananya: seperti file ISO dari sistem operasi.

Apa itu Docker Container?
Container adalah instance (salinan aktif) dari image yang sedang berjalan. Saat kamu menjalankan sebuah image, maka akan dibuat container.
Container bersifat dapat ditulis (writable layer) di atas image yang read-only.

Hubungan:
1 image bisa digunakan untuk membuat banyak container.
Container bisa berjalan, dimodifikasi, dihentikan, lalu dihapus — tapi image-nya tetap tidak berubah. Image itu masih tersimpan pada library. jadi bisa dipakai oleh container lain tak perlu mengunduh ulang

Analogi sederhananya, bayangkan jika
Image = File master installer aplikasi/game (misalnya installer Microsoft Word atau file ISO Ubuntu). Sedangkan Container = Aplikasi/game yang sedang kamu jalankan di komputermu.

---

# C. PERINTAH
Buat dan susun sistem BI untuk penjualan mobil dengan database server ( container) dan Power BI (desktop). 
Data dan ppt dapat anad unduh di https://drive.google.com/drive/folders/10THmB2YZAILg9gXHg42UkIYqd6AKsiRc?usp=sharing





---

# D. PERCOBAAN
## 1. Instalasi Sumber Daya yang Dibutuhkan
Sebelum kita mulai alangkah lebih baiknya kita dengan mengunduh data dari [Link Admin Jaringan Tugas Axon](https://drive.google.com/drive/folders/10THmB2YZAILg9gXHg42UkIYqd6AKsiRc?usp=sharing). Kemudian tak lupa yang kita perlukan adalah mengunduh :
- PowerBI (hanya untuk windows)
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/0a.png)
- MySQL Connector
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/0b.png)
- Docker
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/2.png)
- File Axon ... sql yang ada dalam drive tercantum (yang berisi kode membuat isian table bukan yang ta)


## 2. Mebuat Container dari File Image MySQL
- Pertama kita harus membuat terlebih dahulu suatu folder yang nantinya akan kita beri isian file **dockerfile.yaml**
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/1.png)
- Kedua kita buat file kosongan **dockerfile.yaml** dengan nano pada command line atau bisa juga dengan vs code atau notepad biasa dan nantinya diberi nama yang sama.
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/4.png)
- Kita beri isian filenya seperti ini, safe dan keluar.
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/3.png)
  Isi dari file tadi adalah perintah/format untuk membuat container pada port tertentu. yang mana bisa kita pecah dan jelaskan menjadi seperti ini :
  - version : versi dari docker yang kita pakai
  - services : jenis image yang kita simpan
      - image : tipe / nama sistem yang ingin kita bungkus
      - container_name : nama container yang kita mau
      - restart : kondisi ketika container berjalan apakah selalu restart, bisa always no, dll.
      - environment : berisi kumpulan data penting yang nantinya digunakan untuk mengakses image.
      - volumes : berisi path dimana ia akan disimpan di dalam containernya
      - ports : angka port yang dituju guna pengiriman dan penerimaan container

- Kemudian kita jalankan perintah ini untuk mengeksekusinya
  ```bash
  docker compose -f "docker-compose.yaml" up -d --build
  ```
  Gunanya untuk menjalankan dan membuat container yang siap untuk dijalankan tadi,
  -f artinya filename
  up artinya menyalakan
  -d artinya service di background
  --build gunanya untuk membuat container
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/5.png)

- Tak lupa kita cek isian dari list container yang ada, apakah sudah muncul
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/7.png)

- Tak lupa kita ambil data dari hasil unduhan tadi dan kita salin (di sini saya mengambilnya dari folder download dan memindahkannya ke folder tempat saya melakukan command), baru kemudian kita gunakan docker copy untuk mencopy data itu ke container yang sudah kita buat.
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/6.png)
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/9.png)

- Baru kita jalankan containernya
    ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/8.png)
  -it artinya interactive terminal
  -u artinya username
  -p... (password yang dimasukkan kedalam file yaml) artinya password akan otomatis terinput
    ketiganya akan dicek dan diberikan ke dalam terminal agar user sekali input saja tidak perlu mengetik lama tiap ada inputan

- Lanjut kita amati isi dari mysql ini, perintahnya sama saja sewaktu mengakses query di cli atau gui nya. Yang berbeda mungkin kita wajib menambahkan ";" agar kode berjalan.
  untuk melihat list database
    ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/10.png)
- Tak lupa kita beri isian databasenya dengan menggunakan file yang tadi kita masukkan/salin ke container
    ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/11.png)
- untuk melihat list tables gunakan perintah ini, use untuk masuk ke database dan show untuk menampilkan list.
    ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/12.png)
- Inilah hasil akhirnya :
    ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/13.png)
  

## 3. Menghubungkan Container MySQL ke PowerBI
- Pertama kita buka powerBI dan buat design baru, pilih akses data dari sql
- Masukkan server dan port number yang sudah dibuat di container tadi
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/15.png)
- lanjut kita masukkan username & password
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/14.png)
- Sejujurnya saya tidak bisa terhubung dengan MySQLnya entah karena device atau apa, setiap kali ingin terhubung selalu koneksinya terputus ataupun entah tidak berjalan. adapun setelah saya lihat connectornya juga 32 bit sedangkan power bi 64 bit.
- Namun yang pasti hasilnya jikalau berhasil anda bisa membuat desain dengan data yang berasal dari database yang kita koneksikan. Semacam file pbix (format file power bi) ini, -> didapat dari google drive
  ![](https://github.com/Zorgons905/AdminJaringan2025/blob/main/Gambar6/16.png)

---

# DAFTAR PUSTAKA
1. Hykes, S. (2013). The Future of Linux Containers. PyCon US 2013.
Video Presentasi

2. Docker Inc. (2024). What is a Container?
https://www.docker.com/resources/what-container/

3. Turnbull, J. (2014). The Docker Book: Containerization is the new virtualization. James Turnbull.

4. IBM Cloud Docs (2023). Docker images and containers.
https://cloud.ibm.com/docs/containers?topic=containers-docker

5. Mirantis. (2020). Docker Enterprise acquisition by Mirantis.
https://www.mirantis.com/company/press-center/mirantis-acquires-docker-enterprise-platform/

---
