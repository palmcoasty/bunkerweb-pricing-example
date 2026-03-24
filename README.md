# !!! Disclaimer this is a example to showcase how a pricing system could be implimented in bunkerweb, it is build by a community fellow and is not confirmed nor creating any api keys for bunkerweb its just a simple demonstration.

# BunkerWeb Pricing Page

A static GitHub Pages site styled after [BunkerWeb](https://github.com/bunkerity/bunkerweb) that replicates the official pricing structure — self-hosted plans, cloud offer, PRO feature selection, instance-based pricing, and API key generation.

## Live Demo

Deploy to GitHub Pages and your URL will be:
`https://<your-username>.github.io/<repo-name>/`

---

## What's on the page

### PRO Features (all included in every paid plan)

| Feature | Description |
|---|---|
| 🌊 Anti-DDoS | Advanced protection against DDoS attacks |
| ☁️ Backup S3 | Remote backup to Amazon S3 |
| 🔄 Migration | Easily migrate the database between environments |
| 📊 Monitoring | Monitor service status and performance |
| 📈 Prometheus Exporter | Exposes metrics for Prometheus, compatible with Grafana |
| 📋 Reporting | Generates weekly or monthly usage and threat reports |
| 👥 User Manager | Manage users and their access rights |

### Self-Hosted Plans

| Plan | Price | Best for |
|---|---|---|
| 🛡️ Shield (Standard) | 49€/mo + 15€/extra instance | SMBs, startups, growing IT projects |
| 🏰 Fortress (Enterprise) | 149€/mo + 39€/extra instance | Multi-site orgs, healthcare, finance, education |
| 🔭 Sentinel (Custom) | Get a quote | Specific / enterprise-scale needs |

### Cloud Plans

| Plan | Price | Notes |
|---|---|---|
| ☁️ The Essential | Starting from 639€/mo | Fully managed SaaS by BunkerWeb maintainers |
| 🔧 Need More? | Custom quote | 50+ services, custom SLA, custom dev |

### Interactive features

- **PRO feature picker** — click features to highlight what matters most to you
- **Instance slider** — drag from 1 to 20; price recalculates live per plan
- **Self-hosted / Cloud tab** — switches between the two offering types
- **Sticky summary bar** — shows selected plan, price, and chosen PRO features
- **API key generator** — clicking "Get API Key" shows a `bwk_xxx_xxx_xxx` key with copy-to-clipboard
- **30-day trial callout** — shown for Shield and Fortress plans
- Zero dependencies — single `index.html`, no build step

---

## Deploy to GitHub Pages

### Option 1 — Settings UI (simplest)

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Click **Save** — live in ~60 seconds.

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

## Run locally

```bash
# macOS
open index.html

# Or serve with any static file server
npx serve .
python3 -m http.server 8080
```

---

## Customising prices

All data is in the `<script>` block of `index.html`:

- **`PRO_FEATURES`** — the 7 PRO add-on cards
- **`SELF_PLANS`** — Shield, Fortress, Sentinel; edit `basePrice` and `extraPerInstance`
- **`CLOUD_PLANS`** — The Essential and custom cloud plans

---

## Credits

- Pricing and feature set: [bunkerweb.io](https://www.bunkerweb.io/)
- Open-source WAF: [github.com/bunkerity/bunkerweb](https://github.com/bunkerity/bunkerweb)
- Font: [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
