# macos-terminal-layout

A responsive, configurable macOS CLI to save and apply native `Terminal.app` window layout profiles.

It calculates screen bounds dynamically (excluding the Dock and Menu Bar) using the `AppKit` framework via AppleScriptObjC, supports window reuse, and translates layouts responsively across different screen resolutions.

---

## Key Features

* **Proportional Coordinate Scaling**: When saving layouts, the CLI normalizes window bounds into percentage-based coordinates relative to your usable screen area. This ensures that any layout you capture on a 14" MacBook scales perfectly when applied on a 27" monitor.
* **Layout Capture**: Arrange your terminal windows exactly as you like, then save the entire configuration with a single command. It captures each window's coordinates and active settings profile (e.g. `Clear Dark`).
* **Active Window Reuse**: When applying a layout, it uses your active window as the primary pane, keeping your shell history and running processes intact while spinning up new windows around it.
* **Configurable**: Settings are saved in a simple JSON file at `~/.config/term-layout/config.json`.
* **Zero Dependencies**: Pure Python 3 script using native macOS AppleScriptObjC. No pip installations required.

---

## Installation

```bash
# Clone the repository
git clone https://github.com/alexander-matthew/macos-terminal-layout.git
cd macos-terminal-layout

# Make script executable
chmod +x term-layout

# Copy to your local bin directory (ensure ~/.local/bin is in your $PATH)
mkdir -p ~/.local/bin
cp term-layout ~/.local/bin/
```

---

## Command Usage

If run without arguments, `term-layout` starts an **interactive menu** where you can select a layout and configure options.

### 1. List Layouts
List all currently saved layout profiles:
```bash
term-layout list
# or shorthand:
term-layout ls
```

### 2. Apply a Layout
Apply a saved layout configuration:
```bash
term-layout apply <layout-name>
# or shorthand:
term-layout go <layout-name>
```
**Options:**
* `-c` or `--clean`: Closes all other Terminal windows first, leaving only the applied layout.
  ```bash
  term-layout apply vertical -c
  ```

### 3. Capture/Save Layout
Arrange your Terminal windows on your screen, then save the setup:
```bash
term-layout save <layout-name>
# or shorthand:
term-layout add <layout-name>
```

### 4. Remove a Layout
Delete a saved layout profile:
```bash
term-layout remove <layout-name>
# or shorthand:
term-layout rm <layout-name>
```

### 5. Inspect a Layout
Display the configuration data (JSON format) for a layout profile:
```bash
term-layout show <layout-name>
# or shorthand:
term-layout cat <layout-name>
```

### 6. Edit Configuration
Open the config file in your system's default editor (uses `$EDITOR`, fallback to `nano`):
```bash
term-layout edit
```

---

## Configuration File

The default layouts are populated inside `~/.config/term-layout/config.json` on first run:
* `vertical`: Stacked 2 windows on the right 1/3 of the screen.
* `full`: 4 windows in a 2x2 grid.

Example configuration details:
```json
{
    "layouts": {
        "vertical": [
            {
                "left": 0.6667,
                "top": 0.0,
                "right": 1.0,
                "bottom": 0.5,
                "profile": "Clear Dark"
            },
            {
                "left": 0.6667,
                "top": 0.5,
                "right": 1.0,
                "bottom": 1.0,
                "profile": "Clear Dark"
            }
        ]
    }
}
```

---

## License

This project is licensed under the [MIT License](LICENSE).
