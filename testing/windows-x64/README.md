# Fun Tracks recomp — Windows 64-bit test build

Test build of the next alpha for **Windows 10/11 64-bit**. It is **not a release yet**: it is here so
that the fixes below can be tried before they are published.

**No file from the original game is included.** You need your own copy of the original PC game
(Fun Tracks, or Ignition, its English edition).

## Files

- [`FunTracks-test-windows-x64.zip`](FunTracks-test-windows-x64.zip): `FunTracks.exe`,
  `fun_tracks_recomp.ini`, `dxcompiler.dll` and `dxil.dll`.

## Install

Extract **all** the files of the zip into your game folder (the folder with `LEVELS`, `CARS`…) and
run `FunTracks.exe`. If you already use the recomp there, keep your own `fun_tracks_recomp.ini`
(your settings) and only replace `FunTracks.exe`.

## What to test

1. **Controllers** ([issue 11](https://github.com/Karlos-fr/fun-tracks-recomp-releases/issues/11)):
   in OPTIONS → PLAYER 1 OPTIONS, CONTROLS is now **KEYBOARD** or **CONTROLLER** (the old
   joystick modes and their calibration pages are gone). With CONTROLLER, the buttons set in
   OPTIONS → PLAYERS are used in races, triggers included, and steering, accelerator and brake are
   progressive (left stick and triggers). An old settings file using a joystick mode switches to
   CONTROLLER by itself.
2. **Steam and GOG files (Ignition)**
   ([issue 1](https://github.com/Karlos-fr/fun-tracks-recomp-releases/issues/1)): with the files
   extracted from `game.gog`, the intro should now play to the end instead of stopping on a white
   screen.

Please report in the matching issue: what works, what doesn't, and your controller model.

## Other changes in this build

- Races compute exactly the same on every platform (random draws and maths).
- HD texture packs are only made when the 3D renderer is chosen.

Full list: the *Unreleased* section of [CHANGELOG.md](../../CHANGELOG.md).
