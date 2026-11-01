# Application Windows: No Minimum Size

Resize supported application windows below their usual minimum width and height.
Useful with tiling window managers or when arranging several windows on screen.

Based on [Explorer No Minimum Window Size](https://windhawk.net/mods/explorer-no-min-size)
by [Anixx](https://github.com/Anixx). This adaptation extends the original
Explorer-only approach to eligible top-level application windows.

**Version:** 1.7.3 · **Author:** [SaiLuminous](https://github.com/SaiLuminous)
**Status:** Experimental

## Installation

1. Install [Windhawk](https://windhawk.net/).
2. Open [the mod source](mods/application-windows-no-min-size.wh.cpp) and copy its complete contents.
3. In Windhawk, choose **Create a New Mod**, replace the editor contents with the source, and click **Compile Mod**.
4. Enable the mod. The optional File Pilot override is in its **Settings** tab.

This repository provides source for local installation. It has not yet been
published in the official Windhawk catalog.
## Usage

Enable the mod, then resize a supported window normally or with your window
manager. Existing windows and newly created windows are supported. Disable
other minimum-size mods that target the same applications.

The mod targets all processes by default. Use Windhawk's per-mod advanced
process inclusion/exclusion controls to restrict it to particular applications.
Explorer's desktop, taskbar, and helper windows are excluded; only its folder
window classes are eligible.

## File Pilot override

**File Pilot minimum-size override (experimental)** is disabled by default.
Enable it in the Settings tab if File Pilot snaps back to its minimum size.

This optional override targets a separately verified correction call in one
64-bit File Pilot 0.8.5 build. It checks the executable build and instruction
signature before installing the hook. Other builds are left unchanged.
It does not modify the File Pilot executable on disk. Toggle changes apply
immediately while the mod is running; disabling the option restores File
Pilot's normal size correction.

## Disabling or updating

The mod waits for you to manually close affected windows before unloading.
Windhawk may display **Uninitializing...** during this intentional wait.

- Close windows that were below their reported minimum when unloading began.
- Close File Pilot windows that used the optional override, even if they have
  since been enlarged.
- Complete any save prompts. Minimizing a window is not closing it.
- Hidden windows are excluded from the initial manual-close assessment.
- Unresponsive window threads can delay unloading until they respond or exit.

Minimum-size overrides remain active while waiting. The mod does not close
applications, terminate processes, resize windows automatically, or draw borders.

## Compatibility and limitations

The standard override changes Windows' minimum tracking size. Applications
with independent layout constraints can still refuse smaller sizes. Contents
may clip, overlap, or become inaccessible in very small windows.

This mod does not make fixed-size dialogs resizable or make a window manager
manage excluded windows. Protected processes and applications excluded by
Windhawk are unaffected. Window-manager borders and padding are unchanged.

The File Pilot option is experimental. Source compilation has been checked
for x86 and x86-64; this is not comprehensive application compatibility testing.
The manual-unload behavior needs further live testing before a stable release.

## Credits and license

Original mod: **Explorer No Minimum Window Size** by **Anixx**.
Adaptation: **[SaiLuminous](https://github.com/SaiLuminous)**.

Original source:
https://github.com/ramensoftware/windhawk-mods/blob/main/mods/explorer-no-min-size.wh.cpp

Distributed under the [MIT License](LICENSE).

## Repository layout

- [Mod source](mods/application-windows-no-min-size.wh.cpp) — self-contained Windhawk mod, settings, and embedded documentation.
- [LICENSE](LICENSE) — MIT license and author notices.
- [Publication notes](docs/PUBLICATION-NOTES.txt) — submission notes and remaining runtime validation.

## Development and reporting issues

Edit and compile the source through Windhawk's mod editor. Keep the embedded
README and this README consistent when changing user-facing behavior.

When reporting an issue, include your Windows version, Windhawk version, app
name/version, whether the File Pilot option is enabled, and steps to reproduce.
For an unload wait, mention which affected windows are still open or minimized.

To submit to the official collection, follow
[Windhawk's submission instructions](https://github.com/ramensoftware/windhawk-mods#submitting-a-new-mod).
That pull request should contain only the mod source file under mods/.
