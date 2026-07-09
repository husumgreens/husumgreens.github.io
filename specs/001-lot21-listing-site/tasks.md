# Tasks: Husum Greens Lot 21 – Listing Website

**Input**: Design documents from `specs/001-lot21-listing-site/`  
**Prerequisites**: plan.md ✓, spec.md ✓, research.md ✓, data-model.md ✓, contracts/ ✓, quickstart.md ✓  
**Tests**: Not requested — manual browser verification only  
**Tech Stack**: HTML5 + CSS3, no JavaScript, no build system

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no shared dependencies)
- **[Story]**: Which user story this task belongs to (US1, US2, US3)

---

## Phase 1: Setup

**Purpose**: Create the project file structure and extract/prepare all assets

- [ ] T001 Create `index.html` at repo root with HTML5 boilerplate: `<!DOCTYPE html>`, `<html lang="en">`, empty `<head>`, empty `<body>`
- [ ] T002 Create `styles.css` at repo root (empty file — CSS goes here, no inline styles in HTML)
- [ ] T003 [P] Verify `assets/aerial-rendering.jpg` and `assets/house-photo.jpg` exist and display correctly in a browser (`open assets/aerial-rendering.jpg`)
- [ ] T004 [P] Create `assets/icons/` directory and write the following inline SVG icons as `.svg` files (used for Home Highlights and Utilities sections):
  - `mountain.svg` — mountain silhouette
  - `tree.svg` — pine tree
  - `sun.svg` — sun / light rays
  - `patio.svg` — covered outdoor space / chair
  - `house.svg` — house with clean lines
  - `water.svg` — water drop
  - `irrigation.svg` — sprinkler / water flow
  - `electric.svg` — lightning bolt / plug
  - `internet.svg` — wifi signal
  - `septic.svg` — checkmark with ground lines

---

## Phase 2: Foundational (CSS Design System)

**Purpose**: All CSS variables and base styles MUST exist before any section is built. Every subsequent task depends on this phase.

**⚠️ CRITICAL**: No section HTML/CSS can be written until this phase is complete

- [ ] T005 Add to `styles.css` — CSS custom properties block per `contracts/color-palette.md`:
  ```css
  :root {
    --color-green-dark: #1a3a28;
    --color-green-mid: #2d5a3d;
    --color-gold: #c8a84b;
    --color-cream: #f0ebe0;
    --color-cream-light: #faf8f4;
    --color-white: #ffffff;
    --color-text-dark: #1a1a1a;
    --color-text-body: #3a3a3a;
    --color-text-light: #f5f0e8;
    --font-display: Georgia, 'Times New Roman', serif;
    --font-body: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;
    --space-xs: 4px; --space-sm: 8px; --space-md: 16px;
    --space-lg: 32px; --space-xl: 64px; --space-2xl: 96px;
    --max-width: 1100px;
    --radius-sm: 4px; --radius-md: 8px; --radius-lg: 16px;
  }
  ```
- [ ] T006 Add to `styles.css` — CSS reset and base body styles:
  - `box-sizing: border-box` on `*`
  - `body`: `font-family: var(--font-body)`, `background: var(--color-cream)`, `color: var(--color-text-body)`, `margin: 0`, `line-height: 1.6`
  - `img`: `max-width: 100%`, `display: block`
  - `a`: inherit color, underline only on hover
- [ ] T007 Add to `index.html` `<head>` — link to `styles.css` and set page title:
  `<title>Husum Greens Lot 21 – 21 Ace Way, White Salmon, WA | $199,000</title>`
  `<link rel="stylesheet" href="styles.css">`
  `<meta name="viewport" content="width=device-width, initial-scale=1">`

**Checkpoint**: Open `index.html` in browser — cream background, no errors in DevTools console

---

## Phase 3: User Story 1 – Prospective Buyer Views Lot Details (Priority: P1) 🎯 MVP

**Goal**: Visitor can open the site and immediately see all property information: branding, price, aerial image, description, utilities, highlights, architect plans callout, and selling callout.

**Independent Test**: Open `index.html` at 1280px wide in Chrome. Verify: "Husum Greens / Lot 21 / Your Dream Home, Perfectly Placed." is visible at top. Price "$199,000" is prominent. Aerial image loads. All five Home Highlights are listed. All five utilities are listed. Architect plans callout box is visible. Footer reads "PREMIUM LOCATION • BREATHTAKING VIEWS • ENDLESS POSSIBILITIES".

### Implementation for User Story 1

- [ ] T008 [US1] Add `<header>` section to `index.html` with:
  - `<p class="development-name">HUSUM GREENS</p>` (with `🌲` SVG or inline pine tree icon between two `<hr>` lines)
  - `<h1 class="lot-number">LOT 21</h1>`
  - `<p class="tagline">YOUR DREAM HOME, PERFECTLY PLACED.</p>`
  - Apply CSS: development name in `var(--font-display)` small caps, dark green; LOT 21 in very large display font (5rem desktop, 3rem mobile), dark green; tagline bold sans-serif 1.25rem

- [ ] T009 [US1] Add `.hero` section to `index.html` — two-column layout (text left, image right at ≥768px, stacked on mobile):
  - Left column: address `<p>21 Ace Way, White Salmon, WA</p>`, price badge `<div class="price-badge"><span class="price">$199,000</span><span class="price-note">No additional fees</span></div>`
  - Right column: `<img src="assets/aerial-rendering.jpg" alt="Aerial view of Lot 21, Husum Greens — 0.37 acres with unobstructed Mt. Adams views" class="aerial-img">`
  - Add CSS for two-column grid, price badge (large display font, dark green background or cream with green border), address styling

- [ ] T010 [US1] Add `.description` section below hero in `index.html`:
  - Description paragraph: "Premium sloped lot with unobstructed views of Mt. Adams. A thoughtfully designed home positioned to capture the view and maximize privacy and natural light."
  - Apply CSS: max-width readable line length (~65ch), centered container, `var(--space-xl)` vertical padding

- [ ] T011 [US1] Add `.utilities` section to `index.html` — "Ready to Build" or "Utilities Available" heading with 5-item icon grid:
  - Community Domestic Water (water.svg icon)
  - Pressurized Irrigation (irrigation.svg icon)
  - Underground Electrical Service (electric.svg icon)
  - High-Speed Internet — Starlink & fiber available (internet.svg icon)
  - Septic Approved — perc test completed (septic.svg icon)
  - CSS: 2-column grid on mobile, 5-column on desktop; each item: circular dark-green icon container + label text below

- [ ] T012 [US1] Add `.highlights` section to `index.html` with heading "HOME HIGHLIGHTS" and 5 items (icon + text, inline layout):
  1. mountain.svg — "Front of home oriented due north to capture Mt. Adams views"
  2. tree.svg — "Sloped lot ideal for a daylight basement and multi-level living"
  3. sun.svg — "Expansive windows bring in natural light and scenery"
  4. patio.svg — "Covered outdoor living spaces for year-round enjoyment"
  5. house.svg — "Modern curb appeal with stone, wood, and clean architectural lines"
  - CSS: list with icon (40px circular dark-green container) on left, text on right; dark green icon bg, white SVG fill; generous gap between items

- [ ] T013 [US1] Add `.architect-callout` box to `index.html` — bordered callout with:
  - Checkmark icon (inline SVG) in dark green circle
  - `<strong>ALSO AVAILABLE</strong>` uppercase
  - `<span class="gold-text">FULLY ENGINEERED PLANS</span>` in `var(--color-gold)`
  - `<em>by Portland Architect Alan Mascord</em>`
  - Body text: "Save time and start building sooner with professionally designed, permit-ready plans included with the purchase (optional)."
  - `<img src="assets/house-photo.jpg" alt="Rendered house design for Lot 21 by Alan Mascord">` displayed nearby (right of callout or below on mobile)
  - CSS: cream-light background, 2px dark-green border, padding var(--space-lg), border-radius var(--radius-md)

- [ ] T014 [US1] Add `.selling-callout` banner to `index.html`:
  - Pine tree SVG icon (left)
  - `<strong>SELLING OUR LOT – HUSUM GREENS LOT 21</strong>`
  - `<em>Bring your vision to life in this exceptional location.</em>`
  - CSS: cream-light background, dark green left border (4px), padding, flex layout with icon

- [ ] T015 [US1] Add `<footer>` to `index.html`:
  - `<p>PREMIUM LOCATION &bull; BREATHTAKING VIEWS &bull; ENDLESS POSSIBILITIES</p>`
  - CSS: `background: var(--color-green-dark)`, `color: var(--color-text-light)`, text centered, letter-spacing 0.15em, text-transform uppercase, padding var(--space-md) var(--space-lg)

- [ ] T016 [US1] Write responsive CSS for the full page layout in `styles.css`:
  - Mobile-first base styles (single column, full-width images)
  - `@media (min-width: 768px)`: two-column hero layout, wider utility grid
  - `@media (min-width: 1024px)`: centered container `max-width: var(--max-width)`, larger typography
  - Ensure no horizontal overflow at 320px viewport (test in DevTools)

**Checkpoint**: Open `index.html` in Chrome. Resize from 320px to 1280px — no horizontal scrollbar at any width. All sections visible. Images load. Visual matches the print flyer aesthetic.

---

## Phase 4: User Story 2 – Interested Buyer Contacts the Seller (Priority: P2)

**Goal**: Visitor can tap/click the phone number to call and the email address to open their mail client — from any device.

**Independent Test**: On a mobile device (or DevTools mobile emulation), tap `(360) 525-7688` — phone dialer opens. Tap `seth.macpherson@gmail.com` — mail client opens. On desktop, click email — mail client opens.

### Implementation for User Story 2

- [ ] T017 [US2] Add `.contact` section to `index.html` between `.selling-callout` and the FSBO guide section:
  - Heading: `<h2>Interested?</h2>`
  - Phone: `<a href="tel:+13605257688" class="contact-link contact-phone">(360) 525-7688</a>` with phone icon (inline SVG)
  - Email: `<a href="mailto:seth.macpherson@gmail.com" class="contact-link contact-email">seth.macpherson@gmail.com</a>` with envelope icon (inline SVG)
  - NO QR code (per spec FR-009)

- [ ] T018 [US2] Add CSS for `.contact` section in `styles.css`:
  - Links: large tap targets (minimum 44×44px touch target per WCAG), `color: var(--color-green-dark)`, font-size 1.25rem
  - Hover state: underline + slight color shift to `var(--color-green-mid)`
  - Focus state: visible focus ring (2px solid dark green, 2px offset) — keyboard accessible
  - Icons: 24px, vertically aligned with text

**Checkpoint**: Verify on Chrome DevTools iPhone 14 emulation — both links are large enough to tap. Click each link on desktop — correct handlers open.

---

## Phase 5: User Story 3 – Visitor Understands Lot Orientation & Features (Priority: P3)

**Goal**: Visitor can read the compass indicator and lot size from the aerial image section, and can expand the "How to Buy This Lot" guide to understand the full FSBO purchase process.

**Independent Test**: (1) Verify "Due North to Mt. Adams" indicator and ".37 Acres" text appear near the aerial image. (2) Click "How to Buy This Lot" — section expands showing step-by-step guide with resource links.

### Implementation for User Story 3

- [ ] T019 [US3] Add compass indicator and lot stats to the `.hero` section in `index.html`:
  - Below or overlaid on the aerial image, add:
    ```html
    <div class="lot-stats">
      <div class="compass">↑ Due North to Mt. Adams</div>
      <div class="lot-size">Lot Size: .37 Acres</div>
    </div>
    ```
  - CSS: small text, dark green, positioned below the aerial image (avoid CSS `position: absolute` overlay since it adds complexity — place as a caption div)

- [ ] T020 [US3] Add `<details class="fsbo-guide">` FSBO guide section to `index.html`, above the `<footer>`:
  ```html
  <details class="fsbo-guide">
    <summary>How to Buy This Lot</summary>
    <div class="guide-content">
      <!-- Steps from research.md -->
    </div>
  </details>
  ```
  Populate with all 8 steps from `specs/001-lot21-listing-site/research.md` (Step 1: Prepare → Step 8: Proceeds), including:
  - Step headings as `<h3>` elements
  - Resource links (`target="_blank" rel="noopener"`) for all county/state URLs
  - REET calculation table: $199,000 × 1.35% = $2,686.50
  - County contact info: Treasurer Greg Gallagher (509) 773-4664, Auditor (509) 773-4001
  - Title company recommendations with phone numbers

- [ ] T021 [US3] Add CSS for `<details>` FSBO guide in `styles.css`:
  - `summary`: cursor pointer, font-weight bold, font-size 1.25rem, color `var(--color-green-dark)`, padding `var(--space-md)`, list-style none (remove default triangle, add custom ▸/▾)
  - `.guide-content`: padding `var(--space-lg)`, `border-top: 1px solid var(--color-green-dark)`, cream-light background
  - Guide step headings: `var(--color-green-dark)`, 1rem bold
  - Links inside guide: `var(--color-green-mid)`, underlined
  - On mobile: full-width, stacked layout

**Checkpoint**: Click "How to Buy This Lot" — expands without JavaScript. All 8 steps are visible. Links open in new tab. Works with JS disabled (test via DevTools → Network → Disable JavaScript).

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: SEO, accessibility, final visual review, deployment setup

- [ ] T022 [P] Add SEO meta tags to `index.html` `<head>`:
  ```html
  <meta name="description" content="Lot 21 at Husum Greens — 0.37 acres in White Salmon, WA. Unobstructed Mt. Adams views. $199,000, no fees. Power, water, irrigation, septic approved.">
  <meta property="og:title" content="Husum Greens Lot 21 – 21 Ace Way, White Salmon, WA">
  <meta property="og:description" content="Premium 0.37-acre lot with Mt. Adams views. $199,000, no additional fees. Utilities in place.">
  <meta property="og:image" content="https://husumgreens.github.io/assets/aerial-rendering.jpg">
  <meta property="og:url" content="https://husumgreens.github.io">
  <meta property="og:type" content="website">
  ```

- [ ] T023 [P] Add accessibility attributes in `index.html`:
  - All `<img>` tags have descriptive `alt` text (verify none are empty)
  - All icon-only elements have `aria-hidden="true"` on the SVG
  - `<html lang="en">` is set (verify from T001)
  - `<main>` wraps the primary content (between header and footer)
  - Contact links have `aria-label` if the visible text isn't self-explanatory

- [ ] T024 Add `width` and `height` attributes to both images in `index.html` to prevent layout shift:
  - Aerial rendering: `width="1340" height="1660"`
  - House photo: `width="357" height="260"`

- [ ] T025 Cross-browser and responsive testing — open `index.html` and verify each item:
  - [ ] Chrome desktop (1280px): all sections visible, no overflow
  - [ ] Chrome DevTools iPhone 14 (390px): single column, no horizontal scroll
  - [ ] Chrome DevTools iPad (768px): two-column hero, correct layout
  - [ ] Safari (macOS): open and visually review
  - [ ] Firefox: open and visually review
  - [ ] Phone number tap test (mobile or DevTools): dialer opens
  - [ ] Email tap test: mail client opens
  - [ ] FSBO guide expand/collapse: works without JS
  - [ ] DevTools → disable JS → reload: site fully functional

- [ ] T026 [P] Create `.nojekyll` file at repo root (empty file):
  - Prevents GitHub Pages from processing with Jekyll, which would ignore `assets/` directory
  - `touch .nojekyll`

- [ ] T027 [P] Create `README.md` at repo root documenting:
  - What this repo is (listing site for Husum Greens Lot 21)
  - How to edit content (link to quickstart.md)
  - How to deploy (push to `husumgreens/husumgreens.github.io` main branch)
  - GitHub Pages URL: https://husumgreens.github.io

- [ ] T028 Final visual review — compare `index.html` side-by-side with `assets/flyer-full.jpg`:
  - Color palette matches (dark forest green, cream, gold accent)
  - Typography hierarchy matches (LOT 21 is the dominant text element)
  - Pine tree motif present in header and selling callout
  - All content from flyer is present (excluding QR code)
  - Utilities section is visible and prominent (new addition not in flyer)
  - Price is prominent above the fold on desktop

---

## Dependencies & Execution Order

### Phase Dependencies

- **Phase 1 (Setup)**: No dependencies — start immediately
- **Phase 2 (Foundation)**: Depends on Phase 1 — BLOCKS all subsequent phases
- **Phase 3 (US1)**: Depends on Phase 2 — implements the majority of visible content
- **Phase 4 (US2)**: Depends on Phase 2 — contact section can be built after foundation
- **Phase 5 (US3)**: Depends on Phase 3 (hero must exist before adding compass indicator)
- **Phase 6 (Polish)**: Depends on Phases 3–5 all complete

### User Story Dependencies

- **US1**: Can start immediately after Phase 2 — no dependency on US2 or US3
- **US2**: Can start after Phase 2, parallel to US1 (different sections of index.html — avoid merge conflicts by splitting work on separate tasks)
- **US3**: Depends on US1 (compass adds to hero section) — do US3 after T009 is complete

### Parallel Opportunities Within US1

```
T008 (header)       T010 (description)    T015 (footer)
T009 (hero)         T011 (utilities)      [then T016 responsiveness last]
                    T012 (highlights)
                    T013 (architect box)
                    T014 (selling callout)
```
These can be drafted in parallel (different `<section>` blocks) then assembled in order.

---

## Implementation Strategy

### MVP First (User Story 1 Only — ~3–4 hours)

1. Complete Phase 1 (Setup) — 15 min
2. Complete Phase 2 (Foundation CSS) — 30 min
3. Complete Phase 3 (US1 — all visible content) — 2–3 hours
4. **STOP and VALIDATE**: Open in browser, compare to flyer, verify on mobile
5. If it looks good, push to GitHub Pages

### Incremental Delivery

1. Phase 1 + 2 + 3 → MVP listing site live on GitHub Pages
2. Add Phase 4 (US2 contact section) → contact links tested on real mobile device
3. Add Phase 5 (US3 compass + FSBO guide) → guide content populated from research.md
4. Phase 6 (Polish) → SEO, accessibility, final review

### Single Developer Strategy

Work top-to-bottom in order (T001 → T028). Each task is small enough to complete in 10–30 minutes. Commit after each phase checkpoint.

---

## Notes

- `[P]` tasks touch different files or non-conflicting sections — safe to draft simultaneously
- All styling goes in `styles.css`, no `style=""` attributes in HTML
- SVG icons: write directly as `<svg>` in HTML (inline) rather than loading from `assets/icons/` — saves requests, allows CSS color styling via `currentColor`
- Commit after each phase checkpoint before continuing
- Phase 2 is the most critical — if CSS variables aren't set correctly, everything downstream is wrong
- The FSBO guide in Phase 5 has the most content — copy from `specs/001-lot21-listing-site/research.md` directly
