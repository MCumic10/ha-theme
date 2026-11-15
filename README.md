# Nordic Fantasy - Home Assistant Theme

Natural, earthy fantasy theme for Home Assistant, loosely inspired by the Elder Scrolls. Light and dark modes.

## Install
1. Copy `themes/nordic_fantasy.yaml` to `/config/themes/`.
2. Add to `configuration.yaml`:
   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```
3. Developer Tools -> YAML -> Reload Themes.
4. Profile -> Theme -> **Nordic Fantasy**.

See [VERSION.md](VERSION.md) for the changelog.
