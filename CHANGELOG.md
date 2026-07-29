# PAG Alliance Website — Changelog

This changelog records the evolution of the PAG Alliance static website, tracing updates from the initial single-page baseline to the multi-page, design-system-aligned vanilla implementation.

---

## [1.2.0] - 2026-07-29
### Added
- **Dedicated Contact Page**: Created [contact.html](contact.html) to act as a standalone, lightweight contact flow for researcher and partner inquiries.
  - Custom WhatsApp templates and mailto subject generation tailored dynamically based on URL search parameters (e.g. `?type=researcher` or `?type=partner`).
  - Interactive "Copy to Clipboard" buttons with transient copy state feedback (*"Tersalin!"* / *"Copied!"*).
  - Clean language bar (ID/EN) mirroring the homepage language toggle with auto-detection rules.

### Removed
- **Redundant Footer Domain Link**: Removed the redundant domain link `pagalliance.org` under the Kontak (Contact) section in the footer across all 9 HTML pages (`index.html`, `contact.html`, `support.html`, and the 6 research cluster pages), as it is not a direct contact channel like a phone number or email address.
- **Auto-Detection Label**: Removed the redundant "Detected: ... / Terdeteksi: ..." text label (`#lang-msg`) next to the language switcher across all four HTML pages ([index.html](index.html), [support.html](support.html), [contact.html](contact.html), [cluster-1-afrl.html](cluster-1-afrl.html)) for a cleaner, more streamlined header design.

### Changed
- **Expanded University Names**: Replaced all instances of shortened university acronyms (such as `UB`, `Unhas`, `Unram`, and `Univ. Brawijaya`) with their full proper names (`Universitas Brawijaya`, `Universitas Mataram`, `Universitas Hasanuddin`) across `index.html` and the six cluster detail pages.
- **Bilingual University Names in Clusters**: Integrated the homepage cluster card university names into the `data-i18n` bilingual system, translating them dynamically (e.g., "Universitas Hasanuddin" to "Hasanuddin University").
- **Restructured Cluster Page Coordinator Block**: Modified the cluster detail pages to pull the university name out of the coordinator's name parentheses and display it on a separate line below their name, complete with a new `.coord-univ` CSS class and bilingual translation support.
- **Footer Standardization**: Aligned the footers of `support.html`, `contact.html`, and all six research cluster pages (`cluster-1-afrl.html`, `cluster-2-cdr.html`, `cluster-3-growth.html`, `cluster-4-hegsi.html`, `cluster-5-diais.html`, `cluster-6-gprt.html`) to match the structural layout, social icons, and translation patterns of `index.html`.
  - Added the missing `footer-socials` container (with LinkedIn and WhatsApp links) to all six cluster pages.
  - Refactored the `footer-bottom` copyright containers to isolate and translate only the copyright status suffix (`footer_copy`), avoiding duplicate copyright/brand text.
  - Standardized navigation paths and internal hashes across footers.
  - Unified the `footer_copy` translation strings in the JavaScript registries to use `"Semua hak dilindungi"` (Sentence Case) and `"All rights reserved"`.
  - Cleaned up the registries by removing the obsolete `support_footer_credit` key.
- **Support Page Translations**: Identified and resolved untranslated UI text in [support.html](support.html). Added missing `data-i18n` attributes and updated the corresponding Indonesian and English translation dictionaries (`T` registry) for all UI components including the bank transfer section and footer elements.
- **Unified CTA Button Routing**: Updated registration and contact buttons in [index.html](index.html) (Hero, Card 1, and Card 2) to redirect to [contact.html](contact.html) rather than triggering the modal popup.
- **Get Involved Card Alignment**: Unified the design of the three cards under the Portfolio section (`#contact` in [index.html](index.html)):
  - Removed the `featured` style variance from Card 1.
  - Replaced outline style buttons (`cta-btn-outline`) with solid Navy-900 buttons transitioning to Copper on hover.
  - Implemented card-lift hover animations, smooth transition states, and color-inverting icons on hover.
- **Vanilla CSS Porting**: Refactored [support.html](support.html) and [cluster-1-afrl.html](cluster-1-afrl.html):
  - Completely removed the client-side Tailwind CSS v4 CDN script to optimize load speed and eliminate Flash of Unstyled Content (FOUC).
  - Converted Tailwind utility class selectors into semantic, responsive Vanilla CSS rules within the inline `<style>` block.
  - Standardized font family styling to reference `'Manrope'` (Sans) and `'Fraunces'` (Serif) via design system variables.

---

## [1.1.0] - 2026-07-07
### Added
- **Bilingual Support (ID/EN)**: Implemented the dynamic client-side translation framework using `data-i18n` tags, backed by the `translations` registry in JavaScript.
  - Integrated browser-locale and timezone-based auto-detection (triggering Indonesian layout if Jakarta, Makassar, Jayapura, or Pontianak timezones are present).
- **Interactive Mapping**: Embedded Leaflet.js v1.9.4 to render a customized research coverage map containing active pins across NTB, Banda Aceh, and Kotabaru.
  - Configured custom interactive popup boxes utilizing design-system-aligned colors.
- **Scroll-Triggered Counters**: Added numeric counting animation framework that triggers dynamically via an `IntersectionObserver` when statistics enter the viewport.
- **Core Design Tokens**: Established CSS variables for the color palette (`--navy-900`, `--navy-800`, `--copper`, `--gold`, etc.), font sets, spacing tokens, and `.dot-grid` background styling.
