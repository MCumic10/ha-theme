# CLAUDE.md

## Project
Custom Home Assistant theme, "Nordic Fantasy": natural, earthy fantasy colors with the Elder Scrolls (Skyrim) as a loose guideline — night forest, moss, weathered stone, parchment, aged gold, ember red. Readability comes first; atmosphere second.

## Approach
- Start minimal, grow incrementally. One concern per change/commit.
- Planned growth order: core colors (done in 0.1.0) -> fonts (serif headings) -> card radius/borders -> state/domain colors (light = gold, heater = ember) -> card-mod extras.

## Layout
```
themes/nordic_fantasy.yaml   the theme
hacs.json                    HACS metadata (theme repo; yaml files must stay in themes/)
VERSION.md                   current version + changelog + versioning rules
README.md                    install/usage for humans
```

## Install / test
1. Copy `themes/*.yaml` to HA `/config/themes/`.
2. `configuration.yaml`: `frontend: themes: !include_dir_merge_named themes`
3. Developer Tools -> YAML -> Reload "Themes"; select theme in Profile; check both light and dark.
The HA MCP tools in this environment control devices only; do not use them to edit themes.

## Conventions
- Palette is defined once as YAML anchors at the top of the theme file and referenced in `modes: dark:` / `modes: light:`.
- Do not add colors outside the palette without adding them to the table below.
- Text contrast must meet WCAG AA (4.5:1).
- Every change to `themes/` bumps `VERSION.md` (SemVer, 0.x while experimental) with a changelog entry; releases are tagged `vX.Y.Z`.
- Commit messages: short imperative, conventional prefix (`feat:`, `fix:`, `docs:`, `chore:`).
- Never commit secrets or HA config files.

## Palette
| Role | Dark | Light |
|---|---|---|
| Background | `#111716` deep teal-black | `#e9e2d0` parchment |
| Card | `#1a2321` dark slate teal | `#f4eedd` |
| Primary | `#c9a45c` bronze | `#7d5f26` |
| Accent | `#5fa39b` teal | `#556b3f` |
| Text | `#dce6e1` | `#2b2a24` |
| Secondary text | `#8fa39b` | `#6b6757` |
| Divider | `#2e3b38` | `#cbbf9f` |
| Error / red | `#d96c55` ember red | `#9a3b2e` |
| Warning / amber | `#d6a043` | `#a97618` |
| Success / green | `#7a9a56` spring moss | `#55703a` |
| Info / cool | `#7fa3b5` frost | `#4a7189` |
| Heat | `#d0702f` ember | `#b4571f` |
| Light on | `#e8c46a` candlelight | `#c48a12` |
| Arcane (media) | `#9a80b0` | `#6c5290` |
| Raised surface (inputs, alt rows) | `#232e2b` | `#ece4cf` |
| Sidebar / header bg | `#0d1211` / `#161e1c` | `#ddd5bf` |
| Gold ramp (HA `ha-color-primary-NN`, shared) | 05 `#2a2418`, 10 `#362d1c`, 20 `#4a3b1f`, 30 `#5e4719`, 40 `#7d5f26`, 50 `#a98544`, 60 `#b08d4f`, 70 `#d1b277`, 80 `#ddd5bf`, 90 `#e9e2d0`, 95 `#f4eedd` | same |
| Neutral ramp (HA `ha-color-neutral-NN`) | 05 `#111716`, 10 `#1a2321`, 20 `#232e2b`, 30 `#2e3b38`, 40 `#3f4e49`, 50 `#5f706a`, 60 `#6f817a`, 70 `#7f928a`, 80 `#8fa39b`, 90 `#c3d0ca`, 95 `#dce6e1` | 05 `#1c1f1a`, 10 `#262b24`, 20 `#2f352c`, 30 `#3a4036`, 40 `#4a5045`, 50 `#6b6757`, 60 `#a39d88`, 70 `#bdb597`, 80 `#cbbf9f`, 90 `#ddd5bf`, 95 `#ece4cf` |

Both modes must define the same set of variables. Fonts are a system serif stack (a theme cannot load web fonts). card-mod ornaments live in the shared `card-mod-*` keys of the theme (use only theme variables so both modes work; ignored without card-mod).
