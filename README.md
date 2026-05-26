# Architectus

Glow animations and a control panel sidebar for VS Code.

## Setup

1. Install the extension (`architectus.vsix`)
2. Run once to fix file ownership (required for injection):
   ```bash
   sudo bash ~/ryze-ownership-setup.sh
   ```
3. Open the **Architectus** panel from the activity bar
4. Click **Apply CSS** to write the CSS file
5. Run **Architectus: Enable CSS** from the command palette to inject into VS Code
6. Reload the window when prompted

## Commands

| Command | What it does |
|---|---|
| `Architectus: Enable CSS` | Inject CSS + typing script into VS Code and prompt to reload |
| `Architectus: Disable CSS` | Remove injection and prompt to reload |

## Panel Controls

| Section | Controls |
|---|---|
| **RYZE Background** | Front/back text, opacity, rotation speed, size, glow color, extrude color, glow intensity |
| **Glitch** | Enable/disable, intensity, frequency, typing glitch on keypress |
| **Syntax Glow** | Per-token colors: strings, types, keywords, numbers, functions, variables, errors, comments |
| **Cursor** | Primary/secondary color, pulse speed |
| **Effects** | Scanlines toggle + opacity, scrollbar color + hover color |

The **Apply CSS** button writes `~/.vscode/varun-architectus.css` only — it does not reload or re-inject. Use the command palette to enable/disable injection separately.

## Development

Files in `~/.vscode/extensions/varun.ryze-controls-1.0.0/` are symlinked to this repo. Edit here, push from here.

```bash
# Repackage after changes
cd ~/architectus
vsce package --allow-missing-repository --no-dependencies
```

## How the injection works

The extension patches VS Code's `workbench.desktop.main.html` at:
```
$VSCODE_APP_ROOT/out/vs/workbench/workbench.desktop.main.html
```

It injects a `<link>` to the generated CSS file and a small `<script>` that adds `body.ryze-typing` on keypress, triggering the harder typing glitch animation.

VS Code auto-updates reset file ownership. The `code` shell wrapper in `.zshrc` runs `sudo /usr/local/sbin/ryze-fix-perms` silently before every launch to keep permissions correct.
