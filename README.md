# Tugas 5 - Black-box Testing (Equivalence Partitioning & BVA)

**Nadjlah Cahya Nerik Fadilah** | NIM: 3224001 | Program Studi: Sistem Informasi

Mata Kuliah: Implementasi Pengujian Perangkat Lunak
Pertemuan 5: Black-box Testing (Equivalence Partitioning & Boundary Value Analysis)

---

## Daftar Isi

- [Bagian A: Equivalence Partitioning (30 Poin)](#bagian-a-equivalence-partitioning-30-poin)
  - [Soal 1 - Form Login](#soal-1---form-login-15-poin)
  - [Soal 2 - Form Pemesanan Tiket](#soal-2---form-pemesanan-tiket-15-poin)
- [Bagian B: Boundary Value Analysis (30 Poin)](#bagian-b-boundary-value-analysis-30-poin)
  - [Soal 3 - Form Pendaftaran Mahasiswa](#soal-3---form-pendaftaran-mahasiswa-15-poin)
  - [Soal 4 - Form Transfer Bank](#soal-4---form-transfer-bank-15-poin)
- [Bagian C: Kombinasi EP & BVA (25 Poin)](#bagian-c-kombinasi-ep--bva-25-poin)
  - [Soal 5 - Form Registrasi Akun](#soal-5---form-registrasi-akun)
- [Bagian D: API Testing (15 Poin)](#bagian-d-api-testing-15-poin)
  - [Soal 6 - POST /api/v1/products](#soal-6---post-apiv1products)
- [Bagian E: Studi Kasus Terpadu - Bonus (10 Poin)](#bagian-e-studi-kasus-terpadu---bonus-10-poin)
  - [Soal 7 - Form Pendaftaran Online](#soal-7---form-pendaftaran-online)
- [Kesimpulan](#kesimpulan)

---

## File Tugas

| File | Keterangan |
|---|---|
| [Dokumen Tugas (PDF)](./Tugas/Tugas05/Tugas%205-3224001-NadjlahCahyaNerikFadilah.pdf) | Dokumen test case lengkap dalam format tabel |
| [Dokumen Tugas (Markdown)](./Tugas/Tugas05/Tugas05-3224001-NadjlahCahyaNerikFadilah.md) | Versi teks dari dokumen test case |

---

## Rangkuman Bagian

### Bagian A: Equivalence Partitioning (30 Poin)

Metode ini membagi input menjadi kelas valid dan invalid untuk setiap field.

| Soal | Objek Uji | Field yang Diuji |
|---|---|---|
| Soal 1 (15 Poin) | Form Login | Username, Password, Umur |
| Soal 2 (15 Poin) | Form Pemesanan Tiket | Jumlah Tiket, Kode Promo, Tanggal Keberangkatan |

### Bagian B: Boundary Value Analysis (30 Poin)

Metode ini menguji nilai pada batas minimum dan maksimum (min-1, min, min+1, max-1, max, max+1).

| Soal | Objek Uji | Field yang Diuji |
|---|---|---|
| Soal 3 (15 Poin) | Form Pendaftaran Mahasiswa | Nilai Ujian (0-100), IPK (0.0-4.0), Semester (1-14) |
| Soal 4 (15 Poin) | Form Transfer Bank | Nominal Transfer (Rp10.000 - Rp100.000.000) |

### Bagian C: Kombinasi EP & BVA (25 Poin)

| Soal | Objek Uji | Field yang Diuji |
|---|---|---|
| Soal 5 | Form Registrasi Akun | Nama Lengkap, Username, Email, Password, Umur, No. Telepon |

### Bagian D: API Testing (15 Poin)

| Soal | Endpoint | Test Case |
|---|---|---|
| Soal 6 | `POST /api/v1/products` | Minimal 6 test case (valid, validasi gagal, unauthorized) |

### Bagian E: Studi Kasus Terpadu - Bonus (10 Poin)

| Soal | Objek Uji | Field yang Diuji |
|---|---|---|
| Soal 7 | Form Pendaftaran Online | Nama, Email, No. HP, Tanggal Lahir, Password, Konfirmasi Password |

---

## Kesimpulan

Pengujian black-box menggunakan metode Equivalence Partitioning dan Boundary Value Analysis dilakukan untuk memastikan setiap input pada sistem memenuhi ketentuan yang telah ditetapkan. Equivalence Partitioning digunakan untuk membagi input menjadi kelompok valid dan invalid, sedangkan Boundary Value Analysis digunakan untuk menguji nilai pada batas minimum dan maksimum. Pengujian API juga dilakukan untuk memastikan sistem memberikan status respons yang sesuai terhadap input yang diterima.
