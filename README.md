# hypr-smart-brightness 🔆

**Instant, context-aware brightness control for Hyprland.**

Seamlessly controls both **Laptop Backlights** and **External Monitors (DDC/CI)** using the same keybindings, with zero perceived latency.

## Features
- 🚀 **Extreme Optimization**: Reduces `ddcutil` latency from ~500ms to ~20ms using bus caching and optimized flags.
- 💻 **Laptop Support**: Native kernel control for `eDP` / `LCD` screens.
- 🖥️ **Desktop Support**: Full DDC/CI control for external displays.
- 🎯 **Smart Rounding**: Automatically rounds brightness to the nearest step multiple (e.g., 17% -> 20%).
- 🧹 **Auto-Config**: Includes built-in install/uninstall commands to manage your Hyprland config cleanly.

## Dependencies

The script will automatically check for these during installation:

*   **hyprland**: Required for monitor detection.
*   **jq**: Required for parsing monitor data.
*   **ddcutil**: **Required** for external monitor support.
*   **brightnessctl**: Required for laptop backlight support.
*   **swayosd**: Recommended for the On-Screen Display (OSD) feedback.

## Installation

### Method 1: Manual (Git Clone)
This keeps the script in your `~/Repos` folder and links it.

1.  Clone the repository:
    ```bash
    git clone https://github.com/nlabrad/hypr-smart-brightness.git
    cd hypr-smart-brightness
    ```

2.  Run the installer:
    ```bash
    ./hypr-smart-brightness --install
    ```
    *This will add a `source = ...` line to your `hyprland.conf` pointing to the config file in this directory.*

### Method 2: System Install
If you copy the script to `/usr/local/bin`, make sure to also copy `hypr-smart-brightness.conf` to `/usr/share/hypr-smart-brightness/`.

## Uninstallation

To cleanly remove the configuration edits:

```bash
./hypr-smart-brightness --uninstall
```

Then you can safely delete the repository folder.

## Configuration

The script uses a sourced configuration file (`hypr-smart-brightness.conf`) to avoid cluttering your main config. It handles:
-   **Unbinding** default keys (to avoid double-events).
-   **Binding** standard keys (Step 5).
-   **Binding** Alt+Keys (Step 1 for precise control).

You can edit `hypr-smart-brightness.conf` directly to change keys or step sizes.

## License
MIT