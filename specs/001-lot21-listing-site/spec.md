# Feature Specification: Husum Greens Lot 21 – Listing Website

**Feature Branch**: `001-lot21-listing-site`  
**Created**: 2026-07-07  
**Status**: Draft  
**Input**: User description: "Single-page responsive real estate listing website for Husum Greens Lot 21 (15 Ace Way, White Salmon, WA), hosted on GitHub Pages at https://husumgreens.github.io. Based on print flyer design."

## User Scenarios & Testing *(mandatory)*

### User Story 1 – Prospective Buyer Views Lot Details (Priority: P1)

A prospective buyer visits https://husumgreens.github.io to learn about Lot 21. They want to quickly understand the property, see visuals, and decide if it warrants further inquiry.

**Why this priority**: This is the primary purpose of the site — a buyer landing on the page must immediately understand the property's key selling points.

**Independent Test**: Open the site on desktop and mobile. Verify all sections load, images display, and content is readable without scrolling on a wide viewport.

**Acceptance Scenarios**:

1. **Given** a visitor opens the site on a desktop browser, **When** the page loads, **Then** they see the hero section with "Husum Greens / Lot 21 / Your Dream Home, Perfectly Placed." and the aerial lot rendering prominently displayed.
2. **Given** a visitor scrolls down, **When** they reach each section, **Then** the Home Highlights, architect plans callout, and contact information are all visible and legible.
3. **Given** a visitor is on a mobile device, **When** the page loads, **Then** all content reflows to a single-column layout with no horizontal scrolling and readable font sizes.

---

### User Story 2 – Interested Buyer Contacts the Seller (Priority: P2)

A buyer who is ready to inquire taps/clicks the phone number or email to initiate contact.

**Why this priority**: Converting interest into contact is the site's only CTA.

**Independent Test**: On mobile, tap the phone number — it should open the phone dialer. Tap the email — it should open the default mail client. On desktop, clicking email opens mail client.

**Acceptance Scenarios**:

1. **Given** a visitor views the contact section, **When** they tap/click the phone number `(360) 525-7688`, **Then** their device initiates a phone call or opens the dialer.
2. **Given** a visitor views the contact section, **When** they tap/click `seth.macpherson@gmail.com`, **Then** their mail client opens with that address pre-filled.

---

### User Story 3 – Visitor Understands the Lot's Orientation and Features (Priority: P3)

A visitor wants to understand the lot's physical characteristics — size, slope, north orientation toward Mt. Adams — from the visual and descriptive content.

**Why this priority**: Buyers need to visualize the lot before making contact; the aerial rendering + compass indicator are key to this.

**Independent Test**: Check that the aerial lot image displays with the white boundary outline visible, the "Due North to Mt. Adams" compass indicator is present, and the lot size (.37 acres) is displayed.

**Acceptance Scenarios**:

1. **Given** a visitor views the hero/lot section, **When** the image loads, **Then** the aerial rendering shows the lot boundary and "Due North to Mt. Adams" compass indicator.
2. **Given** a visitor reads the lot details, **When** they scan the key stats, **Then** they can clearly see lot size (.37 acres) and the Mt. Adams view orientation.

---

### Edge Cases

- What happens when images fail to load? Alt text should be descriptive so the content remains meaningful.
- What happens on very narrow viewports (320px)? Text must not overflow or clip.
- What happens when a visitor has JavaScript disabled? The site must be fully functional as a static HTML page with no JS dependency.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: Site MUST display all content from the print flyer (minus the QR code) in a single scrollable page.
- **FR-002**: Site MUST be fully responsive, adapting layout from mobile (≥320px) through desktop (≥1280px) with no horizontal overflow.
- **FR-003**: Site MUST render the aerial lot rendering image with the white lot boundary outline and "Due North to Mt. Adams" compass indicator visible.
- **FR-004**: Site MUST display the lot size (.37 acres) and Mt. Adams view orientation as labeled on the image or in nearby text.
- **FR-005**: Site MUST display the "Also Available: Fully Engineered Plans by Portland Architect Alan Mascord" callout box with the description about permit-ready plans.
- **FR-006**: Site MUST display all five Home Highlights with corresponding icons: (1) Front of home oriented due north to capture Mt. Adams views, (2) Sloped lot ideal for daylight basement and multi-level living, (3) Expansive windows bring in natural light and scenery, (4) Covered outdoor living spaces for year-round enjoyment, (5) Modern curb appeal with stone, wood, and clean architectural lines.
- **FR-007**: Site MUST display the "Selling Our Lot – Husum Greens Lot 21 / Bring your vision to life in this exceptional location." callout.
- **FR-008**: Site MUST display a contact section with a tappable phone number `(360) 525-7688` (tel: link) and tappable email `seth.macpherson@gmail.com` (mailto: link).
- **FR-009**: Site MUST NOT include a QR code.
- **FR-010**: Site MUST display a footer strip with "PREMIUM LOCATION • BREATHTAKING VIEWS • ENDLESS POSSIBILITIES".
- **FR-011**: Site MUST use the dark forest green and cream color palette consistent with the print flyer.
- **FR-012**: Site MUST use the pine tree motif consistent with the print flyer branding.
- **FR-013**: Site MUST be deployable as a static GitHub Pages site at https://husumgreens.github.io with no server-side dependencies.
- **FR-014**: Site MUST display a house rendering image (from the flyer) alongside or below the lot description.
- **FR-015**: Address "21 Ace Way, White Salmon, WA" MUST appear on the page.
- **FR-016**: Asking price "$199,000 — no additional fees" MUST be prominently displayed.
- **FR-017**: Site MUST highlight that the lot has existing power, water, and irrigation infrastructure (former golf course).
- **FR-018**: A "How to Buy" or FSBO guide section MUST be included, summarizing the purchase process for buyers.

### Key Entities

- **Lot**: Lot 21, Husum Greens development, 15 Ace Way, White Salmon, WA. Size: .37 acres. Orientation: north toward Mt. Adams.
- **Images**: Aerial lot rendering (with white boundary outline), house rendering photo.
- **Seller Contact**: Phone (360) 525-7688, Email seth.macpherson@gmail.com.
- **Architect Plans**: Optional permit-ready plans by Portland Architect Alan Mascord.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: The full page content is visible and readable on a 375px-wide mobile viewport without horizontal scrolling.
- **SC-002**: Tapping the phone number on a mobile device opens the dialer within one tap.
- **SC-003**: Tapping the email address opens the mail client with the address pre-filled within one tap.
- **SC-004**: All five Home Highlights are visible on a single page without requiring the user to interact beyond scrolling.
- **SC-005**: The site loads and displays correctly with JavaScript disabled (pure HTML/CSS, no JS required).
- **SC-006**: The site deploys successfully to GitHub Pages and is accessible at https://husumgreens.github.io.
- **SC-007**: Page load time is under 3 seconds on a standard broadband connection (images optimized for web).

## Assumptions

- Images (aerial lot rendering, house photo) will be extracted from the print PDF and provided as web-optimized assets (JPEG/PNG/WebP).
- Asking price: $199,000, no additional fees.
- Address is 21 Ace Way, White Salmon, WA (not 15 Ace Way).
- Lot has existing power, water, and irrigation infrastructure (former golf course — infrastructure already plumbed).
- No inquiry form is needed — contact is via phone/email only.
- The site is a single HTML file with linked CSS; no JavaScript framework required.
- GitHub Pages will serve the site from the root of the `husumgreens` GitHub organization's repository named `husumgreens.github.io`.
- The site does not require analytics tracking, though a placeholder for future addition is acceptable.
- SEO meta tags (title, description, Open Graph) should be included for basic shareability.
- A FSBO buyer guide section will be included on the site, covering the Klickitat County purchase process.
- Visual quality (design fidelity to the flyer) is the first priority; performance optimization is a follow-on phase.
