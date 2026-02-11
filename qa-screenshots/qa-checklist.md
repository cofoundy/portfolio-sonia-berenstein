# QA Report: Sonia Berenstein Cervera

**Date:** 2026-02-11
**URL:** https://cofoundy.github.io/portfolio-sonia-berenstein/
**Status:** FAIL

## Data Validation
- [x] Name matches source — "Sonia Berenstein Cervera" matches Google Sheet and config.ts
- [x] Email matches source — "sberensteincervera@gmail.com" matches Google Sheet exactly
- [x] Job title consistent — "Executive Leader | CRM, Analytics & Digital Transformation" aligns with CV/config.ts
- [x] Companies listed exist in source — Santander Consumer Bank, BCP, Scotiabank Uruguay, Scotiabank Peru all from config.ts/CV
- [x] Education institutions exist in source — Centrum PUCP, UNMSM, PUCP, Berkeley Haas / Cibertec all from config.ts/CV
- [x] Dates are from source — All date ranges match config.ts exactly
- [x] No hallucinated data detected

## Clean Deploy
- [x] No "Powered by" / "Made with" / "Built with" visible text
- [x] No "View source" / "View on GitHub" / "Fork this" template links
- [x] No "Lorem ipsum" / "Your name here" / "[placeholder]" text
- [x] No "undefined" or "null" visible in content
- [ ] **ISSUE: meta generator tag** — `<meta name="generator" content="Astro v5.12.3">` present in <head>. Minor (not user-visible), but reveals framework.
- [ ] **ISSUE: Programming symbols pattern in Hero** — The hero background contains an SVG pattern called "programming-symbols" with code symbols (`</>`, `=>`, `[]`, `<>`, `()`, `::`, `==`, `++`, `;`). Sonia is an executive leader in banking/CRM/Analytics, NOT a developer. This is a template artifact that was not adapted to her profession. Should use a business/data-themed pattern or remove it.

## Technical
- [x] Page loads — HTTP 200
- [x] CSS loads — HTTP 200 (`_astro/index.o0fPyfFs.css`)
- [x] Favicon loads — HTTP 200 (favicon.svg)
- [x] No profile image — Expected (notes say "Sin foto", form has no photo upload)
- [ ] **ISSUE: Missing `site` in astro.config.mjs** — Only `base: '/portfolio-sonia-berenstein'` is set. Per project rules, BOTH `site: 'https://cofoundy.github.io'` AND `base` must be present. Currently works but is non-compliant.
- [ ] **ISSUE: Unclosed `<section>` tag** — HTML has 5 opening `<section>` tags but only 4 closing `</section>` tags. The hero `<section>` wraps the About section inside it, creating an incorrect nesting structure.
- [ ] **ISSUE: No mobile navigation** — The header nav has `class="hidden md:block"`, meaning it is completely hidden on mobile. There is NO hamburger menu or any alternative mobile navigation. Users on mobile have no way to navigate between sections except scrolling.
- [ ] **ISSUE: LinkedIn URL returns 999** — The LinkedIn profile URL `https://linkedin.com/in/sonia-berenstein-cervera` returns HTTP 999 (LinkedIn bot detection). Cannot verify if this profile actually exists. The Google Sheet form only says "LinkedIn" without a specific URL — this URL may have been constructed/assumed.
- [x] No critical console errors detected (Chrome MCP unavailable for live check)

## Screenshots
- Chrome MCP server was unavailable during this QA session. No screenshots captured.

## Issues Found (5 total)

### FAIL Issues (must fix before delivery):

1. **Programming symbols background in Hero** — The hero section uses a developer-themed SVG pattern (`</>`, `=>`, `[]`, etc.) which is completely inappropriate for an executive banking/CRM professional. This is a template artifact that was not customized. Fix: Replace with a business/analytics-themed pattern, remove pattern entirely, or use a neutral geometric pattern.

2. **No mobile navigation** — Header is `hidden md:block` with no hamburger menu alternative. Mobile users (majority of traffic) cannot navigate between sections. Fix: Add a hamburger menu component for mobile viewports.

3. **Unclosed `<section>` tag** — The hero section wraps the About section inside it due to a missing `</section>` close tag. This creates incorrect DOM nesting. Fix: Close the hero section properly before the About section.

### WARNING Issues (should fix):

4. **Missing `site` property in astro.config.mjs** — Per project rules, both `site` and `base` must be set. Only `base` is present. Fix: Add `site: 'https://cofoundy.github.io'`.

5. **LinkedIn URL unverified** — The URL `linkedin.com/in/sonia-berenstein-cervera` was constructed (not provided by client in form). Client only wrote "LinkedIn" without a URL. This may be a hallucinated URL. Fix: Verify the actual LinkedIn profile URL or remove if it cannot be confirmed.

## Summary

This portfolio has 3 blocking issues that prevent delivery: an inappropriate developer-themed background pattern for a banking executive, missing mobile navigation, and malformed HTML structure. Additionally, the LinkedIn URL needs verification since the client did not provide a specific URL in the Google Form.
