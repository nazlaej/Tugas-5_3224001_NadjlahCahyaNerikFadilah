# Tugas 5 - Black-box Testing (Equivalence Partitioning & BVA)
**Nadjlah Cahya Nerik Fadilah (3224001)**

## BAGIAN A: EQUIVALENCE PARTITIONING (30 POIN)

### Soal 1 (15 Poin)

#### 1. Identifikasi Equivalence Partitioning (Valid & Invalid Class)

**Field Username (5-20 karakter, hanya huruf dan angka)**

| Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | 5-20 karakter, hanya huruf & angka | "abcde12" (7 karakter) | Login berhasil / Valid |
| P2 | Invalid | < 5 karakter | "abc" (3 karakter) | Error: Username harus 5-20 karakter |
| P3 | Invalid | > 20 karakter | "abcdefghijklmnopqrstuv" (21 karakter) | Error: Username harus 5-20 karakter |
| P4 | Invalid | Mengandung karakter selain huruf & angka | "abc@123" | Error: Username hanya huruf & angka |

**Field Password (Minimal 8 karakter, huruf besar, huruf kecil, angka)**

| Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | >=8, ada huruf besar, kecil, angka | "Abc12345" | Login berhasil / Valid |
| P2 | Invalid | < 8 karakter | "Abc123" | Error: Password minimal 8 karakter |
| P3 | Invalid | Tidak ada huruf besar | "abc12345" | Error: Harus ada huruf besar |
| P4 | Invalid | Tidak ada huruf kecil | "ABC12345" | Error: Harus ada huruf kecil |
| P5 | Invalid | Tidak ada angka | "Abcdefgh" | Error: Harus ada angka |

**Field Umur (17-100 tahun)**

| Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | 17 ≤ umur ≤ 100 | "17", "50", "100" | Valid |
| P2 | Invalid | < 17 | "16" | Error: Umur minimal 17 tahun |
| P3 | Invalid | > 100 | "101" | Error: Umur maksimal 100 tahun |

#### 2. Rancang test case untuk setiap partisi (6 poin)

Test case dirancang sesuai tabel di atas.

### Soal 2 (15 Poin)

Spesifikasi: Jumlah Tiket (1-10), Kode Promo (5-10 karakter, opsional), Tanggal Keberangkatan (YYYY-MM-DD, minimal hari ini)

#### 1. Equivalence Partitioning

**Jumlah Tiket (1-10)**

| Partisi | Kategori | Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | 1-10 tiket | 5 | Pemesanan valid |
| P2 | Invalid | < 1 | 0 | Error: Minimal 1 tiket |
| P3 | Invalid | > 10 | 11 | Error: Maksimal 10 tiket |

**Kode Promo (5-10 karakter, opsional)**

| Partisi | Kategori | Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | Kosong | "" | Valid (opsional) |
| P2 | Valid | 5-10 karakter | "PROMO1" | Valid |
| P3 | Invalid | < 5 karakter | "PRO1" | Error: Kode promo 5-10 karakter |
| P4 | Invalid | > 10 karakter | "PROMO12345" | Error: Kode promo 5-10 karakter |
| P5 | Invalid | Mengandung spasi/simbol tidak valid | "PRO MO" | Error: Format tidak valid |

**Tanggal Keberangkatan (YYYY-MM-DD, minimal hari ini)**

| Partisi | Kategori | Kondisi | Test Case | Expected Output |
|---|---|---|---|---|
| P1 | Valid | Tanggal >= hari ini (format valid) | "2026-10-15" (contoh hari ini) | Valid |
| P2 | Invalid | Format salah | "15-10-2026" / "2026/10/15" | Error: Format YYYY-MM-DD |
| P3 | Invalid | Tanggal di masa lalu | "2026-10-01" | Error: Tanggal minimal hari ini |

## BAGIAN B: BOUNDARY VALUE ANALYSIS (30 POIN)

### Soal 3 (15 Poin)

Spesifikasi: Nilai Ujian (0-100), IPK (0.0-4.0), Semester (1-14)

**Nilai Ujian (0-100)**

| Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---|
| min-1 | -1 | Invalid | Error: Nilai harus 0-100 |
| min | 0 | Valid | Berhasil |
| min+1 | 1 | Valid | Berhasil |
| max-1 | 99 | Valid | Berhasil |
| max | 100 | Valid | Berhasil |
| max+1 | 101 | Invalid | Error: Nilai harus 0-100 |

**IPK (0.0-4.0)**

| Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---|
| min-1 | -0.1 | Invalid | Error: IPK harus 0.0-4.0 |
| min | 0.0 | Valid | Berhasil |
| min+1 | 0.1 | Valid | Berhasil |
| max-1 | 3.9 | Valid | Berhasil |
| max | 4.0 | Valid | Berhasil |
| max+1 | 4.1 | Invalid | Error: IPK harus 0.0-4.0 |

**Semester (1-14)**

| Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---|
| min-1 | 0 | Invalid | Error: Semester harus 1-14 |
| min | 1 | Valid | Berhasil |
| min+1 | 2 | Valid | Berhasil |
| max-1 | 13 | Valid | Berhasil |
| max | 14 | Valid | Berhasil |
| max+1 | 15 | Invalid | Error: Semester harus 1-14 |

### Soal 4 (15 Poin)

Field Nominal Transfer: Rp10.000 - Rp100.000.000

**BVA Nominal Transfer**

| Boundary | Nilai (Rp) | Kategori | Expected Output |
|---|---|---|---|
| min-1 | 9.999 | Invalid | Error: Nominal minimal Rp10.000 |
| min | 10.000 | Valid | Transfer berhasil |
| min+1 | 10.001 | Valid | Transfer berhasil |
| max-1 | 99.999.999 | Valid | Transfer berhasil |
| max | 100.000.000 | Valid | Transfer berhasil |
| max+1 | 100.000.001 | Invalid | Error: Nominal maksimal Rp100.000.000 |

*Catatan: Perlu memperhatikan saldo minimal Rp50.000 & biaya admin Rp2.500.*

## BAGIAN C: KOMBINASI EP & BVA (25 POIN)

### Soal 5

#### 1. EP untuk setiap field
- Nama Lengkap (3-50 karakter, tidak boleh kosong): Valid 3-50; Invalid < 3, > 50, kosong
- Username (5-20 karakter, huruf & angka, tidak boleh diawali angka): Valid sesuai kriteria; Invalid panjang, ada simbol, diawali angka
- Email (format email valid): Valid format standar; Invalid format
- Password (min 8, huruf besar, kecil, angka): Valid kombinasi; Invalid kurang syarat
- Umur (17-100): Valid 17-100; Invalid < 17, > 100
- No. Telepon (10-13 digit, diawali 08): Valid 10-13 digit & diawali 08; Invalid panjang, tidak diawali 08, ada huruf

#### 2. BVA untuk field dengan range
Nama (3-50): 2(invalid), 3(valid), 4(valid), 49(valid), 50(valid), 51(invalid). Username (5-20): 4,5,6,19,20,21. Umur (17-100): 16,17,18,99,100,101. No.Telepon panjang (10-13 digit): 9,10,11,12,13,14.

#### 3. Test case lengkap (minimal 20 test case)

| No | Test Case | Field Nilai | Expected Result |
|---|---|---|---|
| 1 | TC-01 | Nama valid (min), Username valid, Email valid, Pass valid, Umur valid, Telp valid | Berhasil registrasi |
| 2 | TC-02 | Nama = 2 karakter (<3) | Gagal - Nama minimal 3 |
| 3 | TC-03 | Nama = 3 karakter | Berhasil |
| 4 | TC-04 | Nama = 50 karakter | Berhasil |
| 5 | TC-05 | Nama = 51 karakter (>50) | Gagal - Nama maks 50 |
| 6 | TC-06 | Username < 5 (4) | Gagal |
| 7 | TC-07 | Username diawali angka | Gagal - tidak boleh diawali angka |
| 8 | TC-08 | Username mengandung simbol | Gagal - hanya huruf & angka |
| 9 | TC-09 | Email tanpa @ | Gagal - format email invalid |
| 10 | TC-10 | Email tanpa domain | Gagal - format email invalid |
| 11 | TC-11 | Password tanpa huruf besar | Gagal |
| 12 | TC-12 | Password tanpa angka | Gagal |
| 13 | TC-13 | Password < 8 | Gagal |
| 14 | TC-14 | Umur 16 | Gagal - minimal 17 |
| 15 | TC-15 | Umur 17 | Berhasil |
| 16 | TC-16 | Umur 100 | Berhasil |
| 17 | TC-17 | Umur 101 | Gagal - maks 100 |
| 18 | TC-18 | Telp 9 digit | Gagal - minimal 10 |
| 19 | TC-19 | Telp 10 digit diawali 08 | Berhasil |
| 20 | TC-20 | Telp 13 digit diawali 08 | Berhasil |
| 21 | TC-21 | Telp 14 digit | Gagal - maks 13 |
| 22 | TC-22 | Telp tidak diawali 08 | Gagal |

## BAGIAN D: API TESTING (15 POIN)

### Soal 6

Spesifikasi POST /api/v1/products
- name: string (3-100), price: number (1000-10000000), stock: integer (0-1000), category: enum (electronics, clothing, food)

| No | Test Case | Request Body | Expected Status | Expected Response |
|---|---|---|---|---|
| 1 | Valid request | {"name":"Laptop","price":5000000,"stock":10,"category":"electronics"} | 201 Created | {"id":1,"name":"Laptop",...,"status":"created"} |
| 2 | Name < 3 karakter | {"name":"Lp","price":5000000,"stock":10,"category":"electronics"} | 400 Bad Request | {"error":"name must be 3-100 chars"} |
| 3 | Price < 1000 | {"name":"Mouse","price":500,"stock":10,"category":"electronics"} | 400 Bad Request | {"error":"price must be 1000-10000000"} |
| 4 | Stock > 1000 | {"name":"Keyboard","price":500000,"stock":2000,"category":"electronics"} | 400 Bad Request | {"error":"stock must be 0-1000"} |
| 5 | Category invalid | {"name":"Item","price":500000,"stock":10,"category":"other"} | 400 Bad Request | {"error":"invalid category"} |
| 6 | Unauthorized (no token) | {"name":"Headset","price":300000,"stock":5,"category":"electronics"} | 401 Unauthorized | {"error":"unauthorized"} |

## BAGIAN E: STUDI KASUS TERPADU (BONUS 10 POIN)

### Soal 7

#### 1. EP
- Nama (3-100): Valid 3-100; Invalid <3, >100, kosong
- Email: Valid format; Invalid format
- No. HP (10-13 digit, diawali 08): Valid range & prefix; Invalid panjang, prefix, karakter
- Tanggal Lahir (YYYY-MM-DD, umur min 17 tahun): Valid format & umur>=17; Invalid format, umur<17
- Password (min 8, huruf besar, kecil, angka, simbol): Valid; Invalid kurang syarat
- Konfirmasi Password (harus sama): Valid sama; Invalid beda/kosong

#### 2. BVA untuk field dengan range
Nama 2,3,4,99,100,101. No.HP 9,10,11,12,13,14.

#### 3. Test case lengkap (minimal 25)
Termasuk valid case, boundary cases untuk nama/HP, invalid email, umur < 17, password tanpa simbol, konfirmasi tidak sama, format tanggal salah, dll.

**Keterangan:** Jawaban ini disusun sesuai materi Equivalence Partitioning & BVA (black-box testing).
