# mustafaassaf

Personal profile site for Mustafa Assaf — a single, dependency-free `index.html`.
No build step, no framework, no trackers. Fonts come from Google Fonts; everything
else (CSS, favicon) is inline, so the page is one file you can drop anywhere.

## Local preview

```sh
open index.html          # or: python3 -m http.server 8000
```

## Deploy on GitHub Pages

1. Push to `main`.
2. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*,
   Branch = `main`, folder = `/ (root)`.
3. The site goes live at `https://mkassaf.github.io/mustafaassaf/`.

`.nojekyll` is present so Pages serves the files as-is instead of running Jekyll.

## Custom domain (DNS)

Once the domain is picked, add a `CNAME` file at the repo root containing just the
hostname (no protocol, no trailing slash, one line), e.g.:

```
mustafaassaf.com
```

Then set the DNS records at the registrar:

| Use | Record | Name | Value |
| --- | --- | --- | --- |
| Apex (`example.com`) | `A` | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| Apex, IPv6 (optional) | `AAAA` | `@` | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |
| Subdomain (`www.example.com`) | `CNAME` | `www` | `mkassaf.github.io.` |

Then in **Settings → Pages**, enter the domain under *Custom domain* and tick
**Enforce HTTPS** once the certificate is issued (can take up to ~24h after the DNS
records propagate).

With a custom domain the site is served from the domain root. The page uses only
relative and anchor links, so it works at the root and at the `/mustafaassaf/`
subpath without changes.

## Editing

Everything lives in `index.html`:

- **Design tokens** — colors, fonts, spacing in the `:root` block at the top of
  `<style>`; the dark palette is redefined twice (once under
  `prefers-color-scheme: dark`, once under `[data-theme="dark"]`) — change both.
- **Content** — `<header class="hero">` (name, roles, intro, title block), then the
  `#research`, `#experience`, `#education` and `#contact` sections. Timeline items
  are `<article class="entry">` blocks; copy one to add a role or a degree.
