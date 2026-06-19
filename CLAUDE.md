# The Attuned Practice — Claude Code Handover

## What This Project Is

A seven-page static website for The Attuned Practice (TAP), a private home Pilates studio in Bukit Timah, Singapore. The site is typography-led with no photography. All seven pages are fully designed and built as self-contained HTML/CSS files. Your job is to set up the project structure, connect it to GitHub, and deploy it to Cloudflare Pages.

The site owner (Dorina) has no coding background. She will maintain the site herself after deployment. Keep everything simple and well-commented where it helps.

---

## File Inventory

### HTML Pages (7)
| File | Page |
|------|------|
| `TAP_Home.html` | Home — full-screen nav layout |
| `TAP_About.html` | About Dorina — story, credentials, testimonials |
| `TAP_Approach.html` | The philosophy and teaching method |
| `TAP_Sessions.html` | Session info, pricing, booking |
| `TAP_FAQ.html` | Accordion FAQ |
| `TAP_Terms.html` | Terms & Conditions |
| `TAP_Privacy.html` | Privacy Policy |

### Images (2)
| Filename | Used on |
|---|---|
| `images/fascia-ribbon.jpg` | Home, About, Sessions |
| `images/fascia-ribbon-horizontal.jpg` | Approach, FAQ |

Both image files are already correctly named and placed in the `images/` subfolder. No action required.

---

## Target Folder Structure

```
tap-website/
├── CLAUDE.md
├── index.html              ← rename TAP_Home.html to this
├── about.html              ← rename TAP_About.html (optional, or keep TAP_ prefix)
├── approach.html
├── sessions.html
├── faq.html
├── terms.html
├── privacy.html
└── images/
    ├── fascia-ribbon.jpg
    └── fascia-ribbon-horizontal.jpg
```

**Note on renaming:** The HTML files currently link to each other using the `TAP_` prefix (e.g. `href="TAP_About.html"`). If you rename the files (recommended for clean URLs), you must also do a find-and-replace across all HTML files to update every internal link. This includes:
- All `<a href="TAP_*.html">` links in nav overlays and footer
- All `<a href="TAP_Home.html">` brand wordmark links

If renaming feels risky to do in one step, it is safe to leave the `TAP_` prefix and just rename `TAP_Home.html` to `index.html` (Cloudflare Pages serves `index.html` as the root). The other pages will still work at their full filenames.

---

## Deployment Target

- **Source control:** GitHub (free account)
- **Hosting:** Cloudflare Pages (free tier), connected to the GitHub repo
- **Domain:** Optional, can be added later through Cloudflare

This is a fully static site — no build step, no framework, no dependencies. Cloudflare Pages can serve it directly from the repository root.

---

## Design System Reference

This is for reference only — do not alter the visual design unless explicitly asked.

### Colour Palette
```css
--green:      #021c0e   /* background */
--gold:       #c9a55a   /* primary accent */
--gold-faint: rgba(201,165,90,0.18)
--gold-hover: #e0c070
--cream:      #e8dfc8   /* body text */
--cream-dim:  rgba(232,223,200,0.7)
--header-glass:         rgba(2,28,14,0.82)  /* header at rest */
--header-glass-scrolled: rgba(2,28,14,0.4) /* header on scroll */
```

### Typefaces (loaded via Google Fonts)
| Font | Weights | Used for |
|------|---------|----------|
| Cormorant Garamond | 300, 400, 500 | Brand wordmark, section leads, decorative numbers |
| Spectral | 300 italic | Section titles, clause headings |
| Inter | 300, 400 | Body text, eyebrows, UI elements |
| Bodoni Moda | 400 (opsz 6–96) | Navigation overlay links |

### Navigation Structure
All pages share a hamburger menu that opens a full-screen overlay with links to: Home, About, Approach, Sessions, FAQ, and a WhatsApp Contact button.

WhatsApp link: `https://wa.me/6585885889`

### Key Behaviours (already built into every page)
- **Sticky header** with semi-transparent glass effect — more transparent once scrolling begins
- **Fascia ribbon** (decorative background image) — sits above the header on page load, recedes behind it once scrolling starts
- **Section fade-in** — each content section fades and rises into view as it enters the viewport (IntersectionObserver, with `prefers-reduced-motion` fallback)
- **Brand wordmark** — clicking it returns to Home on every page
- **Footer links** — Terms & Conditions and Privacy Policy are linked on every page

---

## What Does NOT Need Doing in Claude Code

- No CSS extraction to a shared file — each page is intentionally self-contained
- No JavaScript bundling or build tooling
- No CMS or templating
- No analytics (not yet requested)

---

## SEO Notes

- All pages have `<title>` and `<meta name="description">` tags
- `TAP_FAQ.html` includes FAQPage JSON-LD structured data for Google rich results
- Image alt attributes on the ribbon images are intentionally empty (`alt=""`) — they are decorative

---

## After Deployment — How Dorina Updates the Site

Dorina will make content changes by editing HTML files in Claude.ai, then using Claude Code to commit and push the updated file to GitHub. Cloudflare Pages redeploys automatically on every push to the main branch.

When guiding her through updates, keep terminal instructions to single commands with clear explanation of what each one does. She does not need to understand the code, only the workflow.
