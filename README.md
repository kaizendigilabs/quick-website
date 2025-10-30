# Quick Website Design System Playground

This repository hosts a static playground that showcases the modular design system built on top of Bootstrap 5 and Iconoir. It exposes the design tokens, utilities, and component primitives needed to recreate the UI kit from the provided design references.

## Project Structure

```
quick-website/
├── index.html                # Bootstrap + Iconoir playground that renders every component group
├── styles/
│   ├── design-system.bundle.css  # Entry point that aggregates all style layers
│   ├── foundation/           # Global tokens, resets, and typography overrides
│   ├── utilities/            # Reusable layout, icon, and status helpers
│   └── components/           # Action, form, feedback, navigation, overlay, and surface modules
└── images/                   # Reference design exports (not used at runtime)
```

- The bundle imports each layer in dependency order so any consumer can pull in a single stylesheet while keeping the source modules organized by responsibility.【F:styles/design-system.bundle.css†L1-L15】
- Foundation tokens define the design primitives (color palette, spacing, radius, shadows) and map them to Bootstrap CSS variables so native Bootstrap widgets inherit the theme automatically.【F:styles/foundation/tokens.css†L20-L190】
- Component folders group related UI families (actions, forms, overlays, etc.) so the same primitives are reused across examples such as buttons, tabs, inputs, and modals.【F:styles/components/actions.css†L1-L170】【F:styles/components/forms.css†L1-L200】

## Previewing the Playground

Open `index.html` directly in a browser or serve the repository with any static HTTP server (for example, `npx serve .`). The page already loads Bootstrap 5.3, Iconoir, and the bundled design-system stylesheet from the `styles/` directory.【F:index.html†L1-L9】

## Extending the System

1. Add or update tokens inside `styles/foundation/tokens.css` when new colors, spacings, or Bootstrap overrides are required.
2. Create additional utility modules in `styles/utilities/` to share layout or interaction patterns across components.
3. Introduce new component styles inside the appropriate `styles/components/` file (or a new file) and register it inside `styles/design-system.bundle.css` so it is included in the build.
4. Document new patterns inside `docs/styling-guide.md` to keep the usage guidance up to date.

