# macos-terminal-layout

A dynamic macOS shell script helper to organize, size, and layout macOS native `Terminal.app` windows. 

It calculates screen bounds dynamically (excluding the Dock and Menu Bar) using the `AppKit` framework via AppleScriptObjC, supports window reuse, and formats your layout into clean, tiled configurations.

## Features

* **Dynamic Resolution Sizing**: Uses AppKit coordinates so it adjusts automatically for any display size, Dock location, or menu bar settings.
* **Window Reuse**: Keeps your active Terminal session intact by placing your running window as the primary pane, opening new windows to complete the layout.
* **Clear Dark Theme Integration**: Automatically applies the native macOS `Clear Dark` settings profile to all layout windows.
* **Clean Flag**: Option to automatically close all other open Terminal windows before applying a layout.
* **Interactive Mode**: If executed without parameters, prompts you with an interactive selection menu.

---

## Layout Profiles

### 1. Vertical (`vertical` or `v`)
Arranges **two** terminals stacked on top of each other, filling the right third ($33\%$) of the screen and spanning $100\%$ of the screen height.

### 2. Full (`full` or `f`)
Arranges **four** terminals in a perfect $2 \times 2$ grid filling $100\%$ of the screen.

---

## Installation

To install, clone this repository and copy the `term-layout` script to a directory in your system `$PATH` (e.g., `~/.local/bin` or `/usr/local/bin`):

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

## Usage

```bash
# Run the interactive layout selector
term-layout

# Set up stacked terminals on the right 1/3 of the screen
term-layout vertical
# or shorthand:
term-layout v

# Set up 4 terminals in a 2x2 grid covering the full screen
term-layout full
# or shorthand:
term-layout f

# Add the clean flag (-c or --clean) to close other terminal windows first
term-layout full --clean
term-layout v -c
```

---

## License

This project is open-source and available under the [MIT License](LICENSE).
