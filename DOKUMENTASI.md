# 📖 Dokumentasi Website Desa Garahan

## Ringkasan Struktur Website

Website Desa Garahan menggunakan **Page CMS** untuk mengelola konten secara dinamis. Semua konten dapat diubah melalui interface CMS tanpa perlu mengubah kode.

---

## 📋 Daftar Halaman & Bagian yang Dapat Dikelola

### 1. **HOMEPAGE** (Halaman Depan)
- **File**: `index.html`
- **Tipe**: Raw HTML
- **Isi**: Struktur halaman utama (navbar, hero, footer)
- **Edit via**: CMS → Halaman Depan

---

### 2. **BERITA & AGENDA** 
- **File**: `data/berita.json`
- **Tipe**: JSON
- **Isi**: Artikel berita, pengumuman, dan agenda desa
- **Struktur Data**:
  ```json
  {
    "items": [
      {
        "cat": "Kategori Berita",
        "emoji": "🌱",
        "bg": "/media/gambar.jpg",
        "date": "10 Februari 2025",
        "author": "Nama Penulis",
        "readtime": "3 menit baca",
        "title": "Judul Berita",
        "excerpt": "Ringkasan singkat",
        "body": "Isi lengkap HTML",
        "tags": ["tag1", "tag2"]
      }
    ]
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Kategori - untuk klasifikasi berita
  - ✏️ Emoji - ikon visual
  - ✏️ Gambar/Background - upload gambar
  - ✏️ Tanggal - kapan berita dipublikasikan
  - ✏️ Penulis - nama penulis
  - ✏️ Lama Baca - estimasi waktu baca
  - ✏️ Judul - wajib diisi
  - ✏️ Ringkasan - preview singkat
  - ✏️ Isi Berita - konten lengkap (HTML/Rich Text)
  - ✏️ Tag - label untuk kategorisasi

---

### 3. **GALERI KEGIATAN**
- **File**: `data/galeri.json`
- **Tipe**: JSON
- **Isi**: Foto-foto kegiatan desa dengan lightbox viewer
- **Struktur Data**:
  ```json
  {
    "items": [
      {
        "emoji": "🌾",
        "bg": "/media/foto.jpg",
        "label": "Judul Foto",
        "desc": "Deskripsi singkat"
      }
    ]
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Emoji - ikon visual
  - ✏️ Gambar/Background - foto kegiatan
  - ✏️ Judul Foto - wajib diisi
  - ✏️ Deskripsi - keterangan singkat

---

### 4. **LAYANAN ADMINISTRASI DESA** ⭐ (BARU)
- **File**: `data/layanan.json`
- **Tipe**: JSON
- **Isi**: Daftar layanan administratif yang dapat diajukan online
- **Struktur Data**:
  ```json
  {
    "items": [
      {
        "icon": "🏢",
        "title": "Surat Keterangan Usaha",
        "description": "Untuk keperluan perizinan usaha UMKM"
      }
    ]
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Icon/Emoji - visual identifier
  - ✏️ Nama Layanan - wajib diisi
  - ✏️ Deskripsi Layanan - penjelasan lengkap

**Contoh Layanan**:
- Surat Keterangan Usaha
- Surat Keterangan Tidak Mampu
- Surat Domisili
- Surat Pengantar KTP/KK
- Surat Kelahiran/Kematian

---

### 5. **POTENSI DESA**
- **File**: `data/potensi.json`
- **Tipe**: JSON
- **Isi**: Potensi unggulan desa (pertanian, UMKM, wisata, dll)
- **Struktur Data**:
  ```json
  {
    "items": [
      {
        "cat": "Kategori Potensi",
        "emoji": "🌾",
        "bg": "/media/gambar.jpg",
        "title": "Judul Potensi",
        "stats": [
          { "num": "180 Ha", "lbl": "Luas Sawah" }
        ],
        "desc": "Deskripsi lengkap HTML",
        "produk": [
          {
            "icon": "🌾",
            "name": "Nama Produk",
            "desc": "Deskripsi produk"
          }
        ],
        "tags": ["tag1", "tag2"]
      }
    ]
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Kategori - jenis potensi
  - ✏️ Emoji - ikon visual
  - ✏️ Gambar/Background - foto potensi
  - ✏️ Judul - nama potensi
  - ✏️ Statistik Ringkas - data/angka penting
  - ✏️ Deskripsi - penjelasan (HTML)
  - ✏️ Produk/Daya Tarik - item-item unggulan
  - ✏️ Tag - label kategorisasi

---

### 6. **TRANSPARANSI ANGGARAN** ⭐ (BARU)
- **File**: `data/transparansi.json`
- **Tipe**: JSON
- **Isi**: Informasi anggaran, dokumen, dan alokasi dana desa
- **Struktur Data**:
  ```json
  {
    "budget": {
      "year": 2025,
      "title": "Anggaran Pendapatan & Belanja Desa",
      "total": "1,2 M",
      "totalAmount": 1200000000
    },
    "documents": [
      {
        "icon": "📄",
        "title": "APBDes 2026.pdf",
        "url": "https://link-dokumen.pdf"
      }
    ],
    "allocations": [
      {
        "name": "🏗️ Pembangunan Infrastruktur",
        "percentage": 40,
        "amount": 480000000
      }
    ]
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Tahun Anggaran
  - ✏️ Judul Anggaran
  - ✏️ Total Anggaran (text & angka)
  - ✏️ Dokumen Transparansi (icon, nama, URL)
  - ✏️ Alokasi Anggaran (nama, persentase, jumlah)

---

### 7. **PENGATURAN SITUS**
- **File**: `data/site.json`
- **Tipe**: JSON
- **Isi**: Informasi umum desa (nama, lokasi, kepala desa, foto)
- **Struktur Data**:
  ```json
  {
    "villageName": "Desa Garahan",
    "subdistrict": "Silo",
    "regency": "Jember",
    "villageHeadName": "Yongki",
    "villageHeadTitle": "Kepala Desa Garahan",
    "villageHeadPeriod": "Masa Jabatan 2022 – 2030",
    "villageHeadPhoto": "/media/foto-kepala-desa.jpg",
    "villagePhoto": "/media/foto-kantor-desa.jpg"
  }
  ```
- **Fields yang Dapat Diubah**:
  - ✏️ Nama Desa
  - ✏️ Kecamatan
  - ✏️ Kabupaten/Kota
  - ✏️ Nama Kepala Desa
  - ✏️ Jabatan Kepala Desa
  - ✏️ Periode Jabatan Kepala Desa
  - ✏️ Foto Kepala Desa
  - ✏️ Foto Kantor Desa

---

## 🗂️ Struktur Folder Proyek

```
garahan/
├── index.html              # Halaman utama (dinamis)
├── .pages.yml              # Konfigurasi CMS
├── data/
│   ├── berita.json         # Artikel & pengumuman
│   ├── galeri.json         # Foto kegiatan
│   ├── layanan.json        # Layanan administrasi ⭐ BARU
│   ├── potensi.json        # Potensi desa
│   ├── transparansi.json   # Transparansi anggaran ⭐ BARU
│   └── site.json           # Pengaturan situs
└── media/                  # Upload foto & gambar
    ├── wallhaven-p83rxe.jpg
    ├── cafe-garahan-5.jpg
    └── ... (file gambar lainnya)
```

---

## ⚙️ Bagaimana Cara Menambah Konten?

### Menambah Berita Baru
1. Buka **CMS → Berita & Agenda**
2. Klik **"Tambah Item Baru"**
3. Isi form:
   - Kategori (Berita Desa, Pengumuman, Agenda, dll)
   - Emoji (pilih ikon yang sesuai)
   - Gambar (upload atau gunakan warna gradient)
   - Tanggal publikasi
   - Penulis
   - Lama baca (estimasi)
   - **Judul** (wajib)
   - Ringkasan singkat
   - Isi berita (bisa pakai format HTML)
   - Tag (untuk kategorisasi)
4. **Simpan** → Berita akan tampil di halaman Berita

### Menambah Foto Galeri
1. Buka **CMS → Galeri Kegiatan**
2. Klik **"Tambah Foto"**
3. Isi:
   - Emoji (visual identifier)
   - Gambar/Foto
   - Judul Foto
   - Deskripsi singkat
4. **Simpan** → Foto akan tampil di galeri dengan lightbox

### Menambah Layanan Baru ⭐
1. Buka **CMS → Layanan Administrasi**
2. Klik **"Tambah Layanan"**
3. Isi:
   - Icon/Emoji (contoh: 🏢, 📋, 🪪, dll)
   - Nama Layanan (contoh: "Surat Keterangan Usaha")
   - Deskripsi (penjelasan singkat)
4. **Simpan** → Layanan akan tampil di bagian Layanan

### Menambah Potensi Desa
1. Buka **CMS → Potensi Desa**
2. Klik **"Tambah Potensi"**
3. Isi:
   - Kategori (Pertanian, UMKM, Wisata)
   - Emoji
   - Gambar
   - Judul
   - Statistik (angka penting)
   - Deskripsi lengkap
   - Produk/Daya Tarik (list item)
   - Tag
4. **Simpan**

### Update Transparansi Anggaran ⭐
1. Buka **CMS → Transparansi Anggaran**
2. Update:
   - **Budget**: Tahun, judul, total anggaran
   - **Documents**: Tambah dokumen PDF/file
   - **Allocations**: Alokasi anggaran per bidang
3. **Simpan**

### Update Informasi Situs
1. Buka **CMS → Pengaturan Situs**
2. Update:
   - Nama desa
   - Lokasi (kecamatan, kabupaten)
   - Data kepala desa (nama, jabatan, periode)
   - Foto kepala desa & kantor desa
3. **Simpan** → Otomatis terupdate di seluruh halaman

---

## 🎨 Tips Upload Gambar

### Ukuran Optimal
- **Berita (bg)**: 1200x600px, format JPG (optimal: 50-100KB)
- **Galeri**: 800x600px, format JPG/PNG
- **Potensi (bg)**: 1000x800px, format JPG
- **Kepala Desa**: 400x500px, format JPG
- **Kantor Desa**: 800x600px, format JPG

### Nama File
- Gunakan huruf kecil, tanpa spasi
- Contoh: `gotong_royong.jpg`, `posyandu_2025.png`
- Hindari karakter khusus

---

## 📱 Bagian-Bagian Website yang Dinamis

| Bagian | Data Source | Editable |
|--------|------------|----------|
| **Navbar** | site.json | ✅ (melalui Pengaturan) |
| **Hero Section** | Hardcoded | ❌ |
| **Quick Access** | Hardcoded | ❌ |
| **Sambutan Kepala Desa** | site.json | ✅ (Pengaturan) |
| **Profil Desa** | site.json | ✅ (Pengaturan) |
| **Data Desa** | Hardcoded | ❌ |
| **Berita & Informasi** | berita.json | ✅ |
| **Galeri Kegiatan** | galeri.json | ✅ |
| **Layanan Administrasi** | layanan.json | ✅ |
| **Potensi Desa** | potensi.json | ✅ |
| **Transparansi Anggaran** | transparansi.json | ✅ |
| **Footer** | site.json | ✅ (Pengaturan) |

---

## 🔧 Folder Media

Semua gambar, foto, dan file media harus disimpan di folder:
```
/media/
```

Ketika upload, CMS otomatis menyimpan file ke folder ini dengan path:
```
/media/nama-file.jpg
```

---

## 📝 Contoh Data Lengkap

### Contoh Berita Lengkap
```json
{
  "cat": "Berita Desa",
  "emoji": "🌱",
  "bg": "/media/gotong_royong.jpg",
  "date": "10 Februari 2025",
  "author": "Admin Desa",
  "readtime": "3 menit baca",
  "title": "Pelaksanaan Gotong Royong Pembersihan Sungai",
  "excerpt": "Seluruh warga bersama perangkat desa melaksanakan kegiatan gotong royong",
  "body": "Pada hari Minggu, 10 Februari 2025...",
  "tags": ["Lingkungan", "Gotong Royong", "Kebersihan"]
}
```

### Contoh Layanan Lengkap
```json
{
  "icon": "🏢",
  "title": "Surat Keterangan Usaha",
  "description": "Untuk keperluan perizinan usaha UMKM dan bisnis lokal"
}
```

### Contoh Transparansi Lengkap
```json
{
  "budget": {
    "year": 2025,
    "title": "Anggaran Pendapatan & Belanja Desa",
    "total": "1,2 M",
    "totalAmount": 1200000000
  },
  "documents": [
    {
      "icon": "📄",
      "title": "APBDes 2025.pdf",
      "url": "https://example.com/apbdes-2025.pdf"
    }
  ],
  "allocations": [
    {
      "name": "🏗️ Pembangunan Infrastruktur",
      "percentage": 40,
      "amount": 480000000
    }
  ]
}
```

---

## ✅ Checklist Konten yang Dapat Dikelola

- [x] Artikel & Berita
- [x] Pengumuman & Agenda
- [x] Foto Galeri
- [x] Layanan Administrasi
- [x] Potensi Unggulan Desa
- [x] Transparansi Anggaran
- [x] Informasi Kepala Desa
- [x] Data Lokasi Desa
- [x] Foto Kantor Desa

---

## 🚀 Next Steps

Untuk semakin lengkap, pertimbangkan untuk menambahkan:
- [ ] **Contact Form** - untuk pengajuan layanan online
- [ ] **Testimonial** - cerita dari warga
- [ ] **Slider Berita** - headline di homepage
- [ ] **Video** - dokumentasi kegiatan
- [ ] **Perangkat Desa** - profil struktur organisasi

---

**Dokumentasi ini dibuat: 17 Februari 2026**
**Terakhir diupdate: 17 Februari 2026**
