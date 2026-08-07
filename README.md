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

The domain is registered at GoDaddy; DNS is served by Cloudflare
(`carrera.ns.cloudflare.com`, `miguel.ns.cloudflare.com`). Change these in the
**Cloudflare** dashboard, not GoDaddy.

### Records that point at GitHub Pages

Replace the existing apex `A` records with these four, all **DNS only**
(grey cloud, not proxied):

```
A     @    185.199.108.153
A     @    185.199.109.153
A     @    185.199.110.153
A     @    185.199.111.153

AAAA  @    2606:50c0:8000::153
AAAA  @    2606:50c0:8001::153
AAAA  @    2606:50c0:8002::153
AAAA  @    2606:50c0:8003::153

CNAME www  cura-loucura.github.io
```

The grey cloud matters: GitHub needs to reach the domain directly to issue its
Let's Encrypt certificate. Proxying can be turned on later, once HTTPS is
confirmed working, with Cloudflare SSL mode set to **Full (strict)**.

### Records that must not be touched

`contact@vegancheese.info` runs on Microsoft 365, provisioned through GoDaddy.
Deleting or editing any of these breaks email:

```
MX    @    0 vegancheese-info.mail.protection.outlook.com
TXT   @    v=spf1 include:secureserver.net -all
TXT   @    NETORGFT11798637.onmicrosoft.com
TXT   @    NETORGFT19000339.onmicrosoft.com
```

Website and email are independent here. Cancelling the GoDaddy *Website
Builder* plan does not affect the Microsoft 365 mailbox or the domain
registration, which are billed separately.

## Content archive

The original GoDaddy pages and full-resolution images were archived before the
migration. Images live in `assets/img/`; `workshop.jpg` is currently unused and
kept for the workshop section when that launches.
