# Onezero s.r.o. — Company Website

A fast, responsive, single-page marketing site for **Onezero s.r.o.** — Digital Business
Solutions across Cybersecurity & SASE, SD-WAN, Network Engineering, and AI-Driven Operations.

Built as plain HTML/CSS/JS — **no build step, no dependencies**. Just open or host it.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Page structure & content |
| `styles.css` | Dark, modern theme (design tokens at the top) |
| `script.js`  | Nav, scroll reveals, stat counters, hero network animation, contact form |

## View it locally

Open `index.html` directly in a browser, or serve the folder:

```bash
cd onezero-website
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Drag the folder into **Netlify Drop**, **Vercel**, **Cloudflare Pages**, or any static host
(GitHub Pages, S3 + CloudFront, etc.). No configuration required.

## Review before going live

Company contact details (email, phone, registered address, IČO/DIČ) are filled in with
the real **Onezero s. r. o.** data. Still worth a look:

- **Stats** (years, uptime, cost reduction) in the `.stat` blocks of `index.html` are
  illustrative — set real figures.
- **Privacy / Terms** footer links point to `#` — add real pages or remove them.
- Optional: a real logo, social links, and an Open Graph image (`og:image`).
- Email currently uses `onezerosro@gmail.com`; once mail on the onezero.sk domain is set
  up, you can switch to e.g. `info@onezero.sk`.

## Customising

- **Colors / spacing / fonts:** edit the CSS custom properties in `:root` at the top of `styles.css`.
- **Sections:** each section in `index.html` is clearly commented (`<!-- ===== ... ===== -->`).
- **Contact form:** currently opens the visitor's email client (`mailto:`). To capture
  submissions server-side, point the `<form>` at a form service (Formspree, Web3Forms,
  Netlify Forms) or your own endpoint — see the handler in `script.js`.
