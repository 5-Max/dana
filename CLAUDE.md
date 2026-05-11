# CLAUDE.md — Shears a go-go Website

## Project Overview

Static HTML website for **Shears a go-go**, a mobile haircutting business run by Dana in Atlanta, GA. The site is hosted on GitHub Pages at `shearsagogo.com` (custom domain via CNAME).

**Live site:** https://shearsagogo.com  
**GitHub Pages fallback:** https://5-max.github.io/dana/

---

## Repository Structure

```
dana/
├── index.html      # Home page — full-width collage photo
├── about.html      # About Dana — bio, contact links
├── info.html       # FAQ / service info — at-home vs. studio options
├── contact.html    # Contact page — address, phone, email
├── CNAME           # GitHub Pages custom domain: shearsagogo.com
├── README.md       # Minimal repo description
└── pics/
    ├── logo.jpg        # Circular logo in navbar
    ├── me.jpg          # Dana's photo (about page)
    ├── collageBig.jpg  # Hero collage image (home page)
    └── shears.jpg      # Scissors image (unused/backup)
```

---

## Tech Stack

- **Pure static HTML** — no build step, no bundler, no package manager
- **Bootstrap 4.5.0** — layout, responsive grid, navbar (CDN)
- **Google Fonts** — Lora (headings/brand) + Roboto (body) (CDN)
- **Font Awesome 4.7.0** — icons in footer (CDN)
- **jQuery 3.5.1** — required by Bootstrap (CDN)
- **Popper.js 1.16.0** — required by Bootstrap dropdowns (CDN)
- **Google Custom Search** — site search widget embedded on every page

All dependencies are loaded from CDN. There are no local JS or CSS files.

---

## Page Anatomy

Every page shares the same structure:

1. **`<head>`** — consistent meta tags (charset, viewport, description, keywords, author), CDN links for Bootstrap + Google Fonts + Font Awesome
2. **`<nav>`** — Bootstrap dark navbar, dark brown `#251f18`, brand text in lavender `#E296EB`, responsive hamburger menu. The `active` class is on the `<li>` matching the current page.
3. **`<main content>`** — page-specific content using Bootstrap grid
4. **`<footer>`** — dark brown background, lavender text, contact icon + Instagram link + copyright + "Made with ❤️ in ATL" credit
5. **Google Custom Search widget** — below the footer on every page
6. **Bootstrap JS bundle** — jQuery → Popper → Bootstrap at end of `<body>`

---

## Brand / Design Conventions

| Token | Value |
|---|---|
| Background (nav + footer) | `#251f18` (very dark brown) |
| Brand / accent color | `#E296EB` (lavender/lilac) |
| Page background | `white` |
| Primary font | Lora (serif) — navbrand, headings, body text |
| Secondary font | Roboto (sans-serif) — defined but rarely used |
| Logo style | Circular, 100×100px, 3px white border |
| Navbar font size | 24px brand, 18px nav links |

**Active nav item:** `class="nav-item active m-2"` on the `<li>` for the current page (not the `<a>`).

---

## Key URLs & Contact Info

- **Phone:** 404.518.3262 (`sms:4045183262` for click-to-text)
- **Email:** danaddaughtry@yahoo.com
- **Instagram:** https://instagram.com/shearsagogo
- **WordPress contact form:** https://shearsagogo.wordpress.com/send-me-a-message/
- **Google CSE ID:** `012130627112913878732:sxxx5son5fa`

---

## Development Workflow

There is no build step. To edit the site:

1. Edit HTML files directly
2. Open any `.html` file in a browser to preview locally (no server required for basic layout; CDN assets need internet access)
3. Commit and push to `master` — GitHub Pages deploys automatically

**Branch convention (for AI agents):** Work on feature branches (e.g. `claude/...`), then push and open a PR targeting `master`.

---

## Conventions & Gotchas

- **No separate CSS file** — all styling is inline via `style=""` attributes or Bootstrap classes. Keep new styles inline to match existing pattern.
- **No JavaScript beyond Bootstrap** — do not add custom JS unless strictly necessary.
- **Shared nav/footer** — these are copy-pasted across all pages (no templating engine). When updating nav or footer, update all four HTML files.
- **Active class** — must be set on the `<li>` element, not the `<a>`. Only one page should have `active` at a time in each nav.
- **Images** — stored in `pics/`. Reference with relative path `./pics/filename.jpg`. No image optimization pipeline.
- **CDN integrity hashes** — do not remove `integrity` and `crossorigin` attributes on CDN links; they are subresource integrity (SRI) checks.
- **Copyright year** — footer shows `&copy;2020`. Update if refreshing the site.

---

## Common Tasks

**Add a new page:**
1. Copy an existing page as a starting template
2. Update `<title>`, meta description, and main content
3. Set `active` on the correct `<li>` in the navbar
4. Add a link to it in the navbar of all other pages

**Update contact info:**
- Phone/email appears in `about.html` (inline links) and `contact.html` (address block)

**Change brand colors:**
- Search all `.html` files for `#251f18` (dark brown) or `#E296EB` (lavender) and replace consistently

**Add a new image:**
- Place the file in `pics/`
- Reference it as `./pics/filename.ext`
