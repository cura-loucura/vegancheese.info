# vegancheese.info

Static site for *The Science and Practice of Vegan Cheese*. Plain HTML and CSS,
no build step, no dependencies. Served by GitHub Pages.

Migrated off GoDaddy Website Builder in August 2026.

## Editing

Open the `.html` file and edit it. There is nothing to compile.

| File | What it is |
|------|------------|
| `index.html` | Home page |
| `impressum.html` | Impressum / Kontakt |
| `datenschutz.html` | Datenschutzerklärung |
| `404.html` | Not-found page, also redirects the old GoDaddy URLs |
| `assets/style.css` | All styling. Colour and spacing tokens are at the top |
| `assets/fonts.css` | Self-hosted Karla + Old Standard TT |
| `CNAME` | Tells GitHub Pages which domain to answer on — **do not delete** |

To preview locally:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Push to `main` and GitHub Pages redeploys within about a minute.

## Still to do

- [ ] Fill in the postal address in `impressum.html` (§ 5 DDG requires a
      ladungsfähige Anschrift — email alone is not enough) and delete the
      yellow `.todo` box.
- [ ] Fill in the same address in `datenschutz.html`, then delete its
      `.todo` box.
- [ ] Decide whether the VAT section in the Impressum applies; delete it if not.

## Fonts

Karla and Old Standard TT, self-hosted rather than loaded from Google Fonts.
This is deliberate: embedding Google Fonts sends visitor IP addresses to Google
and German courts have treated that as a GDPR violation. Latin and Latin-Ext
subsets only, ~117 KB total. Both faces are SIL Open Font License 1.1.

## DNS

The domain is registered at GoDaddy; DNS is served by Cloudflare. Only the
apex `A`/`AAAA` records and the `www` `CNAME` point at GitHub Pages.

**The `MX` and mail-related `TXT` records must not be touched** — `contact@vegancheese.info`
runs on Microsoft 365 and changing them will break email delivery.

## Content archive

The original GoDaddy pages and full-resolution images were archived before the
migration. Images live in `assets/img/`; `workshop.jpg` is currently unused and
kept for the workshop section when that launches.
