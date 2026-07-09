# Implementation Plan: Husum Greens Lot 21 – Listing Website

**Branch**: `001-lot21-listing-site` | **Date**: 2026-07-07 | **Spec**: [spec.md](spec.md)  
**Input**: Feature specification from `specs/001-lot21-listing-site/spec.md`

## Summary

Build a visually polished, single-page static listing site for Lot 21 at 21 Ace Way, White Salmon, WA — priced at $199,000 with no additional fees. The site mirrors the print flyer design (dark forest green + cream palette, pine tree motifs, aerial lot rendering as hero) and adds a buyer-facing FSBO guide covering the Klickitat County purchase process. Deployed as a static site on GitHub Pages at https://husumgreens.github.io. Phase 1 prioritizes visual fidelity; performance optimization is a follow-on phase.

## Technical Context

**Language/Version**: HTML5, CSS3 — no JavaScript required  
**Primary Dependencies**: None (vanilla HTML/CSS only)  
**Storage**: N/A — fully static  
**Testing**: Manual cross-browser testing (Chrome, Safari, Firefox) on mobile (375px) and desktop (1280px+)  
**Target Platform**: GitHub Pages (static hosting), all modern browsers  
**Project Type**: Static marketing website  
**Performance Goals**: Phase 1 — visual quality first; Phase 2 — <3s LCP, Core Web Vitals green  
**Constraints**: No server-side code, no build system required, no JavaScript framework, pure static files  
**Scale/Scope**: Single index.html page, one CSS file, ~3 image assets. Optional second page or collapsible section for FSBO guide.

## Constitution Check

*No active constitution — blank template present. No gates to enforce.*

No architectural violations. This is the simplest possible scope: a static HTML/CSS page with no dependencies, no server, no database, no auth. All spec requirements are achievable within these constraints.

## Project Structure

### Documentation (this feature)

```text
specs/001-lot21-listing-site/
├── plan.md              ← this file
├── research.md          ← Phase 0: FSBO guide research + image strategy
├── data-model.md        ← Phase 1: content entities (lot, contact, highlights)
├── quickstart.md        ← Phase 1: how to edit and deploy
├── contracts/           ← Phase 1: page structure contract
└── tasks.md             ← Phase 2: /speckit-tasks output
```

### Source Code (repository root)

```text
for-sale/                         ← this repo (becomes husumgreens.github.io)
├── index.html                    ← single page listing site
├── styles.css                    ← all styles (no inline styles in HTML)
├── assets/
│   ├── aerial-rendering.jpg      ← extracted from flyer PDF ✓ done
│   ├── house-photo.jpg           ← extracted from flyer PDF ✓ done
│   └── icons/                    ← SVG icons for Home Highlights section
│       ├── mountain.svg
│       ├── tree.svg
│       ├── sun.svg
│       ├── patio.svg
│       └── house.svg
└── specs/                        ← spec kit (not deployed to GitHub Pages)
```

**Structure Decision**: Flat structure at repo root. GitHub Pages serves `index.html` directly from the `main` branch. No build step. `assets/` holds all images. SVG icons are inline in HTML for zero extra requests and full CSS styling.

**GitHub Pages Setup**: A GitHub organization named `husumgreens` must be created, and this repo pushed as `husumgreens/husumgreens.github.io`. That org + repo name combo makes GitHub Pages serve at https://husumgreens.github.io automatically.

## Phase 0: Research

*Output:* [research.md](research.md)

### Research Tasks

1. **Klickitat County FSBO process** — step-by-step from listing to closing for FSBO land sale in WA *(in progress — background agent)*
2. **WA State REET** — Real Estate Excise Tax rates for $199K sale, who pays
3. **Required disclosures** — WA Seller Disclosure Statement (RCW 64.06) applicability to vacant land
4. **Title/Escrow options** — Title companies serving Klickitat County that handle FSBO closings
5. **Image optimization strategy** — WebP with JPEG fallback, appropriate sizing for hero aerial image

### Key Decisions (from research)

| Decision | Choice | Rationale |
|----------|--------|-----------|
| JS requirement | None | Spec requires JS-disabled compatibility; pure CSS is sufficient |
| Icon delivery | Inline SVG | Zero additional requests; fully styleable with CSS color variables |
| Image format | JPEG (phase 1), WebP (phase 2) | JPEG works everywhere; WebP optimization is a phase 2 task |
| FSBO guide placement | Collapsible `<details>` section on index.html | Keeps single-page, no navigation needed, no JS required |
| Price display | Hero section, prominent | $199K is a key CTA driver — must be above the fold on mobile |

## Phase 1: Design & Contracts

*Output:* [data-model.md](data-model.md), [contracts/](contracts/), [quickstart.md](quickstart.md)

### Content Entities → data-model.md

- **Lot**: address, price, size, orientation, utilities, development
- **Highlight**: icon, heading, body (5 items)
- **ArchitectPlans**: headline, architect name, body text (optional callout)
- **Contact**: phone (tel: link), email (mailto: link)
- **FsboGuide**: steps array, each with title, body, resources

### Interface Contracts → contracts/

- `contracts/page-structure.md` — sections in order, required content per section
- `contracts/color-palette.md` — CSS custom properties (design tokens from flyer)
- `contracts/typography.md` — font sizes, weights, line heights per breakpoint

### Quickstart → quickstart.md

- How to edit content (which lines in index.html to change)
- How to add/replace images
- How to deploy to GitHub Pages (push to main)
- How to test locally (open index.html in browser — no server needed)

## Implementation Phases

### Phase 1A: Visual Shell (do this first — "make it look good")

Build the full page layout with pixel-accurate design from the flyer. Priority: visual fidelity.

1. HTML structure — all sections in order, semantic markup
2. CSS design tokens (colors, typography, spacing extracted from flyer)
3. Hero section — aerial image, "Husum Greens / Lot 21 / Your Dream Home, Perfectly Placed.", price badge
4. Lot details — size, orientation, utilities callout
5. Home Highlights — 5 items with inline SVG icons
6. Architect plans callout box (dark green border, check icon, green headline)
7. "Selling Our Lot" callout banner with pine tree icon
8. Contact section — tel + mailto links, no QR code
9. Footer strip — "PREMIUM LOCATION • BREATHTAKING VIEWS • ENDLESS POSSIBILITIES"
10. Full responsiveness (320px → 1280px+)
11. SEO meta tags (title, description, Open Graph image)

**Success gate**: Page matches flyer design at desktop. All content present. Contact links work on mobile. No horizontal scrolling at 320px.

### Phase 1B: FSBO Buyer Guide (after visual shell)

Add a collapsible "How to Buy This Lot" section above the footer using HTML `<details>`/`<summary>` — no JavaScript needed.

Content (from research.md once available):
1. Overview: FSBO purchase in Klickitat County, WA
2. Step-by-step: Offer → Escrow → Disclosures → Deed → Recording
3. WA State REET (who pays, how much at $199K)
4. Seller Disclosure Statement requirements
5. Title company options for Klickitat County
6. Key public resource links

**Success gate**: A buyer who has never purchased land can read this section and understand every step required to complete the purchase.

### Phase 2: Performance (follow-on — "make it fast")

After Phase 1A is live and approved:

1. Convert images to WebP with JPEG fallback via `<picture>` element
2. Add `loading="lazy"` to below-fold images
3. Add `<link rel="preload">` for hero image
4. Run Lighthouse — target 90+ on Performance, Accessibility, SEO
5. Add `width` and `height` attributes to all images (prevent layout shift)
6. Consider minifying CSS (likely unnecessary — file will be small)

## Key Corrections Applied

| Field | Old Value | Corrected Value |
|-------|-----------|-----------------|
| Address | 15 Ace Way | **21 Ace Way, White Salmon, WA** |
| Price | (not shown) | **$199,000 — no additional fees** |
| Utilities | (not mentioned) | **Power, water, irrigation — already plumbed (former golf course)** |
| FSBO guide | (not in original spec) | **Required — Klickitat County step-by-step process** |
