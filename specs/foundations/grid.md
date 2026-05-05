---
name: Grid & Layout
tier: foundation
status: stable
last-updated: 2026-05-02
---

# Grid & Layout

Almosafer uses a responsive breakpoint system to adapt layouts across devices. Design mobile-first, then enhance for larger screens.

---

## Breakpoints

| Token | Breakpoint | Device | Usage |
|-------|-----------|--------|-------|
| `bp-mobile` | max-width: 599px | Phone, small devices | Primary design target—optimize for touch, single column |
| `bp-tablet` | 600px–1199px | Tablet, landscape phone | Two-column layouts, expanded navigation |
| `bp-desktop` | min-width: 1200px | Desktop, large screens | Multi-column grids, sidebar layouts, full width content |

---

## Container Widths

| Breakpoint | Max Width | Padding | Content Width |
|------------|-----------|---------|----------------|
| Mobile | 100% | 16px | Full width - 32px |
| Tablet | 100% | 20px | Full width - 40px |
| Desktop | 1200px | 24px | 1200px |

---

## Mobile-First Approach

1. **Design for mobile first** (bp-mobile)
   - Single column, stacked content
   - Touch-friendly tap targets (44px minimum)
   - Simplified navigation

2. **Enhance for tablet** (bp-tablet)
   - Add secondary columns if needed
   - Expand navigation to 2-level menus
   - Increase spacing for larger screens

3. **Optimize for desktop** (bp-desktop)
   - Full multi-column layouts
   - Sidebars, complex grids
   - Hero sections, expanded imagery

---

## Dos and Don'ts

### ✓ Do

- **Start mobile.** Design at 375px first, scale up.
- **Use breakpoints consistently.** Apply across all components.
- **Test on real devices.** Not just browser resizing.
- **Keep touch targets 44px+** on mobile.
- **Adjust spacing by breakpoint.** Increase from mobile to desktop.

### ✗ Don't

- **Create custom breakpoints.** Use the 3 defined sizes only.
- **Hide content on mobile.** Restructure instead.
- **Assume desktop behavior on mobile.** Test both.
- **Forget landscape orientation.** Tablet layouts cover landscape phones too.

---

## Figma Variables

Create these in Figma:
- `Breakpoint/Mobile` → max-width: 599px
- `Breakpoint/Tablet` → 600px–1199px
- `Breakpoint/Desktop` → min-width: 1200px

Use breakpoint tokens in component prototypes and responsive variants.
