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
| Background | `#1c1f1a` night forest | `#e9e2d0` parchment |
| Card | `#262b24` mossy stone | `#f4eedd` |
| Primary | `#b08d4f` aged gold | `#7d5f26` |
| Accent | `#6f8f5a` moss | `#556b3f` |
| Text | `#e6dfc9` | `#2b2a24` |
| Secondary text | `#a39d88` | `#6b6757` |
| Divider | `#3a4036` | `#cbbf9f` |
| Error / red | `#b8523f` ember red | `#9a3b2e` |
| Warning / amber | `#d6a043` | `#a97618` |
| Success / green | `#7a9a56` spring moss | `#55703a` |
| Info / cool | `#7fa3b5` frost | `#4a7189` |
| Heat | `#d0702f` ember | `#b4571f` |
| Light on | `#e8c46a` candlelight | `#c48a12` |
| Arcane (media) | `#9a80b0` | `#6c5290` |
| Raised surface (inputs, alt rows) | `#2f352c` | `#ece4cf` |
| Sidebar / header bg | `#161914` / `#20251e` | `#ddd5bf` |
| Gold ramp (HA `ha-color-primary-NN`, both modes) | 05 `#2a2418`, 10 `#362d1c`, 20 `#4a3b1f`, 30 `#5e4719`, 40 `#7d5f26`, 50 `#a98544`, 60 `#b08d4f`, 70 `#d1b277`, 80 `#ddd5bf`, 90 `#e9e2d0`, 95 `#f4eedd` | same |

Both modes must define the same set of variables. Fonts are a system serif stack (a theme cannot load web fonts). card-mod ornaments live in the shared `card-mod-*` keys of the theme (use only theme variables so both modes work; ignored without card-mod).
