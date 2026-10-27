# Changelog

All notable changes to the Fun Tracks recompilation are listed here, newest first.

## [Unreleased] — next alpha

### Added

- The game's six built-in languages are now available: English, German, Italian, Spanish, Swedish
  and French (0.1.0-alpha was French only). The game starts in the system language, or in English
  if it is not one of them.
- New LANGUAGE line in the game options page (AUTO or one of the six languages), applied at once
  and saved in `fun_tracks_recomp.ini` (`langue = auto`, `en`, `de`, `it`, `es`, `sv` or `fr`).
- Widescreen in 3D: races fill 16:9 and 21:9 screens, showing more scenery on the sides without
  stretching the picture; split screen and reduced view sizes follow. The race HUD sits at the
  screen edges (times and position on the left, speedometer and turbo on the right). Menus,
  loading screens and the intro video stay 4:3 with black borders.
- New RENDERER line in the graphics options: SOFTWARE (the original picture), DIRECT3D or VULKAN
  (Windows), VULKAN (Android). Changes apply at once; F11 switches between software and 3D.
  Saved in `fun_tracks_recomp.ini` (`moteur = logiciel`, `direct3d` or `vulkan`).
- New ASPECT line in the graphics options: WIDE or 4:3 for the 3D picture
  (`format = large` or `4:3`).
- Menu pages too tall for the screen now scroll, with arrows above and below.

### Changed

- Settings that have no effect with the chosen renderer are greyed out: resolution, mip-mapping
  and perspective polygons in 3D, aspect in software.
- In 3D, races always use the high-resolution interface layout (sharper HUD); the keypad + and −
  keys no longer change the resolution there. The resolution setting still applies to the
  software renderer.

### Fixed

- Results screen: the "play this track again?" question showed the wrong text in languages other
  than English.
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
