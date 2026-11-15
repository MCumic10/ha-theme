# Version

**Current version: 0.4.0**

## Versioning rules
- [Semantic Versioning](https://semver.org/). Stay on `0.x` while the theme is experimental.
- MAJOR: breaking change (theme renamed, variables removed, palette overhaul).
- MINOR: new variables/features/visual areas covered.
- PATCH: color tweaks and fixes.
- Every change to `themes/` bumps this file and adds a changelog entry.
- Release = commit + git tag `vX.Y.Z`.

## Changelog

### [0.4.0] - 2026-11-15
- Palette switched to user-chosen base colors: brown `#34221b`, oxblood `#552a24`, slate `#4c5059`, stone `#555c5e`, tan `#806653`.
- Oxblood header bar, slate sidebar, stone dividers, brown cards (dark) and warm stone-parchment (light).
- Semantic colors (success, info, warning, etc.) retuned to muted tones that fit the new palette.

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
