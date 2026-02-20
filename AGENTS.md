# Project Guidelines

## Architecture

Static VS Code color theme extension with no build step. All theme definitions live as standalone JSON files in `themes/`. The extension manifest [`package.json`](package.json) registers each theme under `contributes.themes`.

| File | Theme label | UI kind |
|------|-------------|---------|
| `themes/cursor-dark-color-theme.json` | Cursor Dark | `vs-dark` |
| `themes/cursor-light-color-theme.json` | Cursor Light | `vs` |
| `themes/Cursor Dark Midnight-color-theme.json` | Cursor Dark Midnight | `vs-dark` |
| `themes/Cursor Dark High Contrast-color-theme.json` | Cursor Dark High Contrast | `hc-black` |

## Code Style

Theme JSON files use 4-space indentation. Color values use uppercase hex with optional alpha suffix (e.g. `#E4E4E4EB`, `#88C0D066`). The top-level keys are `name`, `colors` (workbench tokens), and `tokenColors` (syntax tokens).

## Build and Test

No build step required. To install locally:

```sh
# Symlink or copy the folder into the VS Code extensions directory
cp -r . ~/.vscode/extensions/local.cursor-official-themes-1.0.0
```

Reload VS Code and select a theme via **Preferences: Color Theme**.

## Project Conventions

- Adding a new theme: create a JSON file in `themes/`, then add an entry to the `contributes.themes` array in `package.json`.
- The `name` field inside each theme JSON is the internal display name and may differ from the `label` in `package.json`.
- No package manager, linter, or test suite is configured — edits are direct JSON modifications.

## Official Documentation

Always consult the official VS Code docs when editing theme tokens or the extension manifest:

| Topic | URL |
|-------|-----|
| Color Theme guide (overview, packaging) | https://code.visualstudio.com/api/extension-guides/color-theme |
| Workbench color reference (`colors` keys) | https://code.visualstudio.com/api/references/theme-color |
| Syntax highlight / TextMate tokens (`tokenColors`) | https://code.visualstudio.com/api/language-extensions/syntax-highlight-guide |
| `contributes.themes` manifest reference | https://code.visualstudio.com/api/references/contribution-points#contributes.themes |

When adding or changing a `colors` key, verify the token name against the **Workbench color reference** above. When editing `tokenColors` scopes, cross-check with the **Syntax Highlight guide**.
