# Styling Guide

This guide explains how to use the modular CSS design system alongside Bootstrap 5 and Iconoir.

## 1. Include the stylesheets

Load Bootstrap 5.3, Iconoir, and the bundled design-system stylesheet in the `<head>` of your document. The playground already demonstrates the correct ordering so Bootstrap variables are overridden by the token layer.【F:index.html†L1-L9】

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/iconoir@6.7.0/css/iconoir.css">
<link rel="stylesheet" href="styles/design-system.bundle.css">
```

## 2. Work with tokens and Bootstrap overrides

Design tokens expose the brand palette, radius scale, shadows, action/field metrics, and a status color map. They also remap Bootstrap variables so default components inherit the same typography and colors.【F:styles/foundation/tokens.css†L20-L190】

- Reference variables like `var(--ds-primary-500)` or `var(--ds-radius-md)` inside custom components.
- Use the status map (`--ds-status-*`) to keep message colors consistent across badges, alerts, and form states.
- When Bootstrap utilities need tweaks, adjust the relevant `--bs-*` override in the same file.

## 3. Utilities

### Layout helpers
- `.u-stack` creates vertical stacks with a configurable gap via `--u-stack-gap` (default 1rem).【F:styles/utilities/layout.css†L1-L5】
- `.u-inline` produces inline-flex rows for icons and labels, honoring `--u-inline-gap`.【F:styles/utilities/layout.css†L7-L10】

### Icon wrapper
- Wrap Iconoir glyphs with `.ds-icon` to normalize size and alignment, or use the `data-size="sm"|"lg"` variants for alternate dimensions.【F:styles/utilities/icon.css†L1-L11】

### Status badge utility
- `.ds-status` standardizes compact status chips using the token map, while modifiers like `data-variant="success"` or `data-tone="soft"` swap colors without redefining styles.【F:styles/utilities/status.css†L1-L37】

## 4. Component primitives

### Actions
- Apply `.ds-action` to buttons or anchors (optionally alongside `.btn`) to inherit shared height, padding, and focus behavior; choose variants such as `.ds-action--solid`, `.ds-action--outline`, or `.ds-action--ghost` for visual differences.【F:styles/components/actions.css†L1-L69】
- Size modifiers (`.ds-action--lg` … `.ds-action--xxs`) tune control height and font size, while `.ds-action--icon-only` enforces square icon buttons.【F:styles/components/actions.css†L77-L89】
- Group controls with `.ds-action-group`, `.ds-pagination`, or `.ds-tabs` to reuse the segmented button and tab styling shown in the playground.【F:styles/components/actions.css†L102-L161】

### Forms and choices
- Structure inputs with `.ds-field` for label/helper spacing and `.ds-control` for the interactive container; add leading/trailing adornments via the respective sub-elements.【F:styles/components/forms.css†L1-L62】
- State modifiers (e.g., `.is-success`, `.is-danger`) recolor borders and helper text using the shared status tokens.【F:styles/components/forms.css†L72-L80】
- Use `.ds-choice` (with optional `data-variant="radio"`) for checkbox/radio patterns, and `.ds-toggle` for switch-style inputs, both of which handle focus and disabled states consistently.【F:styles/components/forms.css†L96-L200】

### Surfaces and avatars
- `.ds-surface` is the baseline elevated container; extend it through `.ds-card`, `.ds-panel`, or `.ds-list` to compose cards, panels, and list groups with consistent radius and shadows.【F:styles/components/surfaces.css†L1-L45】
- `.ds-avatar` (and the `data-size` attribute) standardizes avatar sizes, while `.ds-avatar-stack` creates overlapping clusters for list items or cards.【F:styles/components/surfaces.css†L50-L79】

## 5. Extending components

When building new modules:
1. Start with the closest existing primitive (action, field, surface) to inherit typography, elevation, and spacing.
2. If an additional pattern is shared across multiple components, create a utility inside `styles/utilities/` and import it through `design-system.bundle.css` so every consumer automatically picks it up.【F:styles/design-system.bundle.css†L1-L15】
3. Document the new pattern and any recommended markup additions in this guide to keep implementation notes in sync with the CSS.

