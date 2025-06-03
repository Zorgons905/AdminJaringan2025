

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
Dengan menggunakan proyek yang anada ambil dalam matkul RPL, buatlah uraian lengkap tentang progress anda mulai dari arsitektur bisnis, arsitektur ilayanan, arsitektur aplikasi dan arsitektur infrastruktur . Fokur ke arsitektur aplikasi dan infrastruktur pakailah teknologi docker dalam proses deploymentnya





---

# D. PERCOBAAN
# 📘 Laporan Proyek RPL: Readaily

## 1. Identitas Proyek

- **Nama Aplikasi**: Readaily  
- **Jenis Aplikasi**: Manajemen Bacaan & Pembelajaran Digital  
- **Platform**: Mobile App (Android & iOS) menggunakan Flutter  
- **Backend**: Supabase (PostgreSQL, Auth, Storage, API)  
- **Deployment**: Docker (opsional untuk Flutter Web)

---

## 2. Arsitektur Bisnis

### 2.1 Tujuan

Readaily bertujuan membantu siswa dan dosen dalam mengelola aktivitas belajar secara digital. Aplikasi menyediakan fitur seperti:

- Manajemen kelas
- Distribusi modul
- Kuis interaktif
- Pelacakan progres baca siswa
- Penilaian hasil kuis

### 2.2 Aktor

| Aktor     | Peran                                                             |
|-----------|-------------------------------------------------------------------|
| Siswa     | Bergabung ke kelas, membaca modul, mengerjakan kuis              |
| Dosen     | Membuat kelas, mengunggah modul, membuat kuis, memantau siswa     |
| Admin     | Mengelola data pengguna dan memantau aktivitas keseluruhan       |

### 2.3 Alur Bisnis

1. Dosen membuat kelas dengan kode unik
2. Siswa bergabung ke kelas menggunakan kode
3. Dosen mengunggah modul dan kuis
4. Siswa membaca modul, progres dicatat otomatis
5. Siswa mengerjakan kuis, hasil direkam
6. Dosen melihat progres dan nilai siswa

---

## 3. Arsitektur Layanan

### 3.1 Backend: Supabase

#### Layanan Supabase yang digunakan:
- **Auth**: Pendaftaran & login user
- **Database**: PostgreSQL untuk seluruh data
- **Storage**: Menyimpan file modul
- **Edge Functions (opsional)**: Untuk logika backend khusus

### 3.2 Struktur Tabel Supabase

| Tabel                     | Kolom Utama                                                                 |
|---------------------------|------------------------------------------------------------------------------|
| `auth.users`              | disediakan oleh Supabase (id, email, dsb.)                                  |
| `profiles`                | id, role, name, bio, created_at                                             |
| `classroom`               | id, name, code, lecturer_id, created_at                                     |
| `student_class`           | id, classroom_id, student_id, created_at                                    |
| `module`                  | id, classroom_id, title, file_url, file_type, uploaded_at                   |
| `student_module_progress`| id, student_id, module_id, progress_percent, last_read_at (timestamp)        |
| `quiz`                    | id, classroom_id, title, created_at, is_randomize_question, is_randomize_answer |
| `question`                | id, quiz_id, content, order_number                                          |
| `answer`                  | id, question_id, content, is_correct                                        |
| `student_quiz_result`     | id, student_id, quiz_id, score, submitted_at                                |

---

### 3.3 Fungsi Generator Kode Kelas

#### 🛠 Contoh Kode di Flutter (Dart)
```dart
import 'dart:math';

String generateClassCode({int length = 8}) {
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
  final rand = Random.secure();
  return List.generate(length, (_) => chars[rand.nextInt(chars.length)]).join();
}
```

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
