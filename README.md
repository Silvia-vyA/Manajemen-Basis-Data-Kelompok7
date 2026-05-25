# Penerapan Access Control dan Pencegahan SQL Injection pada Basis Data Rekam Medis Elektronik

## Deskripsi Project
Project ini merupakan implementasi keamanan basis data pada sistem Rekam Medis Elektronik (RME) menggunakan kombinasi:

- Role-Based Access Control (RBAC)
- Deteksi SQL Injection berbasis Regex
- Audit Log Monitoring
- Security Middleware berbasis Python

Penelitian ini bertujuan meningkatkan keamanan dan keandalan basis data RME dengan pendekatan database-level security menggunakan MySQL dan Python middleware.

---

# Tabel Kontribusi Anggota Kelompok

| No | Nama | NIM | Kontribusi |
|---|---|---|---|
| 1 | Margaretta Angela Manulang | 123140010 | Kajian literatur access control, analisis jurnal utama, penyusunan Bab II |
| 2 | Ade Putri Tifani | 123140011 | Penyusunan latar belakang penelitian dan pengumpulan referensi keamanan data |
| 3 | Natasya Felisita Br Ginting | 123140017 | Penyusunan tabel perbandingan studi terdahulu dan analisis metode penelitian |
| 4 | Jesika Filosovi Br P-A | 123140044 | Penyusunan tujuan penelitian, kontribusi penelitian, dan evaluasi sistem |
| 5 | Nabila Ramadhani Mujahidin | 123140062 | Analisis research gap, posisi penelitian, dan penyusunan daftar pustaka |
| 6 | Annisa Salsabila | 123140070 | Implementasi program Python, middleware keamanan, GitHub repository, pengujian sistem, visualisasi hasil |
| 7 | Willy Syifa Luthfia | 123140071 | Penyusunan struktur paper, dokumentasi project, dan integrasi laporan |
| 8 | Silvia | 123140133 | Penyusunan rumusan masalah, pengumpulan referensi tambahan, dan validasi isi laporan |

---

## Persentase Kontribusi

| Nama | Persentase |
|---|---|
| Margaretta Angela Manulang | 12.5% |
| Ade Putri Tifani | 12.5% |
| Natasya Felisita Br Ginting | 12.5% |
| Jesika Filosovi Br P-A | 12.5% |
| Nabila Ramadhani Mujahidin | 12.5% |
| Annisa Salsabila | 12.5% |
| Willy Syifa Luthfia | 12.5% |
| Silvia | 12.5% |

---

## Latar Belakang
Data rekam medis elektronik bersifat sangat sensitif dan rentan terhadap:

- SQL Injection
- Penyalahgunaan hak akses
- Kebocoran data pasien
- Manipulasi data medis

Untuk mengatasi masalah tersebut, sistem ini menerapkan validasi akses berbasis role serta deteksi query berbahaya sebelum query dieksekusi ke database.

---

## Fitur Utama

### 1. Role-Based Access Control (RBAC)

Hak akses dibatasi berdasarkan role pengguna:

| Role | Hak Akses |
|---|---|
| Admin | Full Access |
| Dokter | SELECT, INSERT, UPDATE |
| Perawat | SELECT |
| Pasien | SELECT data milik sendiri |
| Staff Keuangan | Data administrasi & pembayaran |

---

### 2. SQL Injection Detection

Middleware mendeteksi pola serangan seperti:

- OR 1=1
- UNION SELECT
- DROP TABLE
- Comment-based Injection
- Time-based Injection
- Authentication Bypass

Deteksi dilakukan menggunakan Regular Expression (Regex).

---

### 3. Audit Log

Sistem mencatat:

- Username
- Query SQL
- Timestamp
- Status query (Accepted / Rejected)

---

## Arsitektur Sistem

```text
User Input
    ↓
Security Middleware (Python)
    ├── RBAC Validation
    ├── SQL Injection Detection
    ↓
MySQL Database (XAMPP)
    ↓
Audit Log
