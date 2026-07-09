# Contract: Color Palette & Design Tokens

All CSS must use these custom properties. No hardcoded color values in `styles.css` or HTML.

```css
:root {
  /* Primary palette — from flyer */
  --color-green-dark:    #1a3a28;  /* Headers, footer, icon backgrounds, borders */
  --color-green-mid:     #2d5a3d;  /* Hover states, secondary green elements */
  --color-gold:          #c8a84b;  /* Architect headline accent, horizontal rules */
  --color-cream:         #f0ebe0;  /* Page background */
  --color-cream-light:   #faf8f4;  /* Card backgrounds, callout boxes */
  --color-white:         #ffffff;  /* Text on dark backgrounds, button text */

  /* Text */
  --color-text-dark:     #1a1a1a;  /* Headings */
  --color-text-body:     #3a3a3a;  /* Body copy */
  --color-text-light:    #f5f0e8;  /* Text on green backgrounds */

  /* Typography */
  --font-display: Georgia, 'Times New Roman', serif;  /* LOT 21, HUSUM GREENS */
  --font-body:    -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;

  /* Spacing scale */
  --space-xs:   4px;
  --space-sm:   8px;
  --space-md:  16px;
  --space-lg:  32px;
  --space-xl:  64px;
  --space-2xl: 96px;

  /* Max content width */
  --max-width: 1100px;

  /* Border radius */
  --radius-sm:  4px;
  --radius-md:  8px;
  --radius-lg: 16px;
}
```

## Typography Scale

| Element | Font | Size (desktop) | Size (mobile) | Weight |
|---------|------|---------------|---------------|--------|
| `HUSUM GREENS` | display | 2rem | 1.5rem | 700 |
| `LOT 21` | display | 5rem | 3rem | 700 |
| Tagline | body | 1.25rem | 1rem | 700 |
| Price badge | display | 2.5rem | 2rem | 700 |
| Section headings | body | 1.5rem | 1.25rem | 700 |
| Body copy | body | 1rem | 1rem | 400 |
| Footer text | body | 0.875rem | 0.875rem | 600 |

## Print Flyer Color Reference

Exact colors extracted from the flyer PDF:
- Background: warm cream/ivory (not pure white — use `#f0ebe0`)  
- Dark green: very dark forest green — closer to `#1a3a28` than `#2d5a3d`
- Gold/amber: used only for "Fully Engineered Plans" text and horizontal divider lines
- Footer: same dark green as headers
