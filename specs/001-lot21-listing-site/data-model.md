# Data Model: Husum Greens Lot 21 – Listing Website

## Entities

### Lot
The property being sold. All fields are static — no dynamic data.

| Field | Value | Display Location |
|-------|-------|-----------------|
| development | Husum Greens | Hero headline |
| lot_number | 21 | Hero headline |
| address | 21 Ace Way, White Salmon, WA | Hero + contact section |
| price | $199,000 | Hero (prominent badge) |
| price_notes | No additional fees | Adjacent to price |
| lot_size | 0.37 acres | Lot details + aerial image label |
| orientation | Due north toward Mt. Adams | Compass indicator + highlight |
| view | Unobstructed views of Mt. Adams | Hero description + aerial label |
| tagline | Your Dream Home, Perfectly Placed. | Hero subhead |
| description | Premium sloped lot with unobstructed views of Mt. Adams. A thoughtfully designed home positioned to capture the view and maximize privacy and natural light. | Description paragraph |

### Utilities
Unique selling point: all infrastructure already exists (former golf course). Each must be prominently displayed as a bullet/icon item on the site.

| Utility | Display Label | Detail |
|---------|--------------|--------|
| water | Community Domestic Water | Community water supply available |
| irrigation | Pressurized Irrigation | Pressurized irrigation water available |
| electric | Underground Electrical | Underground electrical service to lot |
| internet | High-Speed Internet | Starlink, fiber available |
| septic | Septic Approved | Perc test completed, septic approved |

### Highlights
Five home highlights with icons.

| # | Icon | Heading | Body |
|---|------|---------|------|
| 1 | mountain | Mt. Adams Views | Front of home oriented due north to capture Mt. Adams views |
| 2 | tree | Daylight Basement | Sloped lot ideal for a daylight basement and multi-level living |
| 3 | sun | Natural Light | Expansive windows bring in natural light and scenery |
| 4 | patio | Outdoor Living | Covered outdoor living spaces for year-round enjoyment |
| 5 | house | Modern Design | Modern curb appeal with stone, wood, and clean architectural lines |

### ArchitectPlans
Optional callout — plans available with purchase.

| Field | Value |
|-------|-------|
| headline | Also Available: Fully Engineered Plans |
| architect | Portland Architect Alan Mascord |
| body | Save time and start building sooner with professionally designed, permit-ready plans included with the purchase (optional). |

### Contact
Seller contact information. Both must be tappable links.

| Field | Value | Link Type |
|-------|-------|-----------|
| phone | (360) 525-7688 | tel:+13605257688 |
| email | seth.macpherson@gmail.com | mailto:seth.macpherson@gmail.com |

### FsboGuide
Step-by-step purchase guide for buyers. Rendered as a collapsible section.

| Field | Type | Notes |
|-------|------|-------|
| step_number | integer | Display order (1–N) |
| title | string | Short step name |
| body | string | Explanation paragraph |
| resources | array of {label, url} | Public links (WA DOR, county auditor, etc.) |

See [research.md](research.md) for the populated steps.

## Images

| Asset | File | Dimensions | Usage |
|-------|------|-----------|-------|
| Aerial lot rendering | assets/aerial-rendering.jpg | 1340×1660px | Hero right column / full-width on mobile |
| House photo | assets/house-photo.jpg | 357×260px | Beside architect plans callout |
| Flyer reference | assets/flyer-full.jpg | — | Not displayed; reference only |

## CSS Design Tokens (from flyer)

```css
:root {
  /* Colors */
  --color-green-dark:   #1a3a28;  /* Main dark forest green */
  --color-green-mid:    #2d5a3d;  /* Section backgrounds */
  --color-gold:         #c8a84b;  /* Accent / architect headline */
  --color-cream:        #f5f0e8;  /* Page background */
  --color-cream-light:  #faf8f4;  /* Card backgrounds */
  --color-white:        #ffffff;
  --color-text-dark:    #1a1a1a;
  --color-text-body:    #333333;

  /* Typography */
  --font-display: 'Playfair Display', Georgia, serif;  /* HUSUM GREENS, LOT 21 */
  --font-body:    'Lato', 'Helvetica Neue', sans-serif;

  /* Spacing */
  --space-xs:  4px;
  --space-sm:  8px;
  --space-md:  16px;
  --space-lg:  32px;
  --space-xl:  64px;
}
```

*Note: Playfair Display and Lato are self-hosted or loaded from a CDN-free source (no external requests allowed — see constraints). Use system serif/sans as fallback or embed subset via base64.*
