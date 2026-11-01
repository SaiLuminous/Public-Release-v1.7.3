# Application Windows: No Minimum Size

Resize supported application windows below their usual minimum width and height.
Useful with tiling window managers or when arranging several windows on screen.

Based on [Explorer No Minimum Window Size](https://windhawk.net/mods/explorer-no-min-size)
by [Anixx](https://github.com/Anixx). This adaptation extends the original
Explorer-only approach to eligible top-level application windows.

**Version:** 1.8.0 · **Author:** [SaiLuminous](https://github.com/SaiLuminous)

## Installation

1. Install [Windhawk](https://windhawk.net/).
2. Copy the complete [mod source](mods/application-windows-no-min-size.wh.cpp).
3. Select **Create a New Mod** in Windhawk, paste the source, and compile.
4. Enable the mod and resize a supported window.

## Usage

Enable the mod, then resize a supported window normally or with your window
manager. Existing windows and newly created windows are supported. Disable
other minimum-size mods that target the same applications.

The mod targets all processes by default. Use Windhawk's per-mod advanced
process inclusion/exclusion controls to restrict it to particular applications.
Explorer's desktop, taskbar, and helper windows are excluded; only its folder
window classes are eligible.

## File Pilot support

The optional **File Pilot minimum-size override** currently supports the
verified 64-bit File Pilot 0.8.5 build. It is disabled by default.
Support is planned to be updated alongside File Pilot releases as new builds
are checked. Updates are not automatically compatible: an unrecognized build
is left unchanged until its override has been updated and verified.

File Pilot needs specific support because it enforces its minimum size through
an internal correction that calls SetWindowPos, separately from the standard
Windows minimum-size message. The generic override cannot prevent that
correction. The optional hook suppresses only the identified correction call,
after checking the executable build and code signature; it does not patch
the executable on disk.

Enable this option in the mod's Settings tab. Other mods hooking the same
function may interfere with it. Very small windows may expose application
layout or rendering bugs.
## Compatibility and limitations

The standard override changes Windows' minimum tracking size. Applications
with independent layout constraints can still refuse smaller sizes. Contents
may clip, overlap, or become inaccessible in very small windows.

This mod does not make fixed-size dialogs resizable or make a window manager
manage excluded windows. Protected processes and applications excluded by
Windhawk are unaffected. Window-manager borders and padding are unchanged.

Disabling restores normal minimum-size handling without requiring you to resize
or close windows first. It does not actively resize or close windows.
Applications can apply their minimum on a subsequent resize.

Other applications may enforce independent minimum sizes that the standard override does not bypass. Very small windows can cause clipping or
application-specific rendering problems. Exclude incompatible applications
using Windhawk's per-mod advanced settings.
## Credits and license

Original mod: **Explorer No Minimum Window Size** by **Anixx**.
Adaptation: **[SaiLuminous](https://github.com/SaiLuminous)**.

Original source:
https://github.com/ramensoftware/windhawk-mods/blob/main/mods/explorer-no-min-size.wh.cpp

Distributed under the [MIT License](LICENSE).

## Development

The self-contained source is in mods/. Compile it through Windhawk. See [publication notes](docs/PUBLICATION-NOTES.txt) for validation status and submission context.
