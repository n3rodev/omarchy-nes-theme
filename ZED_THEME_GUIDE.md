# Zed IDE Theme Guide - NES-Inspired Theme

A comprehensive guide to creating a Zed IDE theme using the Omarchy NES color palette.

---

## Table of Contents

1. [Introduction](#introduction)
2. [The NES Color Palette](#the-nes-color-palette)
3. [Zed Theme Structure](#zed-theme-structure)
4. [Creating Your Theme](#creating-your-theme)
5. [Complete Theme Example](#complete-theme-example)
6. [Installation & Testing](#installation--testing)
7. [Theme Overrides](#theme-overrides)
8. [Publishing Your Theme](#publishing-your-theme)

---

## Introduction

Zed is a modern, high-performance code editor built with Rust. Themes in Zed are defined using JSON files and follow a specific schema that allows for comprehensive customization of both UI elements and syntax highlighting.

**Key Features:**
- **JSON-based**: Themes use structured JSON with schema validation
- **Multi-theme support**: One file can contain multiple theme variants (dark/light)
- **Player colors**: Unique collaborative editing cursor colors
- **Real-time updates**: Themes are automatically detected when added to the themes directory

---

## The NES Color Palette

The Omarchy NES theme uses a minimalist palette inspired by the classic Nintendo Entertainment System:

```json
{
  "background":     "#101010",  // Near-black background
  "foreground":     "#CECFC9",  // Light grey text
  "primaryAccent":  "#D93F37",  // Red accent
  "brightAccent":   "#DA0F0F",  // Bright red
  "secondary":      "#9A9D9A",  // Medium grey
  "white":          "#FFFFFF",  // Pure white (highlights only)
  "black":          "#000000"   // True black
}
```

**Color Usage Philosophy:**
- **#101010** - All backgrounds (editor, surfaces, panels)
- **#CECFC9** - Primary text, normal code
- **#D93F37** - Important elements, keywords, selections, borders
- **#DA0F0F** - Errors, warnings, critical highlights
- **#9A9D9A** - Comments, borders, inactive elements
- **#FFFFFF** - Maximum contrast (active elements, highlights)
- **#000000** - True black (terminal, deep shadows)

---

## Zed Theme Structure

Zed themes follow the official schema at `https://zed.dev/schema/themes/v0.2.0.json`.

### Basic Structure

```json
{
  "$schema": "https://zed.dev/schema/themes/v0.2.0.json",
  "name": "Omarchy NES",
  "author": "Your Name",
  "themes": [
    {
      "name": "Omarchy NES Dark",
      "appearance": "dark",
      "style": {
        // UI colors
      },
      "players": [
        // Collaborative cursor colors
      ],
      "syntax": {
        // Code syntax highlighting
      }
    }
  ]
}
```

### Key Sections

**1. Metadata:**
- `$schema` - References the Zed theme schema
- `name` - Theme family name
- `author` - Your name or organization

**2. Themes Array:**
Each theme object contains:
- `name` - Specific theme variant name
- `appearance` - "dark" or "light"
- `style` - UI element colors
- `players` - Collaborative cursor colors (8 players)
- `syntax` - Code syntax highlighting rules

---

## Creating Your Theme

### Step 1: Create the Theme Directory

```bash
# macOS / Linux
mkdir -p ~/.config/zed/themes

# Windows
mkdir %USERPROFILE%\AppData\Roaming\Zed\themes\
```

### Step 2: Create the Theme File

Create a file named `omarchy-nes.json` in the themes directory:

```bash
# macOS / Linux
touch ~/.config/zed/themes/omarchy-nes.json

# Windows
type nul > %USERPROFILE%\AppData\Roaming\Zed\themes\omarchy-nes.json
```

### Step 3: Add the Theme JSON

See the [Complete Theme Example](#complete-theme-example) section below.

---

## Complete Theme Example

Create `omarchy-nes.json` with the following content:

```json
{
  "$schema": "https://zed.dev/schema/themes/v0.2.0.json",
  "name": "Omarchy NES",
  "author": "Omarchy Project",
  "themes": [
    {
      "name": "Omarchy NES Dark",
      "appearance": "dark",
      "style": {
        "border": "#9A9D9A",
        "border.variant": "#9A9D9A80",
        "border.focused": "#D93F37",
        "border.selected": "#D93F37",
        "border.transparent": "#00000000",
        "border.disabled": "#9A9D9A40",
        "elevated_surface.background": "#101010",
        "surface.background": "#101010",
        "background": "#101010",
        "element.background": "#101010",
        "element.hover": "#9A9D9A20",
        "element.active": "#D93F3740",
        "element.selected": "#D93F37",
        "element.disabled": "#9A9D9A40",
        "drop_target.background": "#D93F3760",
        "ghost_element.background": "#00000000",
        "ghost_element.hover": "#9A9D9A20",
        "ghost_element.active": "#D93F3740",
        "ghost_element.selected": "#D93F37",
        "ghost_element.disabled": "#9A9D9A40",
        "text": "#CECFC9",
        "text.muted": "#9A9D9A",
        "text.placeholder": "#9A9D9A",
        "text.disabled": "#9A9D9A60",
        "text.accent": "#D93F37",
        "icon": "#CECFC9",
        "icon.muted": "#9A9D9A",
        "icon.disabled": "#9A9D9A60",
        "icon.placeholder": "#9A9D9A",
        "icon.accent": "#D93F37",
        "status_bar.background": "#101010",
        "title_bar.background": "#101010",
        "title_bar.inactive_background": "#101010",
        "toolbar.background": "#101010",
        "tab_bar.background": "#101010",
        "tab.inactive_background": "#101010",
        "tab.active_background": "#101010",
        "search.match_background": "#D93F3760",
        "panel.background": "#101010",
        "panel.focused_border": "#D93F37",
        "pane.focused_border": "#D93F37",
        "scrollbar.thumb.background": "#9A9D9A40",
        "scrollbar.thumb.hover_background": "#9A9D9A60",
        "scrollbar.thumb.border": "#00000000",
        "scrollbar.track.background": "#00000000",
        "scrollbar.track.border": "#00000000",
        "editor.foreground": "#CECFC9",
        "editor.background": "#101010",
        "editor.gutter.background": "#101010",
        "editor.subheader.background": "#101010",
        "editor.active_line.background": "#FFFFFF08",
        "editor.highlighted_line.background": "#D93F3720",
        "editor.line_number": "#9A9D9A",
        "editor.active_line_number": "#D93F37",
        "editor.invisible": "#9A9D9A40",
        "editor.wrap_guide": "#9A9D9A40",
        "editor.active_wrap_guide": "#9A9D9A60",
        "editor.document_highlight.read_background": "#9A9D9A20",
        "editor.document_highlight.write_background": "#D93F3740",
        "link_text.hover": "#D93F37",
        "conflict": "#DA0F0F",
        "conflict.background": "#DA0F0F20",
        "conflict.border": "#DA0F0F",
        "created": "#9A9D9A",
        "created.background": "#9A9D9A20",
        "created.border": "#9A9D9A",
        "deleted": "#DA0F0F",
        "deleted.background": "#DA0F0F20",
        "deleted.border": "#DA0F0F",
        "error": "#DA0F0F",
        "error.background": "#DA0F0F20",
        "error.border": "#DA0F0F",
        "hidden": "#9A9D9A60",
        "hidden.background": "#101010",
        "hidden.border": "#9A9D9A40",
        "hint": "#9A9D9A",
        "hint.background": "#9A9D9A20",
        "hint.border": "#9A9D9A",
        "ignored": "#9A9D9A60",
        "ignored.background": "#101010",
        "ignored.border": "#9A9D9A40",
        "info": "#D93F37",
        "info.background": "#D93F3720",
        "info.border": "#D93F37",
        "modified": "#D93F37",
        "modified.background": "#D93F3720",
        "modified.border": "#D93F37",
        "predictive": "#9A9D9A80",
        "predictive.background": "#9A9D9A20",
        "predictive.border": "#9A9D9A",
        "renamed": "#D93F37",
        "renamed.background": "#D93F3720",
        "renamed.border": "#D93F37",
        "success": "#9A9D9A",
        "success.background": "#9A9D9A20",
        "success.border": "#9A9D9A",
        "unreachable": "#9A9D9A60",
        "unreachable.background": "#101010",
        "unreachable.border": "#9A9D9A40",
        "warning": "#DA0F0F",
        "warning.background": "#DA0F0F20",
        "warning.border": "#DA0F0F",
        "players": [
          {
            "cursor": "#D93F37",
            "background": "#D93F37",
            "selection": "#D93F3740"
          },
          {
            "cursor": "#DA0F0F",
            "background": "#DA0F0F",
            "selection": "#DA0F0F40"
          },
          {
            "cursor": "#9A9D9A",
            "background": "#9A9D9A",
            "selection": "#9A9D9A40"
          },
          {
            "cursor": "#CECFC9",
            "background": "#CECFC9",
            "selection": "#CECFC940"
          },
          {
            "cursor": "#D93F37",
            "background": "#D93F37",
            "selection": "#D93F3760"
          },
          {
            "cursor": "#DA0F0F",
            "background": "#DA0F0F",
            "selection": "#DA0F0F60"
          },
          {
            "cursor": "#9A9D9A",
            "background": "#9A9D9A",
            "selection": "#9A9D9A60"
          },
          {
            "cursor": "#FFFFFF",
            "background": "#FFFFFF",
            "selection": "#FFFFFF40"
          }
        ],
        "terminal.background": "#101010",
        "terminal.foreground": "#CECFC9",
        "terminal.bright_foreground": "#FFFFFF",
        "terminal.dim_foreground": "#9A9D9A",
        "terminal.ansi.black": "#000000",
        "terminal.ansi.red": "#D93F37",
        "terminal.ansi.green": "#9A9D9A",
        "terminal.ansi.yellow": "#9A9D9A",
        "terminal.ansi.blue": "#9A9D9A",
        "terminal.ansi.magenta": "#D93F37",
        "terminal.ansi.cyan": "#9A9D9A",
        "terminal.ansi.white": "#CECFC9",
        "terminal.ansi.bright_black": "#9A9D9A",
        "terminal.ansi.bright_red": "#DA0F0F",
        "terminal.ansi.bright_green": "#CECFC9",
        "terminal.ansi.bright_yellow": "#CECFC9",
        "terminal.ansi.bright_blue": "#CECFC9",
        "terminal.ansi.bright_magenta": "#DA0F0F",
        "terminal.ansi.bright_cyan": "#CECFC9",
        "terminal.ansi.bright_white": "#FFFFFF",
        "terminal.ansi.dim_black": "#000000",
        "terminal.ansi.dim_red": "#D93F3780",
        "terminal.ansi.dim_green": "#9A9D9A80",
        "terminal.ansi.dim_yellow": "#9A9D9A80",
        "terminal.ansi.dim_blue": "#9A9D9A80",
        "terminal.ansi.dim_magenta": "#D93F3780",
        "terminal.ansi.dim_cyan": "#9A9D9A80",
        "terminal.ansi.dim_white": "#9A9D9A"
      },
      "syntax": {
        "attribute": {
          "color": "#9A9D9A"
        },
        "boolean": {
          "color": "#D93F37"
        },
        "comment": {
          "color": "#9A9D9A",
          "font_style": "italic"
        },
        "comment.doc": {
          "color": "#9A9D9A",
          "font_style": "italic"
        },
        "constant": {
          "color": "#D93F37"
        },
        "constructor": {
          "color": "#CECFC9"
        },
        "embedded": {
          "color": "#CECFC9"
        },
        "emphasis": {
          "color": "#CECFC9",
          "font_style": "italic"
        },
        "emphasis.strong": {
          "color": "#CECFC9",
          "font_weight": 700
        },
        "enum": {
          "color": "#D93F37"
        },
        "function": {
          "color": "#CECFC9"
        },
        "function.method": {
          "color": "#CECFC9"
        },
        "hint": {
          "color": "#9A9D9A",
          "font_weight": 700
        },
        "keyword": {
          "color": "#D93F37",
          "font_weight": 700
        },
        "label": {
          "color": "#D93F37"
        },
        "link_text": {
          "color": "#D93F37",
          "font_style": "underline"
        },
        "link_uri": {
          "color": "#9A9D9A"
        },
        "number": {
          "color": "#CECFC9"
        },
        "operator": {
          "color": "#9A9D9A"
        },
        "predictive": {
          "color": "#9A9D9A80",
          "font_style": "italic"
        },
        "preproc": {
          "color": "#D93F37"
        },
        "primary": {
          "color": "#CECFC9"
        },
        "property": {
          "color": "#CECFC9"
        },
        "punctuation": {
          "color": "#9A9D9A"
        },
        "punctuation.bracket": {
          "color": "#9A9D9A"
        },
        "punctuation.delimiter": {
          "color": "#9A9D9A"
        },
        "punctuation.list_marker": {
          "color": "#9A9D9A"
        },
        "punctuation.special": {
          "color": "#D93F37"
        },
        "string": {
          "color": "#CECFC9"
        },
        "string.escape": {
          "color": "#D93F37"
        },
        "string.regex": {
          "color": "#D93F37"
        },
        "string.special": {
          "color": "#D93F37"
        },
        "string.special.symbol": {
          "color": "#D93F37"
        },
        "tag": {
          "color": "#D93F37"
        },
        "text.literal": {
          "color": "#CECFC9"
        },
        "title": {
          "color": "#D93F37",
          "font_weight": 700
        },
        "type": {
          "color": "#D93F37"
        },
        "variable": {
          "color": "#CECFC9"
        },
        "variable.special": {
          "color": "#D93F37"
        },
        "variant": {
          "color": "#D93F37"
        }
      }
    }
  ]
}
```

---

## Installation & Testing

### Local Installation

1. **Copy the theme file** to your Zed themes directory:

   **macOS / Linux:**
   ```bash
   cp omarchy-nes.json ~/.config/zed/themes/
   ```

   **Windows:**
   ```powershell
   copy omarchy-nes.json %USERPROFILE%\AppData\Roaming\Zed\themes\
   ```

2. **Restart Zed** or wait for automatic detection

3. **Select the theme:**
   - Open Zed settings (`Cmd+,` on macOS, `Ctrl+,` on Windows/Linux)
   - Search for "theme"
   - Select "Omarchy NES Dark" from the dropdown

### Alternative: Theme Selector

1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Type "theme selector"
3. Choose "Omarchy NES Dark"

### Verification

Test your theme with different file types:
- JavaScript/TypeScript
- Python
- Rust
- HTML/CSS
- Markdown
- JSON

Check that:
- Background is consistently `#101010`
- Text is readable with `#CECFC9`
- Keywords and types are highlighted in red (`#D93F37`)
- Comments are grey and italic (`#9A9D9A`)
- Terminal colors match other configurations

---

## Theme Overrides

You can customize specific theme values without creating a new theme file using `settings.json`:

### Override Syntax Colors

```json
{
  "theme_overrides": {
    "Omarchy NES Dark": {
      "syntax": {
        "comment": {
          "color": "#808080",
          "font_style": "italic"
        },
        "keyword": {
          "color": "#FF0000",
          "font_weight": 700
        }
      }
    }
  }
}
```

### Override UI Colors

```json
{
  "theme_overrides": {
    "Omarchy NES Dark": {
      "editor.background": "#0A0A0A",
      "editor.active_line.background": "#1A1A1A"
    }
  }
}
```

### Available Syntax Captures

Common syntax elements you can override:
- `comment`, `comment.doc`
- `string`, `string.escape`, `string.regex`
- `keyword`
- `function`, `function.method`
- `type`, `enum`, `variant`
- `constant`, `boolean`, `number`
- `operator`, `punctuation`
- `variable`, `variable.special`
- `property`, `attribute`
- `tag`, `label`
- `title`, `emphasis`

---

## Publishing Your Theme

### Option 1: Share as JSON File

Simply share your `omarchy-nes.json` file. Users can:
1. Download the file
2. Copy it to their themes directory
3. Restart Zed

### Option 2: Create a Theme Extension

For wider distribution, create a Zed extension:

1. **Create extension structure:**
   ```
   omarchy-nes-theme/
   ├── extension.toml
   └── themes/
       └── omarchy-nes.json
   ```

2. **Create `extension.toml`:**
   ```toml
   id = "omarchy-nes-theme"
   name = "Omarchy NES Theme"
   description = "A retro NES-inspired theme with red, black, and grey aesthetics"
   version = "1.0.0"
   schema_version = 1
   authors = ["Your Name <your.email@example.com>"]
   repository = "https://github.com/yourusername/omarchy-nes-zed-theme"
   ```

3. **Move theme file** to `themes/` directory

4. **Publish to Zed Extensions:**
   - Follow the official [Zed Extension Publishing Guide](https://zed.dev/docs/extensions)
   - Submit a PR to the Zed extensions repository

### Option 3: GitHub Repository

Create a GitHub repository with:
- Theme JSON file
- README with installation instructions
- Screenshots
- License (e.g., MIT)

Users can clone and install manually.

---

## Customization Tips

### Color Opacity

Add transparency using the last two hex digits (alpha channel):

```json
"element.hover": "#9A9D9A20"  // 20 = ~12% opacity
"selection": "#D93F3740"      // 40 = ~25% opacity
"border": "#9A9D9A80"         // 80 = ~50% opacity
```

**Opacity Reference:**
- `20` = 12.5% opacity
- `40` = 25% opacity
- `60` = 37.5% opacity
- `80` = 50% opacity
- `AA` = 66.7% opacity
- `FF` = 100% opacity

### Font Styles

Available font style options:
- `"font_style": "normal"` - Regular text
- `"font_style": "italic"` - Italic text
- `"font_weight": 700` - Bold text
- Combined: `"font_style": "italic", "font_weight": 700`

### Creating Light Variant

To create a light theme variant:

1. Duplicate the theme object in the `themes` array
2. Change `"appearance": "light"`
3. Invert colors:
   - Background: Use light color (e.g., `#F0F0F0`)
   - Foreground: Use dark color (e.g., `#101010`)
   - Keep accents similar but adjust for contrast

---

## Terminal Color Consistency

The theme's terminal colors match the existing terminal configurations:

| Color | Alacritty | Ghostty | Zed | Match |
|-------|-----------|---------|-----|-------|
| Black | #000000 | #000000 | #000000 | ✅ |
| Red | #D93F37 | #D93F37 | #D93F37 | ✅ |
| Green | #9A9D9A | #9A9D9A | #9A9D9A | ✅ |
| Yellow | #9A9D9A | #9A9D9A | #9A9D9A | ✅ |
| Blue | #9A9D9A | #9A9D9A | #9A9D9A | ✅ |
| Magenta | #D93F37 | #D93F37 | #D93F37 | ✅ |
| Cyan | #9A9D9A | #9A9D9A | #9A9D9A | ✅ |
| White | #CECFC9 | #CECFC9 | #CECFC9 | ✅ |
| Bright Black | #9A9D9A | #9A9D9A | #9A9D9A | ✅ |
| Bright Red | #DA0F0F | #DA0F0F | #DA0F0F | ✅ |
| Bright Green | #CECFC9 | #CECFC9 | #CECFC9 | ✅ |
| Bright Yellow | #CECFC9 | #CECFC9 | #CECFC9 | ✅ |
| Bright Blue | #CECFC9 | #CECFC9 | #CECFC9 | ✅ |
| Bright Magenta | #DA0F0F | #DA0F0F | #DA0F0F | ✅ |
| Bright Cyan | #CECFC9 | #CECFC9 | #CECFC9 | ✅ |
| Bright White | #FFFFFF | #FFFFFF | #FFFFFF | ✅ |

---

## Troubleshooting

**Theme not appearing?**
- Verify the file is in the correct directory
- Restart Zed completely
- Check JSON syntax (use a JSON validator)
- Ensure `$schema` points to the correct URL

**Colors not applying?**
- Check color format (must be `#RRGGBB` or `#RRGGBBAA`)
- Verify property names match the schema
- Check for typos in hex codes

**Syntax highlighting issues?**
- Use the exact syntax capture names from the schema
- Test with different file types
- Check that syntax objects have `color` property

---

## Additional Resources

### Official Documentation

- [Zed Themes Documentation](https://zed.dev/docs/themes)
- [Zed Theme Extensions](https://zed.dev/docs/extensions/themes)
- [Zed Theme Schema](https://zed.dev/schema/themes/v0.2.0.json)

### Reference Themes

- [One Dark (Official)](https://github.com/zed-industries/zed/blob/main/assets/themes/one/one.json)
- [Zed Extensions Directory](https://zed.dev/extensions)
- [Community Themes Discussion](https://github.com/zed-industries/zed/discussions/7337)

### Tools

- **JSON Validator**: Verify your theme syntax
- **Zed Theme Previewer**: https://zedtheme.com/
- **Color Picker**: Use Zed's built-in color picker in JSON files

---

## Related Projects

- [Omarchy NES Theme](https://github.com/bjarneo/omarchy-nes-theme) - Multi-app theme collection
- [nes.nvim](https://github.com/bjarneo/nes.nvim) - Neovim colorscheme
- VS Code Theme - See VSCODE_THEME_GUIDE.md in this repository

---

*Created for the Omarchy NES Theme project*
*Author: [@iamdothash](https://x.com/iamdothash)*
*License: MIT*
