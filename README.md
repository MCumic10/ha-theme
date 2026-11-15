# Nordic Fantasy - Home Assistant Theme

Natural, earthy fantasy theme for Home Assistant, loosely inspired by the Elder Scrolls. Light and dark modes.

## Install via HACS (custom repository)
1. HACS -> three-dot menu -> Custom repositories -> add this repo's GitHub URL, type **Theme**.
2. Download **Nordic Fantasy** from HACS.
3. Make sure `configuration.yaml` has `frontend: themes: !include_dir_merge_named themes`, then restart if you added it.
4. Profile -> Theme -> **Nordic Fantasy**.

## Manual install
1. Copy `themes/nordic_fantasy.yaml` to `/config/themes/`.
2. Add to `configuration.yaml`:
   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```
3. Developer Tools -> YAML -> Reload Themes.
4. Profile -> Theme -> **Nordic Fantasy**.

See [VERSION.md](VERSION.md) for the changelog.
