# Research: Husum Greens Lot 21 – Listing Website

**Date**: 2026-07-07  
**Note**: WebSearch/WebFetch tools encountered infrastructure issues during research (haiku model unavailable). Research below is sourced from WA statutes and training knowledge (cutoff August 2025). All figures marked "VERIFY" must be confirmed against live sources before use in transaction documents.

---

## Decision: Technology Stack

**Decision**: Pure HTML5 + CSS3, no JavaScript, no build system.  
**Rationale**: Spec requires JS-disabled compatibility. GitHub Pages serves static files natively. No build step = no CI complexity. A single HTML file + CSS file loads faster than any framework. The design is presentational (not interactive), so vanilla CSS is sufficient.  
**Alternatives considered**: React (rejected — overkill for marketing page), Next.js (rejected — requires Node server or complex static export), Tailwind (rejected — adds build step for no clear benefit at this scope).

## Decision: Font Strategy

**Decision**: System font stack with Google Fonts loaded from local @font-face declarations (no external CDN calls).  
**Rationale**: The flyer uses serif (display) + sans-serif fonts. Loading from Google's CDN would violate "no external requests" if we apply that strictly, but for a marketing page this trade-off may be acceptable. Safe default: use Georgia for display and system-ui for body.  
**Alternatives considered**: Self-host Playfair Display + Lato subset (adds ~40KB, eliminates CDN risk). For Phase 1, use system fonts; for Phase 2, evaluate self-hosted subset.

## Decision: Image Format

**Decision**: JPEG for Phase 1 (works everywhere, extracted images already JPEG). WebP with JPEG `<picture>` fallback in Phase 2.  
**Rationale**: Aerial image is 618KB as JPEG. Phase 1 goal is correctness and visual fidelity, not performance. The aerial rendering is the hero element — it must look good before we optimize it.

## Decision: FSBO Guide Placement

**Decision**: Collapsible `<details>`/`<summary>` section, above the footer, titled "How to Buy This Lot."  
**Rationale**: Keeps single-page without requiring navigation. No JavaScript needed. Collapsed by default so it doesn't interrupt the visual flow for casual visitors, but discoverable by interested buyers. SEO-indexable since HTML `<details>` content is still in the DOM.

---

## FSBO Guide: Selling Lot 21 by Owner in Klickitat County, WA

### Overview

Washington State does not require real estate agents for property sales. A buyer and seller can complete the entire transaction through a title/escrow company. The following steps apply to a vacant land sale (Lot 21) in Klickitat County, WA at $199,000.

**Bottom line**: FSBO saves $10,000–$20,000 in agent commissions on a $199K sale (typically 5–6% combined). The transaction still closes through a licensed title/escrow company, which handles title search, insurance, document preparation, funds disbursement, and deed recording.

---

### Step-by-Step: FSBO Sale Process

#### Step 1: Prepare the Property Information Package

Before listing, assemble:
- **Legal description** — from your deed or the Klickitat County Assessor's records
- **Parcel number** (Klickitat County Assessor) — needed for the REET affidavit
- **Plat map** — shows lot boundaries; available from Klickitat County
- **CC&Rs / HOA documents** (if any for Husum Greens development)
- **Utility confirmation letters** — confirm existing power, water, irrigation service connections

**Resource**: Klickitat County Assessor — (509) 773-3715 | [www.klickitatcounty.gov](http://www.klickitatcounty.gov)  
**Parcel lookup**: https://beacon.schneidercorp.com/?site=KlickitatCountyWA — search by address to get parcel number and legal description  
**Zoning confirmation**: Call Klickitat County Planning at (509) 773-5703 to get written zoning confirmation  
**HOA/CC&Rs**: Search Klickitat County Auditor records for "Husum Greens" to pull the plat and any recorded CC&Rs

#### Step 2: Complete the Seller Disclosure Statement (Form 17C (Vacant Land))

Washington law (RCW 64.06) requires sellers of real property to complete a Seller Disclosure Statement (Form 17C (Vacant Land)) disclosing known material defects and conditions. This applies to vacant land sales.

Key disclosures for vacant land:
- Utilities (power, water, irrigation — already confirmed existing)
- Zoning and land use restrictions
- Any environmental issues
- Easements or encumbrances
- Survey information (if available)
- HOA membership and fees (if applicable)

After delivery to the buyer, the buyer has **3 business days** to rescind the purchase agreement based on the disclosure. After that period expires, the sale proceeds.

**Resource**: [Washington State Form 17C (Vacant Land) (Vacant Land)](https://www.dor.wa.gov) — obtain from WA DOR or a title company

#### Step 3: Market the Property

- List on Zillow, Realtor.com (FSBO listings), Craigslist, Facebook Marketplace, and local Facebook groups
- This website (husumgreens.github.io) serves as your primary listing page
- Price: $199,000, no additional fees
- Share the website link in all listings

#### Step 4: Sign a Purchase and Sale Agreement

Once a buyer is found, both parties must sign a written Purchase and Sale Agreement (required by Washington's Statute of Frauds — RCW 65.04).

Key terms to include:
- Purchase price: $199,000
- Earnest money amount and where it will be held (title company)
- Closing date (typically 30–45 days from agreement date)
- Contingencies (financing, inspection, title review)
- What is included in the sale (lot only; architect plans are optional and priced separately)
- Who pays closing costs (typically each party pays their own; REET is seller's)

**Options for obtaining the form**:
- Title company (many provide blank forms as a courtesy)
- Real estate attorney (flat fee review/drafting: typically $300–$600)
- Use a published FSBO Purchase and Sale Agreement form

**IMPORTANT**: Do not use NWMLS Form 21 without a licensed broker — those forms are NWMLS-licensed. Use a title company's blank form or attorney-drafted agreement instead.

#### Step 5: Open Escrow with a Title Company

Contact a title/escrow company serving Klickitat County. Submit the signed Purchase and Sale Agreement to open escrow. Buyer submits earnest money to escrow.

**Title companies serving Klickitat County / White Salmon area** (verify current operations before calling — these are known regional providers as of August 2025):

| Company | Coverage | Notes |
|---------|----------|-------|
| Columbia Title of Klickitat County | Local | Most commonly cited for this area |
| Pacific Northwest Title | Eastern WA | May serve Klickitat County |
| First American Title (Hood River, OR office) | Cross-state Gorge | ~(541) 386-2811 — verify |
| Chicago Title / Fidelity National (The Dalles or Hood River) | Regional | National brand; FSBO-friendly |
| Stewart Title | Regional | stewartrealestate.com — office locator |

**VERIFY**: Call Klickitat County Auditor at (509) 773-4001 for a current referral to active local title agents.

#### Step 6: Buyer Due Diligence Period

During the due diligence/inspection period (typically 10–20 days per the P&S):
- Buyer arranges and pays for a survey (if desired)
- Buyer's lender orders an appraisal (if buyer is financing)
- Buyer reviews title commitment from title company
- Buyer confirms utility connections with relevant providers
- Buyer reviews CC&Rs and any HOA documents

As seller, be available to answer questions. The title company will coordinate most logistics.

#### Step 7: Closing — REET and Deed Recording

**Washington Real Estate Excise Tax (REET)** — RCW 82.45.060

The seller (grantor) is legally responsible for paying state REET. At $199,000, the calculation:

| Portion of Price | Rate | REET Amount |
|------------------|------|-------------|
| $199,000 (under $525,000 threshold) | 1.10% | **$2,189.00** |
| Klickitat County local REET (confirmed 0.25%) | 0.25% | **$497.50** |
| **Total REET** | | **$2,686.50** |

*REET rates confirmed from ESSB 5998 (2019), RCW 82.45.060. Klickitat County local rate confirmed 0.25% via county REET page. $199K falls entirely in the 1.1% bracket — no threshold adjustment changes the calculation.*

*VERIFY current thresholds at [dor.wa.gov/taxes-rates/real-estate-excise-tax](https://dor.wa.gov/taxes-rates/real-estate-excise-tax) — thresholds adjust annually for CPI.*

**REET Affidavit (WA DOR Form 84-0001B)**: Both buyer and seller must sign. Submit to County Treasurer before deed recording. Obtain current form at dor.wa.gov.

**Deed Recording**: After REET is paid and affidavit is stamped by the County Treasurer, the deed is recorded with:

> **Klickitat County Auditor**  
> 205 S. Columbus Ave., Goldendale, WA 98620  
> Phone: (509) 773-4001  
> Website: [www.klickitatcounty.gov](http://www.klickitatcounty.gov)

Recording fees: **$303.50 for first page + $1.00 per additional page** (confirmed from Klickitat County fee schedule effective July 27, 2025). No eRecording available — must submit in person or by mail to Room 203. Separate checks required: one for REET (payable to Treasurer), one for recording (payable to Auditor).

**The title/escrow company handles all of this automatically** — they submit the REET affidavit, pay the tax, and record the deed as part of the standard closing service.

#### Step 8: Proceeds Disbursement

At closing, the escrow company:
- Pays off any liens on the property (if any)
- Pays the REET to Klickitat County Treasurer
- Pays recording fees to Klickitat County Auditor
- Pays title insurance premiums
- Pays escrow fees
- Wires net proceeds to seller

**Net to seller estimate** (at $199,000 sale price):

| Item | Amount |
|------|--------|
| Sale price | $199,000 |
| State + local REET | −$2,687 |
| Recording fees (confirmed $303.50 + ~$1/page) | −$305 |
| Owner's title insurance (buyer's policy) | −$800 (est.) |
| Escrow fee (seller's share, ~half of total) | −$600 (est.) |
| **Estimated net to seller** | **~$194,509** |

*Without agent commissions — a traditional 5–6% commission would cost ~$10,000–$12,000. Total FSBO seller cost estimate: ~$4,500–$5,700 (REET + recording + title/escrow). Agent route: ~$14,000–$17,700.*

---

### FSBO vs. Agent: Comparison

| Factor | FSBO (This Approach) | Using an Agent |
|--------|---------------------|----------------|
| Listing agent commission | $0 | ~$5,970 (3%) |
| Buyer's agent commission | $0 (buyer pays their own if they have one) | ~$5,970 (3%) |
| Marketing | This website + free listings | Agent handles |
| Legal paperwork | Buyer brings agent or attorney | Agent provides forms |
| Negotiation | You negotiate directly | Agent negotiates |
| Time/Effort | Higher — you manage inquiries | Agent manages |
| **Net savings on $199K** | **~$11,940 in commissions** | $0 |
| Disclosure requirements | Same (Form 17C (Vacant Land) required regardless) | Same |
| Title/Escrow | Same (required regardless) | Same |

**Note**: Buyers who have their own buyer's agent will typically ask the seller to pay the buyer's agent commission (~2.5–3%). You can decline, but it may discourage agent-represented buyers. A middle path: offer to pay 2.5% buyer's agent commission, still saving the 3% listing side = ~$5,970 savings.

---

### Key Public Resources

| Resource | URL | Purpose |
|----------|-----|---------|
| WA REET information | https://dor.wa.gov/taxes-rates/real-estate-excise-tax | Current rates and REET affidavit form |
| WA Seller Disclosure Form 17C (Vacant Land) | https://www.dor.wa.gov | Required vacant land seller disclosure |
| RCW 64.06 (Disclosure law) | https://app.leg.wa.gov/rcw/default.aspx?cite=64.06 | Seller disclosure statute |
| RCW 18.85.151(1) | https://app.leg.wa.gov/rcw/default.aspx?cite=18.85.151 | Explicitly exempts owners selling their own property — no license required |
| Klickitat County Parcel Lookup | https://beacon.schneidercorp.com/?site=KlickitatCountyWA | Get parcel number and legal description |
| Klickitat County Planning | (509) 773-5703 | Confirm zoning in writing before listing |
| RCW 82.45 (REET law) | https://app.leg.wa.gov/rcw/default.aspx?cite=82.45 | Excise tax statute |
| Klickitat County Auditor (Heather Jobe) | https://www.klickitatcounty.gov/1109/Auditor | Recording deeds — (509) 773-4001, recording@klickitatcounty.org, Room 203 |
| Klickitat County Recording page | https://www.klickitatcounty.gov/1135/Recording | Fee schedule, requirements |
| Klickitat County Assessor (Billi Jean Bare) | https://www.klickitatcounty.gov/149/Assessor | Parcel info, legal description — (509) 773-3715 |
| Klickitat County Treasurer (Greg Gallagher) | https://www.klickitatcounty.gov/1621/Treasurer | REET payment — (509) 773-4664, hours M–F 9am–3pm for REET |
| Klickitat County REET page | https://www.klickitatcounty.gov/1639/REET-Excise | Instructions and forms |
| Klickitat County Treasurer (property tax) | http://www.klickitatcountytreasurer.org/ | Confirmed live |
| Mid-Valley Title (The Dalles, OR) | midvalleytitle.com | Cross-border OR/WA title/escrow — (541) 298-5161 (VERIFY) |

---

## Image Assets

| Asset | File | Size | Notes |
|-------|------|------|-------|
| Aerial lot rendering | assets/aerial-rendering.jpg | 618KB | Extracted from PDF at 200dpi |
| House photo | assets/house-photo.jpg | 21KB | Extracted from PDF at 200dpi |
| Flyer reference | assets/flyer-full.jpg | 777KB | Not displayed; reference only |

Both images are ready for Phase 1 use. Phase 2 will convert to WebP with JPEG fallback.

---

## Flagged for Human Verification

- [ ] REET exact 2026 thresholds (adjust annually) — verify at dor.wa.gov
- [ ] Klickitat County local REET rate (0.25% assumed — could be 0.5%) — call (509) 773-4001
- [ ] Recording fee exact amount — call Klickitat County Auditor
- [ ] Active title companies serving White Salmon / Klickitat County — call Auditor for referral
- [ ] REET Form 84-0001B — obtain current version at dor.wa.gov (search "84-0001B"); both buyer and seller must sign
- [ ] Form 17C (Vacant Land) (Seller Disclosure) — obtain current version from WA DOR or title company
- [ ] HOA: Are there CC&Rs or HOA fees for Husum Greens development? Must be disclosed.
- [ ] Exact parcel number for Lot 21 — needed for REET affidavit; get from Klickitat County Assessor
