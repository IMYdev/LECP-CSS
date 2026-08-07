<p align="center"><b>LECP CSS</b></p>

<p align="center">A portable CSS (framework?) implementing the <b>LECP</b> design system: visually inspired by <a href="https://en.wikipedia.org/wiki/Metro_(design_language)">Metro</a> with input-independent interaction rules for keyboard, pointer, touch, and assistive technology.</p>

---

## Features

- Single CSS file, no build step, no dependencies.
- Retheme by overriding CSS custom properties.
- 12-column responsive grid with breakpoint-prefixed column classes (`c-`, `s-`, `w-`).
- Components: tile/card, nav, button, form fields, badge, toast.
- `:focus-visible` defined on every interactive component by default.
- `prefers-reduced-motion` handled once, globally, in the base reset.
- Minimum 44px touch targets on all interactive elements.
---

## Installation

Copy `lecp.css` into your project and link it:

```html
<link rel="stylesheet" href="lecp.css">
```

---

## Usage

### Theming

Override the custom properties defined in `:root` to retheme a project:
```css
:root {
  --lecp-bg: #0b0c10;
  --lecp-surface: #1f2833;
  --lecp-accent: #66fcf1;
  --lecp-accent-soft: #c5c6c7;
  --lecp-font: "Inter", system-ui, sans-serif;
}
```

### Tokens

| Group | Variables |
|---|---|
| Color | `--lecp-bg`, `--lecp-surface`, `--lecp-surface-hover`, `--lecp-surface-raised`, `--lecp-text`, `--lecp-text-secondary`, `--lecp-line`, `--lecp-accent`, `--lecp-accent-hover`, `--lecp-accent-soft`, `--lecp-on-accent`, `--lecp-success`, `--lecp-warning`, `--lecp-error` |
| Spacing | `--lecp-space-1` through `--lecp-space-8` |
| Motion | `--lecp-motion-focus`, `--lecp-motion-activate`, `--lecp-motion-dismiss`, `--lecp-motion-page`, `--lecp-ease-*` |
| Type | `--lecp-type-display` through `--lecp-type-caption`, `--lecp-font` |
| Layout | `--lecp-gap`, `--lecp-margin`, `--lecp-margin-compact`, `--lecp-container-max` |

### Components

| Class | Description |
|---|---|
| `.lecp-container` | Max-width content wrapper with responsive side padding. |
| `.lecp-grid` / `.lecp-col-*` | 12-column grid. `.lecp-col-4` applies at all sizes; `.lecp-col-c-*`, `.lecp-col-s-*`, `.lecp-col-w-*` apply from the compact/standard/wide breakpoint up. |
| `.lecp-tile` | Core interactive unit (card, row, or panel). Modifiers: `--s`/`--m`/`--l`/`--xl` for size, `--primary`, `--selected`, `--loading`, `--error` for state. Tiles with `target="_blank"` receive a static external-link icon automatically. |
| `.lecp-nav` / `.lecp-nav-item` | Navigation list. Vertical by default; add `data-orientation="horizontal"` for a horizontal or tab-style layout. Add `.is-active` to mark the current item. |
| `.lecp-btn` | Button. Modifiers: `--primary`, `--ghost`, `--danger`, `--sm`, `--loading`. |
| `.lecp-field` / `.lecp-label` / `.lecp-input` / `.lecp-select` / `.lecp-textarea` | Form primitives. Add `.lecp-field--error` with a `.lecp-field-error-text` for validation states. |
| `.lecp-badge` | Status indicator. Modifiers: `--success`, `--warning`, `--error`. |
| `.lecp-toast-region` / `.lecp-toast` | Notification container and individual notification. |
| `.lecp-skip-link` / `.lecp-sr-only` | Accessibility utilities for skip-to-content links and visually hidden text. |

A small set of spacing and layout utility classes is also included (`.lecp-mt-*`, `.lecp-mb-*`, `.lecp-gap-*`, `.lecp-flex`, `.lecp-hidden-compact`, etc.) for common one-off adjustments.

---

## Design Principles

LECP CSS implements the following rules from the LECP design specification:

- **Content before chrome**: surfaces exist to communicate grouping or focus, not decoration.
- **Focus is a first-class state**: every interactive component defines a visible, non-color-only `:focus-visible` state.
- **Motion explains change**: transitions occur on focus, activation, and enter/exit; nothing animates without communicating a state change.
- **Size is semantic**: tile size communicates importance, not visual variety.
- **Reflow, not rebuild**: layouts stack and reflow across breakpoints without requiring a separate mobile-specific structure.

---

## Project Structure

- `lecp.css`: Self-explanatory.
- `example.html`: Reference page rendering every component for visual verification.
- `README.md`: Project documentation (you are here :D)

---

## What's Not Included

- **JavaScript.** The CSS exposes the relevant states and classes (`.is-active`, `.lecp-toast--leaving`, `[aria-disabled]`, etc.) to hook into but that's it.
- **An icon set.** Bring your own icons or SVGs (LECP recommends SVGs strongly)

---

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
