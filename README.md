# Tmux Configuration

This directory contains a custom tmux configuration with useful keybindings and plugin support.

## Features

- **Navigation shortcuts**: Alt+Arrow keys to switch windows, Alt+Shift+Arrow to move windows
- **Quick window management**: Alt+n for new window, Alt+w to close window
- **Direct window access**: Alt+0-9 to jump to specific windows
- **Mouse support**: Full mouse integration enabled
- **Session persistence**: Automatic session saving and restoration via tmux-resurrect and tmux-continuum

## Installation

### 1. Link the configuration file

```bash
# Create tmux config directory if it doesn't exist
mkdir -p ~/.config/tmux

# Link the configuration file
ln -sf $(pwd)/tmux.conf ~/.config/tmux/tmux.conf
# OR for traditional location:
ln -sf $(pwd)/tmux.conf ~/.tmux.conf
```

### 2. Install TPM (Tmux Plugin Manager)

The configuration requires TPM to manage plugins. Install it to one of these locations:

**Option A: Default location (recommended)**
```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

**Option B: XDG config directory**
```bash
git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm
```

The configuration will automatically detect TPM in either location.

### 3. Install plugins

1. Start tmux: `tmux`
2. Press `prefix` + `I` (capital i) to fetch and install the plugins
   - Default prefix is `Ctrl+b`, so press `Ctrl+b` then `Shift+i`

## Plugins

This configuration includes:

- **tmux-resurrect**: Save and restore tmux sessions manually
- **tmux-continuum**: Automatic continuous saving of tmux sessions (every 15 minutes)
  - Sessions are automatically restored when tmux starts

## Plugin Management

- `prefix` + `I` - Install new plugins
- `prefix` + `U` - Update plugins
- `prefix` + `alt` + `u` - Uninstall plugins not in the list

## Keybindings

### Window Navigation
- `Alt+Left` - Previous window
- `Alt+Right` - Next window
- `Alt+0-9` - Jump to window 0-9

### Window Management
- `Alt+n` - New window
- `Alt+w` - Close current window
- `Alt+Shift+Left` - Move window left
- `Alt+Shift+Right` - Move window right

### Session Management
- `prefix` + `Ctrl+s` - Save session (tmux-resurrect)
- `prefix` + `Ctrl+r` - Restore session (tmux-resurrect)
- Sessions are automatically saved and restored with tmux-continuum

## Troubleshooting

### Plugins not loading

If plugins aren't working:

1. Verify TPM is installed:
   ```bash
   ls ~/.tmux/plugins/tpm/tpm
   # OR
   ls ~/.config/tmux/plugins/tpm/tpm
   ```

2. If TPM is not found, install it following step 2 above

3. Reload tmux configuration:
   ```bash
   tmux source-file ~/.config/tmux/tmux.conf
   # OR
   tmux source-file ~/.tmux.conf
   ```

4. Install plugins with `prefix` + `I`

### Custom TPM location

If you've installed TPM in a custom location, you'll need to modify line 45 in `tmux.conf` to point to your TPM installation path.
