# 🔧 Data Schema & Technical Documentation

## Frontend Architecture

### Teknologi yang Digunakan
- **HTML5** - Struktur halaman
- **CSS3** - Styling & responsiveness
- **JavaScript (Vanilla)** - Interaktivitas dan loading data dinamis
- **JSON** - Format data
- **Fetch API** - Komunikasi data async

---

## Data Flow Diagram

```
┌─────────────────┐
│  index.html     │
│  (CMS Config)   │
└────────┬────────┘
         │
         ├─→ fetch('data/site.json')
         ├─→ fetch('data/berita.json')
         ├─→ fetch('data/galeri.json')
         ├─→ fetch('data/potensi.json')
         ├─→ fetch('data/layanan.json')      [NEW]
         └─→ fetch('data/transparansi.json') [NEW]
              │
              ├─→ applySiteSettings()
              ├─→ renderBeritaGrid()
              ├─→ renderGaleriGrid()
              ├─→ renderPotensiGrid()
              ├─→ renderLayananGrid()       [NEW]
              └─→ renderTransparansiSection() [NEW]
                   │
                   └─→ [Update DOM dengan data]
```

---

## JSON Schema Details

### 1. berita.json
```typescript
interface BeritaItem {
  cat: string;           // Kategori berita
  emoji?: string;        // Emoji icon (optional)
  bg?: string;          // Path ke gambar/warna background
  date: string;         // Tanggal publikasi (format string)
  author: string;       // Nama penulis
  readtime: string;     // Estimasi waktu baca
  title: string;        // Judul (required)
  excerpt: string;      // Ringkasan singkat
  body?: string;        // Konten HTML (optional)
  tags?: string[];      // Array tag untuk kategorisasi
}

interface BeritaFile {
  items: BeritaItem[];
}
```

### 2. galeri.json
```typescript
interface GaleriItem {
  emoji?: string;       // Emoji icon
  bg: string;          // Path gambar atau warna
  label: string;       // Judul foto (required)
  desc?: string;       // Deskripsi singkat
}

interface GaleriFile {
  items: GaleriItem[];
}
```

### 3. potensi.json
```typescript
interface PotensiStats {
  num: string;         // Angka/statistik
  lbl: string;         // Label statistik
}

interface PotensiProduk {
  icon: string;        // Icon/emoji
  name: string;        // Nama produk
  desc?: string;       // Deskripsi produk
}

interface PotensiItem {
  cat: string;         // Kategori (Pertanian, UMKM, Wisata)
  emoji?: string;      // Emoji icon
  bg?: string;         // Path gambar
  title: string;       // Judul potensi
  stats?: PotensiStats[];      // Array statistik
  desc?: string;       // Deskripsi HTML
  produk?: PotensiProduk[];    // Array produk/daya tarik
  tags?: string[];     // Array tag
}

interface PotensiFile {
  items: PotensiItem[];
}
```

### 4. layanan.json (NEW)
```typescript
interface LayananItem {
  icon: string;        // Icon/emoji (contoh: 🏢)
  title: string;       // Nama layanan (required)
  description: string; // Penjelasan layanan
}

interface LayananFile {
  items: LayananItem[];
}
```

**Contoh:**
```json
{
  "items": [
    {
      "icon": "🏢",
      "title": "Surat Keterangan Usaha",
      "description": "Untuk keperluan perizinan usaha UMKM dan bisnis lokal"
    },
    {
      "icon": "💸",
      "title": "Surat Keterangan Tidak Mampu",
      "description": "Untuk akses beasiswa, layanan kesehatan gratis, dll"
    }
  ]
}
```

### 5. transparansi.json (NEW)
```typescript
interface TransparansiBudget {
  year: number;           // Tahun anggaran
  title: string;          // Judul anggaran
  total: string;          // Total anggaran (format text)
  totalAmount: number;    // Total anggaran (nilai angka)
}

interface TransparansiDocument {
  icon: string;          // Icon dokumen
  title: string;         // Nama dokumen
  url: string;          // URL download/link
}

interface TransparansiAllocation {
  name: string;         // Nama alokasi (bisa include icon)
  percentage: number;   // Persentase (0-100)
  amount: number;       // Jumlah dalam rupiah
}

interface TransparansiFile {
  budget: TransparansiBudget;
  documents?: TransparansiDocument[];
  allocations?: TransparansiAllocation[];
}
```

**Contoh:**
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
      "url": "https://example.com/apbdes-2026.pdf"
    },
    {
      "icon": "📊",
      "title": "Realisasi Q1 2026.pdf",
      "url": "https://example.com/realisasi-q1.pdf"
    }
  ],
  "allocations": [
    {
      "name": "🏗️ Pembangunan Infrastruktur",
      "percentage": 40,
      "amount": 480000000
    },
    {
      "name": "👥 Pemberdayaan Masyarakat",
      "percentage": 25,
      "amount": 300000000
    },
    {
      "name": "🏥 Kesehatan & Sosial",
      "percentage": 20,
      "amount": 240000000
    },
    {
      "name": "🎓 Pendidikan & Budaya",
      "percentage": 10,
      "amount": 120000000
    },
    {
      "name": "🏢 Operasional Pemerintahan",
      "percentage": 5,
      "amount": 60000000
    }
  ]
}
```

### 6. site.json
```typescript
interface SiteConfig {
  villageName: string;      // Nama desa
  subdistrict: string;      // Kecamatan
  regency: string;          // Kabupaten/Kota
  villageHeadName: string;  // Nama kepala desa
  villageHeadTitle: string; // Jabatan
  villageHeadPeriod: string; // Periode masa jabatan
  villageHeadPhoto?: string;  // Path foto kepala desa
  villagePhoto?: string;      // Path foto kantor desa
  villageHeadPhone?: string;  // Nomor telepon (optional)
}
```

---

## Struktur DOM & JavaScript Functions

### Global Variables
```javascript
let siteConfig = null;        // Konfigurasi situs
let beritaData = [];          // Data berita
let galeriData = [];          // Data galeri
let potensiData = [];         // Data potensi
let layananData = [];         // Data layanan [NEW]
let transparansiData = null;  // Data transparansi [NEW]
```

### Key Functions

#### initDynamicContent()
Fungsi utama yang dijalankan saat page load. Ini:
1. Fetch semua JSON files secara parallel
2. Parse data dan assign ke global variables
3. Call semua render functions
4. Apply site settings (nama desa, kepala desa, dll)

```javascript
async function initDynamicContent() {
  // Fetch all data
  const [siteRes, beritaRes, galeriRes, potensiRes, 
         layananRes, transparansiRes] = await Promise.all([...]);
  
  // Parse responses
  // Assign to globals
  // Render ke DOM
}
```

#### renderBeritaGrid()
Render berita ke grid dengan format card:
```javascript
function renderBeritaGrid() {
  const grid = document.getElementById('beritaGrid');
  grid.innerHTML = beritaData.map((d, idx) => `
    <div class="berita-card" onclick="openBerita(${idx})">
      <!-- Card structure -->
    </div>
  `).join('');
}
```

#### renderLayananGrid() [NEW]
Render daftar layanan:
```javascript
function renderLayananGrid() {
  const container = document.getElementById('layananListContainer');
  const html = layananData.map(item => `
    <div class="layanan-item">
      <div class="layanan-icon">${item.icon}</div>
      <div class="layanan-info">
        <h4>${item.title}</h4>
        <p>${item.description}</p>
      </div>
      <div class="layanan-arrow">→</div>
    </div>
  `).join('');
  container.innerHTML = html;
}
```

#### renderTransparansiSection() [NEW]
Render transparansi anggaran:
```javascript
function renderTransparansiSection() {
  // Update budget info (APBDes year, total)
  // Update documents list
  // Update allocations bars
}
```

#### Utility Functions
- `resolveImagePath(bg)` - Resolve path gambar (local/remote)
- `buildBgWrapperAndContent(bg, emoji, title)` - Build background+content
- `renderBody(raw)` - Parse markdown images to HTML
- `applySiteSettings()` - Apply site config ke DOM

---

## Event Listeners & Interactivity

### Mobile Navigation
```javascript
toggleMobileNav()     // Toggle hamburger menu
openMobileNav()       // Open drawer
closeMobileNav()      // Close drawer
```

### Detail View (Modal)
```javascript
openDetail(html)      // Buka detail modal
closeDetail()         // Tutup detail modal
openBerita(idx)       // Buka detail berita
openPotensi(idx)      // Buka detail potensi
```

### Lightbox (Galeri)
```javascript
openLightbox(idx)     // Buka lightbox galeri
closeLightbox()       // Tutup lightbox
lightboxNext()        // Foto berikutnya
lightboxPrev()        // Foto sebelumnya
lightboxGoto(idx)     // Ke foto tertentu
```

### Sharing
```javascript
shareWA(title)        // Share ke WhatsApp
copyLink()            // Copy link ke clipboard
```

---

## Image Path Resolution

API menggunakan image resolver untuk handle berbagai format:

```javascript
function resolveImagePath(bg) {
  if (!bg) return bg;
  
  const val = String(bg).trim();
  
  // Jika URL absolute, return as-is
  if (/^https?:\/\//i.test(val)) return val;
  
  // Jika path relatif ke /media, prepend BASE_ROOT
  if (/^\/?media\//i.test(val)) {
    return BASE_ROOT + val.replace(/^\//, "");
  }
  
  // Default: prepend MEDIA_ROOT
  return MEDIA_ROOT + val;
}
```

**Paths yang valid:**
```
/media/gambar.jpg
media/gambar.jpg
gambar.jpg
https://example.com/gambar.jpg
wallhaven-p83rxe (auto prefix: MEDIA_ROOT + gambar)
```

---

## CSS Architecture

### Color Scheme (CSS Variables)
```css
:root {
  --hijau: #1a5c38;          /* Primary green */
  --hijau-muda: #2d8653;     /* Light green */
  --hijau-terang: #4caf78;   /* Bright green */
  --emas: #c8a84b;           /* Gold */
  --emas-terang: #e2c56f;    /* Light gold */
  --krem: #f8f4ec;           /* Cream */
  --putih: #ffffff;          /* White */
  --gelap: #0f2419;          /* Dark */
  --abu: #f0ede5;            /* Gray */
  --teks: #2c3e2d;           /* Text color */
}
```

### Layout Classes
- `.section-header` - Header untuk setiap section
- `.section-title` - Judul besar section
- `.section-desc` - Deskripsi section
- `.animate` - Animation class (fade-in saat visible)
- `.berita-card` - Card berita
- `.galeri-item` - Item galeri (masonry)
- `.layanan-item` - Item layanan [NEW]
- `.anggaran-item` - Item alokasi anggaran [NEW]

---

## Responsive Design Breakpoints

```css
/* Desktop: 1200px+ */
/* Tablet: 768px - 1199px */
/* Mobile: < 768px */
```

---

## Performance Considerations

1. **Lazy Loading**: Images di load saat visible
2. **Intersection Observer**: Untuk scroll animations
3. **Promise.all()**: Parallel fetch untuk fast loading
4. **CSS Animations**: Smooth scroll & transitions
5. **Minimal JavaScript**: Vanilla JS, no frameworks

---

## Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

---

## Error Handling

### JSON Load Errors
Jika fetch gagal, fallback ke empty data:
```javascript
beritaRes.ok ? beritaRes.json() : Promise.resolve({ items: [] })
```

### Missing Elements
Render functions check elemen existence:
```javascript
const grid = document.getElementById('beritaGrid');
if (!grid || !beritaData.length) return;
```

---

## Future Enhancements

### Potential Features
- [ ] Search functionality
- [ ] Filter by category
- [ ] Pagination
- [ ] Comments on news
- [ ] Newsletter signup
- [ ] Contact form integration
- [ ] Multi-language support
- [ ] Dark mode
- [ ] Social media feed embed
- [ ] Analytics integration

---

## Development Tips

### Testing
1. Check browser console untuk errors
2. Inspect Network tab untuk failed fetches
3. Test pada berbagai screen sizes
4. Validate JSON files di jsonlint.com

### Adding New Section
1. Create `data/section-name.json`
2. Add to `.pages.yml` config
3. Update `initDynamicContent()` fetch
4. Add render function
5. Create HTML container
6. Test rendering

### Debugging
```javascript
// Browser console:
console.log(beritaData);        // Check data
console.log(siteConfig);        // Check config
localStorage.clear();           // Clear cache
location.reload(true);          // Hard refresh
```

---

**Technical Documentation v1.0**
**Last Updated: 17 Februari 2026**
