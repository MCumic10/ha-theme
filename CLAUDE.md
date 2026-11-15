# CLAUDE.md

## Project
Custom Home Assistant theme, "Nordic Fantasy": natural, earthy fantasy colors with the Elder Scrolls (Skyrim) as a loose guideline — weathered stone, slate, oxblood, dark leather brown, tan. Readability comes first; atmosphere second.

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
Base palette (user-chosen, 0.4.0): `#34221b` dark brown, `#552a24` oxblood, `#4c5059` slate, `#555c5e` stone, `#806653` tan. Other colors are derived tints/shades for contrast.

| Role | Dark | Light |
|---|---|---|
| Background | `#2a1c16` | `#e2dbd2` |
| Card | `#34221b` brown | `#eee8e0` |
| Raised surface (inputs, headers of tables) | `#3f2b23` | `#e8e1d8` |
| Primary | `#a58468` lifted tan (base `#806653`) | `#6b533f` deep tan |
| Accent | `#8c9699` stone | `#555c5e` stone |
| Text | `#ebe3d8` | `#34221b` |
| Secondary text | `#b3a699` | `#555c5e` |
| Divider | `#555c5e` | `#c4b9ad` |
| Header bar | `#552a24` oxblood | `#552a24` |
| Sidebar | `#4c5059` slate | `#4c5059` |
| Error | `#bb5548` | `#8f3a31` |
| Warning | `#d1a561` | `#94661c` |
| Success | `#8fa57d` sage | `#5b6e4a` |
| Info / cool | `#8aa3b8` | `#4c6a80` |
| Heat | `#cf7344` | `#a8512a` |
| Light on | `#e6c487` | `#b0832d` |
| Arcane (media) | `#a49fbd` | `#675f80` |

Both modes must define the same set of variables. Fonts are a system serif stack (a theme cannot load web fonts). card-mod ornaments live in the shared `card-mod-*` keys of the theme (use only theme variables so both modes work; ignored without card-mod).
