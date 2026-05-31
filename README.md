# Architectus

Glow animations and a control panel sidebar for VS Code.

## Requirements

- [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) extension
- Add the CSS file path to your `settings.json`:
  ```json
  "vscode_custom_css.imports": [
    "file:///Users/your-username/.vscode/varun-architectus.css"
  ]
  ```

## Setup

1. Install the `.vsix` via **Extensions → Install from VSIX**
2. Add the import path above to `settings.json`
3. Open the **Architectus** panel from the activity bar
4. Click **Apply CSS** to write the CSS file
5. Run **Reload Custom CSS and JS** from the command palette

## Panel

### Background Console

Collapsible module for all glow and animation effects. The toggle in the section header writes the full CSS (on) or clears it (off) — same as clicking Apply CSS. State is persisted across reloads. Run **Reload Custom CSS and JS** after toggling to apply.

| Sub-section | Controls |
|---|---|
| **Custom Background Text** | Front/back text, opacity, rotation speed, size, glow color, extrude color, glow intensity |
| **Glitch** | Enable/disable, intensity, frequency, typing glitch on keypress |
| **Syntax Glow** | Per-token colors: strings, types, keywords, numbers, functions, variables, errors, comments |
| **Cursor** | Primary/secondary color, pulse speed |
| **Effects** | Scanlines toggle + opacity, scrollbar color + hover color |

### Action buttons

| Button | What it does |
|---|---|
| **Apply CSS** | Writes `varun-architectus.css` with current settings |
| **Reload** | Reloads the VS Code window |
| **Reset** | Resets all settings to defaults |
| **Pick Colors from Active Theme** | Pulls colors from the current VS Code theme and applies |

## Development

Files in `~/.vscode/extensions/varun.ryze-controls-1.0.0/` are symlinked to this repo. Edit here, push from here.

```bash
# Repackage after changes
cd ~/architectus
vsce package --allow-missing-repository --no-dependencies
```
