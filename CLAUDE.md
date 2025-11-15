# CLAUDE.md - AI Assistant Guide for omarchy-nes-theme

## Project Overview

**omarchy-nes-theme** is a retro NES-inspired color theme for Linux desktop environments and terminal applications. It provides a cohesive visual experience across multiple applications with a minimalist red, black, and grey color palette reminiscent of classic Nintendo Entertainment System aesthetics.

**Primary Use Case:** This theme is designed to be installed via the `omarchy-theme-install` command and provides configuration files for a complete desktop environment theming solution.

**Project URL:** https://github.com/bjarneo/omarchy-nes-theme
**Related Project:** [nes.nvim](https://github.com/bjarneo/nes.nvim) - Neovim colorscheme
**Author:** [@iamdothash](https://x.com/iamdothash)

---

## Core Color Palette

The theme is built around these consistent colors across all applications:

```
Background:      #101010 (near-black)
Foreground:      #CECFC9 (light grey)
Primary Accent:  #D93F37 (red)
Bright Accent:   #DA0F0F (bright red)
Secondary:       #9A9D9A (medium grey)
Pure White:      #FFFFFF (highlights only)
Pure Black:      #000000 (true black)
```

**Color Usage Conventions:**
- Background is consistently `#101010` across all applications
- Foreground text uses `#CECFC9` for readability
- Red accent colors (`#D93F37` and `#DA0F0F`) are used for highlights, selections, and emphasis
- Grey (`#9A9D9A`) is used for borders, inactive elements, and secondary text
- Pure white is reserved for maximum contrast situations only

---

## Repository Structure

```
omarchy-nes-theme/
├── README.md                  # User-facing documentation
├── CLAUDE.md                  # This file - AI assistant guide
├── theme.png                  # Preview screenshot
│
├── backgrounds/               # Wallpapers
│   ├── 1-nes.png
│   └── 2-nes.png
│
├── hooks/                     # Installation lifecycle scripts
│   ├── install.sh            # Pre-installation hook
│   ├── apply.sh              # Post-installation hook
│   ├── cleanup.sh            # Post-application hook
│   └── uninstall.sh          # Uninstallation hook
│
├── Terminal Emulators
│   ├── alacritty.toml        # Alacritty terminal theme
│   ├── ghostty.conf          # Ghostty terminal configuration
│   └── ghostty-theme         # Ghostty theme palette
│
├── Window Management
│   ├── hyprland.conf         # Hyprland compositor theme (partial config)
│   └── hyprlock.conf         # Hyprland lock screen theme
│
├── UI Components
│   ├── waybar.css            # Status bar styling
│   ├── wofi.css              # Application launcher styling
│   ├── walker.css            # Walker launcher styling
│   ├── mako.ini              # Notification daemon configuration
│   ├── swayosd.css           # On-screen display styling
│   └── icons.theme           # Icon theme configuration
│
├── Applications
│   ├── btop.theme            # System monitor theme
│   └── neovim.lua            # Neovim theme loader (LazyVim)
```

---

## File Purposes and Conventions

### Terminal Configurations

**alacritty.toml**
- Full TOML configuration for Alacritty terminal
- Defines all 16 ANSI colors (normal + bright)
- Uses neutral greys for unused colors (green, yellow, blue, cyan)
- Red is used for both red and magenta channels

**ghostty.conf & ghostty-theme**
- `ghostty.conf`: Main configuration file
- `ghostty-theme`: Palette-only theme file
- Uses palette index 0-15 for color definitions
- Matches Alacritty's color scheme exactly

### Window Manager Configurations

**hyprland.conf**
- **Important:** This is NOT a complete Hyprland configuration
- Designed to be `source`d into an existing hyprland.conf
- Only defines border colors:
  - Active border: dual-color gradient (light grey to medium grey)
  - Inactive border: semi-transparent dark background

**hyprlock.conf**
- Lock screen configuration for Hyprland
- Maintains theme consistency during screen locking

### UI Component Stylesheets

All CSS files follow these conventions:
- Use CSS custom properties (variables) when possible
- Define colors at the top for easy maintenance
- Maintain consistent spacing and formatting
- Example from waybar.css:
  ```css
  @define-color foreground #CECFC9;
  @define-color background #101010;
  ```

**waybar.css** - Status bar styling
**wofi.css** - Application launcher
**walker.css** - Alternative launcher
**swayosd.css** - Volume/brightness OSD

### Application-Specific Themes

**btop.theme**
- System resource monitor
- Defines gradient colors for graphs (grey → red → bright red)
- All metrics use the same color gradient for consistency
- Format: `theme[key]="#HEXCOLOR"`

**mako.ini**
- Notification daemon
- INI format configuration
- Includes app-specific rules (e.g., hiding Spotify notifications)
- Do-not-disturb mode configuration

**neovim.lua**
- LazyVim plugin configuration
- Loads the external `nes.nvim` colorscheme
- Minimal two-plugin setup for theme activation

**icons.theme**
- Icon theme configuration
- Links to system icon sets that match the theme aesthetic

### Installation Hooks

The `hooks/` directory contains shell scripts executed by `omarchy-theme-install`:

1. **install.sh** - Runs before theme files are copied (pre-install)
2. **apply.sh** - Runs after theme files are copied (post-install)
3. **cleanup.sh** - Runs after apply.sh completes (post-apply)
4. **uninstall.sh** - Runs when theme is removed

**Current Status:** All hooks are minimal placeholders that only echo their status.

**Best Practices for Hooks:**
- Keep hooks idempotent (safe to run multiple times)
- Echo clear status messages
- Handle missing dependencies gracefully
- Return proper exit codes (0 for success)
- Don't assume root/sudo access

---

## Development Workflows

### Adding a New Application Theme

1. **Research the application's theming system**
   - Check documentation for config format
   - Identify color configuration locations
   - Determine if it uses hex codes, RGB, or named colors

2. **Create the theme file**
   - Use the core color palette defined above
   - Name the file appropriately (e.g., `app-name.conf` or `app-name.css`)
   - Include a header comment identifying it as part of the Omarchy NES theme

3. **Maintain consistency**
   - Background must be `#101010`
   - Primary text must be `#CECFC9`
   - Use red (`#D93F37` or `#DA0F0F`) for accents/highlights
   - Use grey (`#9A9D9A`) for borders/secondary elements

4. **Test the theme**
   - Verify colors appear correctly in the application
   - Check both light and dark UI elements
   - Ensure text remains readable

5. **Update README.md if needed**
   - Add the application to any relevant lists
   - Update installation instructions if required

### Modifying Colors

**⚠️ Important:** Color changes should be made consistently across ALL files.

When changing a color:
1. Identify all files using that color
2. Update the color in all locations
3. Update this CLAUDE.md file's color palette section
4. Test all affected applications
5. Update theme.png screenshot if visual changes are significant

### Git Workflow

**Branch Naming:**
- Feature branches: `feature/description`
- Bug fixes: `fix/description`
- AI assistant branches: `claude/claude-md-*` (auto-generated)

**Commit Messages:**
- Use clear, descriptive messages
- Start with a verb (Add, Update, Fix, Remove)
- Reference specific applications/files when relevant
- Examples:
  - "Add kitty terminal theme"
  - "Update btop gradients to match new palette"
  - "Fix hyprland border transparency"

**Testing Before Commits:**
- Verify syntax of config files (where applicable)
- Check that color codes are valid hex values
- Ensure no trailing whitespace (use .editorconfig if available)

---

## AI Assistant Guidelines

### When Adding New Themes

1. **Always check the existing files first** to understand the pattern
2. **Use the exact color palette** - don't approximate or create variations
3. **Include descriptive comments** in configuration files
4. **Maintain consistent file naming** - lowercase, use hyphens or dots as appropriate
5. **Consider all color roles** - not just foreground/background

### When Modifying Existing Files

1. **Preserve formatting** - match indentation and spacing
2. **Keep comments** - they provide context for future changes
3. **Test color values** - ensure they're valid hex codes (#RRGGBB)
4. **Check for duplicates** - some apps define colors multiple times for different contexts

### Color Accessibility

While this is a stylistic theme, maintain basic readability:
- Foreground/background contrast should remain high
- Red accents should be visible against dark backgrounds
- Consider users with color blindness (red/grey is relatively safe)

### File Format Specifics

**TOML Files** (alacritty.toml):
- Use proper TOML syntax
- Colors in quotes: `color = '#RRGGBB'`
- Maintain section headers with brackets

**INI Files** (mako.ini):
- No quotes around values
- Colors as: `key=#RRGGBB`
- Sections in brackets: `[section-name]`

**CSS Files**:
- Use @define-color for color variables
- Lowercase hex colors preferred
- Comment sections clearly

**Lua Files** (neovim.lua):
- Follow Lua syntax
- Use proper table formatting
- Maintain plugin structure

**Conf Files** (hyprland.conf, ghostty.conf):
- Application-specific syntax
- Check documentation for proper format
- Use rgba() for transparency where supported

### Common Pitfalls to Avoid

1. **Don't create complete configs** - Many files (like hyprland.conf) are designed to be included in user configs, not replace them
2. **Don't hardcode paths** - Use relative paths or standard XDG locations
3. **Don't add unnecessary dependencies** - Keep theme files standalone
4. **Don't modify hook scripts without testing** - They run during installation
5. **Don't use color names** - Always use hex codes for consistency

### Testing Checklist

Before committing theme changes:
- [ ] All hex colors are valid 6-digit codes
- [ ] Colors match the defined palette
- [ ] File syntax is valid (TOML, CSS, INI, etc.)
- [ ] No trailing whitespace
- [ ] Comments are clear and helpful
- [ ] File naming follows repository conventions
- [ ] Changes don't break existing functionality

---

## Installation and Usage

Users install this theme via:
```bash
omarchy-theme-install https://github.com/bjarneo/omarchy-nes-theme
```

The installation tool:
1. Clones the repository
2. Runs `hooks/install.sh`
3. Copies theme files to appropriate locations
4. Runs `hooks/apply.sh`
5. Runs `hooks/cleanup.sh`

**For AI Development:**
- Don't modify the installation command
- Hook scripts should be safe to run repeatedly
- Theme files should work when copied to standard config locations

---

## Related Resources

- **Neovim Theme:** [nes.nvim](https://github.com/bjarneo/nes.nvim)
- **Omarchy Project:** [omarchy.org](https://omarchy.org)
- **Author:** [@iamdothash on X](https://x.com/iamdothash)

---

## Questions or Issues?

When working on this repository as an AI assistant:
1. **Check existing files** for patterns before creating new ones
2. **Maintain color consistency** above all else
3. **Keep it minimal** - this is a theme, not a complete desktop configuration
4. **Test syntax** where possible before committing
5. **Ask the user** if you're unsure about color choices or file locations

---

*Last Updated: 2025-11-15*
*Repository: https://github.com/bjarneo/omarchy-nes-theme*
