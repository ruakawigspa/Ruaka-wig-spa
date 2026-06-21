# Ruaka Wig Spa Website — Setup Guide

## File Structure
```
ruakawigspa/
├── index.html      ← Main site (all pages)
├── logo.png        ← Logo (place your logo here)
├── sitemap.xml     ← SEO sitemap
├── robots.txt      ← SEO robots file
└── README.md       ← This file
```

## Domain
Point domain **ruakawigspa.com** to your hosting provider.
Update the canonical URL and sitemap once live.

---

## EmailJS Setup (Booking Form)

The booking form uses [EmailJS](https://www.emailjs.com/) — free tier allows 200 emails/month.

### Steps:

1. **Create a free account** at https://www.emailjs.com/

2. **Add an Email Service** (Gmail recommended — connect ruakawigspa@gmail.com)
   - Copy the **Service ID** (e.g. `service_abc123`)

3. **Create Template 1 — Owner Notification** (email to you when someone books)
   - Template name: `booking_owner`
   - Subject: `New Booking Request — {{service}}`
   - Body should include these variables:
     - `{{client_name}}` — client's name
     - `{{client_phone}}` — client's phone
     - `{{service}}` — service requested
     - `{{date}}` — preferred date
     - `{{time}}` — preferred time
     - `{{client_location}}` — their area
     - `{{notes}}` — additional notes
   - Copy the **Template ID**

4. **Create Template 2 — Auto-reply to Client** (optional, if you collect client emails later)
   - Simple confirmation message
   - Copy the **Template ID**

5. **Get your Public Key** — found in EmailJS Dashboard → Account → API Keys

### Fill in index.html (lines ~540–543):
```javascript
emailjs.init({ publicKey: "YOUR_PUBLIC_KEY_HERE" });
const EMAILJS_SERVICE_ID  = "YOUR_SERVICE_ID_HERE";
const EMAILJS_OWNER_TPL   = "YOUR_OWNER_TEMPLATE_ID_HERE";
const EMAILJS_CONFIRM_TPL = "YOUR_AUTOREPLY_TEMPLATE_ID_HERE";
```

---

## TikTok Videos

In `index.html`, find the two `.tiktok-embed-wrap` divs in the `#social-glimpse` section.
Replace the `.tiktok-placeholder` divs with actual TikTok embed codes:

1. Go to TikTok → open a video → Share → Embed
2. Copy the `<blockquote>` + `<script>` embed code
3. Paste it inside the `.tiktok-embed-wrap` div, replacing the placeholder

---

## Hosting Suggestions
- **Netlify** (free, drag-and-drop) — netlify.com
- **GitHub Pages** (free) — github.com
- **Hostinger** (affordable KE option)

---

## SEO Checklist
- [ ] Replace `https://www.ruakawigspa.com` with actual domain everywhere once registered
- [ ] Create and upload `og-image.jpg` (1200×630px) for social sharing previews
- [ ] Submit sitemap.xml to Google Search Console after domain is live
- [ ] Register on Google Business Profile for local SEO (links to the Maps embed)
