# ⚡ Quick Reference - CMS Fields

## ✏️ Layanan Administrasi (Services)

**File**: `data/layanan.json`
**Edit in CMS**: Layanan Administrasi

### Fields
| Field | Type | Required | Example |
|-------|------|----------|---------|
| Icon | String | ✅ Yes | 🏢 |
| Nama Layanan | String | ✅ Yes | Surat Keterangan Usaha |
| Deskripsi | Text | ✅ Yes | Untuk keperluan perizinan usaha... |

### Sample Services
```
🏢 Surat Keterangan Usaha
💸 Surat Keterangan Tidak Mampu
🏠 Surat Domisili
🪪 Surat Pengantar KTP/KK
👶 Surat Kelahiran/Kematian
📋 Surat Keterangan Domisili Usaha
🔔 Surat Pemberitahuan
⚖️ Surat Pernyataan
🗳️ Surat Undangan
🏛️ Surat Rekomendasi
```

---

## 📊 Transparansi Anggaran (Budget Transparency)

**File**: `data/transparansi.json`
**Edit in CMS**: Transparansi Anggaran

### Section 1: Budget Info
| Field | Type | Required |
|-------|------|----------|
| Tahun Anggaran | Number | ✅ Yes |
| Judul Anggaran | String | ✅ Yes |
| Total (Text) | String | ✅ Yes |
| Total (Angka) | Number | ✅ Yes |

**Example**:
- Tahun: `2025`
- Judul: `Anggaran Pendapatan & Belanja Desa`
- Total Text: `1,2 M`
- Total Amount: `1200000000`

### Section 2: Dokumen Transparansi
| Field | Type | Required |
|-------|------|----------|
| Icon | String | ✅ Yes |
| Nama Dokumen | String | ✅ Yes |
| URL Dokumen | String | ✅ Yes |

**Example**:
```
Icon: 📄
Nama: APBDes 2025.pdf
URL: https://example.com/apbdes-2025.pdf
```

### Section 3: Alokasi Anggaran
| Field | Type | Required |
|-------|------|----------|
| Nama Alokasi | String | ✅ Yes |
| Persentase | Number | ✅ Yes |
| Jumlah | Number | ✅ Yes |

**Example**:
```
Nama: 🏗️ Pembangunan Infrastruktur
Persentase: 40
Jumlah: 480000000
```

### Allocation Categories (Típical)
- 🏗️ Pembangunan Infrastruktur (40%)
- 👥 Pemberdayaan Masyarakat (25%)
- 🏥 Kesehatan & Sosial (20%)
- 🎓 Pendidikan & Budaya (10%)
- 🏢 Operasional Pemerintahan (5%)

---

## 📰 Berita (News)

**File**: `data/berita.json`
**Edit in CMS**: Berita & Agenda

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| Kategori | String | ✅ | Berita Desa, Pengumuman, Agenda |
| Emoji | String | ❌ | Visual icon |
| Gambar | Image | ❌ | Or use color gradient |
| Tanggal | String | ❌ | "10 Februari 2025" |
| Penulis | String | ❌ | Author name |
| Lama Baca | String | ❌ | "3 menit baca" |
| **Judul** | String | ✅ | Required |
| Ringkasan | Text | ❌ | Short excerpt |
| Isi Berita | Rich Text | ❌ | Full HTML content |
| Tag | Array | ❌ | Multiple tags |

### Kategori Options
- Berita Desa
- Pengumuman
- Agenda
- Keputusan Pemerintah
- Event

---

## 📸 Galeri (Gallery)

**File**: `data/galeri.json`
**Edit in CMS**: Galeri Kegiatan

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| Emoji | String | ❌ | Visual icon |
| Gambar | Image | ✅ | Photo required |
| Judul Foto | String | ✅ | Required |
| Deskripsi | Text | ❌ | Short description |

### Photo Categories
- 🌾 Pertanian & Perkebunan
- 💉 Kesehatan & Posyandu
- 🏆 Perayaan & PHBN
- 🏗️ Pembangunan
- 🌳 Lingkungan & Gotong Royong
- 👨‍👩‍👧‍👦 Keluarga & Pendidikan
- 🏪 UMKM & Perdagangan

---

## 📊 Potensi Desa (Village Potential)

**File**: `data/potensi.json`
**Edit in CMS**: Potensi Desa

### Main Fields
| Field | Type | Required |
|-------|------|----------|
| Kategori | String | ✅ |
| Emoji | String | ❌ |
| Gambar | Image | ❌ |
| Judul | String | ✅ |
| Deskripsi | Rich Text | ❌ |
| Tag | Array | ❌ |

### Sub-Sections

#### Statistik
| Field | Type | Required |
|-------|------|----------|
| Angka | String | ✅ |
| Label | String | ✅ |

#### Produk/Daya Tarik
| Field | Type | Required |
|-------|------|----------|
| Icon | String | ✅ |
| Nama | String | ✅ |
| Deskripsi | Text | ❌ |

### Example Categories
- 🌾 Pertanian
- 🛍️ UMKM
- 🌊 Wisata
- 🐟 Perikanan
- 🎨 Kerajinan
- 🌿 Perkebunan
- 🏭 Industri Lokal

---

## ⚙️ Pengaturan Situs (Site Settings)

**File**: `data/site.json`
**Edit in CMS**: Pengaturan Situs

| Field | Type | Required | Used In |
|-------|------|----------|---------|
| Nama Desa | String | ✅ | Navbar, Hero, Footer |
| Kecamatan | String | ✅ | Navbar |
| Kabupaten | String | ✅ | Navbar |
| Nama Kepala Desa | String | ✅ | Profil, Sambutan |
| Jabatan Kepala Desa | String | ✅ | Profil |
| Periode Jabatan | String | ✅ | Profil |
| Foto Kepala Desa | Image | ❌ | Profil Section |
| Foto Kantor Desa | Image | ❌ | Profil Section |

---

## 🖼️ Image Upload Guidelines

### Recommended Sizes
```
Berita (bg):        1200 x 600 px  → JPG (50-100KB)
Galeri:             800 x 600 px   → JPG/PNG
Potensi (bg):       1000 x 800 px  → JPG
Kepala Desa:        400 x 500 px   → JPG
Kantor Desa:        800 x 600 px   → JPG
```

### File Naming
- Use lowercase
- No spaces (use `_` or `-`)
- Keep descriptive
- Examples:
  - `gotong_royong.jpg`
  - `posyandu-balita.png`
  - `kepala-desa-yongki.jpg`

### Path
All files auto-save to `/media/` folder

---

## 🎨 Emoji Quick List

### Common Service Icons
🏢 Office
💸 Money
🏠 House
🪪 ID Card
👶 Baby
📋 Document
🏥 Health
📧 Mail
📞 Phone
📲 Mobile

### Common Category Icons
🌾 Agriculture
🛍️ Shop/Commerce
🌊 Water/Tourism
🐟 Fish
🎨 Craft
🌿 Plants
🏭 Industry
🍽️ Food
🎓 Education
🏆 Achievement

### Common Budget Icons
🏗️ Infrastructure
👥 People/Social
🏥 Health
🎓 Education
🏢 Operations
🌳 Environment
🛣️ Roads
💧 Water
⚡ Energy
🎪 Culture

---

## ✅ CMS Checklist

### Monthly Tasks
- [ ] Update Berita (news articles)
- [ ] Add Galeri (new photos)
- [ ] Review Layanan (services info)
- [ ] Check Transparansi (budget updates)
- [ ] Update Potensi (if changes)

### Quarterly Tasks
- [ ] Verify Pengaturan (site settings)
- [ ] Update Kepala Desa info (if changed)
- [ ] Check Foto Kepala Desa (quality)
- [ ] Verify all links in Transparansi

### Yearly Tasks
- [ ] Update APBDes (budget year)
- [ ] Revise Potensi descriptions
- [ ] Add new Layanan services (if any)
- [ ] Update Periode Jabatan Kepala Desa

---

## 📱 Mobile Check

After updates, test on mobile:
- [ ] Services layout looks good
- [ ] Budget transparency readable
- [ ] Images load properly
- [ ] Text not cut off
- [ ] Links clickable

---

## 🆘 Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| Section doesn't show | Check JSON syntax at jsonlint.com |
| Images not loading | Verify file path: `/media/filename.jpg` |
| Text formatting broken | Check HTML tags are closed properly |
| CMS won't save | Check for special characters in fields |
| Data not updating | Clear browser cache (Ctrl+Shift+Delete) |

---

### Quick Links
- 📖 Full Guide: See `DOKUMENTASI.md`
- 🔧 Technical: See `TECHNICAL.md`
- 📦 Setup Info: See `README.md`

---

**Last Updated: 17 Februari 2026**
