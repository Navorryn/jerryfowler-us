# JerryFowler.US — Project Instructions

## What this is
Personal website for Jerry & Beth Fowler, live at **https://jerryfowler.us**. Static HTML — no framework, no build step, no CMS. Every page is a single self-contained `.html` file.

---

## Rules of Engagement

- **Do not break email.** GoDaddy Workspace Email runs on `jerry@jerryfowler.us` and `beth@jerryfowler.us`. The DNS records for `mail.jerryfowler.us` (A record → 216.69.168.151, DNS Only / NOT proxied) and the MX record must never be touched.
- **Do not touch DNS unless explicitly asked.** DNS is managed in Cloudflare (zone: jerryfowler.us). Any DNS change is potentially destructive.
- **Confirm before deleting any file or DNS record.** These are the live production assets.
- **Match the existing design system.** New pages must use the token set below. Do not introduce new fonts, color systems, or CSS frameworks.
- **No third-party JS dependencies** unless Jerry explicitly approves. No jQuery, no React, no bundlers. Vanilla HTML/CSS/JS only.
- **All pages must link back to `index.html`** via the nav and footer. No orphan pages.
- **Images go in `/images/`.** Large raw source files are gitignored (`raw images/`). Committed images are web-optimized copies.

---

## Design System

| Token | Value | Usage |
|---|---|---|
| `--cream` | `#F7F4EF` | Page background |
| `--cream-dk` | `#EDE8E0` | Alternate section background |
| `--charcoal` | `#1C1B1A` | Dark sections, footer |
| `--terra` | `#C85A35` | Primary accent, CTAs |
| `--terra-lt` | `#E07A57` | Hover states, dark-bg accents |
| `--forest` | `#2C4A3E` | Contact section background |
| `--sand` | `#D4C4A8` | Borders |
| `--text` | `#3A3836` | Body text |
| `--text-lt` | `#7A7570` | Muted / secondary text |

**Fonts:** `Playfair Display` (serif headings) + `Inter` (sans body). Loaded from Google Fonts — already in `<head>` on every page.

**Border radius:** `--radius: 12px`  
**Max content width:** `--max-w: 1120px`

---

## Site Structure

```
index.html          — Main page (hero, about, ventures, adventures, contact)
resume.html         — Jerry's executive resume
web-services.html   — Web Services venture page with client showcase
images/             — All committed web images
  beach-sunrise-wide.jpg
  beach-sunrise-waves.jpg
  blue-ridge-lake-fall.jpg
  biltmore-christmas-library.jpg
  both-on-bed.jpg
  dogs-cabin-fireplace.jpg
  dock-sunrise.jpg
  everglades-sunset.jpg
  hoover-dam-aerial.jpg
  hoover-dam-bridge-drive.jpg
  jax-indoor.jpg
  jax-outdoor.jpg
  narah-deck.jpg
  narah-outdoor.jpg
  narah-snow.jpg
  narah-sunlight.jpg
  palm-tree-dusk.jpg
  ruby-falls-cave.jpg
  st-augustine-cannons.jpg
```

---

## Ventures & Links

| Venture | URL | Card on index.html |
|---|---|---|
| Veritas AI | https://veritas-ai.io | ✅ (opens new tab) |
| Veritas Property & Asset Management | https://veritaspmgroup.com/ | ✅ (opens new tab) |
| Stoic Soul Press | https://stoicsoulpress.com | ✅ (opens new tab) |
| Web Services | web-services.html | ✅ (internal) |

Client on web-services.html: **Dragon Light Ventures** → https://dragonlightventures.com

---

## How to Publish

Every change follows this workflow:

### 1. Edit files
All source files live at:
```
/Users/jerrydhfowler/Documents/Claude/Projects/JerryFowler.US/
```

### 2. Commit and push
```bash
cd /Users/jerrydhfowler/Documents/Claude/Projects/JerryFowler.US
git add .
git commit -m "Brief description of what changed"
git push origin main
```

GitHub repo: **Navorryn/jerryfowler-us** (private)

### 3. Cloudflare auto-deploys
Cloudflare Pages watches the `main` branch. Deployment takes ~60 seconds after push. No manual deploy step needed.

**Live URL:** https://jerryfowler.us  
**Pages preview URL:** https://jerryfowler-us.pages.dev  
**Cloudflare account:** ccf29345506c9b841f8f6be0325a4eb3  
**Zone ID:** 0739237d2675dd586360d5b6be7b4baf

### Adding a new page
1. Create `your-page.html` in the project root, matching the nav/footer pattern from existing pages
2. Add a link to it from `index.html` (ventures section or nav)
3. Commit and push — it's live automatically

---

## Rollback
To revert to a previous version:
```bash
git log --oneline          # find the commit hash you want
git revert HEAD            # undo the last commit (creates a new commit)
git push origin main       # push — Cloudflare deploys the revert
```
To revert DNS to GoDaddy (nuclear option): change nameservers at GoDaddy back to `ns73.domaincontrol.com` and `ns74.domaincontrol.com`.
