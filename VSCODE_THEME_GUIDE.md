# VS Code Theme Guide - NES-Inspired Theme

A comprehensive guide to creating a Visual Studio Code theme using the Omarchy NES color palette.

---

## Table of Contents

1. [Introduction](#introduction)
2. [The NES Color Palette](#the-nes-color-palette)
3. [VS Code Theme Structure](#vs-code-theme-structure)
4. [Creating Your Theme](#creating-your-theme)
5. [Complete Theme Example](#complete-theme-example)
6. [Installation & Testing](#installation--testing)
7. [Customization Tips](#customization-tips)
8. [Publishing Your Theme](#publishing-your-theme)

---

## Introduction

VS Code themes consist of two main components:
- **UI Colors**: Editor interface, sidebars, status bar, etc.
- **Syntax Colors**: Code highlighting (tokens, strings, keywords, etc.)

This guide will walk you through creating a complete NES-inspired theme that maintains the retro aesthetic across all parts of VS Code.

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
- **#101010** - All backgrounds (editor, sidebar, panels)
- **#CECFC9** - Primary text, normal code
- **#D93F37** - Important elements, keywords, selections
- **#DA0F0F** - Errors, warnings, critical highlights
- **#9A9D9A** - Comments, borders, inactive elements
- **#FFFFFF** - Maximum contrast (active line, find matches)
- **#000000** - Deep shadows, complete absence

---

## VS Code Theme Structure

VS Code themes are defined in JSON format with two main sections:

```json
{
  "name": "Omarchy NES",
  "type": "dark",
  "colors": {
    // UI element colors (editor, sidebar, terminal, etc.)
  },
  "tokenColors": [
    // Syntax highlighting rules
  ]
}
```

### Key Color Categories

**Editor Colors:**
- `editor.background` - Main editor background
- `editor.foreground` - Default text color
- `editor.lineHighlightBackground` - Active line highlight
- `editor.selectionBackground` - Selected text background

**UI Colors:**
- `sideBar.background` - File explorer background
- `activityBar.background` - Left icon bar
- `statusBar.background` - Bottom status bar
- `terminal.background` - Integrated terminal

**Syntax Colors:**
- Keywords (if, function, class, etc.)
- Strings and characters
- Comments
- Variables and functions
- Operators and punctuation

---

## Creating Your Theme

### Step 1: Set Up Your Extension

Create a new directory for your theme:

```bash
mkdir omarchy-nes-vscode-theme
cd omarchy-nes-vscode-theme
```

Create the basic structure:

```
omarchy-nes-vscode-theme/
├── package.json
├── themes/
│   └── omarchy-nes-color-theme.json
└── README.md
```

### Step 2: Create package.json

```json
{
  "name": "omarchy-nes-theme",
  "displayName": "Omarchy NES Theme",
  "description": "A retro NES-inspired theme with red, black, and grey aesthetics",
  "version": "1.0.0",
  "publisher": "your-name",
  "icon": "images/icon.png",
  "license": "MIT",
  "engines": {
    "vscode": "^1.80.0"
  },
  "categories": [
    "Themes"
  ],
  "contributes": {
    "themes": [
      {
        "label": "Omarchy NES",
        "uiTheme": "vs-dark",
        "path": "./themes/omarchy-nes-color-theme.json"
      }
    ]
  },
  "keywords": [
    "theme",
    "dark theme",
    "nes",
    "retro",
    "red",
    "minimalist"
  ],
  "repository": {
    "type": "git",
    "url": "https://github.com/yourusername/omarchy-nes-vscode-theme"
  }
}
```

**Optional Fields Explained:**
- `icon`: Path to a 128x128px PNG icon for the extension marketplace
- `license`: License identifier (e.g., "MIT", "Apache-2.0")
- `$schema`: Added to theme JSON for IntelliSense support when editing

### Step 3: Create the Theme File

See the [Complete Theme Example](#complete-theme-example) section below for the full theme JSON.

---

## Complete Theme Example

Create `themes/omarchy-nes-color-theme.json`:

```json
{
  "$schema": "vscode://schemas/color-theme",
  "name": "Omarchy NES",
  "type": "dark",
  "colors": {
    // === EDITOR ===
    "editor.background": "#101010",
    "editor.foreground": "#CECFC9",
    "editorLineNumber.foreground": "#9A9D9A",
    "editorLineNumber.activeForeground": "#D93F37",
    "editorCursor.foreground": "#DA0F0F",
    "editor.selectionBackground": "#D93F3740",
    "editor.inactiveSelectionBackground": "#D93F3720",
    "editor.lineHighlightBackground": "#FFFFFF08",
    "editor.lineHighlightBorder": "#00000000",
    "editorWhitespace.foreground": "#9A9D9A40",
    "editorIndentGuide.background": "#9A9D9A20",
    "editorIndentGuide.activeBackground": "#9A9D9A60",
    "editorRuler.foreground": "#9A9D9A40",

    // === EDITOR WIDGETS ===
    "editorWidget.background": "#101010",
    "editorWidget.border": "#9A9D9A",
    "editorSuggestWidget.background": "#101010",
    "editorSuggestWidget.border": "#9A9D9A",
    "editorSuggestWidget.foreground": "#CECFC9",
    "editorSuggestWidget.selectedBackground": "#D93F3740",
    "editorHoverWidget.background": "#101010",
    "editorHoverWidget.border": "#9A9D9A",

    // === FIND/REPLACE ===
    "editor.findMatchBackground": "#D93F3760",
    "editor.findMatchHighlightBackground": "#D93F3740",
    "editor.findRangeHighlightBackground": "#9A9D9A20",
    "searchEditor.findMatchBackground": "#D93F3760",

    // === GUTTER ===
    "editorGutter.background": "#101010",
    "editorGutter.modifiedBackground": "#D93F37",
    "editorGutter.addedBackground": "#9A9D9A",
    "editorGutter.deletedBackground": "#DA0F0F",

    // === DIFF EDITOR ===
    "diffEditor.insertedTextBackground": "#9A9D9A20",
    "diffEditor.removedTextBackground": "#DA0F0F20",

    // === ACTIVITY BAR ===
    "activityBar.background": "#101010",
    "activityBar.foreground": "#CECFC9",
    "activityBar.inactiveForeground": "#9A9D9A",
    "activityBar.border": "#9A9D9A40",
    "activityBarBadge.background": "#D93F37",
    "activityBarBadge.foreground": "#FFFFFF",

    // === SIDE BAR ===
    "sideBar.background": "#101010",
    "sideBar.foreground": "#CECFC9",
    "sideBar.border": "#9A9D9A40",
    "sideBarTitle.foreground": "#CECFC9",
    "sideBarSectionHeader.background": "#101010",
    "sideBarSectionHeader.foreground": "#CECFC9",
    "sideBarSectionHeader.border": "#9A9D9A40",

    // === LISTS AND TREES ===
    "list.activeSelectionBackground": "#D93F3740",
    "list.activeSelectionForeground": "#FFFFFF",
    "list.inactiveSelectionBackground": "#D93F3720",
    "list.inactiveSelectionForeground": "#CECFC9",
    "list.hoverBackground": "#9A9D9A20",
    "list.hoverForeground": "#CECFC9",
    "list.focusBackground": "#D93F3740",
    "list.focusForeground": "#FFFFFF",
    "list.highlightForeground": "#DA0F0F",

    // === STATUS BAR ===
    "statusBar.background": "#101010",
    "statusBar.foreground": "#CECFC9",
    "statusBar.border": "#9A9D9A40",
    "statusBar.debuggingBackground": "#D93F37",
    "statusBar.debuggingForeground": "#FFFFFF",
    "statusBar.noFolderBackground": "#101010",
    "statusBarItem.prominentBackground": "#D93F37",
    "statusBarItem.prominentHoverBackground": "#DA0F0F",

    // === TITLE BAR ===
    "titleBar.activeBackground": "#101010",
    "titleBar.activeForeground": "#CECFC9",
    "titleBar.inactiveBackground": "#101010",
    "titleBar.inactiveForeground": "#9A9D9A",
    "titleBar.border": "#9A9D9A40",

    // === TABS ===
    "editorGroupHeader.tabsBackground": "#101010",
    "editorGroupHeader.tabsBorder": "#9A9D9A40",
    "tab.activeBackground": "#101010",
    "tab.activeForeground": "#CECFC9",
    "tab.activeBorder": "#D93F37",
    "tab.activeBorderTop": "#00000000",
    "tab.inactiveBackground": "#101010",
    "tab.inactiveForeground": "#9A9D9A",
    "tab.border": "#9A9D9A40",
    "tab.hoverBackground": "#9A9D9A20",
    "tab.hoverForeground": "#CECFC9",

    // === PANEL (Terminal, Output, etc.) ===
    "panel.background": "#101010",
    "panel.border": "#9A9D9A40",
    "panelTitle.activeBorder": "#D93F37",
    "panelTitle.activeForeground": "#CECFC9",
    "panelTitle.inactiveForeground": "#9A9D9A",

    // === TERMINAL ===
    "terminal.background": "#101010",
    "terminal.foreground": "#CECFC9",
    "terminal.ansiBlack": "#000000",
    "terminal.ansiRed": "#D93F37",
    "terminal.ansiGreen": "#9A9D9A",
    "terminal.ansiYellow": "#9A9D9A",
    "terminal.ansiBlue": "#9A9D9A",
    "terminal.ansiMagenta": "#D93F37",
    "terminal.ansiCyan": "#9A9D9A",
    "terminal.ansiWhite": "#CECFC9",
    "terminal.ansiBrightBlack": "#9A9D9A",
    "terminal.ansiBrightRed": "#DA0F0F",
    "terminal.ansiBrightGreen": "#CECFC9",
    "terminal.ansiBrightYellow": "#CECFC9",
    "terminal.ansiBrightBlue": "#CECFC9",
    "terminal.ansiBrightMagenta": "#DA0F0F",
    "terminal.ansiBrightCyan": "#CECFC9",
    "terminal.ansiBrightWhite": "#FFFFFF",

    // === NOTIFICATIONS ===
    "notificationCenter.border": "#9A9D9A",
    "notificationCenterHeader.background": "#101010",
    "notificationCenterHeader.foreground": "#CECFC9",
    "notifications.background": "#101010",
    "notifications.border": "#9A9D9A",
    "notifications.foreground": "#CECFC9",
    "notificationLink.foreground": "#D93F37",

    // === BUTTONS ===
    "button.background": "#D93F37",
    "button.foreground": "#FFFFFF",
    "button.hoverBackground": "#DA0F0F",

    // === INPUT FIELDS ===
    "input.background": "#101010",
    "input.border": "#9A9D9A",
    "input.foreground": "#CECFC9",
    "input.placeholderForeground": "#9A9D9A",
    "inputOption.activeBorder": "#D93F37",
    "inputValidation.errorBackground": "#101010",
    "inputValidation.errorBorder": "#DA0F0F",

    // === DROPDOWN ===
    "dropdown.background": "#101010",
    "dropdown.border": "#9A9D9A",
    "dropdown.foreground": "#CECFC9",

    // === BADGES ===
    "badge.background": "#D93F37",
    "badge.foreground": "#FFFFFF",

    // === SCROLLBAR ===
    "scrollbarSlider.background": "#9A9D9A40",
    "scrollbarSlider.hoverBackground": "#9A9D9A60",
    "scrollbarSlider.activeBackground": "#9A9D9A80",

    // === PROGRESS BAR ===
    "progressBar.background": "#D93F37",

    // === PEEK VIEW ===
    "peekView.border": "#D93F37",
    "peekViewEditor.background": "#101010",
    "peekViewEditor.matchHighlightBackground": "#D93F3760",
    "peekViewResult.background": "#101010",
    "peekViewResult.matchHighlightBackground": "#D93F3760",
    "peekViewResult.selectionBackground": "#D93F3740",
    "peekViewTitle.background": "#101010",
    "peekViewTitleDescription.foreground": "#9A9D9A",
    "peekViewTitleLabel.foreground": "#CECFC9",

    // === GIT DECORATIONS ===
    "gitDecoration.modifiedResourceForeground": "#D93F37",
    "gitDecoration.deletedResourceForeground": "#DA0F0F",
    "gitDecoration.untrackedResourceForeground": "#9A9D9A",
    "gitDecoration.ignoredResourceForeground": "#9A9D9A80",
    "gitDecoration.conflictingResourceForeground": "#DA0F0F",

    // === BREADCRUMBS ===
    "breadcrumb.foreground": "#9A9D9A",
    "breadcrumb.background": "#101010",
    "breadcrumb.focusForeground": "#CECFC9",
    "breadcrumb.activeSelectionForeground": "#D93F37",
    "breadcrumbPicker.background": "#101010",

    // === SETTINGS ===
    "settings.headerForeground": "#CECFC9",
    "settings.modifiedItemIndicator": "#D93F37",
    "settings.dropdownBackground": "#101010",
    "settings.dropdownBorder": "#9A9D9A",
    "settings.checkboxBackground": "#101010",
    "settings.checkboxBorder": "#9A9D9A",
    "settings.textInputBackground": "#101010",
    "settings.textInputBorder": "#9A9D9A",
    "settings.numberInputBackground": "#101010",
    "settings.numberInputBorder": "#9A9D9A"
  },
  "tokenColors": [
    {
      "name": "Comments",
      "scope": [
        "comment",
        "punctuation.definition.comment"
      ],
      "settings": {
        "foreground": "#9A9D9A",
        "fontStyle": "italic"
      }
    },
    {
      "name": "Strings",
      "scope": [
        "string",
        "string.quoted",
        "string.template"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "String Escape Characters",
      "scope": [
        "constant.character.escape",
        "constant.other.placeholder"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "Numbers",
      "scope": [
        "constant.numeric",
        "constant.language"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Keywords",
      "scope": [
        "keyword",
        "storage.type",
        "storage.modifier"
      ],
      "settings": {
        "foreground": "#D93F37",
        "fontStyle": "bold"
      }
    },
    {
      "name": "Control Keywords",
      "scope": [
        "keyword.control",
        "keyword.operator.new"
      ],
      "settings": {
        "foreground": "#DA0F0F",
        "fontStyle": "bold"
      }
    },
    {
      "name": "Operators",
      "scope": [
        "keyword.operator",
        "punctuation"
      ],
      "settings": {
        "foreground": "#9A9D9A"
      }
    },
    {
      "name": "Functions",
      "scope": [
        "entity.name.function",
        "support.function"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Function Calls",
      "scope": [
        "meta.function-call",
        "variable.function"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Classes & Types",
      "scope": [
        "entity.name.type",
        "entity.name.class",
        "support.type",
        "support.class"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "Variables",
      "scope": [
        "variable",
        "support.variable"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Object Properties",
      "scope": [
        "variable.other.property",
        "variable.other.object.property",
        "support.variable.property"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Constants",
      "scope": [
        "constant",
        "variable.other.constant"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "Tags (HTML/XML)",
      "scope": [
        "entity.name.tag"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "Tag Attributes",
      "scope": [
        "entity.other.attribute-name"
      ],
      "settings": {
        "foreground": "#9A9D9A"
      }
    },
    {
      "name": "Markdown Headings",
      "scope": [
        "markup.heading",
        "entity.name.section"
      ],
      "settings": {
        "foreground": "#D93F37",
        "fontStyle": "bold"
      }
    },
    {
      "name": "Markdown Bold",
      "scope": [
        "markup.bold"
      ],
      "settings": {
        "foreground": "#CECFC9",
        "fontStyle": "bold"
      }
    },
    {
      "name": "Markdown Italic",
      "scope": [
        "markup.italic"
      ],
      "settings": {
        "foreground": "#CECFC9",
        "fontStyle": "italic"
      }
    },
    {
      "name": "Markdown Links",
      "scope": [
        "markup.underline.link",
        "string.other.link"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "Markdown Code",
      "scope": [
        "markup.inline.raw",
        "markup.fenced_code"
      ],
      "settings": {
        "foreground": "#9A9D9A"
      }
    },
    {
      "name": "JSON Keys",
      "scope": [
        "support.type.property-name.json"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "CSS Selectors",
      "scope": [
        "entity.name.tag.css",
        "entity.other.attribute-name.class.css",
        "entity.other.attribute-name.id.css"
      ],
      "settings": {
        "foreground": "#D93F37"
      }
    },
    {
      "name": "CSS Properties",
      "scope": [
        "support.type.property-name.css"
      ],
      "settings": {
        "foreground": "#CECFC9"
      }
    },
    {
      "name": "Invalid",
      "scope": [
        "invalid",
        "invalid.illegal"
      ],
      "settings": {
        "foreground": "#DA0F0F",
        "fontStyle": "underline"
      }
    },
    {
      "name": "Deprecated",
      "scope": [
        "invalid.deprecated"
      ],
      "settings": {
        "foreground": "#DA0F0F",
        "fontStyle": "strikethrough"
      }
    }
  ]
}
```

---

## Installation & Testing

### Local Testing

1. **Open VS Code**
2. Press `F5` to open Extension Development Host
3. Your theme will be available in the development window
4. Go to: `File > Preferences > Color Theme` and select "Omarchy NES"

### Manual Installation

1. **Find your VS Code extensions folder:**
   - **Windows:** `%USERPROFILE%\.vscode\extensions`
   - **macOS/Linux:** `~/.vscode/extensions`

2. **Copy your theme folder** to the extensions directory

3. **Reload VS Code** (Ctrl+Shift+P → "Developer: Reload Window")

4. **Select the theme:**
   - `File > Preferences > Color Theme`
   - Choose "Omarchy NES"

### Testing Checklist

Test your theme across different file types:
- [ ] JavaScript/TypeScript
- [ ] Python
- [ ] HTML/CSS
- [ ] Markdown
- [ ] JSON
- [ ] Terminal colors
- [ ] Diff view
- [ ] Search results
- [ ] Settings UI

---

## Customization Tips

### Adjusting Opacity

Add transparency to colors using hex alpha values:

```json
"editor.selectionBackground": "#D93F3740"  // 40 = 25% opacity
```

Opacity values:
- `20` = 12.5% opacity
- `40` = 25% opacity
- `60` = 37.5% opacity
- `80` = 50% opacity
- `AA` = 66.7% opacity
- `CC` = 80% opacity
- `FF` = 100% opacity (fully opaque)

### Adding Font Styles

You can add font styling to syntax tokens:

```json
{
  "scope": ["keyword.control"],
  "settings": {
    "foreground": "#DA0F0F",
    "fontStyle": "bold"           // bold, italic, underline, strikethrough
  }
}
```

### Finding Scope Names

To find the right scope for syntax highlighting:

1. Open Command Palette (`Ctrl+Shift+P`)
2. Run "Developer: Inspect Editor Tokens and Scopes"
3. Click on any text in your editor
4. Copy the scope names shown

### Color Variations

Create theme variants by tweaking the base colors:

**Lighter variant:**
```json
"editor.background": "#1A1A1A"  // Slightly lighter background
```

**More aggressive red:**
```json
"keyword.control": "#FF0000"    // Pure red for maximum impact
```

---

## Publishing Your Theme

### Prerequisites

1. Install `vsce` (Visual Studio Code Extension Manager):
   ```bash
   npm install -g @vscode/vsce
   ```

2. Create a publisher account at [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage)

### Publishing Steps

1. **Package your extension:**
   ```bash
   vsce package
   ```
   This creates a `.vsix` file.

2. **Test the package:**
   ```bash
   code --install-extension omarchy-nes-theme-1.0.0.vsix
   ```

3. **Publish to marketplace:**
   ```bash
   vsce publish
   ```

4. **Update version** (for future releases):
   ```bash
   vsce publish patch   # 1.0.0 → 1.0.1
   vsce publish minor   # 1.0.0 → 1.1.0
   vsce publish major   # 1.0.0 → 2.0.0
   ```

### README.md Template

Create a README.md for your extension:

```markdown
# Omarchy NES Theme

A retro NES-inspired dark theme for Visual Studio Code featuring a minimalist red, black, and grey color palette.

![Theme Preview](screenshot.png)

## Installation

1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search for "Omarchy NES Theme"
4. Click Install
5. Select the theme: File > Preferences > Color Theme > Omarchy NES

## Color Palette

- Background: `#101010`
- Foreground: `#CECFC9`
- Primary Accent: `#D93F37`
- Bright Accent: `#DA0F0F`
- Secondary: `#9A9D9A`

## Related Projects

- [Omarchy NES Theme](https://github.com/bjarneo/omarchy-nes-theme) - Multi-app theme collection
- [nes.nvim](https://github.com/bjarneo/nes.nvim) - Neovim colorscheme

## Credits

Inspired by the Omarchy NES theme by [@iamdothash](https://x.com/iamdothash)
```

---

## Additional Resources

### Official Documentation

- [VS Code Theme Guide](https://code.visualstudio.com/api/extension-guides/color-theme)
- [Theme Color Reference](https://code.visualstudio.com/api/references/theme-color)
- [TextMate Scopes](https://www.sublimetext.com/docs/scope_naming.html)

### Useful Tools

- **Theme Studio**: [https://themes.vscode.one/](https://themes.vscode.one/) - Visual theme editor
- **Color Picker**: Use VS Code's built-in color picker in JSON files
- **Scope Inspector**: Built into VS Code (Command: "Developer: Inspect Editor Tokens and Scopes")

### Example Themes to Study

- [One Dark Pro](https://github.com/Binaryify/OneDark-Pro)
- [Dracula](https://github.com/dracula/visual-studio-code)
- [Nord](https://github.com/arcticicestudio/nord-visual-studio-code)

---

## Troubleshooting

**Theme not appearing?**
- Reload window: Ctrl+Shift+P → "Developer: Reload Window"
- Check package.json contributes section
- Verify JSON syntax (no trailing commas, proper quotes)

**Colors not applying?**
- Check color key names against [official reference](https://code.visualstudio.com/api/references/theme-color)
- Ensure hex colors are 6 digits (#RRGGBB) or 8 digits (#RRGGBBAA)
- Try reloading the window

**Syntax highlighting issues?**
- Use Scope Inspector to find correct scope names
- Check scope array syntax (strings in brackets)
- Verify tokenColors array structure

---

## Contributing

Found an issue or want to suggest improvements? This theme is part of the [Omarchy NES Theme](https://github.com/bjarneo/omarchy-nes-theme) project.

---

*Created for the Omarchy NES Theme project*
*Author: [@iamdothash](https://x.com/iamdothash)*
*License: MIT*
