
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
Bapak Dr Ferry Astika Saputra ST, M.Sc <br><br>
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
A. Instalasi NTP Client 
  1. Install dan konfigurasi NTP client agar host anda mempunyai Waktu yang sinkron dengan NTP server di Indonesia.
  2. Nama NTP server yang harus dirujuk adalah ntp server Indonesia Referensi :
    - https://www.server-world.info/en/note?os=Debian_12&p=ntp&f=1
    - https://www.ntppool.org/en/zone/id Package terkait : ntp ntpssec

B. Instalasi dan konfigurasi Samba
  1. Membuat public shared folder . Folder tersebut harus bisa diakses melalui Windows Client dan Linux Client via file manager
  2. Membuat limited shared Folder.
  3. Akses ke folder Share dari CLI client Referensi :
     - https://www.server-world.info/en/note?os=Debian_12&p=samba&f=1
     - Package terkait : samba, smbclient, cifs-tools

C. Buat rangkuman tentang package management. 
  - Bahan ada di Materi ethol debian 12 sysadmin) Di tiap nomor buat langkah-langkah instalasi, konfigurasi dan hasil (ouput) dari perintah-perintah terkait yang memastikan layanan  dapat digunakan dengan baik 

<p align="center">1</p>

---

### A. Instalasi NTP Client
1. Kita instal terlebih dulu dengan menggunakan perintah ini di debian linux :
   ```bash
   zidan-3123600013:~$ sudo apt update                -->untuk mengupdate jikalau ada pembaruan di linux
   zidan-3123600013:~$ sudo apt install ntp -y        -->untuk menginstall ntp

   # bisa juga menggunakan ntpsec
   zidan-3123600013:~$ sudo apt install ntpsec -y     -->untuk menginstall ntpsec
   ```
2. Konfigurasi ntp
   ```bash
   # pertama kita ubah dulu server yang dipantau oleh ntp
   zidan-3123600013:~$ sudo nano /etc/ntp.conf

   # atau /etc/ntpsec/ntp.conf jika menggunakan ntpsec
   zidan-3123600013:~$ sudo nano /etc/ntpsec/ntp.conf
   ```
   kemudian kita tambahkan server yang kita mau, kali ini di indonesia maka kita tambahkan ini :
   --Gambar--
   Jika sudah disimpan dan jalankan perintah ini :
   ```bash
   zidan-3123600013:~$ sudo systemctl restart ntp
   zidan-3123600013:~$ sudo systemctl enable ntp
   zidan-3123600013:~$ sudo systemctl status ntp
    ntpsec.service - Network Time Service
 	Loaded: loaded (/lib/systemd/system/ntpsec.service; enabled; preset: enabled)
 	Active: active (running) since Mon 2025-03-10 18:21:29 WIB; 10h ago
   	Docs: man:ntpd(8)
	Process: 4629 ExecStart=/usr/libexec/ntpsec/ntp-systemd-wrapper (code=exited, status=0/SUCCESS)
   Main PID: 4632 (ntpd)
  	Tasks: 1 (limit: 2293)
 	Memory: 10.6M
    	CPU: 42ms
 	CGroup: /system.slice/ntpsec.service
         	└─4632 /usr/sbin/ntpd -p /run/ntpd.pid -c /etc/ntpsec/ntp.conf -g -N -u ntpsec:ntpsec
   Mar 10 18:21:34 vbox ntpd[4632]: DNS: dns_probe: 2.id.pool.ntp.org, cast_flags:1, flags:20901
   Mar 10 18:21:34 vbox ntpd[4632]: DNS: dns_check: processing 2.id.pool.ntp.org, 1, 20901
   Mar 10 18:21:34 vbox ntpd[4632]: DNS: Server taking: 116.12.47.30
   Mar 10 18:21:34 vbox ntpd[4632]: DNS: dns_take_status: 2.id.pool.ntp.org=>good, 0
   Mar 10 18:21:35 vbox ntpd[4632]: DNS: dns_probe: 1.id.pool.ntp.org, cast_flags:1, flags:20901
   Mar 10 18:21:35 vbox ntpd[4632]: DNS: dns_check: processing 1.id.pool.ntp.org, 1, 20901
   Mar 10 18:21:35 vbox ntpd[4632]: DNS: Server taking: 202.65.114.202
   Mar 10 18:21:35 vbox ntpd[4632]: DNS: dns_take_status: 1.id.pool.ntp.org=>good, 0
   Mar 11 04:32:50 vbox ntpd[4632]: CLOCK: time stepped by 36669.858416
   Mar 11 04:32:50 vbox ntpd[4632]: INIT: MRU 10922 entries, 13 hash bits, 65536 bytes
~

   ```
   

---

### B. Instalasi dan Konfigurasi Samba


---

### C. Rangkuman Debian 12 Sysadmin (Package Management)

---
