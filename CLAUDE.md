# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**acocado** is a Jekyll-based static e-commerce storefront for premium electronics, hosted on GitHub Pages at `acocado.com`. Products are managed through Jekyll collections with YAML front-matter — no database or backend.

## Local Development

```bash
gem install bundler jekyll
jekyll serve
# View at http://localhost:4000
```

Deployment is automatic on push to `main` via GitHub Actions (`.github/workflows/jekyll-gh-pages.yml`).

## Architecture

### Layouts (`_layouts/`)
- `default.html` — master layout: navigation, footer, global styles (Tailwind CSS v4 via CDN, Space Grotesk font)
- `product.html` — product page: image carousel (vanilla JS, up to 3 visible thumbnails), pricing, Stripe/Bitcoin checkout buttons

### Products (`_products/`)
Each product is a folder containing one markdown file per language (e.g., `en.md`, `bg.md`). The YAML front-matter drives everything — title, price, payment links, image filenames, category, features. Products automatically appear in the homepage grid via Jekyll's collection output.

**Product front-matter structure:**
```yaml
---
layout: product
title: "Product Name"
price: "€299"
category: "Audio"
language: en
images:
  - image1.jpg
  - image2.jpg
stripe_link: "https://buy.stripe.com/..."
bitcoin_link: "https://checkout.opennode.com/..."
features:
  - Feature one
  - Feature two
---
Product description in markdown.
```

### Pages
- `index.html` — homepage, iterates `site.products` to render product grid
- `about.html` — company info

### Styling
Tailwind CSS v4 (CDN). Custom color palette defined as CSS variables:
- Deep plum `#584053` — primary text
- Teal `#8DC6BF` — accents/navigation
- Coral `#F97B4F` — hover, prices
- Yellow `#FCBC66` — highlights
- Off-white `#fdfdfd` — backgrounds

### Multi-language
Languages configured in `_config.yml` (`["en", "bg"]`). Each product folder contains one file per locale. No automated translation — content is manually written per language.

## Adding a Product

1. Create `_products/<product-slug>/` directory
2. Add `en.md` (and optionally `bg.md`) with full YAML front-matter
3. Add product images to the same folder
4. Update `stripe_link` and `bitcoin_link` with real payment URLs

## Key Config

- `_config.yml` — site metadata, collection settings, language list
- `CNAME` — custom domain (`acocado.com`)
