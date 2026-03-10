# acocado Store - Jekyll Setup

Premium electronics store built with Jekyll and GitHub Pages.

## Quick Start

### 1. Create GitHub Repository
```bash
# On GitHub, create a new repository named "acocado-store" (or any name)
# Don't initialize with README (you already have one)
```

### 2. Upload Your Files

**Your folder structure should look like this:**
```
acocado-store/
├── _config.yml
├── _layouts/
│   ├── default.html
│   └── product.html
├── _products/
│   ├── xbox-series-s/
│   │   └── en.md
│   └── tascam-portacapture-x8/
│       └── en.md
├── index.html
├── about.html
└── README.md
```

### 3. Push to GitHub
```bash
cd acocado-store
git init
git add .
git commit -m "Initial acocado store setup"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/acocado-store.git
git push -u origin main
```

### 4. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings**
3. Scroll to **Pages** (left sidebar)
4. Under **Source**, select **main** branch
5. Click **Save**
6. Wait 1-2 minutes

Your store will be live at: `https://YOUR-USERNAME.github.io/acocado-store/`

### 5. Custom Domain (acocado.com)

1. In your domain registrar (where you bought acocado.com):
   - Add CNAME record: `www` → `YOUR-USERNAME.github.io`
   - Add A records for apex domain:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`

2. In GitHub Pages settings:
   - Enter `acocado.com` in **Custom domain**
   - Check **Enforce HTTPS** (wait for SSL cert)

## Adding Products

### Create a new product:
```bash
# 1. Create product folder
mkdir -p _products/new-product-name

# 2. Create English description
cat > _products/new-product-name/en.md << 'EOF'
---
title: Product Name
price: 299
stripe_link: https://buy.stripe.com/YOUR_LINK
opennode_link: https://checkout.opennode.com/YOUR_LINK
category: electronics
language: en
featured: true
images:
  - product-image.jpg
features:
  - Feature 1
  - Feature 2
  - Feature 3
---

Product description goes here.

Multiple paragraphs supported.
EOF

# 3. Add product image (optional for now)
# cp your-image.jpg _products/new-product-name/product-image.jpg

# 4. Push to GitHub
git add _products/new-product-name
git commit -m "Add new product"
git push
```

Product appears automatically in ~1 minute!

## Adding Translations

### Add Bulgarian translation:
```bash
cat > _products/xbox-series-s/bg.md << 'EOF'
---
title: Xbox Series S - Стартов пакет
price: 199
stripe_link: https://buy.stripe.com/placeholder-xbox
opennode_link: https://checkout.opennode.com/placeholder-xbox
category: gaming
language: bg
featured: true
images:
  - placeholder-xbox.jpg
---

Български превод на описанието...
EOF

git add _products/xbox-series-s/bg.md
git commit -m "Add Bulgarian translation for Xbox"
git push
```

## Updating Stripe/OpenNode Links

### Replace placeholder links with real ones:

1. Open product file (e.g., `_products/xbox-series-s/en.md`)
2. Replace:
   - `stripe_link: https://buy.stripe.com/placeholder-xbox`
   - With your real Stripe Payment Link
3. Replace:
   - `opennode_link: https://checkout.opennode.com/placeholder-xbox`
   - With your real OpenNode checkout link
4. Save, commit, push

## Adding Product Images

1. Add image to product folder:
```bash
   cp xbox-image.jpg _products/xbox-series-s/
```

2. Update `en.md`:
```yaml
   images:
     - xbox-image.jpg
```

3. Push to GitHub

## Customizing Design

### Change colors:

Edit `_layouts/default.html` - search for:
- `bg-gray-900` → change to your color (e.g., `bg-blue-900`)
- `text-gray-900` → change text color

### Change fonts:

Edit `_layouts/default.html` - replace:
```html
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap');
```

With your preferred Google Font.

## Testing Locally (Optional)
```bash
# Install Jekyll
gem install bundler jekyll

# Run local server
jekyll serve

# View at http://localhost:4000
```

## Support

- Jekyll Documentation: https://jekyllrb.com/docs/
- GitHub Pages: https://docs.github.com/en/pages
- Tailwind CSS: https://tailwindcss.com/docs

---

Built with Jekyll + Tailwind CSS + GitHub Pages