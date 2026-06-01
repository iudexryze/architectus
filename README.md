# Architectus

Control panel sidebar for VS Code — glow animations, quick commands, focus mode, font controls, scratch pad, and color tools.

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

## Panel Sections

### Action Buttons

| Button | What it does |
|---|---|
| **Apply CSS** | Writes `varun-architectus.css` with current settings |
| **Reload** | Reloads the VS Code window |
| **Reset** | Resets all CSS settings to defaults |
| **Pick Colors from Active Theme** | Pulls colors from the current VS Code theme and applies |

### Background Console

Glow and animation effects. Toggle in the section header writes the full CSS (on) or clears it (off) — state persists across reloads. Run **Reload Custom CSS and JS** after toggling to apply.

| Sub-section | Controls |
|---|---|
| **Custom Background Text** | Front/back text, opacity, speed, size, glow/extrude color, glow intensity |
| **Glitch** | Enable, intensity, frequency, typing glitch on keypress |
| **Syntax Glow** | Per-token colors: strings, types, keywords, numbers, functions, variables, errors, comments |
| **Cursor** | Primary/secondary color, pulse speed |
| **Effects** | Scanlines, scrollbar colors |

### Quick Commands

Configurable one-click terminal commands. Add a label and command, click **Run** to execute in the integrated terminal. Commands are saved globally across workspaces.

### Focus Mode

Individual toggles to show/hide Activity Bar, Status Bar, Minimap, Breadcrumbs, and Panel. Changes apply immediately via VS Code settings.

### Font Controls

Adjust editor font family, size, line height, and letter spacing live. **Reset to VS Code defaults** clears all overrides.

### Scratch Pad

Persistent text area saved per workspace. Auto-saves 500ms after you stop typing. Good for notes, temp values, snippets you don't want to commit.

### Color Tools

Color picker with instant HEX / RGB / HSL readout. Click **Copy** next to any format to copy to clipboard.

## Development

Files in `~/.vscode/extensions/varun.ryze-controls-1.0.0/` are symlinked to this repo. Edit here, push from here.

```bash
# Repackage after changes
cd ~/architectus
vsce package --allow-missing-repository --no-dependencies
```
