# Tugas Docker - Flask API CI/CD & DevSecOps

# Kelompok 8

Maghfirli Alif Al Ayubi - 2502022925 
Claudius Cezar - 2802544646  
Muhammad Arifando Akbar - 2602179170 
Lumban Tobing - 2802534241

Mata Kuliah: Server and Network Administration




**Security Features**

Bandit: Fitur ini digunakan untuk melakukan static code analysis pada source code Python.
pip-audit: Fitur ini berfungsi untuk mengecek vulnerability (kerentanan keamanan) pada dependency Python yang digunakan dalam proyek.
Trivy: Fitur ini digunakan untuk melakukan scanning terhadap Docker image.

# Fitur

# Deskripsi Project

Project ini merupakan implementasi CI/CD dan DevSecOps menggunakan GitHub Actions pada aplikasi backend sederhana berbasis Python Flask yang dijalankan menggunakan Docker.

Aplikasi menyediakan API sederhana yang dapat digunakan untuk:

* Menampilkan response utama aplikasi
* Melakukan health check terhadap service

Tujuan utama project ini bukan hanya menjalankan aplikasi Flask, tetapi juga mengotomatisasi proses testing, security scanning, dan build Docker image menggunakan pipeline CI/CD.


# Pipeline Sistem

Developer
↓
Git Push
↓
GitHub Actions
↓
Pytest
↓
Bandit Scan
↓
pip-audit Scan
↓
Docker Build
↓
Trivy Scan
↓
Success

Setiap perubahan kode yang di-push ke repository akan memicu pipeline otomatis untuk memastikan aplikasi tetap berjalan dengan baik dan aman.



# Endpoint API

# Home Endpoint

URL:

http://localhost:5000/

Response:

{
"message": "Hello from Flask API"
}

Fungsi:

Menampilkan response utama dari aplikasi.



# Health Check Endpoint

URL:

http://localhost:5000/health

Response:

{
"status": "healthy"
}

Fungsi:

Digunakan untuk memastikan service berjalan dengan normal.



# Tools yang Digunakan

* Python 3.12
* Flask
* Docker Desktop
* GitHub Actions
* Pytest
* Bandit
* pip-audit
* Trivy



# Implementasi Security (DevSecOps)

Project ini menggunakan 3 security tools utama:

#  1. Bandit

Fungsi:

Melakukan Static Application Security Testing (SAST) pada source code Python.

Contoh kerentanan yang dapat dideteksi:

* os.system()
* eval()
* hardcoded password
* command injection

Menjalankan Bandit:

bandit -r .



# 2. pip-audit

Fungsi:

Memeriksa dependency Python yang digunakan aplikasi dan mencocokkannya dengan database vulnerability (CVE).

Contoh:

Jika menggunakan Flask versi lama yang memiliki vulnerability, pip-audit akan memberikan peringatan.

Menjalankan pip-audit:

pip-audit


# 3. Trivy

Fungsi:

Melakukan scanning terhadap Docker image untuk mendeteksi vulnerability pada package dan dependency di dalam container.

Menjalankan Trivy:

trivy image tugas-docker-flask



# Cara Menjalankan Project

# 1. Clone Repository

git clone https://github.com/kelompok8-SNA-devops/tugas-docker-flask.git

cd tugas-docker-flask



# 2. Build Docker Image

docker build -t tugas-docker-flask .



# 3. Jalankan Container

docker run --name flask-api -p 5000:5000 tugas-docker-flask



# 4. Akses Aplikasi

Home Endpoint:

http://localhost:5000/

Health Check Endpoint:

http://localhost:5000/health


# Cara Menjalankan Tanpa Docker

Install dependency:

pip install -r requirements.txt

Jalankan aplikasi:

python app.py

Akses:

http://localhost:5000



# Cara Menjalankan Testing

pytest -v

Hasil yang diharapkan:

2 passed



# Cara Menjalankan Security Testing

- Bandit:

bandit -r .

- pip-audit:

pip-audit

- Trivy:

trivy image tugas-docker-flask



# Validasi Efektivitas Security Tools

Untuk membuktikan security tools bekerja dengan baik, dilakukan simulasi:

Bandit:

* Menambahkan kode os.system()
* Bandit berhasil mendeteksi potensi command injection

pip-audit:

* Menggunakan dependency versi lama yang memiliki vulnerability
* pip-audit berhasil mendeteksi vulnerability

Trivy:

* Menggunakan Docker image versi lama
* Trivy berhasil mendeteksi vulnerability pada image


# Kesimpulan

Project ini berhasil mengimplementasikan CI/CD dan DevSecOps menggunakan GitHub Actions. Pipeline mampu melakukan testing otomatis, security scanning, dan build Docker image setiap terjadi perubahan pada source code.

Implementasi Bandit, pip-audit, dan Trivy membantu meningkatkan keamanan aplikasi sejak tahap pengembangan sehingga potensi vulnerability dapat dideteksi lebih awal sebelum aplikasi digunakan pada lingkungan production.
