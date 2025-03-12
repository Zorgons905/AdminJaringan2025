
---

<p align="right">
    SURABAYA <br> 04 DESEMBER 2024
</p> <br>

<h1 align="center"><ins>LAPORAN RESMI</ins></h1>
<h3 align="center"><em>"Tugas 3 Mereview Materi Praktikum"</em></h3>
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
   kemudian kita tambahkan server yang kita mau, kali ini di indonesia maka scroll hingga menemukan ini dan kita tambahkan ini :
   # pool 2.debian.pool.ntp.org iburst
   # pool 3.debian.pool.ntp.org iburst
   ...
   server 0.id.pool.ntp.org iburst
   server 1.id.pool.ntp.org iburst
   server 2.id.pool.ntp.org iburst
   server 3.id.pool.ntp.org iburst
   ... 
   # Access control configuration; see /usr/share/doc/ntpsec-doc/html/accopt.html
   # for details.

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
   
   Sehingga bila kita ketik perintah ini maka akan nampak server indonesia yang ada di sekitar kita dan tersinkronisasi
   ```bash
   zidan-3123600013@vbox:~$ ntpq -p
 	remote                              	refid  	st t when poll reach   delay   offset   jitter
   ======================================================================================================
   ns1.ads.net.id                     	.STEP.      	16 u	-   64	0   0.0000   0.0000   0.0001
   ns3.ads.net.id                     	.STEP.      	16 u	-   64	0   0.0000   0.0000   0.0001
   27.54.117.72                       	.STEP.      	16 u	-   64	0   0.0000   0.0000   0.0001
   2.ntp.maxindo.net.id               	.STEP.      	16 u	-   64	0   0.0000   0.0000   0.0001
   ```

---

### B. Instalasi dan Konfigurasi Samba
1. Install Paket Samba
   lakukan perintah ini agar menginstall samba :
   ```bash
   zidan-3123600013@vbox:~$ sudo apt update
   zidan-3123600013@vbox:~$ sudo apt install samba smbclient cifs-utils -y
   ```
2. Buat public shared folder / directory
   Pertama-tama kita buat folder terlebih dahulu di dalam direktori /srv/samba/ (nama folder/direktorinya terserah). Folder ini nantinya akan digunakan untuk mneruh file yang kita share/bagikan.
   ```bash
   zidan-3123600013@vbox:~$ sudo mkdir -p /srv/samba/public
   zidan-3123600013@vbox:~$ sudo chmod 777 /srv/samba/public
   zidan-3123600013@vbox:~$ sudo chown nobody:nogroup /srv/samba/public
   ```
   
   Kemudian edit file berikut dan ikuti perintah ini :
   ```bash
   zidan-3123600013@vbox:~$ sudo nano /etc/samba/smb.conf
   ```

   lalu tambahkan ini pada bagian terakhir (di situ public adalah nama folder yang nantinya akan tertera pada saat kita menampilkannya di client):
   ```bash
   ....
   [Public]
   path = /srv/samba/public
   browseable = yes
   writable = yes
   guest ok = yes
   create mask = 0777
   directory mask = 0777
   ```

   Kemudian simpan dan restart ulang smb/samba nya, serta cek statusnya :
   ```bash
   zidan-3123600013@vbox:~$ sudo systemctl restart smb
   zidan-3123600013@vbox:~$ sudo systemctl status smb
   [sudo] password for zidan-3123600013:
   ● smbd.service - Samba SMB Daemon
 	Loaded: loaded (/lib/systemd/system/smbd.service; enabled; preset: enabled)
 	Active: active (running) since Tue 2025-03-11 20:07:14 WIB; 1h 14min ago
   	Docs: man:smbd(8)
         	man:samba(7)
         	man:smb.conf(5)
	Process: 10820 ExecCondition=/usr/share/samba/is-configured smb (code=exited, status=0/SUCCESS)
	Process: 10823 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 10833 (smbd)
 	Status: "smbd: ready to serve connections..."
  	Tasks: 5 (limit: 2293)
 	Memory: 35.9M
    	CPU: 672ms
 	CGroup: /system.slice/smbd.service
         	├─10833 /usr/sbin/smbd --foreground --no-process-group
         	├─10835 /usr/sbin/smbd --foreground --no-process-group
         	├─10836 /usr/sbin/smbd --foreground --no-process-group
         	├─11200 /usr/sbin/smbd --foreground --no-process-group
         	└─11218 /usr/sbin/smbd --foreground --no-process-group
   Mar 11 20:07:14 vbox systemd[1]: Starting smbd.service - Samba SMB Daemon...
   Mar 11 20:07:14 vbox systemd[1]: Started smbd.service - Samba SMB Daemon.
   Mar 11 20:11:52 vbox smbd[10949]: pam_unix(samba:session): session closed for user nobody
   Mar 11 20:24:00 vbox smbd[11218]: pam_unix(samba:session): session opened for user smbuser(uid=1001) by (uid=0)
   ```
   
4. Buat limited shared folder / directory
   Pertama-tama kita buat folder juga sama seperti public shared folder tadi, bedanya ada pada bagaimana folder tersebut diakses / permission-nya,
   ```bash
   zidan-3123600013@vbox:~$ sudo mkdir -p /srv/samba/limited
   zidan-3123600013@vbox:~$ sudo chmod 770 /srv/samba/limited
   zidan-3123600013@vbox:~$ sudo chown nobody:sambashare /srv/samba/limited
   ```

   Tak lupa juga kita buat user baru yang hanya bisa diakses client dan juga kita buat user itu memiliki group agar server juga bisa mengisi/membuat file di dalamnya :
   ```bash
   zidan-3123600013@vbox:~$ sudo useradd -M -s /sbin/nologin smbuser
   [sudo] password for zidan-3123600013:
   New password:
   Retype new password:
   passwd: password updated successfully

   zidan-3123600013@vbox:~$ sudo smbpasswd -a smbuser
   New SMB password:
   Retype new SMB password:

   zidan-3123600013@vbox:~$ sudo smbpasswd -e smbuser
   Enabled user smbuser.
   
   zidan-3123600013@vbox:~$ sudo usermod -aG sambashare smbuser

   # tak lupa kita buat agar user kita satu group dengan smbuser
   zidan-3123600013@vbox:~$ sudo usermod -aG sambashare zidan-3123600013
   ```

   Kemudian edit file smb.conf lagi :
   ```bash
   zidan-3123600013@vbox:~$ sudo nano /etc/samba/smb.conf
   ```
   
   lalu tambahkan ini pada bagian terakhir (di situ Limited adalah nama folder yang nantinya akan tertera pada saat kita menampilkannya di client):
   ```bash
   [Limited]
   path = /srv/samba/limited
   browseable = yes
   writable = yes
   guest ok = no
   valid users = @sambashare
   create mask = 0660
   directory mask = 0770
   ```

   
   Kemudian simpan dan restart ulang smb/samba nya, serta cek statusnya :
   ```bash
   zidan-3123600013@vbox:~$ sudo systemctl restart smb
   zidan-3123600013@vbox:~$ sudo systemctl status smb
   [sudo] password for zidan-3123600013:
   ● smbd.service - Samba SMB Daemon
 	Loaded: loaded (/lib/systemd/system/smbd.service; enabled; preset: enabled)
 	Active: active (running) since Tue 2025-03-11 20:07:14 WIB; 1h 14min ago
   	Docs: man:smbd(8)
         	man:samba(7)
         	man:smb.conf(5)
	Process: 10820 ExecCondition=/usr/share/samba/is-configured smb (code=exited, status=0/SUCCESS)
	Process: 10823 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 10833 (smbd)
 	Status: "smbd: ready to serve connections..."
  	Tasks: 5 (limit: 2293)
 	Memory: 35.9M
    	CPU: 672ms
 	CGroup: /system.slice/smbd.service
         	├─10833 /usr/sbin/smbd --foreground --no-process-group
         	├─10835 /usr/sbin/smbd --foreground --no-process-group
         	├─10836 /usr/sbin/smbd --foreground --no-process-group
         	├─11200 /usr/sbin/smbd --foreground --no-process-group
         	└─11218 /usr/sbin/smbd --foreground --no-process-group
   Mar 11 20:07:14 vbox systemd[1]: Starting smbd.service - Samba SMB Daemon...
   Mar 11 20:07:14 vbox systemd[1]: Started smbd.service - Samba SMB Daemon.
   Mar 11 20:11:52 vbox smbd[10949]: pam_unix(samba:session): session closed for user nobody
   Mar 11 20:24:00 vbox smbd[11218]: pam_unix(samba:session): session opened for user smbuser(uid=1001) by (uid=0)
   ```
   
6. Gunakan file manajer untuk mengakses shared folder tersebut
   Pertama kita cek dulu pada server samba yang kita buat di 
   - Untuk mengakses samba dari file manager kita hanya perlu memasukkan alamat ipnya beserta nama folder tadi yang sudah kita masukkan ke smb.conf.
   - Untuk linux sendiri harus didahului dengan menginstall gvfs-smb guna mengakses smb di dalam file manager. Untuk windows tidak perlu menginstall apa-apa.
   Berikut tampilannya di linux (Kita masukkan smb://192.168.1.64/<nama_direktori>).
   
   Berikut tampilannya di windows (Kita masukkan \\192.168.188.94\<nama_direktori>)
   

   
8. Gunakan CLI (khusus untuk client linux)
   Pertama kita tampilkan dulu apa saja direktori yang ada:
   ```bash
   > smbclient -L 192.168.1.64 -N

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Public          Disk
	Limited         Disk
	IPC$            IPC       IPC Service (Samba 4.17.12-Debian)
	nobody          Disk      Home Directories
   ```
   
   Ini adalah tampilan ketika mengakses public folder
   ```bash
   # untuk masuk ke direktori yang dituju gunakan ini :
   > smbclient //192.168.188.94/Public -N
   Try "help" to get a list of possible commands.
   smb: \> ls
   .                                   D        0  Mon Mar 10 14:36:02 2025
   ..                                  D        0  Mon Mar 10 14:33:53 2025
   tes                                 N       11  Mon Mar 10 14:35:59 2025

		19480400 blocks of size 1024. 12861968 blocks available
   # kita coba untuk mendownload file tes tersebut dari server samba yang kita buat (gunakan perintah get / mget jika banyak file)
   > smb: \> get tes
   getting file \tes of size 11 as tes (5.4 KiloBytes/sec) (average 5.4 KiloBytes/sec)
   > smb: \> exit

   # kita coba untuk mengupload file yang sudah kita buat di home kita sebelumnya (gunakan perintah put / mput jika banyak file)
   > nano helloworld
   > smbclient //192.168.188.94/Public -N
   > smb: \> put helloworld						
   putting file helloworld as \helloworld (2.9 kb/s) (average 2.9 kb/s)
   ```
   
   Ini adalah tampilan ketika mengakses limited folder
   ```bash
   # fungsi sama untuk mengecek list direktori
   > smbclient -L //192.168.188.94/Limited -U smbuser
   > smbclient //192.168.188.94/Limited -U smbuser
   Password for [WORKGROUP\smbuser]:
   session setup failed: NT_STATUS_LOGON_FAILURE
   > smbclient //192.168.188.94/Limited -U smbuser
   Password for [WORKGROUP\smbuser]:
   Try "help" to get a list of possible commands.
   smb: \> ls
   .                                   D        0  Mon Mar 10 10:59:24 2025
   ..                                  D        0  Mon Mar 10 14:33:53 2025

		19480400 blocks of size 1024. 12862464 blocks available\
   smb: \> exit
   ```
   
---

### C. Rangkuman Debian 12 Sysadmin (Package Management)


---
