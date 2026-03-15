# BunkerWeb Feature Pricing Page

A static GitHub Pages site styled after [BunkerWeb](https://github.com/bunkerity/bunkerweb) that lets users interactively build their own security feature stack, see live pricing, and generate a random API key.

## Live Demo

> Deploy to GitHub Pages (see below) and your URL will be:
> `https://<your-username>.github.io/<repo-name>/`

---

## Features

- **BunkerWeb-style dark UI** — matches the official dashboard aesthetic (dark theme, green accent, Inter font)
- **6 feature groups** spanning Core Protection, Auth, TLS, Caching, Monitoring, and Advanced features
- **Live pricing sidebar** — total updates instantly as you toggle features
- **Monthly / Annual billing toggle** — annual plan shows 20% discount
- **API key generator** — clicking "Generate API Key" produces a unique `bwk_xxx_xxx_xxx` key
- **Copy to clipboard** — one-click copy inside the modal
- **Zero dependencies** — single `index.html`, no build step, no npm

---

## Feature Groups & Pricing

| Group | Feature | Price |
|---|---|---|
| Core Protection | Web Application Firewall (WAF) | Free |
| Core Protection | Rate Limiting | $5/mo |
| Core Protection | Anti-Bot Challenge | $9/mo |
| Core Protection | IP / DNSBL Blacklisting | $7/mo |
| Authentication | HTTP Basic Auth | Free |
| Authentication | Auth Request (SSO) | $12/mo |
| Authentication | Multi-Factor Authentication | $15/mo |
| TLS & Certificates | Let's Encrypt Auto-Renewal | Free |
| TLS & Certificates | Custom Certificate Upload | $4/mo |
| TLS & Certificates | HSTS + Preload | Free |
| TLS & Certificates | Mutual TLS (mTLS) | $10/mo |
| Caching & Performance | Redis Cluster Integration | $8/mo |
| Caching & Performance | Static Asset Caching | $5/mo |
| Caching & Performance | Gzip / Brotli Compression | Free |
| Monitoring | Structured JSON Logs | Free |
| Monitoring | Security Reports Dashboard | $14/mo |
| Monitoring | Real-Time Alerting | $11/mo |
| Monitoring | SIEM Export | $18/mo |
| Advanced | CrowdSec Integration | $10/mo |
| Advanced | Automatic IP Banning | Free |
| Advanced | Geo-Blocking | $6/mo |
| Advanced | gRPC Proxying | $8/mo |
| Advanced | Custom Plugin Support | $20/mo |

---

## Deploy to GitHub Pages

### Option 1 — Automatic (recommended)

1. Fork or push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Click **Save** — your site will be live within ~60 seconds.

### Option 2 — GitHub Actions

Create `.github/workflows/pages.yml`:

```yaml
name: Deploy to Pages
on:
  push:
    branches: [main]
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - id: deployment
        uses: actions/deploy-pages@v4
```

---

## Run Locally

No build step needed — just open the file:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Or serve with any static server
npx serve .
python3 -m http.server 8080
```

---

## Customising

All feature data lives in the `GROUPS` array at the top of the `<script>` block in `index.html`. Each feature has:

```js
{ id: 'unique_id', name: 'Display Name', desc: 'Short description', price: 0 }
```

Set `price: 0` for free features — the UI renders them as "Free" automatically.

---

## Credits

- UI inspired by [BunkerWeb](https://www.bunkerweb.io/) — the open-source Web Application Firewall
- Font: [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
