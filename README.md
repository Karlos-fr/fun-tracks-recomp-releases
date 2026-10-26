![Fun Tracks](images/header.png)

# Fun Tracks — recompiled

Fun Tracks (1997) is a top-down racing game with small toy cars on dirt tracks, cornfields and
canyons. This project rebuilds the original Windows game from its decompiled C code, so it runs
natively on today's systems.

This repository only hosts the **releases** (Windows 64-bit and Android). Current version:
**alpha** — expect bugs.

## You need the original game

**No file from the original game is included here.** You must own a copy of the original PC
game (Fun Tracks, 1997) and use the files of its installation folder (the folder that contains
`fun_win.btz`, `LEVELS`, `CARS`...).

Optional: the CD music can be played from OGG files named `Music/track02.ogg`,
`Music/track03.ogg`... in the game folder (ripped from your CD).

## Install — Windows 64-bit

Requirements: Windows 10 or 11 (64-bit), a graphics card with DirectX 12.

1. Download `FunTracks-…-windows-x64.zip` from the [Releases](../../releases) page.
2. Extract `FunTracks.exe` and `fun_tracks_recomp.ini` into your Fun Tracks game folder.
3. Run `FunTracks.exe`.

Keyboard as in the original game. Alt+Enter: fullscreen / window. F11: 3D renderer / original
renderer.

## Install — Android

Requirements: Android 10 or later, 64-bit ARM device. Made for handheld consoles with buttons
(tested on the AYN Odin 2 Portal); a gamepad is needed.

1. Download `FunTracks-…-android-arm64.apk` from the [Releases](../../releases) page and install
   it (allow installing apps from unknown sources).
2. Start the game once, then close it: this creates its data folder.
3. Connect the device to a PC with a USB cable and copy **the content** of your Fun Tracks game
   folder into `Android/data/com.karlos.funtracks/files/` on the device
   (or: `adb push <game folder>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Start the game.

To use the 3D renderer, also copy `fun_tracks_recomp.ini` (from the Windows zip) into that folder.

Gamepad: stick / d-pad to steer and move in menus, A to accelerate or confirm, B to brake or go
back, X turbo, LB / RB gears, Y rear view, Start pause. Buttons can be changed in the game's key
settings page.

## Known limitations (alpha)

- 4:3 picture only (black borders on wide screens).
- No network multiplayer.
- Only one player on Android.
