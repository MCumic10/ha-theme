# Version

**Current version: 2.3.3**

## Versioning rules
- [Semantic Versioning](https://semver.org/). Stable from 1.0.0 (0.x was the experimental phase).
- MAJOR: breaking change (theme renamed, variables removed, palette overhaul).
- MINOR: new variables/features/visual areas covered.
- PATCH: color tweaks and fixes.
- Every change to `themes/` bumps this file and adds a changelog entry.
- Release = commit + git tag `vX.Y.Z`.

## Changelog

### [2.3.3] - 2026-11-22
- Test: removed all card-mod keys from the theme (card-mod-theme, -card-yaml, -root, -sidebar, -more-info-yaml) to isolate card-mod issues. Ornaments and tile effects from 2.2.0-2.3.0 are inactive until restored (see git history).

### [2.3.2] - 2026-11-22
- Refactor: repeated palette colors in dark/light modes are now YAML anchors with role names (d-*/l-*); resolved values are unchanged.

### [2.3.1] - 2026-11-22
- Chore: removed all comments from the theme file (no value changes).

### [2.3.0] - 2026-11-20
- Phase 3 tile effects (card-mod, best effort, all animations off under `prefers-reduced-motion`): candle flicker on lights that are on, frost breath on cooling climate tiles, arcane shimmer on playing media players, slow red pulse on active alerts, locks glow moss when sealed and amber when unsealed (unsealed tiles also get an amber border).
- Removed the sidebar snowflake added in 2.2.0: it made "Home Assistant" in the sidebar title get cut off. Title letter spacing reduced slightly for the same reason.
- Not done yet from phase 3: extra theme variants (Minimal / Hearth / OLED) and opt-in snowfall.

### [2.2.1] - 2026-11-20
- Fix: card styling from card-mod did not show in 2.2.0 (card title flourish, small caps, corner brackets, hover, glows, drop cap). Having both `card-mod-card` and `card-mod-card-yaml` made card-mod ignore the plain one. All card rules now live in a single `card-mod-card-yaml` (`.:` for the card, `ha-markdown$:` for the drop cap).

### [2.2.0] - 2026-11-20
- Phase 2 "typography and ornaments" (all card-mod, best effort, ignored without card-mod; not verified in a live HA):
  - Heading font stack now starts with Cinzel / Trajan Pro (carved Roman capitals), used only if installed on the device, otherwise Georgia as before. No web font is loaded: `@font-face` inside card-mod's shadow roots does not register, and it would send requests to an external host.
  - Cards: gold L-shaped corner flourishes on the inner hairline (via `ha-card::before`); card titles get a small diamond at the start of the gold rule.
  - Markdown cards: illuminated drop cap (large gold first letter) via `card-mod-card-yaml`.
  - Sidebar: snowflake sigil before the title; group dividers are a gold hairline fading out at both ends.
  - More-info dialog: matching double frame. Fix: the old `card-mod-more-info` key contained YAML text (not valid CSS) and never applied; it is now `card-mod-more-info-yaml`.
  - Added `card-mod-theme: Winterhold`, which card-mod's theme docs require to equal the theme name.

### [2.1.0] - 2026-11-20
- Card edges (`ha-card-box-shadow`, no card-mod needed): dark cards get a thin icy highlight on the bottom edge and a faint frost glow beneath; light cards get an aged, darker bottom edge and a warmer brown shadow, like a worn parchment sheet.
- Dialog scrims: dark is a frosted night blue (`rgba(8,15,24,0.72)`), light is a warm candle-lit umber (`rgba(72,50,24,0.58)`).

### [2.0.1] - 2026-11-20
- Skyline mountains are now irregular ridgelines (about 50 points each, uneven peaks and saddles, sharp crests with gently curved slopes instead of straight lines) instead of simple triangles, with small snow caps on the two tallest peaks. Still two layers.

### [2.0.0] - 2026-11-20
- Dashboard background gets a mountain skyline along the bottom edge (non-tiling inline SVG, no seams): dark = dark ridges under a faint moss-green aurora glow, light = faint ink-wash ridges like an old map. Alpha kept low so card/text contrast is unchanged.

### [1.1.0] - 2026-11-18
- card-mod, standard cards: card titles get a small gold flourish (❖) before the text; active tile cards get a faint inner glow in their state color; glance card entities get a faint gold wash on hover. All best effort (ignored without card-mod or if a card's structure differs).

### [1.0.2] - 2026-11-18
- Switch entity icons (when on) now use the primary color (frost in dark, gold in light) instead of moss, so they match the toggle next to them. Locks and other "ok" states stay moss.

### [1.0.1] - 2026-11-18
- Fix: serif fonts did not apply on current HA versions. Added `ha-font-family-body`, `ha-font-family-heading` and `ha-font-family-longform` (the tokens newer HA reads); the older `paper-font-*` keys stay for compatibility.

### [1.0.0] - 2026-11-16
- First stable release. BREAKING: theme renamed "Nordic Fantasy" -> "Winterhold"; file renamed `themes/nordic_fantasy.yaml` -> `themes/winterhold.yaml`. Re-select the theme in your profile and delete any old `nordic_fantasy.yaml` from `/config/themes/`.
- Added README/HACS preview banner (`docs/banner.svg` source, `docs/banner.png` linked).

### [0.13.0] - 2026-11-16
- Dark palette changed to "Winterhold": cold slate night (`#12171c`, cards `#1b222a`), frost-blue primary `#8fb3c9`, gold accent `#c9a15a`. Earlier dark palettes: Blackreach in tag v0.11.0, Embers of Whiterun in tag v0.12.0. Light theme unchanged.
- `ha-color-primary-NN` is now defined per mode (frost-blue ramp in dark, gold ramp in light) so primary fills match each mode.
- Dark info color moved to `#6db3d6` so it stays distinct from the frost primary; cool/fan states keep `#7fa3b5`.
- Palette table in CLAUDE.md re-synced (dark semantic colors had drifted since 0.12.0).

### [0.12.0] - 2026-11-16
- Dark palette changed from "Blackreach" (still available in tag v0.11.0) to "Embers of Whiterun": warm hearth-black `#1a1511`, umber cards `#251e18`, ember-amber primary `#d08a3c`, moss accent `#8a9a5b`. Light theme unchanged.
- Dark semantic colors retuned so they stay distinct from the amber primary: error `#e0705a`, heat `#e4672c`, warning `#e2b24a`, success `#86a65f`, arcane `#a98cc0` (all >= 4.7:1 on cards).
- Dark neutral ramp re-tinted warm.

### [0.11.0] - 2026-11-16
- Dark palette replaced: "Blackreach" (deep teal-black `#111716`, slate-teal cards `#1a2321`, bronze primary `#c9a45c`, teal accent `#5fa39b`). Light theme unchanged.
- Dark error red brightened to `#d96c55` (4.8:1 on cards, was 3.3:1 against the new card color).
- `ha-color-neutral-NN` is now defined per mode (teal ramp in dark, parchment ramp in light) instead of shared.
- Palette table in CLAUDE.md updated for dark.

### [0.10.0] - 2026-11-16
- Dark mode parity with light: dashboard background gets the same layered structure (vignette, faint moss/gold blotches, faint lines) in forest tones; cards get the double gold frame (outer border + inner hairline 3px in) and soft inner edge.
- Removed the card-mod `ha-card` background rule (corner brackets, top tint, laid lines): it never rendered in practice. Corner brackets are dropped for good; the gold top rule and frame stay in `ha-card-box-shadow`.
- Verified dark and light define the same 140 variables.

### [0.9.0] - 2026-11-16
- Entity state accents on tile cards (card-mod): active icons glow in their state color, lights glow stronger (candlelight), heating climate icons pulse softly in ember (disabled with prefers-reduced-motion).

### [0.8.0] - 2026-11-16
- Header and sidebar (card-mod): subtle gold top tint and laid lines, inset edge shadow on the sidebar, selected sidebar item gets a gold left bar and engraved inset, active tab gets a pressed-in wash.
- Focus ring on dashboard tabs recolored gold (best effort).
- Scrollbar thumbs recolored to gold-brown tones (dark `#6b5428`, light `#a98544`).

### [0.7.1] - 2026-11-16
- Fix: white input fields (e.g. time pickers). HA form backgrounds/surfaces/text read `--ha-color-neutral-NN`; overridden with a warm parchment/forest grey ramp (shared, both modes). Two shades added to the palette table.

### [0.7.0] - 2026-11-16
- HA design-token scale: `ha-color-primary-05..95` overridden with a gold ramp (shared, both modes), so buttons, switches and other primary fills stop being HA blue. Three new dark ramp shades added to the palette table.

### [0.6.3] - 2026-11-16
- Fix: bold black halo on chart labels (energy flow sankey, graphs). HA reads `--ha-card-background` as a plain color (label outline + chart background), so the layered gradient from 0.4.0 broke it. `ha-card-background` is a plain color again in both modes.
- Gold top rule moved into `ha-card-box-shadow` (reliable). Corner brackets, top tint and laid lines moved to `card-mod-card` (best effort; needs card-mod to reach `ha-card`).

### [0.6.2] - 2026-11-16
- Fix: toggles showed HA default blue; set `ha-switch-checked-border-color` to the primary gold in both modes.

### [0.6.1] - 2026-11-16
- Corner brackets thinner: 1px strokes (was 2px), sitting exactly on the inner hairline.

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
