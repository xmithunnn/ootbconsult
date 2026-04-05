# OOTB Consulting — SEO Implementation Package

## Files to deploy to root of outoftheboxca.com

| File | Purpose | Deploy to |
|------|---------|-----------|
| `index.html` | Main HTML shell with all SEO meta tags, schema, favicon | `/` (root) |
| `robots.txt` | Crawler instructions pointing to sitemap | `/robots.txt` |
| `sitemap.xml` | All 12 indexable pages with priorities | `/sitemap.xml` |
| `llms.txt` | LLM-readable site summary (new SEO standard) | `/llms.txt` |
| `vercel.json` | Clean URLs, routing rewrites, security headers | `/vercel.json` |

---

## What this gives you

### Google Search appearance (matches your screenshot):
- **Title:** `OOTB Consulting | Achieve Growth—Partner with Us`
- **Description:** `Expert boutique consulting firm specializing in data-driven strategies for retail, hospitality, real estate, tech, healthcare, and professional services.`

### Schema markup included:
- `Organization` — name, email, address, social profiles
- `LocalBusiness` — Toronto, ON, CA
- `WebSite` — for sitelinks search box eligibility
- `WebPage` — page-level context

### Social sharing:
- Full Open Graph tags (Facebook, LinkedIn, Slack previews)
- Twitter/X Card tags
- 1200×630 OG image slot at `/og-image.jpg` — **create this image**

---

## Post-deployment checklist (manual steps)

1. **Create OG image** — 1200×630px JPG, OOTB logo + tagline on navy background. Save as `/og-image.jpg`
2. **Submit sitemap** → Google Search Console → Sitemaps → add `https://www.outoftheboxca.com/sitemap.xml`
3. **Request indexing** → Google Search Console → URL Inspection → `https://www.outoftheboxca.com/` → Request Indexing
4. **Add GA4** → get measurement ID from Google Analytics → add `<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>` to index.html head
5. **Verify social links** in schema match live profiles:
   - Instagram: `https://www.instagram.com/outoftheboxca/`
   - LinkedIn: `https://www.linkedin.com/company/ootbconsulting`

---

## How to integrate with Vite/React

In `vite.config.js`, ensure the build output is `index.html`. The current `index.html` references `/src/main.jsx` — this is the standard Vite entrypoint. Your existing JSX file should be your `App.jsx` imported from `main.jsx`.

```js
// main.jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'

ReactDOM.createRoot(document.getElementById('root')).render(<App />)
```

The `vercel.json` rewrites all routes back to `index.html` so React Router (or your page state) handles navigation client-side.
