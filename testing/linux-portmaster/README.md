# Fun Tracks recomp — Linux ARM64 test build (PortMaster)

Test build for Linux handhelds (Anbernic RG35XX family and others) running a system with
PortMaster: Knulli, muOS, ROCKNIX, ArkOS/dArkOS, AmberELEC… It is **not a release yet**: a release
will be published once this build has been tested on real devices
([issue 9](https://github.com/Karlos-fr/fun-tracks-recomp-releases/issues/9)).

**No file from the original game is included.** You need your own copy of the original PC game
(Fun Tracks, 1997).

## Files

- [`funtracks.zip`](funtracks.zip): the port, ready to install (launch script `Fun Tracks.sh`
  and folder `funtracks/` with the game program `funtracks.aarch64`, Linux ARM 64-bit).

## Install

1. Download `funtracks.zip` and extract it **into the ports folder** of your system (the folder
   where PortMaster installs its ports, usually `roms/ports/`), so that you get
   `ports/Fun Tracks.sh` and `ports/funtracks/` side by side with your other ports.
2. Copy **the content** of your Fun Tracks install folder (the folder with `FUN_WIN.EXE`, `LEVELS`,
   `CARS`…) into `ports/funtracks/gamedata/`. Optional CD music: `Music/track02.ogg`,
   `Music/track03.ogg`… in the same folder.
3. Refresh the game list of your system (or restart it), then start **Fun Tracks** from the Ports
   section.

If the game files are missing, the port shows a message and quits.

## Controls

| Button | Action |
|--|--|
| D-pad / left stick | Steer, move in menus |
| A | Accelerate, confirm |
| B | Brake, back |
| X | Turbo |
| Y | Rear view |
| L1 / R1 | Gears |
| D-pad up | Headlights |
| Start | Pause |
| Select + Start | Quit |

Buttons can be changed in the game's key settings page.

## Renderer

The port starts with the **original 2D renderer**, which should run on every device. The 3D renderer
(OPTIONS → DISPLAY OPTIONS → ENGINE) needs Vulkan and Wayland on the device; without them, the game
goes back to the 2D renderer by itself. On the RG35XX family (H700) with Knulli or muOS, expect the
2D renderer only.

Settings are kept in `ports/funtracks/gamedata/fun_tracks_recomp.ini`.

## What to test

Please report in [issue 9](https://github.com/Karlos-fr/fun-tracks-recomp-releases/issues/9),
with your device, its system and version:

1. The game starts: logo, intro, menus.
2. A single race from start to finish: smooth or slow?
3. Gamepad in the menus and in the race, and quitting with Select + Start.
4. Sound effects, and CD music if you added the OGG files.
5. Optional: the 3D renderer, if your system has Vulkan.

**Log file**: after each launch, `ports/funtracks/log.txt` holds the game's messages. Please
attach it to your report, above all after a problem.

## Known limitations

- First Linux build: only tested on a PC (Linux, and ARM64 under emulation), not yet on a handheld.
- No automatic update on Linux: new test builds will be posted here.
