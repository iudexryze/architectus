# Architectus

A developer toolkit living in your VS Code sidebar. Not just a background styler — Architectus puts the tools you reach for every day (path copying, git actions, snippets, regex testing, and more) one click away, alongside its signature glow and animation engine.

## Requirements

- [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) extension (for Background Console features)
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
4. For background effects: click **Apply CSS**, then run **Reload Custom CSS and JS** from the command palette

## Panel Sections

### Action Buttons

| Button | What it does |
|---|---|
| **Apply CSS** | Writes `varun-architectus.css` with current settings |
| **Reload** | Reloads the VS Code window |
| **Reset** | Resets all CSS settings to defaults |
| **Pick Colors from Active Theme** | Pulls colors from the current VS Code theme |

### Background Console

Glow and animation effects for the editor. Toggle in the section header writes the full CSS (on) or clears it (off) — state persists across reloads. Run **Reload Custom CSS and JS** after toggling to apply.

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

### Path Utils

One-click copy of the active file's path in four forms:

| Button | Output |
|---|---|
| **Copy Absolute** | Full filesystem path |
| **Copy Relative** | Path relative to workspace root |
| **Copy Filename** | Just the filename with extension |
| **Copy Directory** | Parent directory path |

### TODO Scanner

Scans your workspace for `TODO`, `FIXME`, `HACK`, `NOTE`, and `XXX` comments across all common source file types. Results show the tag type, file, line number, and comment text. Excludes `node_modules`, `.git`, `dist`, `build`, and similar noise directories.

### Git Quick Actions

Run the most common git operations without leaving the sidebar:

| Button | Command |
|---|---|
| **git status** | Shows working tree status in terminal |
| **git add -A** | Stages all changes |
| **git pull** | Pulls from remote |
| **git push** | Pushes to remote |
| **Commit** | `git commit -m "<your message>"` — type message + Enter or click |

### Snippet Bank

Save reusable text snippets with labels. Click **Insert** to paste the snippet at your cursor in the active editor (replaces selection if text is selected). Snippets are saved globally across workspaces.

### Text Transform

Paste or type text and transform it instantly:

| Transform | Result |
|---|---|
| UPPER CASE / lower case / Title Case | Case conversion |
| camelCase / snake_case / kebab-case / SCREAMING_SNAKE | Identifier format conversion |
| Trim Whitespace | Strips leading/trailing space, collapses internal runs |
| URL Encode / URL Decode | `encodeURIComponent` / `decodeURIComponent` |
| Base64 Encode / Base64 Decode | UTF-8 safe encode/decode |

### Timestamp Tools

Live epoch counter in the section header. Two converters:

- **Unix timestamp → ISO date** (auto-detects seconds vs milliseconds)
- **ISO date string → Unix epoch** (returns both seconds and milliseconds)

### Regex Tester

Live regex matching as you type. Enter a pattern (with or without surrounding slashes) and optional flags, then a test string. Matches are highlighted inline. Shows match count and error messages for invalid patterns.

## Development

Files in `~/.vscode/extensions/varun.ryze-controls-1.0.0/` are symlinked to this repo. Edit here, push from here.

```bash
# Repackage after changes
cd ~/architectus
vsce package --allow-missing-repository --no-dependencies
```
