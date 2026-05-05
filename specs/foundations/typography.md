---
name: Typography
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Typography

> Headings should guide users through search and results. Body copy should be legible and support quick scanning of hotel cards, flight details, and booking information.

Almosafer uses **Open Sans** (from Google Fonts) as the primary typeface. All sizes, weights, and line heights in the Type Scale below are the single source of truth.

---

## Type Scale

| Token | Size | Weight | Line Height | Usage |
|-------|------|--------|-------------|-------|
| `display-xl` | 34px | 600 | 120% | Hero titles, page hero |
| `display-lg` | 26px | 600 | 123% | Large section headings |
| `display-md` | 22px | 600 | 127% | Section headings, titles |
| `heading-lg` | 20px | 600 | 130% | Card titles, subsections |
| `heading-md` | 18px | 600 | 133% | Form labels, emphasis |
| `body-lg` | 18px | 600 | 133% | Emphasized body, CTAs, strong emphasis |
| `body-md` | 16px | 400 | 150% | Standard body text |
| `body-sm` | 14px | 400 | 143% | Secondary text, captions |
| `label-md` | 14px | 600 | 143% | Form labels, small emphasis |
| `label-sm` | 12px | 600 | 133% | Badge labels, helper text |
| `caption-md` | 12px | 400 | 133% | Disclaimers, fine print |

> Line heights are written as percentages to match Figma's stored values. CSS-equivalent unitless multipliers: divide by 100 (e.g. `120%` = `1.2`).

---

## Usage Guidelines

### Display Tier
Use for hero sections, page titles, and primary entry points.
- `display-xl` (34px, 600) — Full-page hero ("Book Hotels in Jeddah")
- `display-lg` (26px, 600) — Section headers ("Recommended for You")
- `display-md` (22px, 600) — Sub-section headers

### Heading Tier
Use for card titles, form sections, and grouped content.
- `heading-lg` (20px, 600) — Hotel/flight card titles
- `heading-md` (18px, 600) — Filter group headers, subsection titles

### Body Tier
Use for all readable content and primary information.
- `body-lg` (18px, 600) — Emphasized body, CTAs, primary actions, strong emphasis
- `body-md` (16px, 400) — Standard paragraph text
- `body-sm` (14px, 400) — Secondary info, descriptions, metadata

### Label Tier
Use for form labels, badges, and small UI text.
- `label-md` (14px, 600) — Form field labels, small emphasis
- `label-sm` (12px, 600) — Badge text, inline labels
- `caption-md` (12px, 400) — Disclaimers, fine print, helper text

---

## Dos and Don'ts

### ✓ Do

- **Use semantic tokens.** Pick `heading-lg`, not a size. Tokens evolve; names endure.
- **Pair size with weight intentionally.** Larger sizes = lighter weight (34px @ 600). Smaller sizes = heavier weight (12px @ 600).
- **Maintain hierarchy.** Line height increases with body text. Headings tighter. Captions compact.
- **Test on small screens.** Ensure 16px+ base size for mobile readability.

### ✗ Don't

- **Mix font families.** Stick to Open Sans. No serif exceptions.
- **Use weights outside 400–600.** 300 is too light; 700 is redundant.
- **Hardcode sizes.** Never `font-size: 16px`. Always use tokens.
- **Override line height per use case.** Follow the scale. If it doesn't fit, restructure.
- **Forget WCAG contrast.** All text must be ≥4.5:1 for body, ≥3:1 for headings. Test with tools.
- **Add custom letter spacing.** Open Sans is kerned. Letter spacing only when explicitly needed.

---

## Accessibility

### Readability Standards
- **Minimum font size:** 16px on mobile (prevents auto-zoom on iOS input focus)
- **Line height:** 150% or higher for body text on mobile (easier to track lines)
- **Letter spacing:** Keep Open Sans default kerning—only adjust in rare cases

### Touch Targets
When combining text with interactive elements:
- **Minimum height:** 44px (includes padding)
- **Minimum width:** 44px (buttons, links, selectable text areas)

### Typography Hierarchy for Scanning
Use the type scale to create clear visual hierarchy:
1. **Display tier** — Draw attention to primary content
2. **Heading tier** — Organize sections and groupings
3. **Body tier** — Deliver readable content
4. **Label tier** — Support forms and small UI text

This layering helps users quickly scan and find information.

### Testing
- Test all text at actual sizes on mobile (not desktop previews)
- Verify line length (45–75 characters optimal for body text)
- Check that interactive text meets 44px minimum touch target
- Test zoom: all text should remain readable at 200% zoom

---

## Figma Variables — Two Layers

Typography uses a **two-layer** model. The `Primitives` collection holds atomic primitives (one variable per unique value, no duplication) under the `Typography/` group. The `Aliases` collection holds the semantic tokens (`Display/XL`, `Body/MD`, etc.) which **reference** those primitives.

### Layer 1 — Primitives (`Primitives` collection, 18 variables under `Typography/`)

| Group | Variables | Type | Scope |
|---|---|---|---|
| `Typography/family/` | `Default` (Open Sans) | STRING | `FONT_FAMILY` |
| `Typography/font-weight/` | `Regular`, `SemiBold` | STRING | `FONT_STYLE` |
| `Typography/font-size/` | `12, 14, 16, 18, 20, 22, 26, 34` | FLOAT | `FONT_SIZE` |
| `Typography/line-height/` | `41, 32, 28, 26, 24, 20, 16` (px) | FLOAT | `LINE_HEIGHT` |

Line-heights are stored as **pixel values** computed from `font-size × multiplier`, then rounded to integers. This lets the variable be bound to text-style `lineHeight` with `PIXELS` unit (which Figma supports without breaking bindings). The 11 text styles share 7 unique pixel values. Open Sans uses two style names in Figma: `Regular` and `SemiBold` (one word, no space).

| Variable | Used by | Math |
|---|---|---|
| `line-height/41` | Display/XL | 34 × 1.2 |
| `line-height/32` | Display/LG | 26 × 1.23 |
| `line-height/28` | Display/MD | 22 × 1.27 |
| `line-height/26` | Heading/LG | 20 × 1.3 |
| `line-height/24` | Heading/MD, Body/LG, Body/MD | 18 × 1.33, 18 × 1.33, 16 × 1.5 |
| `line-height/20` | Body/SM, Label/MD | 14 × 1.43 |
| `line-height/16` | Label/SM, Caption/MD | 12 × 1.33 |

### Layer 2 — Text styles (all 4 properties bound to primitives)

Typography is exposed to designers as **text styles**, not variable aliases. Each style binds all four properties (`fontFamily`, `fontStyle`, `fontSize`, `lineHeight`) directly to the primitives above. Designers click once to apply; change a primitive, all bound styles update.

| Text style | fontFamily → | fontStyle → | fontSize → | lineHeight → |
|---|---|---|---|---|
| `Typography/Display/XL` | family/Default | font-weight/SemiBold | font-size/34 | line-height/41 |
| `Typography/Display/LG` | family/Default | font-weight/SemiBold | font-size/26 | line-height/32 |
| `Typography/Display/MD` | family/Default | font-weight/SemiBold | font-size/22 | line-height/28 |
| `Typography/Heading/LG` | family/Default | font-weight/SemiBold | font-size/20 | line-height/26 |
| `Typography/Heading/MD` | family/Default | font-weight/SemiBold | font-size/18 | line-height/24 |
| `Typography/Body/LG` | family/Default | font-weight/SemiBold | font-size/18 | line-height/24 |
| `Typography/Body/MD` | family/Default | font-weight/Regular | font-size/16 | line-height/24 |
| `Typography/Body/SM` | family/Default | font-weight/Regular | font-size/14 | line-height/20 |
| `Typography/Label/MD` | family/Default | font-weight/SemiBold | font-size/14 | line-height/20 |
| `Typography/Label/SM` | family/Default | font-weight/SemiBold | font-size/12 | line-height/16 |
| `Typography/Caption/MD` | family/Default | font-weight/Regular | font-size/12 | line-height/16 |

> **Why text styles, not variable aliases?** Variables can hold one value each, so a "typography token" would otherwise need four separate alias variables per style — and designers would pick four times per text node. Text styles bundle the bindings into a single unit, matching the same pattern used for `Elevation/*` effect styles.

> **Why is line-height stored in pixels (not percent)?** Figma forces `PIXELS` units when a `FLOAT` variable is bound to `lineHeight`, and assigning `lineHeight = {unit: PERCENT, value: ...}` clears any binding. To get **both** auto-update and correct rendering, line-heights are computed once (`font-size × multiplier`), rounded to an integer, and stored as a pixel primitive. If you ever change a `font-size` primitive, also update the corresponding `line-height` primitive by hand to keep the multiplier intact.

**CSS code syntax (primitives):**
- `var(--typography-family-default)`
- `var(--typography-font-weight-semibold)` / `var(--typography-font-weight-regular)`
- `var(--typography-font-size-{n})` (e.g. `--typography-font-size-34`)
- `var(--typography-line-height-{n})` (e.g. `--typography-line-height-120`)
