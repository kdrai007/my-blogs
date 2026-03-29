---
title: "hyprland_shortcuts"
draft: false
---

# Hyprland Keybindings Cheat Sheet

**Mod Key:** `SUPER` (Windows Key)

## 🚀 Applications & Launchers
| Key Binding | Action | Command / Script |
| :--- | :--- | :--- |
| **$Mod + Return** | Open Terminal | `$terminal` (Kitty) |
| **$Mod + F** | Open Firefox | `firefox` |
| **$Mod + E** | Open File Manager | `nautilus` |
| **$Mod + D** | App Launcher (Menu) | `fuzzel` |
| **$Mod + Shift + D** | Alternative Launcher | `wmenu-launcher` |
| **$Mod + . (Period)** | Emoji Picker | `fuzzel_emojii.sh` |
| **$Mod + V** | Clipboard History | `cliphist list | wofi` |

## 🪟 Window Management
| Key Binding | Action | Notes |
| :--- | :--- | :--- |
| **$Mod + Q** | Close Window | `killactive` |
| **Alt + F** | Toggle Fullscreen | `fullscreen` |
| **$Mod + Shift + V** | Toggle Floating | `togglefloating` |
| **$Mod + P** | Dwindle: Pseudo Tiling | Keeps aspect ratio |
| **$Mod + J** | Dwindle: Toggle Split | Changes split direction |
| **$Mod + Arrows** | Move Focus | Left, Right, Up, Down |
| **$Mod + Mouse Left** | Move Window | Drag with mouse |
| **$Mod + Mouse Right** | Resize Window | Drag with mouse |

## 🛠️ Utilities & Tools
| Key Binding | Action | Command / Script |
| :--- | :--- | :--- |
| **Print** | Screenshot (Region) | Select area → Copy & Save |
| **Shift + Print** | Screenshot (Full) | Capture all → Copy & Save |
| **$Mod + Shift + X** | Extract Text (OCR) | Select area → Copy text to clipboard |
| **$Mod + Shift + T** | Extract Text (OCR) | *(Alternative bind)* |
| **$Mod + Shift + A** | Google Lens Search | `snip_to_search.sh` |
| **Super + Numpad-** | Zoom Out | `code:82` (Continuous zoom) |

## ⚙️ System & Hardware
| Key Binding | Action | Command / Script |
| :--- | :--- | :--- |
| **$Mod + L** | Lock Screen | `hyprlock` |
| **$Mod + Shift + L** | Suspend System | `systemctl suspend` |
| **$Mod + M** | Exit Hyprland | Log out |
| **$Mod + Shift + W** | Toggle Waybar | Hide/Show status bar |
| **Alt + W** | Wallpaper Picker | `wallpaper` script |
| **$Mod + T** | Toggle Trackpad | `toggle_trackpad.sh` |
| **Lid Switch** | Auto Monitor | Disables internal screen when closed |

## 📦 Workspaces
| Key Binding | Action | Notes |
| :--- | :--- | :--- |
| **$Mod + 0-9** | Switch Workspace | Go to workspace 1-10 |
| **$Mod + Shift + 0-9** | Move Window | Move active window to workspace |
| **$Mod + Scroll** | Cycle Workspaces | Scroll mouse wheel on desktop |
| **$Mod + S** | Toggle Scratchpad | Open/Close "Special" workspace |
| **$Mod + Shift + S** | Move to Scratchpad | Send window to "Special" workspace |
