# 📊 Analytics & External Services Setup

## Google Analytics 4 Setup

### Step 1: Create Google Analytics Account
1. Go to: https://analytics.google.com
2. Click **Create Account**
3. Fill in:
   - Account name: `Desa Garahan`
   - Property name: `garahan.desa.id`
   - Website URL: `https://garahan.desa.id`
   - Industry category: `Government`
   - Business size: `Small`

### Step 2: Get Measurement ID
1. After creating property, you'll get: `G-XXXXXXXXXX`
2. Copy this ID

### Step 3: Add to Website
1. Open `index.html`
2. Add before `</head>`:
```html
<!-- Google Analytics 4 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX', {
    'page_path': window.location.pathname,
    'page_title': document.title
  });
</script>
```

Replace `G-XXXXXXXXXX` dengan ID Anda

### Step 4: Verify Tracking
1. Go back to Google Analytics
2. Go to **Real-time → Overview**
3. Open website in new tab
4. You should see 1 active user

---

## Google Search Console

### Step 1: Add Property
1. Go to: https://search.google.com/search-console
2. Click **Start Now** or **Add Property**
3. Choose **URL prefix**
4. Enter: `https://garahan.desa.id`

### Step 2: Verify Domain
Options (choose one):
- **Domain name verification** (via DNS) - Recommended
- **HTML file upload** - Upload verification file
- **HTML tag** - Add meta tag to HTML
- **Google Analytics** - If already connected

### Step 3: Submit Sitemap
1. Go to **Sitemaps** (left menu)
2. Enter: `sitemap.xml`
3. Click **Submit**

### Step 4: Monitor Performance
- **Coverage** - Which pages are indexed
- **Performance** - Search impressions & clicks
- **Enhancements** - Mobile, Core Web Vitals

---

## Bing Webmaster Tools

### Step 1: Add Site
1. Go to: https://www.bing.com/webmasters
2. Click **Add a site**
3. Enter: `https://garahan.desa.id`

### Step 2: Verify With Search Console
1. Choose verification method
2. Or import from Google Search Console

### Step 3: Submit Sitemap
1. Go to **Sitemaps** (left menu)
2. Enter: `sitemap.xml`
3. Click **Submit**

---

## Google My Business Setup

### For Local SEO (Very Important)
1. Go to: https://business.google.com
2. Click **Create account** or **Login**
3. Fill in:
   - Business name: `Pemerintah Desa Garahan`
   - Category: `Government Office` or `Local Government`
   - Address: Your village address
   - Phone: Your phone number
   - Website: `https://garahan.desa.id`

4. Verify business (phone call, postcard, or email)

### Benefits:
✅ Show up in Google Maps
✅ Local search results
✅ Customer reviews
✅ Business info in Search

---

## Facebook Pixel Setup

### For Tracking & Retargeting
1. Go to: https://www.facebook.com/business
2. Create/Login to Business Account
3. Go to **Events Manager**
4. Create new pixel
5. Get Pixel ID
6. Add before `</head>` in HTML:

```html
<!-- Facebook Pixel Code -->
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window, document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', 'YOUR_PIXEL_ID_HERE');
  fbq('track', 'PageView');
</script>
<noscript><img height="1" width="1" style="display:none"
  src="https://www.facebook.com/tr?id=YOUR_PIXEL_ID_HERE&ev=PageView&noscript=1"
/></noscript>
<!-- End Facebook Pixel Code -->
```

Replace `YOUR_PIXEL_ID_HERE` dengan ID pixel Anda

---

## Email Newsletter Signup

### Mailchimp Setup (Recommended - Free)
1. Go to: https://mailchimp.com
2. Create account
3. Create audience
4. Get sign-up form code
5. Add form to website

Contoh HTML form:
```html
<!-- Mailchimp Subscribe Form -->
<form action="https://mailchimp-url.com/subscribe" method="post">
  <input type="email" name="email" placeholder="Email Anda" required>
  <button type="submit">Subscribe</button>
</form>
```

---

## Social Media Integration

### Facebook Page
1. Create: https://www.facebook.com/pages/create
2. Category: `Community Organization` or `Government Organization`
3. Page name: `Desa Garahan`
4. Add link ke website di About
5. Share berita & galeri regularly

### Instagram Account
1. Create: https://instagram.com
2. Username: `desagarahan` atau `garahan_silo`
3. Bio:
   ```
   Pemerintah Desa Garahan
   Kec. Silo, Kab. Jember
   🌾 Desa Mandiri Maju
   
   garahan.desa.id
   ```
4. Link website in bio
5. Share visual content regularly

### YouTube Channel (Optional)
1. Go to: https://youtube.com
2. Create channel: `Desa Garahan`
3. Upload:
   - Welcome video
   - Dokumentasi kegiatan
   - Tutorial layanan desa
4. Add website link di deskripsi

---

## Email Service Domain Setup

### Setup Email di Hostinger
1. Go to: **Hostinger → Email**
2. Create: `admin@garahan.desa.id`
3. Create: `info@garahan.desa.id`
4. Setup SPF, DKIM untuk deliverability

### SPF Record (Add to DNS)
```
v=spf1 mx ~all
```

### DKIM Setup
Generated automatically by Hostinger

---

## Performance Monitoring Tools

### Website Speed Monitoring
1. **Google PageSpeed Insights**: https://pagespeed.web.dev
2. **GTmetrix**: https://gtmetrix.com
3. **WebPageTest**: https://www.webpagetest.org
4. **Lighthouse**: Integrated in Chrome DevTools

Target Score: **85+**

### Uptime Monitoring (Free)
1. **UptimeRobot**: https://uptimerobot.com
2. Configure to ping website every minute
3. Get alerts jika website down

---

## Internal Link Tracking

Add this to track clicks:

```javascript
// Track internal links
document.addEventListener('click', function(e) {
  if (e.target.tagName === 'A' && e.target.href) {
    const href = e.target.href;
    if (href.includes('garahan.desa.id') || href.startsWith('#')) {
      gtag('event', 'click', {
        'link_text': e.target.textContent,
        'link_url': href
      });
    }
  }
});
```

---

## Submission Checklist

### Before Launch
- [ ] Google Analytics configured
- [ ] Google Search Console verified
- [ ] Bing Webmaster Tools verified
- [ ] Sitemap submitted
- [ ] robots.txt verified
- [ ] Meta tags all correct
- [ ] Schema.org validated
- [ ] Mobile Friendly Test passed
- [ ] SSL/HTTPS working
- [ ] All internal links working
- [ ] External links tested
- [ ] Images optimized
- [ ] Page speed tested

### Post-Launch (First Week)
- [ ] Google Analytics showing traffic
- [ ] Search Console showing impressions
- [ ] Bing indexed pages
- [ ] Google My Business set up
- [ ] Social media pages set up
- [ ] Email newsletter ready

### Ongoing (Every Month)
- [ ] Monitor Search Console keywords
- [ ] Check Google Analytics metrics
- [ ] Add fresh content (berita)
- [ ] Update social media
- [ ] Monitor uptime
- [ ] Check page speed

---

## Target Metrics (3-6 months)

| Metric | Target |
|--------|--------|
| Monthly Organic Visitors | 500+ |
| Pages Per Session | 2+ |
| Avg. Session Duration | 2+ minutes |
| Bounce Rate | < 60% |
| Top Keyword | "Desa Garahan" → Position 1 |
| Indexed Pages | 20+ |
| Backlinks | 5+ quality links |

---

**Analytics Setup Date: 17 Februari 2026**
**Next Review: 1 Maret 2026**
