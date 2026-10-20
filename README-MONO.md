# MONO app source update

MONO uses a charcoal interface, grayscale text, and left-to-right graphite gradients on active navigation buttons, tabs, and switches.

This package contains 20 edited files from the supplied Vesta 1.2.1 source, arranged in their original project paths. It is a replacement-file package for the original project, not a standalone project or compiled executable.

## Apply

1. Back up your existing source project.
2. Copy `src/`, `configs/`, `CMakeLists.txt`, and `CMakePresets.json` from this package into that project's root, merging directories and replacing the corresponding files.
3. Reconfigure and rebuild using the project's normal build instructions. With its Visual Studio 2022 toolchain installed:

   ```powershell
   cmake --preset release
   cmake --build --preset release
   ```

4. The release executable is named `build/bin/mono.exe`.

Alternatively, apply `MONO.patch` at the original project root with `git apply --check MONO.patch`, then `git apply MONO.patch`. Use either the replacement files or the patch.

## Changes

- MONO branding in the sidebar, watermark, welcome guide, startup dialogs, import dialogs, translated text, hotkey file heading, and Lua callback error.
- Neutral grayscale default palette and toggle tracks.
- Animated rounded gradients on selected navigation, tabs, and enabled switches, using the existing gradient renderer and alpha handling.
- Bundled configuration files explicitly select the MONO palette.
- Loading a saved configuration with the complete original default palette migrates it to MONO. Custom palettes remain editable under Misc → General → Interface.
- Build presets produce `mono.exe` or `mono-profile.exe`.

Internal configuration identifiers, the Lua `vesta` API, and the existing `%TEMP%\vesta` storage location remain compatible with existing data and scripts. Gameplay settings and website files were not edited. Original licensing and attribution are included.

## Verification

Configuration and preset JSON were parsed successfully. The bundled profiles were compared against the originals after removing the new palette; all other settings match. The patch passed whitespace validation and applied cleanly to copies of the original supplied files. The release preset is recognized by CMake.

The Windows application has not been compiled or run, so rendering and runtime behavior still require verification in a built app.
