# Tugas Docker - Flask API

## Contributors

- Maghfirli
- reyhan225
- Claudiuscpm
- ArifandoAr

## Deskripsi

Project ini adalah tugas mata kuliah Server and Network Administration.

Aplikasi ini dibuat menggunakan Python Flask dan dijalankan menggunakan Docker.
Tujuan dari tugas ini adalah untuk memahami cara membuat Dockerfile, build image, dan menjalankan container.

## Fitur

Aplikasi memiliki 2 endpoint:

1. `/`
   Menampilkan pesan utama dari aplikasi.

2. `/health`
   Mengecek apakah aplikasi berjalan dengan baik.

## Tools yang Digunakan

- Python 3.12
- Flask
- Docker Desktop
- GitHub

## Cara Menjalankan Project

### 1. Build Docker Image

Masuk ke folder project, lalu jalankan:

```bash
docker build -t tugas-docker-flask .
```

Keterangan:

- `docker build` untuk membuat image dari Dockerfile
- `-t tugas-docker-flask` untuk memberi nama image
- `.` artinya mengambil Dockerfile dari folder saat ini

### 2. Jalankan Container

```bash
docker run --name flask-api -p 5000:5000 tugas-docker-flask
```

Keterangan:

- `--name flask-api` memberi nama container
- `-p 5000:5000` menghubungkan port laptop dengan port container
- `tugas-docker-flask` adalah nama image

### 3. Akses Aplikasi

Buka browser dan ketik:
http://localhost:5000

Untuk mengecek status aplikasi:
http://localhost:5000/health

Jika berhasil, akan muncul data dalam bentuk JSON.

## Cara Menghentikan Container

Tekan `CTRL + C` di terminal.

Atau jika berjalan di background:

bash
docker stop flask-api

## Cara Menghapus Container

bash
docker rm flask-api

## Kesimpulan

Dengan menggunakan Docker, aplikasi dapat dijalankan tanpa perlu menginstall Python dan Flask secara manual di komputer. Semua dependency sudah berada di dalam container.

Docker memudahkan proses deployment dan memastikan aplikasi bisa berjalan dengan environment yang sama di komputer lain.

KELOMPOK : KELOMPOK 8
Mata Kuliah : Server and Network Administration
