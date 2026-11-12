# Docker Compose: WordPress dengan MariaDB

Project ini dibuat untuk memenuhi tugas individu mengenai implementasi aplikasi *multi-container* menggunakan Docker Compose yang menghubungkan layanan WordPress dan database MariaDB.

## Identitas Pembuat

* **Nama Lengkap:** Muhammad Fakhri Nur Zafran

* **Kelas:** XI SIJA 2

* **Nomor Absen:** 17

* **Tautan Repository GitHub:** \[Isi dengan tautan repository GitHub pribadimu\]

## Deskripsi Singkat Project

Project ini bertujuan untuk membangun dan menjalankan aplikasi web WordPress yang terintegrasi dengan sistem manajemen basis data MariaDB di dalam lingkungan container yang terisolasi menggunakan Docker Compose. Dengan konfigurasi ini, proses deployment menjadi lebih cepat, terstandarisasi, dan memastikan data tetap tersimpan secara permanen (*persistent*) menggunakan Docker Volumes meskipun container dimatikan atau dibuat ulang.

## Prasyarat Perangkat dan Software

Untuk menjalankan project ini secara lokal, pastikan perangkat telah terinstal:

* Sistem Operasi (Windows, Linux, atau macOS)

* **Docker Desktop** atau **Docker Engine**

* **Docker Compose** (v2+)

* Web Browser dan Terminal/Command Prompt

## Struktur Folder Project

```
wordpress-compose-fakhri/
├── compose.yaml
├── .env                 # Tidak diunggah ke GitHub (berisi kredensial rahasia)
├── .env.example
├── .gitignore
├── README.md
└── bukti-running/
    ├── docker-ps.png
    ├── wordpress-browser.png

```

## Cara Instalasi dan Menjalankan Project

1. **Clone repository ini** ke komputer lokal kamu:

   ```
   git clone <tautan-repository-github-pribadi-kamu>
   cd wordpress-compose-fakhri
   
   ```

2. **Buat file `.env`** dari template `.env.example`:

   ```
   cp .env.example .env
   
   ```

3. **Atur nilai kredensial** di dalam file `.env` menggunakan editor teks sesuai keinginan (jangan bagikan nilai ini ke publik):

   ```
   WORDPRESS_DB_NAME=wordpress_db
   WORDPRESS_DB_USER=wordpress_user
   WORDPRESS_DB_PASSWORD=password_aman_kamu
   MARIADB_ROOT_PASSWORD=password_root_aman_kamu
   
   ```

4. **Periksa validitas konfigurasi** Docker Compose:

   ```
   docker compose config
   
   ```

5. **Jalankan layanan container** di latar belakang (*detached mode*):

   ```
   docker compose up -d
   
   ```

6. **Akses WordPress** melalui browser pada alamat:
   `http://localhost:8080`

## Daftar Perintah Docker Compose yang Digunakan

| Perintah | Penjelasan Fungsi | 
| ----- | ----- | 
| `docker compose config` | Memvalidasi sintaks file `compose.yaml` dan memastikan variabel dari file `.env` terbaca dengan benar. | 
| `docker compose up -d` | Membuat network, volume, dan menjalankan seluruh container layanan di latar belakang (*background*). | 
| `docker compose ps` | Menampilkan daftar dan status container yang berjalan di dalam project ini. | 
| `docker compose logs wordpress` | Melihat log aktivitas atau pesan error khusus dari layanan container `wordpress`. | 
| `docker compose down` | Menghentikan dan menghapus container serta network yang dibuat, namun tetap mempertahankan data pada volumes. | 

## Bukti Hasil Running

### 1. Status Container Berjalan (`docker compose ps`)


*Penjelasan: Kedua layanan (`wordpress-app` dan `wordpress-db`) berstatus `Up` dan berjalan normal di background.*

### 2. Tampilan WordPress di Browser (`http://localhost:8080`)


*Penjelasan: Halaman instalasi/dashboard WordPress berhasil diakses melalui browser pada port 8080 dan terhubung ke database MariaDB.*

### 3. Halaman/Artikel Uji & Uji Persistensi Data


*Penjelasan: Artikel uji berhasil dibuat dan disimpan. Setelah layanan dihentikan dengan `docker compose down` dan dijalankan kembali dengan `docker compose up -d`, artikel uji tersebut terbukti tetap tersimpan tanpa hilang.*
