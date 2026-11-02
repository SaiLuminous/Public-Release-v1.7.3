# Application Windows: No Minimum Size

Resize supported application windows below their usual minimum width and height.
Useful with tiling window managers or when arranging several windows on screen.

Based on [Explorer No Minimum Window Size](https://windhawk.net/mods/explorer-no-min-size)
by [Anixx](https://github.com/Anixx). This adaptation extends the original
Explorer-only approach to eligible top-level application windows.

![Window resizing demonstration](https://i.imgur.com/iYyPe1o.gif)

[Watch the demonstration on Imgur](https://imgur.com/a/7klvrgt).

**Version:** 1.8.7 · **Author:** [SaiLuminous](https://github.com/SaiLuminous)

## Installation

1. Install [Windhawk](https://windhawk.net/).
2. Copy the complete [mod source](mods/application-windows-no-min-size.wh.cpp).
3. Select **Create a New Mod** in Windhawk, paste the source, and compile.
4. Enable the mod and resize a supported window.
**Before disabling or updating:** save your work and enlarge undersized windows
to their normal minimum, or close them yourself. Crashes have been reported
when disabling with undersized windows open; affected applications may crash.
This is an application-dependent risk, not a guaranteed outcome for every window.
The mod does not automatically close windows, show close prompts, or wait for
you to resize them.
## Usage

Enable the mod, then resize a supported window normally or with your window
manager. Disable other minimum-size mods that target the same applications.

The mod targets all processes by default. Use Windhawk's per-mod advanced
process inclusion/exclusion controls to restrict it to particular applications.
Explorer's desktop, taskbar, and helper windows are excluded; only its folder
window classes are eligible. Only resizable desktop windows are subclassed;
fixed-size helpers and message-only windows are excluded.

## File Pilot support

The optional **File Pilot minimum-size override** is disabled by default.
Its code pattern was verified against 64-bit File Pilot 0.8.5. Other versions
are eligible only when the same pattern matches uniquely; they have not been
runtime-tested.

Support is planned to be updated alongside File Pilot releases as new builds
are checked. The scan tolerates changed object offsets and call displacements.
Missing or ambiguous patterns leave the override disabled.

File Pilot needs specific support because it enforces its minimum through an
internal resize correction, separately from Windows' standard minimum-size
message. The optional hook suppresses only the identified correction call.
It does not patch the executable on disk.

Enable the option in the Settings tab. Other mods hooking the same function
may interfere with it.

## Compatibility and limitations

Applications with independent layout constraints can still refuse smaller
sizes. Contents may clip, overlap, or become inaccessible in very small windows.
Exclude incompatible applications using Windhawk's per-mod advanced settings.

The mod does not make fixed-size dialogs resizable or make a window manager
manage excluded windows. Protected processes and applications excluded by
Windhawk are unaffected. Window-manager borders and padding are unchanged.

Existing eligible windows are handled at startup. Windows created through
unhooked APIs, or made eligible by a later style change, may not be handled
until their next ShowWindow call.

## Credits and license

Original mod: **Explorer No Minimum Window Size** by **Anixx**.
Adaptation: **[SaiLuminous](https://github.com/SaiLuminous)**.

[Original source](https://github.com/ramensoftware/windhawk-mods/blob/main/mods/explorer-no-min-size.wh.cpp)

Distributed under the [MIT License](LICENSE).

## Development

The self-contained source is in mods/. Compile it through Windhawk. See
[publication notes](docs/PUBLICATION-NOTES.txt) for validation status and
submission context.
