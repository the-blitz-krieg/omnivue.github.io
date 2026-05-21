# Omni Vue AI — Website

Static HTML/CSS/JS marketing site for omnivueai.com. No build step. Drop-in deployable to any static host (GitHub Pages, Cloudflare Pages, Netlify, Vercel, S3, etc.).

---

## Folder structure (deploy this exactly)

```
omnivueai/
├── index.html              ← Home
├── platform.html           ← The Platform
├── pricing.html            ← Pricing
├── demo.html               ← Book a Demo
├── about.html              ← About
├── robots.txt              ← Crawler directives
├── sitemap.xml             ← Sitemap (5 pages + 2 llms files)
├── llms.txt                ← AI engine signal (concise)
├── llms-full.txt           ← AI engine signal (extended)
├── css/
│   ├── base.css            ← Design tokens, reset, typography
│   └── components.css      ← Nav, footer, buttons, cards, forms, FAQ, etc.
├── js/
│   └── main.js             ← Hero verb-flip, nav, FAQ, scroll reveals
└── img/
    ├── logo-mark.svg       ← Navigation/header logo (also inlined in HTML)
    ├── favicon.svg         ← Browser tab icon
    └── og-default.svg      ← Open Graph image for social sharing (1200x630)
```

Upload everything to your repo root preserving this structure.

---

## Tech stack

- **HTML5 + CSS + vanilla JS** — no framework, no build step
- **Fonts:** Fraunces (display), Inter Tight (body), JetBrains Mono (technical labels). Loaded from Google Fonts.
- **No external dependencies** other than the Google Fonts CDN
- **No JavaScript framework** — single ~6KB main.js handles all interactions

---

## SEO / AEO / GEO baseline

Every page ships with:

- Click-earning `<title>` and meta description written as ad copy
- Canonical URL + hreflang tags
- Geo entity meta tags (region CA-NS, position 44.6488;-63.5752)
- AI content declaration meta tag
- Reference to /llms.txt as alternate type=text/plain
- Open Graph + Twitter Card (image: /img/og-default.svg)
- Full Schema.org JSON-LD `@graph` covering:
  - Organization
  - WebSite
  - WebPage / AboutPage / ContactPage (per page type)
  - BreadcrumbList
  - SoftwareApplication (Home, Platform)
  - Service
  - Product + Offer (Pricing — one per tier)
  - Person (About — Nivin)
  - FAQPage (8 questions on Home, 5 on Platform, 6 on Pricing, 6 on Demo)

---

## Brand and design system

- **Palette:** Ink `#0A1628` (deep navy), Vellum `#F5F1EA` (warm ivory), Signal `#00E58A` (electric green accent), Graphite `#1A1F2E` (body text), Stone `#8A8578` (muted)
- **Typography:** Fraunces display + Inter Tight body + JetBrains Mono labels
- **Voice:** Assured, Precise, Provocative, Human
- **Signature line:** Authentic. Actionable. Agile. Adaptive Intelligence.

All design tokens are CSS custom properties in `css/base.css`. Change one variable and every component updates.

---

## Brand contact

- **Email:** hello@omnivueai.com
- **Phone:** +1 902-540-0111
- **Location:** Halifax, Nova Scotia, Canada
- **Founder & CEO:** Nivin Xavier (nivin@omnivueai.com)

---

## Crawler policy

The `robots.txt` is permissive to all search engines and major AI/generative crawlers (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, Applebot-Extended, Meta, Amazon, CCBot, etc.).

The Internet Archive (ia_archiver, archive.org_bot), Wayback Machine, and Heritrix are explicitly blocked.

---

## Deployment checklist

1. Upload entire folder to repo root, preserving structure
2. Confirm site loads at https://omnivueai.com/
3. Confirm /robots.txt, /sitemap.xml, /llms.txt all return text/plain (or appropriate MIME)
4. Submit sitemap to Google Search Console: https://omnivueai.com/sitemap.xml
5. Submit sitemap to Bing Webmaster Tools: same URL
6. Verify Open Graph preview using Facebook Sharing Debugger and Twitter Card Validator
7. Run Lighthouse and aim for 95+ across all four categories
8. Confirm FAQPage schema appears in Google Rich Results Test

---

## Pages remaining (Phase 3)

The conversion-critical five are complete. The next-phase build will add:

- For Brands (audience landing)
- For Agencies (audience landing)
- For Rights Holders (audience landing)
- Insights / Blog
- Case Studies
- Integrations
- Security
- Glossary
- 404 page

Each will be built to match the existing design system, using the same shared `css/` and `js/` assets.

---

## Maintenance notes

- **Nav and footer are duplicated across all 5 HTML files** (no includes, no build step). When you update the nav or footer, update it in all 5 files. If maintenance becomes painful, the migration path is to a static site generator (Astro, Eleventy, or similar) that compiles partials at build time without changing the deployed output.
- **OG image is a single SVG used across all pages.** For per-page OG images, generate per-page SVGs and update the `og:image` meta tag in each HTML file's head.
- **Schema dates** (`datePublished`, `dateModified`) should be updated when content materially changes. Search engines use these to decide whether to re-crawl.
