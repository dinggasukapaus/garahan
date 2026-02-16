# 🔍 SEO Setup Guide - Desa Garahan Website

## 📋 SEO yang Sudah Diterapkan

✅ Meta tags (description, keywords, robots)
✅ Open Graph tags (untuk social media sharing)
✅ Twitter Card tags
✅ Canonical URLs
✅ Structured Data (Schema.org JSON-LD)
✅ Sitemap.xml
✅ robots.txt
✅ Favicon & Apple Touch Icon
✅ Responsive design (mobile-first)
✅ Fast loading optimization
✅ Proper heading hierarchy (H1, H2, H3)
✅ Internal linking structure
✅ Image alt text (untuk berita & galeri)
✅ Preconnect untuk external resources

---

## 🚀 Setup di Hostinger

### Step 1: Upload Website ke Hostinger

1. **Login ke Hostinger Control Panel**
   - Buka https://www.hostinger.com/cpanel
   - Login dengan email & password

2. **Upload Files menggunakan File Manager**
   - Go to: **File Manager** → pilih folder **public_html** atau **www**
   - Upload seluruh folder `garahan` ke hosting
   - Pastikan direktori structure:
     ```
     public_html/
     ├── index.html
     ├── robots.txt          ← Penting untuk SEO
     ├── sitemap.xml         ← Penting untuk SEO
     ├── data/
     ├── media/
     └── ... (file lainnya)
     ```

3. **Alternative: Git Integration** (Lebih mudah untuk update)
   - Go to: **Hostinger → Settings → Git**
   - Connect GitHub repository
   - Auto-push/deploy saat commit

---

### Step 2: Domain Configuration

1. **Koneksikan Domain ke Hostinger**
   - Go to: **Domains & Hosting → Your Domain → Manage**
   - Pastikan DNS pointing ke Hostinger
   - DNS records:
     ```
     A Record: 76.76.19.XXX (Hostinger IP)
     AAAA Record: 2001:4860:4864::8844 (IPv6)
     ```

2. **Setup SSL Certificate (HTTPS)** ⭐ PENTING untuk SEO
   - Go to: **Security → SSL Certificate**
   - Options:
     - ✅ Auto-generated (Free Let's Encrypt) - Recommended
     - ✅ Self-signed
   - Enable di hosting control panel
   - Hostinger auto-renews setiap tahun

3. **Force HTTPS Redirect**
   - Go to: **Hostinger → Settings → SSL**
   - Enable "Force HTTPS" / "Redirect to HTTPS"
   - Pastikan semua URL menggunakan `https://`

---

### Step 3: SSL Certificate Setup

1. **Enable HTTPS**
   ```
   http://garahan.desa.id → https://garahan.desa.id
   ```

2. **Update .htaccess** (jika menggunakan Apache)
   ```apache
   # Force HTTPS
   <IfModule mod_rewrite.c>
     RewriteEngine On
     RewriteCond %{HTTPS} off
     RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   </IfModule>

   # Remove www
   RewriteCond %{HTTP_HOST} ^www\. [NC]
   RewriteRule ^(.*)$ https://garahan.desa.id/$1 [L,R=301]
   ```

3. **Update Canonical URLs in HTML**
   - Ubah di `index.html`:
     ```html
     <link rel="canonical" href="https://garahan.desa.id/">
     ```
   - Ganti `https://garahan.desa.id/` dengan domain actual

---

### Step 4: Sitemap dan Robots Configuration

1. **Verify Sitemap Upload**
   - Upload `sitemap.xml` ke root folder
   - URL akan: `https://garahan.desa.id/sitemap.xml`

2. **Verify robots.txt Upload**
   - Upload `robots.txt` ke root folder
   - URL akan: `https://garahan.desa.id/robots.txt`

3. **Test dengan Browser**
   ```
   https://garahan.desa.id/sitemap.xml
   https://garahan.desa.id/robots.txt
   ```

---

## 🔧 Google Search Console Setup

### Step 1: Verify Domain
1. Go to https://search.google.com/search-console
2. Click **Add Property**
3. Pilih **Domain** (https://garahan.desa.id)
4. Follow verification (DNS, HTML, atau Upload file)

### Step 2: Submit Sitemap
1. Go to: **Sitemaps** section
2. Click **Add/test sitemap**
3. Enter: `sitemap.xml`
4. Click **Submit**

### Step 3: Configure Settings
1. **Preferred Domain**: Set to `https://garahan.desa.id` (without www)
2. **Coverage**: Monitor crawl errors
3. **Mobile Usability**: Check mobile compatibility
4. **Core Web Vitals**: Monitor loading speed

### Step 4: Monitor Performance
- Check **Performance** report untuk:
  - Impressions (berapa banyak muncul di search)
  - Clicks (berapa banyak yang diklik)
  - CTR (Click-through rate)
  - Average position

---

## 🔍 Bing Webmaster Tools Setup

1. Go to https://www.bing.com/webmasters
2. Click **Add a site**
3. Enter: `https://garahan.desa.id`
4. Verify domain
5. Submit sitemap: `sitemap.xml`

---

## 📧 Schema.org Validation

### Test Structured Data
1. Go to: https://schema.org/validator
   - Atau: https://search.google.com/test/rich-results

2. Enter dan test:
   - LocalBusiness schema
   - Organization schema
   - WebSite schema
   - BreadcrumbList schema

3. Pastikan tidak ada errors (warnings boleh)

---

## 📱 Mobile Optimization

✅ **Sudah dioptimasi:**
- Responsive design (mobile-first)
- Touch-friendly buttons
- Viewport meta tag
- Fast loading
- Mobile-friendly layout

### Test di Mobile Friendly Test
1. Go to: https://search.google.com/test/mobile-friendly
2. Enter: `https://garahan.desa.id`
3. Pastikan "Page is mobile friendly"

---

## ⚡ Performance Optimization untuk Hostinger

### Step 1: Enable Caching
1. Go to: **Hostinger → Settings → Caching**
   - Enable **Browser Caching**
   - Enable **Gzip Compression**
   - Enable **Cache 404 Pages** (optional)

2. Go to: **Hostinger → Performance**
   - Select PHP version: **8.1 or higher**
   - Enable **OpCache**
   - Enable **Redis Cache** (jika available)

### Step 2: Image Optimization
1. **Compress images sebelum upload**
   - Tools: TinyPNG, ImageOptim, Squoosh
   - Target: < 100KB per image

2. **Use WebP format**
   - Modern browsers support WebP
   - Size lebih kecil dari JPG/PNG

3. **Lazy Load Gambar**
   - HTML sudah optimal untuk lazy loading
   - Gambar load saat di-scroll ke view

### Step 3: Minimize CSS/JS
1. No external CSS/JS yang heavy
2. All CSS inline di `<style>` tag
3. JavaScript vanilla (no jQuery)
4. Total page size < 500KB ideal

### Step 4: CDN Setup (Optional tapi recommended)
1. **Hostinger CDN** (jika available)
   - Go to: **Hostinger → Settings → CDN**
   - Enable CDN untuk media files

2. **Alternative: Cloudflare** (Free)
   - Go to: https://www.cloudflare.com
   - Add domain
   - Change nameservers di Hostinger

---

## 📝 SEO Checklist Harian/Mingguan

### Daily
- [ ] Monitor Google Search Console
- [ ] Check website loading speed
- [ ] Verify sitemap updated

### Weekly
- [ ] Add new content (berita)
- [ ] Check mobile responsiveness
- [ ] Monitor search rankings

### Monthly
- [ ] Update sitemap.xml (new change dates)
- [ ] Add new metadata/schema
- [ ] Review Search Console metrics
- [ ] Check SSL certificate status
- [ ] Backup database & files

### Quarterly
- [ ] Update robots.txt (if needed)
- [ ] Review domain expiry
- [ ] Check hosting plan limits
- [ ] Security audit

---

## 🎯 SEO Targets

### Target Keywords (untuk Google ranking)
```
Primary:
- "Desa Garahan" → Target: Position 1
- "Desa Silo" → Position dalam top 5
- "Pemerintah Desa Jember" → Position dalam top 10

Secondary:
- "Layanan administrasi desa"
- "Transparansi anggaran desa"
- "Potensi desa Jember"
- "Berita desa Silo"
```

### Target Traffic
- Month 1-3: 50-100 organic visitors
- Month 4-6: 200-500 organic visitors
- Month 6+: 500-1000+ organic visitors

---

## 🔐 Security & SEO

### HTTPS/SSL
✅ Configured

### Security Headers (untuk Hostinger)
Add di `.htaccess`:
```apache
# Security Headers
<IfModule mod_headers.c>
  Header always set X-Content-Type-Options "nosniff"
  Header always set X-Frame-Options "SAMEORIGIN"
  Header always set X-XSS-Protection "1; mode=block"
  Header always set Referrer-Policy "strict-origin-when-cross-origin"
</IfModule>
```

### Update Content Security Policy
```html
<meta http-equiv="Content-Security-Policy" 
      content="default-src 'self' 'unsafe-inline' 'unsafe-eval' *.googlefonts.com *.gstatic.com">
```

---

## 🐛 Common SEO Issues & Solutions

| Issue | Solution |
|-------|----------|
| Website tidak muncul di Google | Submit sitemap di Search Console, tunggu 2-4 minggu |
| HTTPS warning | Enable SSL di Hostinger, force HTTPS redirect |
| Mobile unfriendly | Test di Mobile Friendly Test tool, fix issues |
| Slow loading | Enable caching, compress images, use CDN |
| Duplicate content | Update canonical URLs |
| Missing metadata | Edit meta tags di `index.html` head |
| Sitemap errors | Validate di sitemap validator tool |

---

## 📚 External SEO Tools (Free & Paid)

### Free Tools
- [Google Search Console](https://search.google.com/search-console) - Track rankings
- [Bing Webmaster Tools](https://www.bing.com/webmasters) - Bing submissions
- [Mobile Friendly Test](https://search.google.com/test/mobile-friendly) - Mobile check
- [PageSpeed Insights](https://pagespeed.web.dev/) - Performance
- [Schema Validator](https://schema.org/validator) - Structured data
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - Audit
- [Ubersuggest](https://ubersuggest.com) - Keyword research
- [Keyword Planner](https://ads.google.com/home/tools/keyword-planner/) - Keywords

### Premium Tools (Optional)
- [Semrush](https://semrush.com) - Comprehensive SEO
- [Ahrefs](https://ahrefs.com) - Backlinks & rankings
- [Moz](https://moz.com) - Rank tracking
- [SE Ranking](https://seranking.com) - Budget-friendly

---

## 🚨 Hostinger-Specific Tips

### Good to Know
1. **Automatic Backups** - Set daily backups di Hostinger
2. **Email Forwarding** - Setup admin@garahan.desa.id
3. **File Limits** - Hostinger usually allows 100GB+ storage
4. **Bandwidth** - Unlimited bandwidth (good for scaling)
5. **WordPress Ready** - Can upgrade to WordPress if needed

### Hostinger Support
- 24/7 Chat support: Hostinger dashboard
- Email: support@hostinger.com
- Phone: Check hostinger.com for local numbers

---

## ✨ Final Checklist sebelum Go Live

- [ ] SSL/HTTPS enabled & forced
- [ ] Domain pointed to Hostinger
- [ ] All files uploaded (robots.txt, sitemap.xml)
- [ ] Meta tags verified (title, description, keywords)
- [ ] Open Graph tags for social sharing
- [ ] Schema.org data validated
- [ ] Google Search Console setup & sitemap submitted
- [ ] Bing Webmaster Tools setup
- [ ] Mobile Friendly Test passed
- [ ] PageSpeed Insights checked (>80 score ideal)
- [ ] robots.txt accessible
- [ ] sitemap.xml accessible
- [ ] Caching enabled
- [ ] Images optimized & compressed
- [ ] Internal links working
- [ ] Favicon showing properly
- [ ] Footer links correct
- [ ] Contact info updated with real data
- [ ] Email address verified
- [ ] Backup created

---

## 📈 Post-Launch Monitoring

### Week 1
- Monitor Google Search Console for crawl errors
- Check Core Web Vitals
- Verify all pages indexed

### Week 2-4
- Watch search impressions increase
- Monitor bounce rate
- Check average session duration
- Update content if needed

### Month 2 onwards
- Continue adding fresh content
- Monitor keyword rankings
- Build backlinks (mention in local directories)
- Engage in local community online

---

## 🎯 Additional SEO Boost Tips

1. **Local SEO**
   - Add ke Google My Business
   - Submit ke direktori lokal Indonesia
   - List di maps.google.com

2. **Content Strategy**
   - Update berita minimal 2x per minggu
   - Target long-tail keywords
   - Create helpful content for visitors

3. **Backlinks**
   - Get links from kabupaten website
   - Collaborate dengan media lokal
   - List di Indonesia.go.id

4. **Social Media**
   - Share berita di Facebook & Instagram
   - Link ke website di bio
   - Engage dengan followers

5. **Email Marketing**
   - Build subscriber list
   - Send newsletter dengan link ke blog
   - Share new articles via email

---

**SEO Setup Date: 17 Februari 2026**
**Status: Ready for Hostinger Deployment**
**Next Review: 17 Maret 2026**
