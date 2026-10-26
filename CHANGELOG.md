# Changelog

All notable changes to the Fun Tracks recompilation are listed here, newest first.

## [Unreleased] — next alpha

### Fixed

- 3D renderer, Snake Island: banners and flags no longer flicker, vanish too early or show their
  texture mirrored; the race HUD (lap times, gauges) is drawn properly over the water.
- Car physics now compute exactly the same on every platform (one math function still came from
  each system's C library and could differ in the last digit during long races).

## [0.1.0-alpha] — 2026-10-26

First alpha release.

### Platforms

- Windows 64-bit (Windows 10 / 11).
- Android 10 or later, 64-bit ARM, for handheld consoles with a built-in gamepad
  (tested on the AYN Odin 2 Portal).

### Features

- The whole game rebuilt from the decompiled original code, running natively: no emulator and no
  original executable needed (original game files still required).
- Two renderers: the original 2D renderer, and a GPU 3D renderer (Direct3D 12 on Windows, Vulkan
  on Android). F11 switches between them; `moteur=3d` in `fun_tracks_recomp.ini` starts in 3D.
- CD music played from OGG files (`Music/track02.ogg`, `Music/track03.ogg`...).
- Windows: window or fullscreen (Alt+Enter).
- Android: fullscreen, gamepad controls for menus and races, gamepad buttons can be set in the
  game's key settings page ("PAD A", "PAD X"...).
- Original game icon.

### Known limitations

- 4:3 picture only (black borders on wide screens).
- No network multiplayer.
- Android: one player only; game files must be copied to the device by hand.

[0.1.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.1.0-alpha
