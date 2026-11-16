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
| Background | `#12171c` slate-black | `#e9e2d0` parchment |
| Card | `#1b222a` dark slate | `#f4eedd` |
| Primary | `#8fb3c9` frost | `#7d5f26` |
| Accent | `#c9a15a` gold | `#556b3f` |
| Text | `#dde5ea` | `#2b2a24` |
| Secondary text | `#93a0ab` | `#6b6757` |
| Divider | `#2b353f` | `#cbbf9f` |
| Error / red | `#e0705a` ember red | `#9a3b2e` |
| Warning / amber | `#e2b24a` | `#a97618` |
| Success / green | `#86a65f` spring moss | `#55703a` |
| Info / cool | `#6db3d6` frost | `#4a7189` |
| Heat | `#e4672c` ember | `#b4571f` |
| Light on | `#e8c46a` candlelight | `#c48a12` |
| Arcane (media) | `#a98cc0` | `#6c5290` |
| Raised surface (inputs, alt rows) | `#232c36` | `#ece4cf` |
| Sidebar / header bg | `#0d1217` / `#161d24` | `#ddd5bf` |
| Primary ramp (HA `ha-color-primary-NN`) | 05 `#0f1a22`, 10 `#16242e`, 20 `#1f3441`, 30 `#2b4658`, 40 `#3f6379`, 50 `#5f8199`, 60 `#8fb3c9`, 70 `#b5d0e0`, 80 `#cfe0ea`, 90 `#e3edf3`, 95 `#f1f6f9` | gold: 05 `#2a2418`, 10 `#362d1c`, 20 `#4a3b1f`, 30 `#5e4719`, 40 `#7d5f26`, 50 `#a98544`, 60 `#b08d4f`, 70 `#d1b277`, 80 `#ddd5bf`, 90 `#e9e2d0`, 95 `#f4eedd` |
| Neutral ramp (HA `ha-color-neutral-NN`) | 05 `#12171c`, 10 `#1b222a`, 20 `#232c36`, 30 `#2b353f`, 40 `#404c57`, 50 `#677582`, 60 `#738190`, 70 `#82909c`, 80 `#93a0ab`, 90 `#c3ced6`, 95 `#dde5ea` | 05 `#1c1f1a`, 10 `#262b24`, 20 `#2f352c`, 30 `#3a4036`, 40 `#4a5045`, 50 `#6b6757`, 60 `#a39d88`, 70 `#bdb597`, 80 `#cbbf9f`, 90 `#ddd5bf`, 95 `#ece4cf` |

Both modes must define the same set of variables. Fonts are a system serif stack (a theme cannot load web fonts). card-mod ornaments live in the shared `card-mod-*` keys of the theme (use only theme variables so both modes work; ignored without card-mod).
