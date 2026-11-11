# Geometry Dash 2.2091 port validation

## Scope

Validate the existing Geode 6.0.0-alpha.1 codebase against Geometry Dash 2.2091 for:

- Windows x64, using the Steam installation.
- Android ARM64 (arm64-v8a).
- Android ARMv7 (armeabi-v7a), where the installed game build supports it.

## Initial repository audit

- The root CMake configuration already selects `GEODE_GD_VERSION=2.2091` and `GEODE_COMP_GD_VERSION=22091`.
- The platform configuration already defines `Win64`, `Android64`, and `Android32`.
- The upstream bindings repository contains `bindings/2.2091`.
- The existing `.github/workflows/build-docker.yml` already defines build jobs for Windows, Android32, and Android64 and checks for their expected binaries.

## Validation checklist

- [ ] CI produces `Geode.dll` and `GeodeUpdater.exe` for Windows.
- [ ] CI produces `Geode.android64.so`.
- [ ] CI produces `Geode.android32.so`.
- [ ] Test Windows loader startup against an installed Steam copy of Geometry Dash 2.2091.
- [ ] Test Android loader startup against a legitimately installed Geometry Dash 2.2091 build, separately for each supported ABI.
- [ ] Check startup, mod loading, settings UI, and crash logs on each target.

## Compatibility boundary

This branch targets the game's 2.2091 interfaces and supported installation paths. It does not add DRM, license, purchase, or signature-check bypasses for unofficial game copies. Android compatibility must be validated against the exact game package/version and ABI rather than assumed from the version number alone.
