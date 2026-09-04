# Keymaps

- `default/` contains untouched reference layouts.
- `saved/` contains your own inactive layouts and snapshots.
- The only keymap compiled by the normal workflow is `../config/keychron_b1_us.keymap`.

Recommended workflow:

1. Copy the active keymap into `saved/` before a major experiment.
2. Edit a copy in `saved/` if you want to develop it separately.
3. When ready to test, copy that version to `config/keychron_b1_us.keymap`.
4. Push; GitHub Actions builds the active file.
5. After flashing, use Fn+J+Z factory reset if persisted Keychron settings hide your new bindings.
