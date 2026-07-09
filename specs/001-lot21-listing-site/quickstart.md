# Quickstart: Husum Greens Lot 21 – Listing Website

## Prerequisites

None. This is pure HTML + CSS — no build tools, no Node.js, no package manager.

## Local Development

Open `index.html` in any web browser:

```bash
open index.html       # macOS
start index.html      # Windows
xdg-open index.html   # Linux
```

For testing responsive layouts, use browser DevTools (F12) → Toggle device toolbar.

## File Structure

```
for-sale/
├── index.html          # All page content
├── styles.css          # All styles
└── assets/
    ├── aerial-rendering.jpg   # Main hero image
    └── house-photo.jpg        # Small house rendering photo
```

## Editing Content

### Update the price
In `index.html`, find the element with class `.price` and update the text.

### Update contact info
Search for `tel:+13605257688` and `mailto:seth.macpherson@gmail.com` — update both the `href` attribute and the visible text.

### Update FSBO guide steps
Find the `<details>` element with class `.fsbo-guide`. Each step is in a `<div class="step">`. Add, remove, or reorder steps as needed.

### Replace an image
Drop the new file into `assets/` with the same filename, or update the `src` attribute in the relevant `<img>` tag.

## Deploy to GitHub Pages

### First-time setup

1. Create a GitHub organization named `husumgreens` at https://github.com/organizations/new
2. Create a repository named `husumgreens.github.io` in that org
3. Add this repo as a remote:

```bash
git remote add github https://github.com/husumgreens/husumgreens.github.io.git
```

4. Enable GitHub Pages in the repo settings: Settings → Pages → Source: main branch, root folder

### Deploy an update

```bash
git add index.html styles.css assets/
git commit -m "Update listing"
git push github main
```

GitHub Pages will rebuild and publish within 1–3 minutes. The site is live at https://husumgreens.github.io.

### Verify deployment

```bash
curl -I https://husumgreens.github.io
# Should return HTTP/2 200
```

## Testing Checklist

Before pushing to GitHub Pages, verify:

- [ ] Page loads without errors in Chrome, Safari, Firefox
- [ ] Phone number tap works on a mobile device (opens dialer)
- [ ] Email tap works on a mobile device (opens mail client)
- [ ] No horizontal scrolling at 375px viewport width
- [ ] All images load (check browser DevTools → Network → Images)
- [ ] "How to Buy This Lot" section expands/collapses when tapped
- [ ] Footer text is readable (white on dark green, sufficient contrast)

## Phase 2: Performance

When ready to optimize (after Phase 1 looks good):

1. Convert images to WebP:
   ```bash
   cwebp -q 80 assets/aerial-rendering.jpg -o assets/aerial-rendering.webp
   cwebp -q 80 assets/house-photo.jpg -o assets/house-photo.webp
   ```

2. Update `<img>` tags to `<picture>` with WebP + JPEG fallback:
   ```html
   <picture>
     <source srcset="assets/aerial-rendering.webp" type="image/webp">
     <img src="assets/aerial-rendering.jpg" alt="..." width="1340" height="1660" loading="eager">
   </picture>
   ```

3. Run Lighthouse in Chrome DevTools → target 90+ on all four scores.
