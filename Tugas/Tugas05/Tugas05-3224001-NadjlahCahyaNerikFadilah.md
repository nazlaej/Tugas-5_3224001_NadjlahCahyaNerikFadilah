# Tugas 5 - Black-box Testing (Equivalence Partitioning & BVA)
**Nadjlah Cahya Nerik Fadilah (3224001)**

---

## BAGIAN A: EQUIVALENCE PARTITIONING (30 POIN)

### Soal 1 (15 Poin) - Form Login

Spesifikasi: Username 5-20 karakter (huruf & angka), Password minimal 8 karakter (huruf besar, kecil, angka), Umur 17-100 tahun.

#### 1. Identifikasi Equivalence Partitioning

**Field Username (5-20 karakter, hanya huruf dan angka)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Username | P1 | Valid | 5-20 karakter, hanya huruf & angka | "abcde12" (7 karakter) | Login berhasil |
| Username | P2 | Invalid | < 5 karakter | "abc" (3 karakter) | Error: Username harus 5-20 karakter |
| Username | P3 | Invalid | > 20 karakter | "abcdefghijklmnopqrstuv" (21 karakter) | Error: Username harus 5-20 karakter |
| Username | P4 | Invalid | Mengandung karakter selain huruf & angka | "abc@123" | Error: Username hanya huruf & angka |

**Field Password (Minimal 8 karakter, huruf besar, huruf kecil, angka)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Password | P1 | Valid | >= 8, ada huruf besar, kecil, angka | "Abc12345" | Login berhasil |
| Password | P2 | Invalid | < 8 karakter | "Abc123" | Error: Password minimal 8 karakter |
| Password | P3 | Invalid | Tidak ada huruf besar | "abc12345" | Error: Harus ada huruf besar |
| Password | P4 | Invalid | Tidak ada huruf kecil | "ABC12345" | Error: Harus ada huruf kecil |
| Password | P5 | Invalid | Tidak ada angka | "Abcdefgh" | Error: Harus ada angka |

**Field Umur (17-100 tahun)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Umur | P1 | Valid | 17 ≤ umur ≤ 100 | "17", "50", "100" | Valid |
| Umur | P2 | Invalid | < 17 | "16" | Error: Umur minimal 17 tahun |
| Umur | P3 | Invalid | > 100 | "101" | Error: Umur maksimal 100 tahun |

#### 2. Rancangan Test Case

| No. | Field | Input | Expected Output |
|---|---|---|---|
| 1 | Username | `nazla123` | Username diterima |
| 2 | Username | `naz` | Validasi gagal karena kurang dari 5 karakter |
| 3 | Username | `nazla@123` | Validasi gagal karena mengandung karakter khusus |
| 4 | Password | `Nazla1234` | Password memenuhi ketentuan |
| 5 | Password | `Naz12` | Validasi gagal karena kurang dari 8 karakter |
| 6 | Password | `nazlaabcd` | Validasi gagal karena tidak mengandung huruf besar dan angka |
| 7 | Umur | `20` | Umur diterima |
| 8 | Umur | `16` | Validasi gagal karena umur di bawah 17 tahun |
| 9 | Umur | `101` | Validasi gagal karena umur melebihi 100 tahun |

---

### Soal 2 (15 Poin) - Form Pemesanan Tiket

Spesifikasi: Jumlah Tiket 1-10, Kode Promo 5-10 karakter (opsional), Tanggal Keberangkatan format YYYY-MM-DD (minimal hari ini).

#### 1. Equivalence Partitioning

**Jumlah Tiket (1-10)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Jumlah Tiket | P1 | Valid | 1-10 tiket | 5 | Pemesanan valid |
| Jumlah Tiket | P2 | Invalid | < 1 | 0 | Error: Minimal 1 tiket |
| Jumlah Tiket | P3 | Invalid | > 10 | 11 | Error: Maksimal 10 tiket |

**Kode Promo (5-10 karakter, opsional)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Kode Promo | P1 | Valid | Kosong | "" | Valid (opsional) |
| Kode Promo | P2 | Valid | 5-10 karakter | "PROMO1" | Valid |
| Kode Promo | P3 | Invalid | < 5 karakter | "PRO1" | Error: Kode promo 5-10 karakter |
| Kode Promo | P4 | Invalid | > 10 karakter | "PROMO12345" | Error: Kode promo 5-10 karakter |
| Kode Promo | P5 | Invalid | Mengandung spasi/simbol | "PRO MO" | Error: Format tidak valid |

**Tanggal Keberangkatan (YYYY-MM-DD, minimal hari ini)**

| Field | Partisi | Kategori | Range/Kondisi | Test Case | Expected Output |
|---|---|---|---|---|---|
| Tanggal | P1 | Valid | Format YYYY-MM-DD, >= hari ini | "2026-10-16" | Valid |
| Tanggal | P2 | Invalid | Format salah | "16-10-2026" / "2026/10/16" | Error: Format YYYY-MM-DD |
| Tanggal | P3 | Invalid | Tanggal di masa lalu | "2026-10-01" | Error: Tanggal minimal hari ini |

#### 2. Rancangan Test Case

| No. | Field | Input | Expected Output |
|---|---|---|---|
| 1 | Jumlah Tiket | `5` | Pemesanan valid |
| 2 | Jumlah Tiket | `0` | Validasi gagal (minimal 1 tiket) |
| 3 | Jumlah Tiket | `11` | Validasi gagal (maksimal 10 tiket) |
| 4 | Kode Promo | `PROMO1` | Kode promo diterima |
| 5 | Kode Promo | `""` | Valid karena opsional |
| 6 | Kode Promo | `PRO1` | Validasi gagal (kurang dari 5 karakter) |
| 7 | Tanggal | `2026-10-16` | Valid |
| 8 | Tanggal | `16-10-2026` | Validasi gagal (format salah) |
| 9 | Tanggal | `2026-10-01` | Validasi gagal (tanggal lampau) |

---

## BAGIAN B: BOUNDARY VALUE ANALYSIS (30 POIN)

### Soal 3 (15 Poin) - Form Pendaftaran Mahasiswa

Spesifikasi: Nilai Ujian 0-100, IPK 0.0-4.0, Semester 1-14.

**Nilai Ujian (0-100)**

| Field | Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---:|---|---|
| Nilai Ujian | min-1 | -1 | Invalid | Nilai ditolak |
| Nilai Ujian | min | 0 | Valid | Nilai diterima |
| Nilai Ujian | min+1 | 1 | Valid | Nilai diterima |
| Nilai Ujian | max-1 | 99 | Valid | Nilai diterima |
| Nilai Ujian | max | 100 | Valid | Nilai diterima |
| Nilai Ujian | max+1 | 101 | Invalid | Nilai ditolak |

**IPK (0.0-4.0)**

| Field | Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---:|---|---|
| IPK | min-1 | -0.1 | Invalid | IPK ditolak |
| IPK | min | 0.0 | Valid | IPK diterima |
| IPK | min+1 | 0.1 | Valid | IPK diterima |
| IPK | max-1 | 3.9 | Valid | IPK diterima |
| IPK | max | 4.0 | Valid | IPK diterima |
| IPK | max+1 | 4.1 | Invalid | IPK ditolak |

**Semester (1-14)**

| Field | Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---:|---|---|
| Semester | min-1 | 0 | Invalid | Semester ditolak |
| Semester | min | 1 | Valid | Semester diterima |
| Semester | min+1 | 2 | Valid | Semester diterima |
| Semester | max-1 | 13 | Valid | Semester diterima |
| Semester | max | 14 | Valid | Semester diterima |
| Semester | max+1 | 15 | Invalid | Semester ditolak |

---

### Soal 4 (15 Poin) - Form Transfer Bank

Spesifikasi: Nominal Transfer Rp10.000 - Rp100.000.000, Biaya admin Rp2.500, Saldo minimal Rp50.000.

| Field | Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---:|---|---|
| Nominal Transfer | min-1 | Rp9.999 | Invalid | Transfer ditolak |
| Nominal Transfer | min | Rp10.000 | Valid | Nominal diterima jika saldo mencukupi |
| Nominal Transfer | min+1 | Rp10.001 | Valid | Nominal diterima jika saldo mencukupi |
| Nominal Transfer | max-1 | Rp99.999.999 | Valid | Nominal diterima jika saldo mencukupi |
| Nominal Transfer | max | Rp100.000.000 | Valid | Nominal diterima jika saldo mencukupi |
| Nominal Transfer | max+1 | Rp100.000.001 | Invalid | Transfer ditolak |

**Catatan:** Nominal dalam rentang belum tentu bisa ditransfer apabila saldo tidak mencukupi nominal transfer ditambah biaya admin Rp2.500 dan tetap menyisakan saldo minimal Rp50.000.

---

## BAGIAN C: KOMBINASI EP & BVA (25 POIN)

### Soal 5 - Form Registrasi Akun

Spesifikasi:

| Field | Validasi |
|---|---|
| Nama Lengkap | 3-50 karakter, tidak boleh kosong |
| Username | 5-20 karakter, huruf & angka, tidak boleh diawali angka |
| Email | Format email valid |
| Password | Minimal 8 karakter, huruf besar, huruf kecil, angka |
| Umur | 17-100 tahun |
| No. Telepon | 10-13 digit, diawali 08 |

#### 1. Equivalence Partitioning

| Field | Partisi | Kategori | Range/Kondisi |
|---|---|---|---|
| Nama Lengkap | P1 | Valid | 3-50 karakter |
| Nama Lengkap | P2 | Invalid | < 3 karakter |
| Nama Lengkap | P3 | Invalid | > 50 karakter atau kosong |
| Username | P1 | Valid | 5-20 karakter, huruf & angka, tidak diawali angka |
| Username | P2 | Invalid | < 5 atau > 20 karakter |
| Username | P3 | Invalid | Diawali angka atau mengandung simbol |
| Email | P1 | Valid | Format email valid |
| Email | P2 | Invalid | Format email tidak valid |
| Password | P1 | Valid | >= 8, huruf besar, kecil, angka |
| Password | P2 | Invalid | Kurang dari 8 karakter atau tidak memenuhi kombinasi |
| Umur | P1 | Valid | 17-100 tahun |
| Umur | P2 | Invalid | < 17 atau > 100 tahun |
| No. Telepon | P1 | Valid | 10-13 digit, diawali 08 |
| No. Telepon | P2 | Invalid | < 10 atau > 13 digit |
| No. Telepon | P3 | Invalid | Tidak diawali 08 atau mengandung huruf |

#### 2. Boundary Value Analysis (field ber-range)

| Field | Range | Nilai Uji |
|---|---|---|
| Nama Lengkap | 3-50 | 2 (invalid), 3 (valid), 4 (valid), 49 (valid), 50 (valid), 51 (invalid) |
| Username | 5-20 | 4 (invalid), 5 (valid), 6 (valid), 19 (valid), 20 (valid), 21 (invalid) |
| Umur | 17-100 | 16 (invalid), 17 (valid), 18 (valid), 99 (valid), 100 (valid), 101 (invalid) |
| No. Telepon | 10-13 digit | 9 (invalid), 10 (valid), 11 (valid), 12 (valid), 13 (valid), 14 (invalid) |

#### 3. Rancangan Test Case (minimal 20)

| No. | Field | Input | Kategori | Expected Output |
|---|---|---|---|---|
| 1 | Nama Lengkap | `Nad` | Valid | Nama diterima |
| 2 | Nama Lengkap | `Na` | Invalid | Nama ditolak, kurang dari 3 karakter |
| 3 | Nama Lengkap | `(50 karakter)` | Valid | Nama diterima |
| 4 | Nama Lengkap | `(51 karakter)` | Invalid | Nama ditolak, lebih dari 50 karakter |
| 5 | Nama Lengkap | `""` | Invalid | Nama ditolak, tidak boleh kosong |
| 6 | Username | `nazla123` | Valid | Username diterima |
| 7 | Username | `naz` | Invalid | Username ditolak, kurang dari 5 karakter |
| 8 | Username | `123nazla` | Invalid | Username ditolak, diawali angka |
| 9 | Username | `nazla@1` | Invalid | Username ditolak, mengandung simbol |
| 10 | Email | `nazla@gmail.com` | Valid | Email diterima |
| 11 | Email | `nazlagmail.com` | Invalid | Email ditolak, tanpa @ |
| 12 | Email | `nazla@` | Invalid | Email ditolak, tanpa domain |
| 13 | Password | `Nazla123` | Valid | Password diterima |
| 14 | Password | `Nazla12` | Invalid | Password ditolak, kurang dari 8 karakter |
| 15 | Password | `nazla123` | Invalid | Password ditolak, tanpa huruf besar |
| 16 | Password | `NAZLA123` | Invalid | Password ditolak, tanpa huruf kecil |
| 17 | Password | `Nazlabcd` | Invalid | Password ditolak, tanpa angka |
| 18 | Umur | `17` | Valid | Umur diterima |
| 19 | Umur | `100` | Valid | Umur diterima |
| 20 | Umur | `16` | Invalid | Umur ditolak, kurang dari 17 |
| 21 | Umur | `101` | Invalid | Umur ditolak, lebih dari 100 |
| 22 | No. Telepon | `0812345678` | Valid | Telepon diterima (10 digit) |
| 23 | No. Telepon | `0812345678901` | Valid | Telepon diterima (13 digit) |
| 24 | No. Telepon | `081234567` | Invalid | Telepon ditolak, kurang dari 10 digit |
| 25 | No. Telepon | `08123456789012` | Invalid | Telepon ditolak, lebih dari 13 digit |
| 26 | No. Telepon | `1234567890` | Invalid | Telepon ditolak, tidak diawali 08 |

---

## BAGIAN D: API TESTING (15 POIN)

### Soal 6 - POST /api/v1/products

Spesifikasi:
- name: string (3-100 karakter)
- price: number (1000-10000000)
- stock: integer (0-1000)
- category: enum ("electronics", "clothing", "food")

| No. | Test Case | Request Body | Expected Status | Expected Response |
|---|---|---|---|---|
| 1 | Valid request | `{"name":"Laptop","price":5000000,"stock":10,"category":"electronics"}` | 201 Created | Produk berhasil dibuat |
| 2 | Nama < 3 karakter | `{"name":"TV","price":5000000,"stock":10,"category":"electronics"}` | 400 Bad Request | Validasi nama gagal |
| 3 | Harga < 1000 | `{"name":"Mouse","price":500,"stock":10,"category":"electronics"}` | 400 Bad Request | Validasi harga gagal |
| 4 | Stok > 1000 | `{"name":"Keyboard","price":500000,"stock":1001,"category":"electronics"}` | 400 Bad Request | Validasi stok gagal |
| 5 | Kategori tidak valid | `{"name":"Item","price":500000,"stock":10,"category":"furniture"}` | 400 Bad Request | Validasi kategori gagal |
| 6 | Token tidak valid | `{"name":"Headset","price":300000,"stock":5,"category":"electronics"}` | 401 Unauthorized | Token tidak valid |

---

## BAGIAN E: STUDI KASUS TERPADU (BONUS 10 POIN)

### Soal 7 - Form Pendaftaran Online

Spesifikasi:

| Field | Validasi |
|---|---|
| Nama | 3-100 karakter |
| Email | Format email valid |
| No. HP | 10-13 digit, diawali 08 |
| Tanggal Lahir | Format YYYY-MM-DD, umur minimal 17 tahun |
| Password | Minimal 8 karakter, huruf besar, huruf kecil, angka, simbol |
| Konfirmasi Password | Harus sama dengan password |

*Tanggal acuan pengujian: 16 Oktober 2026. Batas umur 17 tahun berarti tanggal lahir maksimal 16 Oktober 2009.*

#### 1. Equivalence Partitioning

| Field | Partisi | Kategori | Range/Kondisi |
|---|---|---|---|
| Nama | P1 | Valid | 3-100 karakter |
| Nama | P2 | Invalid | < 3 atau > 100 karakter |
| Email | P1 | Valid | Format email valid |
| Email | P2 | Invalid | Format email tidak valid |
| No. HP | P1 | Valid | 10-13 digit, diawali 08 |
| No. HP | P2 | Invalid | Panjang di luar 10-13 digit |
| No. HP | P3 | Invalid | Tidak diawali 08 atau ada karakter selain angka |
| Tanggal Lahir | P1 | Valid | YYYY-MM-DD, umur >= 17 tahun |
| Tanggal Lahir | P2 | Invalid | Format salah |
| Tanggal Lahir | P3 | Invalid | Umur < 17 tahun |
| Password | P1 | Valid | >= 8, huruf besar, kecil, angka, simbol |
| Password | P2 | Invalid | Tidak memenuhi salah satu syarat |
| Konfirmasi Password | P1 | Valid | Sama dengan password |
| Konfirmasi Password | P2 | Invalid | Berbeda atau kosong |

#### 2. Boundary Value Analysis

| Field | Range | Nilai Uji |
|---|---|---|
| Nama | 3-100 | 2 (invalid), 3 (valid), 4 (valid), 99 (valid), 100 (valid), 101 (invalid) |
| No. HP | 10-13 digit | 9 (invalid), 10 (valid), 11 (valid), 12 (valid), 13 (valid), 14 (invalid) |
| Umur (dari tanggal lahir) | >= 17 | 16 th 364 hari (invalid), tepat 17 th (valid), 17 th 1 hari (valid) |
| Password | >= 8 | 7 (invalid), 8 (valid), 9 (valid) |

#### 3. Rancangan Test Case (minimal 25)

| No. | Field | Input | Kategori | Expected Output |
|---|---|---|---|---|
| 1 | Nama | `Andi` | Valid | Nama diterima |
| 2 | Nama | `An` | Invalid | Nama ditolak, kurang dari 3 karakter |
| 3 | Nama | `(100 karakter)` | Valid | Nama diterima |
| 4 | Nama | `(101 karakter)` | Invalid | Nama ditolak, lebih dari 100 karakter |
| 5 | Email | `andi@gmail.com` | Valid | Email diterima |
| 6 | Email | `andigmail.com` | Invalid | Email ditolak, tanpa @ |
| 7 | Email | `andi@` | Invalid | Email ditolak, tanpa domain |
| 8 | No. HP | `0812345678` | Valid | No. HP diterima (10 digit) |
| 9 | No. HP | `0812345678901` | Valid | No. HP diterima (13 digit) |
| 10 | No. HP | `081234567` | Invalid | No. HP ditolak, kurang dari 10 digit |
| 11 | No. HP | `08123456789012` | Invalid | No. HP ditolak, lebih dari 13 digit |
| 12 | No. HP | `0812abcd` | Invalid | No. HP ditolak, mengandung huruf |
| 13 | No. HP | `1234567890` | Invalid | No. HP ditolak, tidak diawali 08 |
| 14 | Tanggal Lahir | `2000-01-01` | Valid | Tanggal diterima, umur >= 17 |
| 15 | Tanggal Lahir | `01-01-2000` | Invalid | Format salah |
| 16 | Tanggal Lahir | `2010-06-15` | Invalid | Umur < 17 tahun |
| 17 | Password | `Andi1234!` | Valid | Password diterima |
| 18 | Password | `Andi123` | Invalid | Password ditolak, kurang dari 8 karakter |
| 19 | Password | `andi1234!` | Invalid | Password ditolak, tanpa huruf besar |
| 20 | Password | `ANDI1234!` | Invalid | Password ditolak, tanpa huruf kecil |
| 21 | Password | `AndiAndi!` | Invalid | Password ditolak, tanpa angka |
| 22 | Password | `Andi12345` | Invalid | Password ditolak, tanpa simbol |
| 23 | Konfirmasi Password | `Andi1234!` | Valid | Konfirmasi cocok |
| 24 | Konfirmasi Password | `Andi12345!` | Invalid | Konfirmasi tidak sama dengan password |
| 25 | Konfirmasi Password | `""` | Invalid | Konfirmasi kosong |
| 26 | Semua field | Data valid lengkap | Valid | Pendaftaran berhasil |

---

## KESIMPULAN

Pengujian black-box menggunakan metode Equivalence Partitioning dan Boundary Value Analysis dilakukan untuk memastikan setiap input pada sistem memenuhi ketentuan yang telah ditetapkan. Equivalence Partitioning digunakan untuk membagi input menjadi kelompok valid dan invalid, sedangkan Boundary Value Analysis digunakan untuk menguji nilai pada batas minimum dan maksimum. Pengujian API juga dilakukan untuk memastikan sistem memberikan status respons yang sesuai terhadap input yang diterima.
