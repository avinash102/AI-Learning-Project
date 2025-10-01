# Slow Coffee Brunch Poster – Design & Implementation Spec (Revised)

Updated to reflect the current lightweight HTML/CSS implementation. Original aspirational ideas moved to Future Enhancements.

---

## 1. LAYOUT & CANVAS

### Canvas
- Base size: 1080 × 1350 px (4:5 social ratio)
- Strategy: Fixed-dimension poster scaled down (never upscaled) via a small JS transform wrapper
- Margins / internal padding: ~50–60px edge spacing
- Grid: No explicit CSS Grid in code (simple flow + absolute positioning where needed)

### Visual Order (Implemented)
1. Header micro text (address / tagline)
2. Primary headline “Brunch”
3. Sub-head “Is Here to Stay”
4. Layered image stack (mimosa photo)
5. Time & Day block
6. Footer (logo and circular icon)

---

## 2. COLOR PALETTE (Current)

| Role | Hex | Notes |
|------|-----|-------|
| Primary Coral | `#FF5742` | All text, accents, icon stroke |
| Warm Beige | `#E8E0D5` | Background canvas |
| White | `#FFFFFF` | Image highlight / neutral |
| Accent Yellow | `#FFB84D` | From photo (not forced) |
| Accent Sky | `#A8D8E8` | From photo (reference) |
| Accent Brown | `#C89B6D` | From photo (reference) |

Palette exists as CSS custom properties in `:root`.

---

## 3. TYPOGRAPHY (Implemented)

| Element | Family | Weight | Size px | Letter-spacing | Line-height |
|---------|--------|--------|--------|----------------|-------------|
| Address / Tagline | Inter | 500 | 14 | 0.02em | 1.4 |
| H1 “Brunch” | Playfair Display | 400 | 160 | -0.01em | 0.9 |
| H2 Sub-head | Lora | 300 | 106 | -0.005em | 1.1 |
| H3 Time | Playfair Display | 700 | 186 | -0.02em | 0.9 |
| H4 Day | Lora | 400 | 120 | 0 | 1.2 |
| Logo wordmark (SVG) | Inter | 500 | 14 | 0 | 1 |

Original spec (GT Super / Canela) replaced by open-source equivalents for simplicity & licensing.

---

## 4. IMAGE TREATMENT (Current)

Technique: Five absolutely positioned layers using the same `background-image` with horizontal offsets (-40, -20, 0, +20, +40 px) and subtle rotations (-2°, -1°, 0°, +1°, +2°).

Simplifications:
- Opacity staggering and gradient shimmer removed.
- Uniform vivid rendering; could reintroduce 100/85/70/85/100 opacity pattern later.
- Soft shadowing retained for depth.

Recommended source: High‑resolution JPEG ≥ 1600px width named `mimosa-image.jpg`.

---

## 5. DESIGN ELEMENTS

### Logo (Bottom Left)
SVG wordmark (approx 80×30) in coral; padding ~50px left / 60px bottom.

### Circular Icon (Bottom Right)
60px diameter outline circle + bean motif (stroke 2px coral) with similar padding.

### Dividers
None (intentional minimalism).

---

## 6. SPACING & ALIGNMENT (Practical Values)

| Area | Approx Value |
|------|--------------|
| Header top | 60px |
| Headline block margin-top | ~80px |
| Image stack top margin | ~150px |
| Time/Day section bottom offset | ~85px |
| Footer bottom padding | 60px |
| Side padding (general) | 50px |

Image cluster centered horizontally; text left-aligned relative to left padding.

---

## 7. WEB IMPLEMENTATION (Current)

### Structural Skeleton
```html
<div class="poster-container">
  <header class="poster-header">…</header>
  <section class="headline-section">…</section>
  <section class="image-container">…</section>
  <section class="info-section">…</section>
  <footer class="poster-footer">…</footer>
</div>
```

### Techniques Used
- Flexbox for header/footer distribution
- Absolute positioning for layered images
- CSS custom properties for palette
- Google Fonts for Inter / Playfair Display / Lora
- Tiny inline JS to scale container to viewport (maintains aspect ratio)

### Responsive Strategy
No breakpoint reflow; entire poster uniformly scales down to fit available viewport (maintains design fidelity).

---

## 8. TECHNICAL SPECS (Adjusted)

| Context | Current Approach |
|---------|------------------|
| Print | Browser print to PDF (poster scales to 100% if viewport large enough) |
| Social Export | Screenshot / print-to-file at native 1080×1350 |
| Web Delivery | Single HTML + CSS + inline JS |

Accessibility Notes:
- Only one descriptive container needed; additional image layers are decorative (use `aria-hidden="true"`).
- Color contrast acceptable for display poster; can darken coral or add outline for strict WCAG.

---

## 9. BRAND CONSISTENCY

Maintain: Coral accent, warm neutral backdrop, refined serif headlines, clean spacing, lifestyle beverage imagery.

Variable: Photography, seasonal copy, schedule text.

---

## 10. IMPLEMENTATION STACK

| Layer | Status |
|-------|--------|
| Framework | None (plain HTML/CSS/JS) |
| Build Tools | None |
| Animations | Removed (future optional) |
| Fonts | Google-hosted Inter / Playfair Display / Lora |

Photo Guidance (optional): Natural light, subject-centered mimosas, airy negative space for layering.

---

## 11. CSS CUSTOM PROPERTIES (Updated Names)

```css
:root {
  --color-coral: #FF5742;
  --color-beige: #E8E0D5;
  --color-white: #FFFFFF;
  --color-yellow: #FFB84D;
  --color-blue: #A8D8E8;
  --color-brown: #C89B6D;

  --font-serif-display: 'Playfair Display', Georgia, serif;
  --font-serif-body: 'Lora', Georgia, serif;
  --font-sans: 'Inter', 'Helvetica Neue', Arial, sans-serif;

  --margin-horizontal: 50px;
  --margin-vertical: 60px;
  --grid-gutter: 20px; /* Placeholder if grid introduced later */

  --poster-width: 1080px;
  --poster-height: 1350px;
}
```

---

## 12. FUTURE ENHANCEMENTS

- Reintroduce subtle entrance animations (fade/slide) w/ reduced-motion fallback
- Layer opacity variation (100 / 85 / 70 / 85 / 100)
- Optional gradient / shimmer highlight overlay
- Export button (PNG/PDF via canvas or print pipeline)
- Seasonal theming (autumn, holiday, spring palettes)
- True responsive reflow (alternate layout at narrow widths) instead of uniform scale
- React/Vue component abstraction if reused in broader site

---

This revised spec documents what is shipped today and clearly separates aspirational ideas for incremental improvement.
