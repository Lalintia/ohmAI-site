# OhmWebsite — ohmai.me Progress

## Project Overview
- **URL:** https://ohmai.me
- **Type:** Portfolio website สำหรับ ohmAI — AI-Powered Digital Solutions
- **Stack:** Static HTML/CSS/JS (single page)
- **Hosting:** AWS EC2 (`54.169.168.58`) ผ่าน Cloudflare DNS proxy
- **Repo:** github.com/Lalintia/ohmAI-site
- **Deploy:** GitHub Actions auto-deploy เมื่อ push ไป `main` → SSH ไป EC2 แล้ว `git pull`

---

## File Structure
```
OhmWebsite/
├── index.html          # Main portfolio page (single-page)
├── favicon.svg         # SVG favicon (gradient oA logo)
├── og-image.png        # Open Graph image 1200x630
├── og-image.svg        # OG image source SVG
├── sitemap.xml         # Sitemap สำหรับ search engines
├── robots.txt          # Allow all bots + sitemap link
├── llms.txt            # AI bot-readable site description
├── img/
│   ├── aicheck.jpg     # AI Visibility Checker project image
│   ├── ptt.jpg         # PTT IR Chatbot project image
│   ├── hmc.jpg         # HMC Polymers Chatbot project image
│   └── esg.jpg         # FTSE ESG Analyzer project image
└── .github/workflows/
    └── deploy.yml      # Auto-deploy to EC2 on push to main
```

---

## Infrastructure
| Component | Detail |
|---|---|
| EC2 Instance | `n8n Singapore` (t3.medium) — `54.169.168.58` |
| EC2 Key | `n8n-singapore-key` |
| EC2 Path | `/var/www/ohmai.me` |
| DNS | Cloudflare (proxy mode) — nameservers: aarav.ns, melina.ns |
| Domain Registrar | Onamae.com |
| SSL | Cloudflare edge certificate (auto) |

---

## SEO & AEO ที่ทำแล้ว (3 เม.ย. 2569)

### Meta Tags
- `<title>` — ohmAI — AI-Powered Digital Solutions | AI Chatbot, Automation & AEO
- `<meta name="description">` — เพิ่มแล้ว
- `<meta name="author">` — Sawarut Akkarawan
- `<link rel="canonical">` — https://ohmai.me/

### Open Graph + Twitter Card
- og:title, og:description, og:image, og:type, og:url, og:site_name, og:locale
- twitter:card, twitter:title, twitter:description, twitter:image
- og-image.png สร้างแล้ว (1200x630, gradient branding)

### Schema.org JSON-LD
- ProfessionalService (ohmAI organization)
- Person (Sawarut Akkarawan)
- WebSite
- OfferCatalog (3 services: Chatbot, Automation, AEO/GEO)

### Semantic HTML
- `<header>` ครอบ `<nav>`
- `<main>` ครอบ content sections
- `<footer>` อยู่แล้ว
- `nav aria-label="Main navigation"`

### Files สำหรับ Bots
- `sitemap.xml` — homepage entry
- `robots.txt` — Allow all + sitemap link
- `llms.txt` — AI-readable description (services, projects, tech stack, contact)
- `favicon.svg` — SVG gradient favicon

### Cloudflare Settings
- **AI Crawl Control > Cloudflare Managed robots.txt** → ปิดแล้ว (ไม่บล็อก AI bots)
- **Block AI training bots** → Do not block (allow crawlers)

---

## Security ที่ทำแล้ว (3 เม.ย. 2569)

| # | สิ่งที่แก้ | Detail |
|---|----------|--------|
| 1 | `rel="noopener noreferrer"` | ทุก `target="_blank"` link มี noreferrer แล้ว |
| 2 | deploy.yml pin SHA | ใช้ commit SHA แทน mutable tag `v1.0.3` |
| 3 | ลบ email จาก llms.txt | ลดความเสี่ยง spam/phishing |
| 4 | Self-host images | โหลด Unsplash images มาเก็บใน `img/` (ไม่ leak visitor IP) |
| 5 | SSH fingerprint | เพิ่ม `EC2_HOST_FINGERPRINT` ใน GitHub Secrets + deploy.yml |

---

## Projects แสดงบนเว็บ
1. **AI Visibility Checker** — aicheck.ohmai.me (AEO/GEO tool)
2. **PTT IR Chatbot** — ptt.ohmai.me (GPT-5.1 chatbot)
3. **HMC Polymers Chatbot** — hmc.ohmai.me (product spec AI)
4. **FTSE ESG Analyzer** — esg.ohmai.me (ESG scoring)

---

## History (สำคัญ)
- เว็บเริ่มจาก personal profile → PTT IR Chatbot landing page → Portfolio site ปัจจุบัน
- มีช่วงที่ local code ไม่ตรงกับ live (แก้ไขบน server โดยตรง) → sync แล้ว 3 เม.ย. 2569
- Git history เก่ามี commit message ไม่ดี ("Update index.html" ซ้ำๆ) → ใหม่ใช้ Conventional Commits

---

## TODO
- [ ] สร้าง `favicon-32x32.png` + `apple-touch-icon.png` (แปลงจาก SVG)
- [ ] เพิ่ม `www` subdomain redirect ใน Cloudflare DNS
- [ ] เพิ่ม MX record หรือ SPF/DKIM/DMARC (ป้องกัน email spoofing)
- [ ] พิจารณาเพิ่ม FAQ section (เพิ่มคะแนน AEO)
- [ ] พิจารณาเปลี่ยนรูป project cards เป็น screenshot จริงแทน stock photos
