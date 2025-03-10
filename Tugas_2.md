
---

<p align="right">
    SURABAYA <br> 04 DESEMBER 2024
</p> <br>

<h1 align="center"><ins>LAPORAN RESMI</ins></h1>
<h3 align="center"><em>"Tugas 2 Me-Review Materi"</em></h3>
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

# DAFTAR ISI

[DAFTAR ISI........................................i](#daftar-isi)<br>
A. [TUJUAN PEMBELAJARAN............................1](#a-tujuan-pembelajaran)<br>
B. [SOAL...................................1](#b-soal)<br>
C. [HASIL REVIEW..............................1](#c-hasil-review)<br>
1. [Process Control............................1](#1-process-control)<br>
2. [The Filesystem..............................1](#2-the-filesystem)<br>


<p align="center">i</p>

---

## A. TUJUAN PEMBELAJARAN
1. Memahami apa itu proses
2. Memahami bagaimana cara melihat list proses yang berjalan di Linux
3. Memahami cara mematikan proses yang tak diinginkan
4. Memahami penamaan file dalam Linux
5. Memahami struktur file dalam Linux

## B. SOAL
Download / clone / kunjungi materi dari [Materi Linux](https://github.com/ferryastika/unix-and-linux-sysadmin-notes), tak lupa lakukan / setting dulu docker agar bisa mencoba de kemudian lakukan ini :<br>
1. Me-*review* materi *chapter 4: Process Control*
2. Me-*review* materi *chapter 3: The Filesystem* <br>

<p align="center">1</p>

---

## HASIL REVIEW
<br>
**1. Process Control**
### Komponen-komponen dari Proses
Sebuah proses terdiri dari ruang alamat dan satu set struktur data dalam kernel. Ruang alamat adalah satu set halaman memori yang telah ditandai kernel untuk penggunaan proses. (Halaman adalah unit di mana memori dikelola. Mereka biasanya 4KiB atau 8KiB dalam ukuran.) Halaman-halaman ini digunakan untuk memegang kode, data, dan tumpukan proses. Struktur data dalam kernel melacak keadaan proses, prioritasnya, parameter penjadwalannya, dan sebagainya.
<br><br>
Anggap saja proses sebagai wadah untuk seperangkat sumber daya yang dikelola kernel atas nama program yang berjalan. Sumber daya ini termasuk halaman memori yang memegang kode dan data program, deskriptor file yang mengacu pada file yang terbuka, dan berbagai atribut yang menggambarkan keadaan proses.
<br><br>
Struktur data internal kernel mencatat berbagai bagian informasi tentang setiap proses:
- Peta ruang alamat proses
- Status proses saat ini (berlari, tidur, dan sebagainya)
- Prioritas proses
- Informasi tentang sumber daya yang telah digunakan oleh proses (CPU, memori, dan sebagainya)
- Informasi tentang file dan port jaringan proses telah dibuka
- Masker sinyal proses (set sinyal yang saat ini diblokir)
- Pemilik proses (ID pengguna pengguna yang memulai proses)

"Thread" adalah konteks eksekusi dalam suatu proses. Sebuah proses dapat memiliki beberapa threads, yang semuanya berbagi ruang alamat yang sama dan sumber daya lainnya. Thread digunakan untuk mencapai paralelisme dalam suatu proses. Thread juga dikenal sebagai proses ringan karena jauh lebih murah untuk dibuat dan dihancurkan daripada proses.

Sebagai contoh untuk memahami konsep proses dan thread, pertimbangkan web server. Server web mendengarkan koneksi masuk dan kemudian membuat thread baru untuk menangani setiap permintaan yang masuk. Setiap thread menangani satu permintaan pada satu waktu, tetapi server web secara keseluruhan dapat menangani banyak permintaan secara bersamaan karena memiliki banyak thread. Di sini, server web adalah sebuah proses, dan setiap thread adalah konteks eksekusi yang terpisah dalam proses.

#### PID: nomor process ID
Setiap proses diidentifikasi dengan nomor ID proses yang unik, atau PID. PID adalah bilangan termakai yang ditugaskan kernel untuk setiap proses ketika proses dibuat. PID digunakan untuk merujuk pada proses dalam berbagai panggilan sistem, misalnya, untuk mengirim sinyal ke proses.

Konsep proses "namespaces" memungkinkan proses yang berbeda untuk memiliki PID yang sama. Namespace digunakan untuk membuat wadah, yang merupakan lingkungan terisolasi yang memiliki pandangan sendiri tentang sistem. Kontainer digunakan untuk menjalankan beberapa contoh aplikasi pada sistem yang sama, masing-masing di lingkungan yang terisolasi sendiri.

#### PPID: nomor parent process ID
Setiap proses juga terkait dengan proses orang tua, yaitu proses yang menciptakannya. Proses ibu ID nomor, atau PPID, adalah PID dari induk proses. PPID digunakan untuk merujuk pada proses induk dalam berbagai panggilan sistem, misalnya, untuk mengirim sinyal ke proses induk.

#### UID dan EUID: user ID dan effective user ID
User ID, atau UID, adalah ID pengguna pengguna yang memulai proses. ID pengguna yang efektif, atau EUID, adalah ID pengguna yang digunakan proses untuk menentukan sumber daya apa yang dapat diakses oleh proses. EUID digunakan untuk mengontrol akses ke file, port jaringan, dan sumber daya lainnya.

### PS: Pemantauan Proses
Perintah ps adalah alat utama administrator sistem untuk proses pemantauan. Meskipun versi ps berbeda dalam argumen dan tampilan mereka, mereka semua memberikan informasi yang sama pada dasarnya.

'ps' dapat menunjukkan PID, UID, prioritas, dan kontrol terminal proses. Ini juga memberi tahu Anda berapa banyak memori yang digunakan suatu proses, berapa banyak waktu CPU yang telah dikonsumsi, dan apa statusnya saat ini (berjalan, berhenti, tidur, dan sebagainya).

Anda dapat memperoleh gambaran yang berguna tentang sistem dengan menjalankan ps [tambahan kata kunci], yang kurang lebihnya kata kunci tambahan dari perintah ps yang dapat digunakan seperti ini (kata kunci bisa digabung misal aux, dll) : 
| Kata Kunci | Deskripsi |
|------------|-----------|
| l | Menampilkan ps dalam format panjang,memberikan informasi tambahan seperti prioritas proses (PRI) dan nice value (NI) |
| a | Menampilkan all / semua proses dalam komputer bukan hanya user dari terminal tersebut |
| u | Menampilkan detail dalam format user-oriented (menampilkan informasi seperti pemilik proses, CPU usage, dan memory usage) |
| x | Menampilkan proses yang tidak terhubung dengan terminal (misalnya, daemon atau background processes) |
| e | Menampilkan semua proses yang sedang berjalan di sistem |
| f | Format "full listing", memberikan detail tambahan seperti PID, PPID, UID, waktu eksekusi, dan perintah lengkap |
| j | Menampilkan informasi tentang job control, termasuk PGID (Process Group ID) dan SID (Session ID)|
| s | Menampilkan informasi tentang status prosesor (termasuk flag sistem)|
| m | Menampilkan informasi terkait penggunaan memori oleh proses|
| -o [namaKolom1, Kolom2, dst tanpa kurung siku] | Menentukan kolom tertentu yang ingin ditampilkan, seperti PID, PPID, command, CPU usage, dan memory usage|
| --sort=-[namaKolomTanpaKurungSiku] | Mengurutkan proses berdasarkan kolom tertentu, misalnya berdasarkan penggunaan CPU dari yang tertinggi|

Adapun keterangan dari tiap kolom ps adalah :
| Kolom | Deskripsi |
|-------|-----------|
| USER | Nama user dari pemilik proses |
| PID | ID dari proses |
| %CPU | Persentase CPU yang digunakan proses |
| %MEM | Persentase Memori yang digunakan proses |
| VSZ | Bobot virtual dari proses (byte) |
| RSS | Resident set size (nomor halaman dalam memory) |
| TTY | Control terminal ID |
| STAT | Current process status: <br> R = Runnable / Berjalan <br> D = Sleep yang tak bisa dibatalkan <br> S = Sleeping / tertidur (< 20 detik) <br> T = Traced / Berhenti <br> I = Idle / diam <br> Z = Zombie <br> X = Dead / mati <br> tambahan flag : <br> W = Proses bertukar tempat <br> < = Proses lebih tinggi dari prioritas normal <br> N = Proses lebih rendah dari prioritas normal <br> L = Proses sedag menggunakan memory paging <br> s = Proses ialah leader session <br> l = Proses memiliki banyak thread <br> + = Proses berjalan di foreground dalam terminal |

Berikut contoh penggunaan ps :
```bash
zidan@f039c979e5f2:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   4188   568 pts/0    Ss+  Mar02   0:00 /bin/bash
root           7  0.0  0.0   4704  2724 pts/1    Ss   Mar02   0:00 bash
root        5459  0.0  0.0   4140  2520 pts/1    S    01:19   0:00 su - zidan
zidan       5460  0.0  0.0   4188  3428 pts/1    S    01:19   0:00 -bash
zidan       5463  0.0  0.0   8088  4188 pts/1    R+   01:19   0:00 ps aux

zidan@f039c979e5f2:~$ ps lax
F   UID     PID    PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
4     0       1       0  20   0   4188   184 -      Ss+  pts/0      0:00 /bin/bash
4     0       7       0  20   0   4704  2084 -      Ss   pts/1      0:00 bash
4     0    5459       7  20   0   4140  2520 -      S    pts/1      0:00 su - zidan
4  1000    5460    5459  20   0   4188  3428 do_wai S    pts/1      0:00 -bash
0  1000    5465    5460  20   0   8088  4076 -      R+   pts/1      0:00 ps lax
```
*ps lax itu lebih cepat dari ps aux karena ia tak perlu menampilkan nama-nama user & group.
<br><br>

Adapun untuk mencari proses tertentu kita gunakan :

```bash
zidan@f039c979e5f2:~$ ps aux | grep -v grep | grep bash
root           1  0.0  0.0   4188   184 pts/0    Ss+  Mar02   0:00 /bin/bash
root           7  0.0  0.0   4704  2084 pts/1    Ss   Mar02   0:00 bash
zidan       5460  0.0  0.0   4188  3428 pts/1    S    01:19   0:00 -bash
zidan       5467  0.0  0.0   4188  1836 pts/1    D+   22:10   0:00 -bash
zidan       5468  0.0  0.0   4188  1588 pts/1    D+   22:10   0:00 -bash
```
<br>
Untuk mencari PID dari nama proses tertentu kita gunakan :

```bash
zidan@f039c979e5f2:~$ pgrep bash
1
7
5460
```


### Siklus Hidup dari Proses


#### Sinyal
Sinyal adalah cara untuk mengirim pemberitahuan ke suatu proses. Mereka digunakan untuk memberitahukan sebuah proses bahwa peristiwa tertentu telah terjadi.<br>
Sekitar tiga puluh jenis yang berbeda didefinisikan, dan mereka digunakan dalam berbagai cara:
- Mereka dapat dikirim di antara proses sebagai sarana komunikasi.
- Mereka dapat dikirim oleh pengemudi terminal untuk membunuh, mengganggu, atau menangguhkan proses ketika kunci seperti dan ditekan.
- Mereka dapat dikirim oleh administrator (dengan membunuh) untuk mencapai berbagai tujuan.
- Mereka dapat dikirim oleh kernel ketika suatu proses melakukan pelanggaran seperti pembagian dengan nol.
- Mereka dapat dikirim oleh kernel untuk memberi tahu proses kondisi “menarik” seperti kematian proses anak atau ketersediaan data di saluran I / O.

![Signal on Linux]()

Sinyal KILL, INT, TERM, HUP, and QUIT semuanya nampak memiliki makna yang sama, tetapi penggunaannya sebenarnya agak berbeda.
- **KILL** itu tak bisa dibatalkan dan memutus proses pada level kernel. Proses tertentu bisa saja tidak benar-benar mendapatkan atau menangani sinyal ini.
- **INT** itu dikirimkan oleh driver terminal ketika user menekan <Control-C>. Itu adalah permintaan untuk memutus operasi terkini. Program simpel pasti keluar (jika mereka mendapatkan sinyal) atau mudahnya membiarkan dirinya untuk dimusnahkan, yang merupakan default jika sinyal tidak tertangkap. Program yang memiliki garis perintah interaktif (seperti shells) harus menghentikan apa yang mereka lakukan, membersihkan, dan menunggu masukan pengguna lagi.
- **TERM** adalah permintaan untuk mengakhiri eksekusi sepenuhnya. Diharapkan bahwa proses penerimaan akan membersihkan keadaannya dan keluar.
- **HUP** dikirim ke proses ketika terminal pengendali ditutup. Awalnya digunakan untuk menunjukkan "hang up" dari koneksi telepon, sekarang sering digunakan untuk menginstruksikan proses daemon untuk mengakhiri dan memulai kembali, sering untuk mempertimbangkan konfigurasi baru. Perilaku yang tepat tergantung pada proses spesifik yang menerima sinyal HUP.
- **QUIT** mirip dengan TERM, kecuali bahwa itu default untuk memproduksi dump inti jika tidak tertangkap. Beberapa program mengkanibalisasi sinyal ini dan menafsirkannya berarti sesuatu yang lain.


#### kill: mengirim sinyal apa?
Seperti namanya, perintah kill paling sering digunakan untuk mengakhiri suatu proses. **kill** dapat mengirim sinyal apa pun, tetapi secara default mengirimkan TERM. membunuh dapat digunakan oleh pengguna normal pada proses mereka sendiri atau dengan akar pada proses apa pun. Sintaksnya adalah:

di mana sinyal adalah nomor atau nama simbolis dari sinyal yang akan dikirim dan pid adalah nomor identifikasi proses dari proses target.

**kill**' tanpa nomor sinyal tidak menjamin bahwa proses akan mati, karena sinyal JAR dapat ditangkap, diblokir, atau diabaikan. Perintah membunuh -9 pipa dijamin untuk membunuh proses karena sinyal KILL tidak dapat ditangkap, diblokir, atau diabaikan.

killall membunuh proses dengan nama bukan dengan ID proses. Ini tidak tersedia di semua sistem. Contoh:

### Pemantauan Interaktif dengan Perintah "top" 
Perintah 'top' memberikan tampilan real-time yang dinamis dari sistem yang sedang berjalan. Hal ini dapat menampilkan informasi ringkasan sistem serta daftar proses atau thread yang saat ini sedang dikelola oleh kernel Linux. Jenis informasi ringkasan sistem yang ditampilkan dan jenis, pesanan, dan ukuran informasi yang ditampilkan untuk proses adalah semua pengguna yang dapat dikonfigurasi dan konfigurasi itu dapat dibuat terus-menerus di seluruh restart.

Secara default, tampilanya diperbarui setiap 1-2 detik, tergantung pada sistem.

```
zidan@f039c979e5f2:~$ top
top - 00:02:47 up 1 day, 14:27,  0 user,  load average: 1.37, 1.28, 1.18
Tasks:   5 total,   1 running,   4 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  1.0 sy,  0.0 ni, 96.6 id,  0.1 wa,  1.1 hi,  0.1 si,  0.0 st
MiB Mem :   7120.9 total,   1334.4 free,   5305.7 used,    771.4 buff/cache
MiB Swap:  14848.0 total,  13916.0 free,    932.0 used.   1815.2 avail Mem
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0    4188    184    184 S   0.0   0.0   0:00.01 bash
      7 root      20   0    4704   1700   1700 S   0.0   0.0   0:00.11 bash
   5459 root      20   0    4140   2392   2392 S   0.0   0.0   0:00.00 su
   5460 zidan     20   0    4188   2916   2660 S   0.0   0.0   0:00.02 bash
   5475 zidan     20   0    8572   4776   2728 R   0.0   0.1   0:00.00 top
```

Ada juga perintah 'htop', yang merupakan penampil proses interaktif untuk sistem Unix. Ini adalah aplikasi text-mode (untuk terminal konsol atau X) dan membutuhkan rasa sakit. Ini mirip dengan 'top', tetapi memungkinkan Anda untuk menggulir secara vertikal dan horizontal, sehingga Anda dapat melihat semua proses berjalan pada sistem, bersama dengan garis perintah penuh mereka. 'htop' juga memiliki antarmuka pengguna yang lebih baik dan lebih banyak pilihan untuk operasi.

![htop.png]()


### Nice dan renice: mengubah prioritas proses
**Niceness** adalah petunjuk numerik untuk kernel tentang bagaimana proses harus diperlakukan dalam kaitannya dengan proses lain yang bersaing untuk CPU.

**Niceness** yang tinggi berarti prioritas rendah untuk proses Anda. Nilai rendah atau negatif berarti prioritas tinggi.

Kisaran nilai **Niceness** yang diijinkan bervariasi di antara sistem. Di Linux rentangnya adalah -20 hingga +19, dan di FreeBSD itu -20 hingga +20.

Proses prioritas rendah adalah proses yang tidak terlalu penting. Ini akan mendapatkan waktu CPU kurang dari proses prioritas tinggi. Proses prioritas tinggi adalah salah satu yang penting dan harus diberikan lebih banyak waktu CPU daripada proses prioritas rendah.

Misalnya, jika Anda menjalankan pekerjaan intensif CPU yang ingin Anda jalankan di latar belakang, Anda dapat memulainya dengan nilai bagus yang tinggi. Ini akan memungkinkan proses lain berjalan tanpa diperlambat oleh pekerjaan Anda.

Perintah 'nice' digunakan untuk memulai proses dengan nilai 'niceness' yang diberikan. Sintaksnya adalah:
```bash
# Syntax
nice -n nice_val [command]

nice -n 10 sh infinite.sh &
```
Sedangkan 'renice' digunakan untuk mengubah nilai niceness dari proses yang berjalan. Sintaksnya adalah :

### filesystem /proc
Versi Linux dari ps dan top membaca informasi status proses mereka dari direktori /proc, pseudo-filesystem di mana kernel mengekspos berbagai informasi menarik tentang keadaan sistem.

Terlepas dari namanya,/proc berisi informasi lain selain hanya proses (statistik yang dihasilkan oleh sistem, dll).

Proses diwakili oleh direktori di /proc, dan setiap proses memiliki direktori yang dinamai PID-nya. Direktori /proc berisi berbagai file yang memberikan informasi tentang proses, seperti baris perintah, variabel lingkungan, deskriptor file, dan sebagainya.

### Strace dan truss
Untuk mengetahui apa yang dilakukan proses, Anda dapat menggunakan strace pada Linux atau truss pada FreeBSD. Perintah ini melacak panggilan sistem dan sinyal. Mereka dapat digunakan untuk men-debug program atau untuk memahami apa yang dilakukan program.

Misalnya, log berikut dihasilkan oleh strace run yang bebas terhadap salinan aktif top (yang berjalan sebagai PID 5810):


top akan memulai dengan memeriksa waktu saat ini. Kemudian membuka dan menyatakan direktori /proc, dan membaca file /proc/1/stat untuk mendapatkan informasi tentang proses ini.

### Proses Tak Terkontrol
Kadang-kadang sebuah proses akan berhenti menanggapi sistem dan berjalan liar. Proses-proses ini mengabaikan prioritas penjadwalan mereka dan bersikeras mengambil 100% dari CPU. Karena proses lain hanya bisa mendapatkan akses terbatas ke CPU, mesin mulai berjalan sangat lambat. Ini disebut proses pelarian.

Perintah kill dapat digunakan untuk mengakhiri proses tak terkontrol. Jika proses tidak menanggapi sinyal TERM, Anda dapat menggunakan sinyal KILL untuk mengakhirinya.

```bash
kill -9 pid

or

kill -KILL pid
```
Kita dapat menyelidiki penyebab proses pelarian dengan menggunakan strace atau truss. Proses pelarian yang menghasilkan output dapat mengisi seluruh sistem file.

Anda dapat menjalankan df -h untuk memeriksa penggunaan sistem file. Jika filesystem penuh, Anda dapat menggunakan perintah du untuk menemukan file dan direktori terbesar.

Anda juga dapat menggunakan perintah lsof untuk mengetahui file mana yang terbuka oleh proses tak terkontrol.

```bash
lsof -p pid
# Contoh
```

### Proses Periodik
#### cron: perintah penjadwal
Perintah cron (crond di distro redhad) adalah alat tradisional untuk menjalankan perintah pada jadwal yang telah ditentukan. Ini dimulai ketika sistem boot dan berjalan selama sistem naik.

Cron membaca file konfigurasi yang berisi daftar baris perintah dan waktu di mana mereka harus dipanggil. Garis perintah dieksekusi oleh sh, jadi hampir semua yang dapat Anda lakukan dengan tangan dari shell juga dapat dilakukan dengan cron.

Sebuah file konfigurasi cron disebut "crobtab," singkatan untuk "tabel cron." Cronta untuk pengguna individu disimpan di bawah /var/spool/cron (Linux) atau /var/cron/tabs (FreeBSD).

#### format crontab
File crontab memiliki lima bagian tersendiri, jika dirunut dari kiri ke kanan maka angka yang diinputkan adalah menit, jam, tanggal hari, bulan, hari dalam mingguan,  dan diikuti oleh perintah yang akan dijalankan pada rentang waktu tersebut.
Contoh :
```bash
*     *     *     *     *  command to be executed
-     -     -     -     -
|     |     |     |     |
|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
|     |     |     +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
```
Beberapa contoh:


#### Systemd timer
Timer systemd adalah file konfigurasi unit yang namanya berakhir di direktori .timer . timer sistemd dapat digunakan sebagai alternatif untuk pekerjaan cron. Mereka lebih fleksibel dan lebih kuat dari pekerjaan cron.

Sebuah unit timer diaktifkan oleh unit layanan yang sesuai. Unit layanan dipicu oleh unit timer pada waktu yang ditentukan dalam unit timer. Unit timer juga dapat diaktifkan oleh boot sistem atau oleh suatu peristiwa.

Perintah sistem digunakan untuk mengelola unit sistem. Opsi list-timer digunakan untuk daftar timer aktif.
Dalam contoh di atas, unit logrotate.timer dijadwalkan untuk mengaktifkan unit logrotate.service pada tengah malam setiap hari.

Inilah yang tampak seperti unit logrotate.timer:

#### Penggunaan umum dari perintah terjadwal
- **Mengirim pesan**
```bash
zidan@f039c979e5f2:~$ echo "Selamat pagi! Jangan lupa sarapan." | sudo wall
zidan@f039c979e5f2:~$ crontab -e
crontab: installing new crontab

```
- **Membersihkan filesystem**
Menghapus file di /tmp yang lebih lama dari 7 hari setiap malam pukul 23:00:
```bash
0 23 * * * find /tmp -type f -mtime +7 -exec rm -f {} \;

```

**Memutar file log**

**Menjalankan kumpulan jobs**
**Backing up dan mirroring**


2. The Filesystem
### Pathnames
### Filesystem Mounting dan Unmounting

### Pengorganisasian dari silsilah file
### Tipe file
### Atribut file


### Access Control List
**Implementasi ACLs**<br>
**POSIX ACLs**<br>
**NFSv4 ACLs**<br>



<p align="center">2</p>

---

