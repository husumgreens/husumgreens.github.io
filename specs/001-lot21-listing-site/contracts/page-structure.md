# Contract: Page Structure

The `index.html` MUST contain these sections in this order, with this required content. Changing the order or omitting a section violates this contract.

## Section 1: `<header>` — Branding

- "Husum Greens" in display serif, dark forest green (#1a3a28)
- Pine tree icon (inline SVG)
- "LOT 21" in large display serif
- "Your Dream Home, Perfectly Placed." tagline in bold sans-serif

## Section 2: `.hero` — Price + Aerial Image

- Price badge: "$199,000" prominent, with "No additional fees" subtext
- Aerial lot rendering image (assets/aerial-rendering.jpg)
- Address: "21 Ace Way, White Salmon, WA"
- "Due North to Mt. Adams" compass indicator (overlaid on or adjacent to image)
- Lot size label: ".37 Acres"

## Section 3: `.description` — Property Description

- Body paragraph: "Premium sloped lot with unobstructed views of Mt. Adams. A thoughtfully designed home positioned to capture the view and maximize privacy and natural light."
- Utilities callout — 5 items displayed as icon+text list:
  1. Community Domestic Water available
  2. Pressurized Irrigation available
  3. Underground Electrical service to lot
  4. High-Speed Internet (Starlink, fiber)
  5. Septic Approved — perc test completed

## Section 4: `.architect-callout` — Plans Callout Box

- Check mark icon
- "Also Available" uppercase
- "Fully Engineered Plans" in gold/accent (#c8a84b)
- "by Portland Architect Alan Mascord" italic
- Body: "Save time and start building sooner with professionally designed, permit-ready plans included with the purchase (optional)."
- House photo (assets/house-photo.jpg) displayed nearby

## Section 5: `.highlights` — Home Highlights

Exactly 5 items, each with:
- Circular dark-green icon container with inline SVG icon
- Highlight text (see data-model.md for all 5)

## Section 6: `.selling-callout` — Lot Callout Banner

- Pine tree icon
- "Selling Our Lot – Husum Greens Lot 21" bold
- "Bring your vision to life in this exceptional location." italic

## Section 7: `.contact` — Contact Information

- "Interested?" heading
- Phone: `(360) 525-7688` as `<a href="tel:+13605257688">` link
- Email: `seth.macpherson@gmail.com` as `<a href="mailto:seth.macpherson@gmail.com">` link
- NO QR code

## Section 8: `<details>` — How to Buy This Lot (FSBO Guide)

- `<summary>` text: "How to Buy This Lot"
- Collapsed by default
- Contains the full FSBO step-by-step guide from research.md
- All external links open in `target="_blank" rel="noopener"`

## Section 9: `<footer>` — Footer Strip

- Dark forest green background
- Text: "PREMIUM LOCATION • BREATHTAKING VIEWS • ENDLESS POSSIBILITIES"
- All caps, letter-spaced

## Responsive Breakpoints

| Breakpoint | Layout |
|------------|--------|
| ≤767px (mobile) | Single column; aerial image full-width above description |
| ≥768px (tablet) | Two-column hero (text left, image right) |
| ≥1024px (desktop) | Two-column hero, max-width container centered |

## Accessibility Requirements

- All images have descriptive `alt` text
- Color contrast ratio ≥ 4.5:1 for body text (WCAG AA)
- `tel:` and `mailto:` links have visible focus styles
- `<details>` section uses native HTML semantics (no ARIA required)
- `<html lang="en">` set
- Page title: "Husum Greens Lot 21 – 21 Ace Way, White Salmon, WA | $199,000"
