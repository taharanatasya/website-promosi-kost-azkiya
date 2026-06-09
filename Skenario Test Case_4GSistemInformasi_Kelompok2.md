# Skenario Test Case - Proyek PJBL

**Nama Kelas:** [4GSistemInformasi]  
**Nama Kelompok:** [Kelompok2]  

---

## 1. Fitur: Login

### A. Positive Case
* **Skenario:** Login dengan kredensial yang valid.
* **Deskripsi:** Memastikan pengguna dapat masuk ke dalam sistem menggunakan email dan kata sandi yang sudah terdaftar.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman login.<br>2. Masukkan email dan kata sandi yang valid.<br>3. Klik tombol "Login". | - Email: `user@example.com`<br>- Password: `Password123` | Sistem berhasil memvalidasi data, menampilkan pesan "Login Berhasil", dan mengarahkan pengguna ke halaman utama (*dashboard*). | [ ] Pass<br>[ ] Fail |

### B. Negative Case
* **Skenario:** Login dengan kata sandi yang salah.
* **Deskripsi:** Memastikan sistem menolak akses jika pengguna memasukkan kata sandi yang keliru.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman login.<br>2. Masukkan email yang valid dan kata sandi yang salah.<br>3. Klik tombol "Login". | - Email: `user@example.com`<br>- Password: `SalahPassword` | Sistem menolak akses dan menampilkan pesan kesalahan: "Kata sandi yang Anda masukkan salah." | [ ] Pass<br>[ ] Fail |

### C. Edge Case
* **Skenario:** Login dengan format email yang tidak valid secara ekstrem (tanpa domain).
* **Deskripsi:** Memastikan sistem dapat menangani input teks yang tidak memenuhi standar format email.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman login.<br>2. Masukkan teks acak tanpa format email.<br>3. Masukkan kata sandi.<br>4. Klik tombol "Login". | - Email: `userexample.com`<br>- Password: `Password123` | Sistem langsung memberikan peringatan validasi pada kolom input: "Format email tidak valid" sebelum menekan tombol atau mengirim data ke server. | [ ] Pass<br>[ ] Fail |

---

## 2. Fitur: Register (Pendaftaran Akun)

### A. Positive Case
* **Skenario:** Registrasi akun baru dengan data lengkap dan valid.
* **Deskripsi:** Memastikan pengguna baru dapat membuat akun dengan mengisi seluruh formulir sesuai ketentuan.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman registrasi.<br>2. Isi nama, email baru, dan kata sandi.<br>3. Klik tombol "Daftar". | - Nama: `Budi Santoso`<br>- Email: `budi.baru@example.com`<br>- Password: `BudiSecure789` | Akun baru berhasil dibuat, data tersimpan di database, dan sistem menampilkan pesan "Registrasi Berhasil. Silakan cek email untuk verifikasi." | [ ] Pass<br>[ ] Fail |

### B. Negative Case
* **Skenario:** Registrasi dengan email yang sudah terdaftar sebelumnya.
* **Deskripsi:** Memastikan sistem mencegah adanya duplikasi akun dengan email yang sama.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman registrasi.<br>2. Masukkan nama baru, tetapi gunakan email yang sudah ada di sistem.<br>3. Klik tombol "Daftar". | - Nama: `Andi Wijaya`<br>- Email: `user@example.com` *(Sudah ada)*<br>- Password: `AndiPass456` | Sistem menolak pendaftaran dan menampilkan pesan error: "Email sudah terdaftar. Silakan gunakan email lain." | [ ] Pass<br>[ ] Fail |

### C. Edge Case
* **Skenario:** Registrasi dengan kata sandi yang hanya terdiri dari 1 karakter (sangat pendek).
* **Deskripsi:** Menguji batas minimum kekuatan kata sandi yang diizinkan oleh sistem keamanan.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Buka halaman registrasi.<br>2. Isi nama dan email valid.<br>3. Masukkan kata sandi hanya 1 karakter.<br>4. Klik tombol "Daftar". | - Nama: `Siti`<br>- Email: `siti@example.com`<br>- Password: `1` | Sistem menolak proses registrasi dan memunculkan pesan validasi: "Kata sandi terlalu pendek. Minimal terdiri dari 8 karakter." | [ ] Pass<br>[ ] Fail |

---

## 3. Fitur: Pemesanan Kamar

### A. Positive Case
* **Skenario:** Melakukan pemesanan kamar pada tanggal yang tersedia.
* **Deskripsi:** Memastikan pengguna dapat memesan kamar hotel/penginapan dengan memilih tanggal check-in dan check-out yang masih kosong.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Pilih jenis kamar.<br>2. Tentukan tanggal yang tersedia.<br>3. Klik "Pesan Sekarang". | - Kamar: `Deluxe Room`<br>- Check-in: `2026-07-10`<br>- Check-out: `2026-07-12` | Kamar berhasil dipesan, status kamar berubah menjadi 'Booked' pada tanggal tersebut, dan pengguna diarahkan ke halaman pembayaran. | [ ] Pass<br>[ ] Fail |

### B. Negative Case
* **Skenario:** Memesan kamar pada tanggal yang sudah dipesan orang lain (*Double Booking*).
* **Deskripsi:** Memastikan sistem menolak pemesanan jika jadwal kamar yang dipilih bentrok dengan pengguna lain.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Pilih kamar yang sama.<br>2. Masukkan tanggal yang sudah terisi.<br>3. Klik "Pesan Sekarang". | - Kamar: `Deluxe Room`<br>- Check-in: `2026-07-10`<br>- Check-out: `2026-07-12` | Sistem menolak pemesanan dan memberikan informasi: "Maaf, kamar tidak tersedia pada tanggal yang Anda pilih." | [ ] Pass<br>[ ] Fail |

### C. Edge Case
* **Skenario:** Memesan kamar dengan tanggal check-out yang mendahului tanggal check-in (Tanggal Terbalik).
* **Deskripsi:** Menguji logika sistem dalam menangani input rentang tanggal yang tidak masuk akal secara kronologis.

| Langkah Pengujian | Data Masukan (Input) | Hasil yang Diharapkan | Status |
| :--- | :--- | :--- | :--- |
| 1. Pilih jenis kamar.<br>2. Masukkan tanggal check-in.<br>3. Masukkan tanggal check-out yang tanggalnya lebih lampau dari check-in.<br>4. Klik "Pesan Sekarang". | - Kamar: `Deluxe Room`<br>- Check-in: `2026-07-15`<br>- Check-out: `2026-07-12` | Sistem otomatis menolak input tersebut, memblokir tombol submit, atau menampilkan pesan: "Tanggal check-out tidak boleh 
sebelum tanggal check-in." | [ ] Pass<br>[ ] Fail |
--- Test Update Naufal 09 Juni ---