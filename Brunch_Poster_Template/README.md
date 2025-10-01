# Brunch Poster Template

Pixel‑perfect static promotional brunch poster (1080×1350) with a layered image stack and classic serif/sans typography.

## Quick Start
Open `brunch-poster.html` in a modern browser. A tiny script auto‑scales the fixed poster to fit the viewport (it never scales above 100%).

## Features
- **Fixed Design Fidelity** – 1080×1350 base canvas, proportionally scaled down
- **Layered Image Stack** – 5 offset overlays for subtle depth
- **Typography** – Playfair Display (headline), Lora (sub-head), Inter (support)
- **Exact Palette** – Coral Red `#FF5742`, Warm Beige `#E8E0D5`
- **Print Ready** – Use your browser print dialog (shadows/animations stripped via `@media print`)
- **Reduced Motion Friendly** – Animations disabled if the user prefers reduced motion

## Customization
- **Image:** Replace `mimosa-image.jpg` with another file (keep the same name or update the CSS `background-image` in `.image-overlay`)
- **Colors:** Edit the `:root` color variables in `brunch-poster.css`
- **Text Content:** Edit headings, address, tagline, and times directly in the HTML
- **Logo/Icon:** Swap or remove the inline SVGs in the footer
- **Scaling (Optional):** Remove the inline `<script>` if you prefer natural scrolling on small screens

## Files
- `brunch-poster.html` – Markup + scaling script
- `brunch-poster.css` – Layout, layering, palette, print styles
- `brunch-poster-design-spec.md` – Original detailed design spec (reference)

## Notes
Only the front visible image layer is exposed for accessibility; the additional overlaid layers are decorative and hidden from assistive tech.

## Future Enhancements (Optional)
- Toggle: Fit / Actual Size
- Export: Generate PNG/PDF from poster
- Theme variants (dark / seasonal color palette)
