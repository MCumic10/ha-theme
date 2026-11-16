# Version

**Current version: 0.6.0**

## Versioning rules
- [Semantic Versioning](https://semver.org/). Stay on `0.x` while the theme is experimental.
- MAJOR: breaking change (theme renamed, variables removed, palette overhaul).
- MINOR: new variables/features/visual areas covered.
- PATCH: color tweaks and fixes.
- Every change to `themes/` bumps this file and adds a changelog entry.
- Release = commit + git tag `vX.Y.Z`.

## Changelog

### [0.6.0] - 2026-11-16
- Graph series colors: `graph-color-1..10` use palette colors in both modes (history graphs no longer default blue/yellow/red/teal).
- card-mod (best effort, needs card-mod): gold card border on hover, gold hairline dividers between entity rows (fading at both ends), faint gold wash on row hover.

### [0.5.1] - 2026-11-16
- Fix: card-mod `card-mod-card` did not reach `ha-card`, so the gold top rule and corner brackets never showed. They are now background layers in `ha-card-background` (both modes). The title rule stays in card-mod.

### [0.5.0] - 2026-11-16
- card-mod: gold corner brackets on cards (overlay on the double frame, click-through) and card titles get a gold rule fading out to the right.

### [0.4.2] - 2026-11-16
- Fix: seams were still visible. Dropped all SVG noise; the light texture is now pure CSS gradients (soft blotches, faint laid-paper lines, vignette) that cannot tile or seam.

### [0.4.1] - 2026-11-16
- Fix: visible seams between parchment texture tiles. Grain and mottling are now rendered once at full size (no tiling, no `stitchTiles`) instead of repeating 200px/600px tiles.

### [0.4.0] - 2026-11-16
- Light mode: parchment texture. Dashboard background gets paper grain, large aged mottling and an edge vignette (inline SVG noise, low alpha).
- Light mode: cards become parchment sheets with fine grain, a double gold frame (outer border + inner hairline 3px in) and a soft aged inner edge.
- Card top tint moved from card-mod into the new `ha-card-background` variable (defined in both modes; dark looks unchanged).

### [0.3.2] - 2026-11-16
- Removed the picture-elements state-label rules added in 0.3.1: `card-mod-card` cannot reach them (labels live in the picture-elements card's own shadow tree). Style them with `card_mod` on the card itself instead.

### [0.3.1] - 2026-11-16
- card-mod: picture-elements state labels get a near-invisible, tight plaque (gold hairline, serif text) that brightens with a candlelight glow on hover. (Did not work from the theme; removed in 0.3.2.)

### [0.3.0] - 2026-11-15
- card-mod ornaments (optional, needs card-mod): gold top rule and soft gold glow on cards, small-caps spaced card titles, gold rule under dashboard header, sidebar edge and small-caps title, framed more-info dialogs.

### [0.2.1] - 2026-11-15
- Sharper corners: card 4px, button 3px, dialog 6px, tooltip 3px (was 10/8/14/6).

### [0.2.0] - 2026-11-15
- Full theme pass, dark and light (128 variables each).
- Typography: serif stack (Palatino/Georgia), larger card headers.
- Shape: card/dialog/button radii, thin borders, layered shadows.
- Dashboard background gradients (forest glow / parchment).
- Entity state colors: candlelight lights, ember heat, frost cool, moss locks/switches, arcane media.
- Switches, sliders, inputs, lists, dialogs (blurred scrim), tables, code editor syntax colors, energy dashboard.
- Light-mode primary darkened to `#7d5f26` for AA contrast on filled buttons.
- Palette extended with semantic colors (ember, amber, moss, frost, arcane).

### [0.1.0] - 2026-11-15
- Initial minimal theme "Nordic Fantasy" with light and dark modes.
- Core variables only: primary/accent, backgrounds, text, divider, header, sidebar.
