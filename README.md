# NOTULENSI DIGITAL - SISTEM PENCATATAN HASIL MEETING

Aplikasi web modern, profesional, responsif, dan mudah digunakan untuk kebutuhan pencatatan dan dokumentasi hasil meeting internal perusahaan (Evaluasi & Kalibrasi).

---

## 🌟 Fitur Utama

### 1. Desain & Antarmuka Modern
- **Palet Warna Profesional:** Dominasi Biru `#0A66FF`, Putih `#FFFFFF`, dan Abu-abu Muda (`#F8FAFC`, `#E2E8F0`).
- **Tipografi:** Google Font *Inter* dengan rendering tajam di semua resolusi.
- **Komponen Elegan:** Card dengan sudut membulat (*rounded corners* 12–16px), shadow halus, serta responsif penuh untuk Desktop, Tablet, dan Smartphone.
- **Navigasi Single Page Application (SPA):** Transisi mulus antara menu **Dashboard**, **Buat Notulensi**, dan **Riwayat Notulensi**.

### 2. Formulir Notulensi Lengkap & Terstruktur
- **Jenis Notulensi:** Dropdown wajib pilih (*Evaluasi* / *Kalibrasi*).
- **Tanggal Otomatis:** Terisi otomatis sesuai Waktu Indonesia Barat (WIB) dalam format `DD/MM/YYYY`, serta dilengkapi pemilih kalender interaktif jika ingin diubah manual.
- **Nama Notulensi & Notulis:** Judul notulensi dan nama pembuat tercatat jelas.
- **Peserta Meeting Interaktif:** Tambah peserta secara dinamis menggunakan tombol Tambah atau tombol Enter, tampil dalam bentuk chip/tag dengan tombol hapus individual.
- **Detail Notulensi Nyaman:** Textarea luas dengan toolbar format teks (Tebal `**`, Miring `*`, Poin Bullet `•`, Poin Angka `1.`, Subjudul, dan Bersihkan Teks) serta mendukung copy-paste teks panjang.
- **Hasil & Action Plan:**
  - Poin pembahasan utama
  - Hasil diskusi
  - Keputusan meeting
  - Action plan / tindak lanjut
  - PIC (Person in Charge)
  - Deadline tindak lanjut

### 3. Dashboard Ringkasan & Real-time KPI
- Total Notulensi tersimpan.
- Jumlah Notulensi Evaluasi vs Kalibrasi.
- Total akumulasi peserta meeting.
- Tabel notulensi terbaru dengan aksi cepat.
- Indikator status koneksi Firebase Firestore real-time.

### 4. Sistem Riwayat & Interactive Search Bar
- **Search Bar Interaktif:**
  - Ikon search di sebelah kiri dan efek fokus border biru `#0A66FF`.
  - Tombol Clear (X) untuk menghapus kata kunci seketika.
  - Pencarian real-time saat mengetik tanpa perlu tekan Enter atau reload halaman.
  - Pencarian multi-kriteria: mencari berdasarkan nama notulensi, jenis, tanggal, pembuat notulensi, nama peserta, hingga kata kunci di dalam isi pembahasan, hasil diskusi, keputusan, dan PIC.
  - Tidak membedakan huruf besar/kecil (*case-insensitive*) dan mengabaikan spasi berlebih.
- **Filter & Kategorisasi:**
  - Filter Kategori: *Semua Notulensi*, *Evaluasi*, *Kalibrasi*.
  - Filter Periode: *Semua Waktu*, *Hari ini*, *Minggu ini*, *Bulan ini*, dan *Rentang Tanggal Khusus (Start - End Date)*.
  - Filter Urutan: *Tanggal Terbaru (Default)*, *Tanggal Terlama*, *Nama (A-Z)*.
- **Hasil Pencarian & Empty State:**
  - Menampilkan jumlah notulensi yang cocok secara dinamis.
  - Tampilan khusus *"Notulensi tidak ditemukan"* dengan tombol reset cepat jika pencarian nihil.
- **Pagination:** Navigasi halaman yang rapi saat data bertambah banyak.

### 5. Fitur Pratinjau, Detail, Edit, Hapus & Cetak PDF
- **Preview Notulensi:** Melihat format rapi sebelum data disimpan ke database.
- **Detail Notulensi:** Modal eksekutif menampilkan seluruh arsip meeting secara menyeluruh.
- **Edit Notulensi:** Mengubah kembali isi notulensi yang telah tersimpan.
- **Hapus Notulensi:** Menghapus dokumen dengan modal konfirmasi keamanan.
- **Download PDF Korporat:** Mengunduh dokumen resmi format A4 berstandar korporat yang memuat kop surat perusahaan, nomor dokumen, tabel peserta, hasil meeting, tabel action plan & PIC, serta kolom tanda tangan.

### 6. Integrasi Firebase Firestore Real-Time
- **Project ID:** `kabinnet12-d8305`
- **Penyimpanan:** Data tersimpan permanen di cloud Firebase Firestore pada dokumen `app/notulensiData`.
- **Real-Time Sync:** Menggunakan listener `onSnapshot` sehingga setiap perubahan data langsung tersinkronkan ke seluruh perangkat dan browser lain tanpa perlu refresh.
- **Dual Layer Caching:** Disertai cache lokal `localStorage` untuk kecepatan render instan dan perlindungan saat jaringan offline.

---

## 🚀 Cara Menjalankan Aplikasi

### Opsi 1: Menjalankan dengan Local Web Server (Direkomendasikan)
Cukup klik dua kali file **`start.bat`** di dalam folder ini, atau jalankan perintah berikut di PowerShell:
```powershell
powershell -ExecutionPolicy Bypass -File .\serve.ps1
```
Browser default Anda akan terbuka secara otomatis di alamat:
👉 **`http://localhost:8089`**

### Opsi 2: Membuka Langsung File HTML
Buka file **`index.html`** langsung menggunakan browser modern (Google Chrome, Microsoft Edge, Firefox, atau Safari).

---

## ☁️ Deployment ke Firebase Hosting

Project ini sudah dilengkapi konfigurasi `.firebaserc` dan `firebase.json` untuk project `kabinnet12-d8305`.

Untuk melakukan deploy:
```bash
firebase use kabinnet12-d8305
firebase deploy --only hosting
```
Setelah deploy selesai, website dapat diakses secara publik melalui domain Firebase Hosting.

---

## 📁 Struktur File

```
TL NOTE/
├── index.html                 # Halaman utama Single Page Application (SPA)
├── css/
│   └── style.css              # Design system, warna biru #0A66FF, tipografi Inter, responsif
├── js/
│   ├── firebase-config.js     # Modul konfigurasi dan sinkronisasi real-time Firestore
│   └── app.js                 # Logika form, validasi, pencarian real-time, filter, pagination, PDF
├── serve.ps1                  # Web server statis ringan (PowerShell)
├── start.bat                  # Shortcut sekali klik untuk menjalankan server lokal
├── firebase.json              # Konfigurasi Firebase Hosting
├── .firebaserc                # Konfigurasi target project Firebase
└── README.md                  # Dokumentasi teknis aplikasi
```
