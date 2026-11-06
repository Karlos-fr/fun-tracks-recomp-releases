# Changelog

All notable changes to the Fun Tracks recompilation are listed here, newest first.

## [Unreleased]

### Added

- Graphics options: SMOOTH SURFACES (3D renderer, with the dynamic lighting). Light changes smoothly
  from one face to the next instead of showing the facets of the scenery, while sharp edges stay sharp.
  The normals are computed over the whole track at once, so no step of light remains between its
  sections.
- Graphics options: ROUNDED SHAPES (3D renderer), a slider. The faces of the scenery (not the road,
  water nor moving objects) are cut and bulged, without cracks between the sections of the track, in
  races and in the menus. The slider sets which edges get rounded: higher values round sharper edges
  too. It costs about 10 % of the frame rate.
- Graphics options: CAMERA SHAKE (3D renderer), a strength slider, off by default. The camera shakes
  when the player's car takes a shock (crash, jump landing, big bump), more for a bigger shock; in
  split screen, each view follows its own player. The race itself does not change.
- HD texture pack: textures of three more tracks (Gold Rush, Snake Island and Lost Ruins), the race
  effects (sparks, police lights, dust, smoke, explosions), the dashboards for two and more players,
  the championship cups and the car medallions.

### Fixed

- CD images: with the game played from a `.cue`/`.bin` or `.iso` image, there were no sound effects
  and no sound in the intro, while the music played (issue 12). The sound folders inside the image
  are now found.
- HD texture pack: the pause menu, the quit prompt and the race results and score screens kept HD
  capsules, letters and car icons of the previous screen underneath the new ones (overlapping menus,
  black squares around the car icons), and after a while some menu capsules showed no text (issue 13).
- HD texture pack: the speed digits touched the edge of their window and the needle hub was too small
  (issue 13); the speedometers now match the original dials.
- HD texture pack: on Lost Ruins, the jungle foliage and the waterfall mist would show gold and red
  patches instead of green leaves and white mist; sparks and police lights keep their glow and colours.

- 3D renderer: trees, the start banner, fences and the other cut-out objects now cast shadows, shaped
  like their picture.
- Frames per second: with the FRAMES PER SECOND setting at 60, the race showed about 45 uneven frames
  per second while the counter said 60 (issue 8); frames between two game steps now land on their
  screen refresh and are placed evenly, which also removes a small stutter with MAX.

## [0.9.0-alpha] — 2026-11-04

Ninth alpha release: every edition of the game (Fun Tracks, Ignition, Bleifuss Fun; CD, CD image,
GOG and Steam), texture packs made of real artwork, larger menus, car suspension in 3D, Linux test
builds for PCs and for PortMaster handhelds, and many 3D fixes (lightning, beacons, shadows).

### Added

- Graphics options: MENU SIZE (NORMAL, LARGE or LARGER). Menus can be 1.25 or 1.5 times bigger, so
  they are easier to read on large screens. In 3D, even the longest pages still fit on screen, in
  widescreen or 4:3.
- Graphics options: SUSPENSION (3D renderer). As in the DOS version, the car bodies lean out of
  curves, dip under braking and lift when accelerating, while the wheels stay on the road. It
  changes only the picture, not the race.
- Menus: holding an arrow key (or the D-pad) keeps moving through the menu, after a short delay,
  about nine times a second.
- Every edition of the game is supported: **Fun Tracks** (French), **Ignition** (English, Spanish,
  Italian, Swedish; CD, GOG and Steam) and **Bleifuss Fun** (German). The game can be read from an
  installed copy, from the folder installed by GOG or Steam (the DOS version, with the CD kept in
  `game.gog`), or directly from an image of the game CD (`.cue` with its `.bin`, or `.iso`). Ignition
  keeps its records in `ign_win.btz`, as the original did. Checked on four CDs and on GOG: races
  look the same, pixel for pixel, in every edition. Steam is not tested on a real installation yet.
- HD texture pack, a separate download: `FunTracks-hd-pack-0.1.0-alpha.zip` (unzip it into the game
  folder, then GRAPHICS OPTIONS → TEXTURES). Partial: race HUD and its fonts, signs and start lights,
  menu logo, capsules and font, car cards, loading screens, car textures and the first track, Moosejaw
  Falls. Its README gives its version and the fonts its letters are drawn from. How to make other
  packs: [Making a texture pack](https://github.com/Karlos-fr/fun-tracks-recomp-releases/wiki/Making-a-texture-pack) (draft).
- Music can also be played from WAV files (`Music/trackNN.wav`) or from the audio tracks of a CD
  image.
- READMEs: a table of the supported editions and installations (CD, CD image, GOG, Steam, DOS-only),
  with what has been checked.
- Linux for PCs (x86_64), test build: `FunTracks-0.9.0-alpha-linux-x64.tar.gz`. Unpack it into the folder
  of the game files (or next to a CD image) and run `FunTracks.sh`. It needs glibc 2.35 or newer; the 3D
  engine uses Vulkan, and without a Vulkan driver the game falls back to the original renderer.
- Linux ARM64 for PortMaster handhelds, test build, now attached to the release:
  `FunTracks-0.9.0-alpha-linux-arm64-portmaster.zip`; the `testing` folder of this repository is gone. It
  supports every edition; its launcher also accepts a CD image in
  `gamedata/`. READMEs: an install chapter for both Linux builds.

### Changed

- Texture packs (3D renderer), reworked. A pack is a folder in `packs/` next to the game files, chosen
  in the graphics options: the TEXTURES line now lists ORIGINAL and the packs found. A pack follows
  the paths of the game files, one image per image in the file: `CARS/Cars.tex/00.png` replaces the
  first page of `CARS/Cars.tex`. Images can have any size as long as they keep the proportions of the
  original; whatever a pack lacks stays original. It covers the textures of the cars, scenery and
  effects, and the race HUD: a block of a picture sheet (`H_pan1.pic/0_72_157_130.png`, the rev
  counter) or a letter of a font (`fonts/POS_H.LFT/0036.png`); see-through glass on the counters stays
  see-through. In the menus (with the background race), the capsules become whole HD pills from
  `MenuBkg.dat/capsule.png` and `capsule_bleu.png`, drawn at screen resolution with the texts over
  them, the settings pages included; the menu font and the car cards have HD images too (the letters
  of the HD font are see-through around them). A page can also be given one texture at a time
  (`LEVELS/Canada/CANADA.TEX/05/0_128_64_64.png`, a 64 × 64 texture of page 5), the cells of the 3dfx
  scenery under the place they come from in the `.TFX` file; a texture the game rewrites (animated
  water) stays original. The track loading screen is drawn by the graphics card too, with the track
  picture of the pack (`LEVELS/Canada/CANADA.PIC/0_0_320_200.png`) under the HD capsules, texts and
  frame. The menu logo, the race signs and start lights and the HUD fonts (position, times, speed) can
  be replaced too. Pack pages are compressed by the graphics card (BC3, 4096 × 4096 pages at a
  quarter of the memory) and kept in `packs/<name>/.cache`, so later launches read them back instead of
  decoding the images. `tools/dump_textures.py` and `tools/dump_interface.py` write the
  original images under these names, and `tools/make_pack.py` builds a pack from page images or from
  single interface elements.

### Removed

- The HD texture packs the game made by itself on first launch (`textures_hd`), the HD 2X / HD 4X
  values of the TEXTURES line and `tools/upscale_textures.py`: a pack is now real artwork, chosen by
  the player. The old `textures_hd` folder can be deleted.

### Known limitations

- Linux: both builds are test versions. The PC build was only tried under WSL (Windows Subsystem for
  Linux), the PortMaster build not yet on a real handheld.
- Steam: not yet tested on a real installation.
- The HD pack covers the interface, the cars and Moosejaw Falls only: the other tracks keep their
  original textures.
- Network game tested between a PC and an Android console on the same Wi-Fi network, not yet
  between two PCs nor over the Internet with real players.

### Fixed

- 3D renderer: the lightning of the Moosejaw Falls storm shows again. Its bolt was never handed to
  the 3D renderer, which skipped it.
- 3D renderer: a crushed car stays visible, flattened, instead of vanishing.
- 3D renderer: flashing beacons shine by day and at night. Their flash keeps a halo by day; at night
  it glows instead of making a dark disc, and the beacons (like the start banner and smoke) are lit by
  headlights and lamps instead of staying black.
- HD menu letters sit a little lower in their capsules instead of touching the top, and the Q stands on
  the same line as the other letters.
- 3D renderer with HD textures: pack images now follow the palette effects of the game, the flash of
  a lightning bolt and the darker colours of the rain zone, as the original textures do.
- 3D renderer with HD textures: the start banner of Moosejaw Falls (a face with see-through parts)
  takes its pack image; such faces used the original texture.
- 3D renderer: sun shadow edges are smooth instead of showing stair steps, with or without soft
  shadows; the car previews of the menus are anti-aliased too (FXAA or MSAA).
- GOG, Steam and other DOS installations: the game no longer stops on a missing `Default.psq` (issue
  10); it reads the Windows files from the CD image, or the DOS ones.
- 3D renderer: the 3DFX EFFECTS and SCENERY lines are greyed out when the 3dfx patch files (`.TFX`)
  are missing, instead of doing nothing.
- Moosejaw Falls: the rain on the dirt section, up to the bridge, shows again in the 2D renderer of
  the 64-bit builds (Windows, Android, Linux). Its drops were drawn by a 1997 assembly routine that
  had not been rewritten in C yet. All the remaining drawing routines of the 2D renderer are now in
  C, checked pixel for pixel against the original on every track.
- 3D renderer: the game's own rain drops now show with the ORIGINAL weather, drawn like the 2D
  renderer. An added weather (rain, storm, snow) replaces them.
- Player names keep their capital letters in `fun_tracks_recomp.ini` (they were read back in lower
  case).
- The settings file can no longer be lost if writing it fails: it is written in full beside the old one,
  then put in its place. Saving a player now writes the file once instead of 23 times.
- 32-bit builds: a corrupt track surface file (`.SRF`) announcing huge dimensions is now refused, as in
  64-bit builds.
- 3D renderer with HD textures: fewer stutters when going from the menus to a race. The game frees and
  reloads the same textures between screens; the decoded HD images are now kept (128 MB at most)
  instead of being read and decoded again, about 6 ms each. Over a menus-then-race run, 26 decodes
  instead of 58.

## [0.8.0-alpha] — 2026-11-03

Eighth alpha release: smooth frame rate beyond 36 images per second in 3D, a modern controller with
progressive stick and triggers, a Linux test build for handhelds, the Steam and GOG intro fixed, and a
clear message instead of a crash when a game file is missing.

### Added

- Linux ARM64 test build for handhelds with PortMaster (Anbernic RG35XX family and others):
  [testing/linux-portmaster](testing/linux-portmaster), not a release yet. The 3D renderer works
  on Linux too (Wayland or X11, with Vulkan); without Vulkan the game goes back to the 2D renderer
  by itself.
- Graphics options: FRAME RATE (36, 60, 120, 144 or MAX, MAX by default). With the 3D renderer,
  races and the live race behind the menus are no longer limited to the game's 36 steps per
  second: in-between images show the camera and the cars between two steps, up to the chosen rate
  or the screen's. The race itself is unchanged and adds no input delay; 36 gives the 1997 look,
  one image per step. Rain, ripples, flicker and other 3D effects follow game time, so they keep
  the same speed at any frame rate.

### Changed

- Races compute exactly the same on every platform: random draws now follow the sequence of the
  original 1997 game everywhere, and Android and Linux do their maths like Windows (no fused
  multiply-add on ARM).
- HD texture packs are made only when the 3D renderer is chosen (at launch, or when switching to
  3D): with the 2D renderer they kept the computer busy for nothing.
- Player options: CONTROLS is now KEYBOARD or CONTROLLER, the same setting as the player's device
  in PLAYERS. The 1997 joystick, pedals and joypad modes, with their fixed buttons, are gone with
  their calibration pages; a settings file using them switches to CONTROLLER. With a controller,
  steering, accelerator and brake are progressive (stick and triggers).
- Code cleanup, with no change in the game: code that nothing used is removed (measured by the
  linker on the 64-bit and 32-bit builds), sizes and counts are written in decimal, and no name
  in the C code carries an address of the original program any more. Every routine now has a
  complete comment (parameters and returned value).

### Known limitations

- Frame rates above 60 tested in races and in the menus, not yet measured on 120 and 144 Hz screens.
- Linux: a test build, not yet tried on a real handheld.
- Network game tested between a PC and an Android console on the same Wi-Fi network, not yet
  between two PCs nor over the Internet with real players.

### Fixed

- Controller buttons changed in PLAYERS were ignored in races when CONTROLS was set to a joystick
  mode: A and B kept accelerating and braking, the stick gave turbo and rear view, and the
  triggers did nothing.
- Steam and GOG releases (Ignition, the English edition of the game): the game stopped on a white
  screen after the first two intro videos, because Ignition names its intro videos differently.
- A game folder missing some original files (for example `Baltazar\data\Default.psq`) made the
  game crash right after the intro videos, or quit without a word later on. Whenever the game
  needs a file that is not there, a message in the game's language now gives its full path, then
  the game stops.

## [0.7.0-alpha] — 2026-11-02

Seventh alpha release: realistic light with a moon and its phases, two-level shadows, reflective car
paint and water, a headlights key, a 3D start in the background with a progress capsule, and an
update check on Windows.

### Added

- OPTIONS → ATMOSPHERE, new lines (3D renderer, DYNAMIC lighting): LIGHT (soft or realistic),
  SUN HEIGHT and SUN DIRECTION, SOFT SHADOWS, FILM LOOK, GLOW, LIGHT RAYS, AMBIENT SHADING,
  CLOUDS, RAIN AMOUNT and WIND. Realistic light takes its colour, sky light and exposure from the
  height of the sun, so the scenery looks right at any time of day.
- Sliders in the settings pages for amounts (sun position, shadow softness, glow, clouds, rain,
  wind…); RELIEF becomes a slider too.
- Car paint reflections (with REFLECTIONS): cars mirror the sky and the ground with a horizon line,
  more at grazing angles, and catch glints from the sun or the moon; metallic paint tints its
  reflections and sparkles in the sun, windows are darker and more mirror-like.
- Water (with REFLECTIONS): seas, lakes and rivers behave like the puddles, reflecting the sky and
  the scenery, with waves, a slow swell and sun glints (Snake Island's sea included).
- A moon in the night sky, lighting the track with a bluish moonlight; MOON PHASE chooses how much
  of it is lit, from a thin crescent to a full moon.
- Windows: at launch, the game checks GitHub for a newer version and shows its release notes; INSTALL
  AND RESTART downloads its zip, unpacks it, closes the game, puts the new files in place (your
  settings file is kept) and restarts. UPDATES in DISPLAY OPTIONS turns the check off.
- HEADLIGHTS key to switch your car's headlights on or off (L for player 1, X for player 2, D-pad up
  on a gamepad), set like the other keys in the player settings. They are on at night and off by day
  when the race starts.
- RAIN AMOUNT also sets the puddles and the drops hitting the ground: small, rare puddles in a
  drizzle, wide ones and many ripples in a downpour.

### Changed

- Faster start with the 3D renderer on Windows: the window opens at once and the logo and intro play
  while the 3D renderer gets ready in the background (PREPARING 3D and a progress capsule at the bottom), then the
  game switches to 3D without a flash.
- Shadows use two maps: a fine one around the camera for sharper shadows, and a wide one for the
  distance, blended into each other, so long shadows of cliffs and buildings are drawn in full.
- REFLECTIONS cost less (about 1 to 2 ms per frame on a GTX 1050), with the same picture: the sky
  is no longer computed for dry ground, and water skips the work it does not need.

### Known limitations

- The update check starts with this version: from 0.6.0 or older, install 0.7.0 by hand.
- Atmosphere, car and water reflections tested on PC, not yet with a gamepad on an Android console.
- Network game tested between a PC and an Android console on the same Wi-Fi network, not yet
  between two PCs nor over the Internet with real players.
- Android: same-screen multiplayer not yet tested on a device; game files must be copied to the
  device by hand.

### Fixed

- The shadow of a tall cliff grew longer as the camera came closer.
- With the 3dfx effects, the arrow above the player's car at the start was an orange square.
- With the 3dfx shadows, the car's original shadow stayed under it next to the dynamic shadow.
- The menus no longer close to show the credits while the background race is running.
- Widescreen: the closing circle of the menus only covered the top-left corner, and the opening
  circle of a race ended abruptly on the sides.

## [0.6.0-alpha] — 2026-11-01

Sixth alpha release: a real sky, puddles and splashes, HD textures made on first launch, round
wheels, one settings page for the menus and the pause, and a faster 3D start on Windows.

### Added

- HD textures without any download: on first launch, the game upscales the textures of your own
  install in the background (a few seconds) into a `textures_hd` folder; TEXTURES (HD ×2 / HD ×4)
  then becomes available, with MIPMAPS on. Images already in `textures_hd` are kept.
- OPTIONS → ATMOSPHERE (3D renderer): weather, weather on the camera, rain ripples, time of day and
  the new SKY line, gathered in one sub-menu.
- SKY (with DYNAMIC lighting): a real sky behind the scenery instead of the plain background, seen
  as soon as the camera is low: blue with drifting clouds by day, a red sunset at dusk, stars at
  night, grey and overcast in the rain; each track keeps its own light. Water, wet roads, puddles
  and cars reflect it.
- Puddles under added rain or storm (with REFLECTIONS): clear water with irregular edges and a
  soaked fringe of darker asphalt. Seen from above you see the asphalt through it; at low angles it
  reflects the sky and the scenery. Headlights and street lamps light it up, and wheels leave
  ripples that spread and fade.
- Splashes: cars running through puddles throw a crown of water as they enter, then a translucent
  sheet and a rear spray that fall back, with a veil of mist pushed by the wind. Every crossing
  looks different (strength, side drift, more water on the outside of a bend).
- ROUND WHEELS (DISPLAY OPTIONS, 3D renderer, off by default): the cars' five-sided wheels become
  round, keeping their painted rims, and they roll with the car's speed, backwards in reverse.

### Changed

- One settings page for the menus and the pause menu: the pause OPTIONS line opens the same DISPLAY
  OPTIONS page as the menus (3D renderer), with its ATMOSPHERE and 3DFX sub-pages, the same look and
  scroll arrows. Lines that cannot change during a race (engine, resolution, format…) are greyed out.
- The key help lines are gone from the settings pages, the network lobby and the player panels.

### Known limitations

- Puddles and splashes tested on PC, not yet with a gamepad on an Android console.
- Network game tested between a PC and an Android console on the same Wi-Fi network, not yet
  between two PCs nor over the Internet with real players.
- Android: same-screen multiplayer not yet tested on a device; game files must be copied to the
  device by hand.

### Fixed

- DISPLAY OPTIONS no longer crashes with a settings file saved by an older version.
- Changing TEXTURES in the settings page could switch the renderer.
- HD textures no longer slow down the menu background race.
- The OPTIONS page opens on its first entry at launch.
- Windows, windowed mode: the window opens centred with its title bar (move, minimise, maximise)
  and can be resized.
- Alt+Enter switches between full screen and window at once (it took several seconds).
- Faster start with the 3D renderer on Windows (Direct3D 12): about 4 seconds instead of 11.

## [0.5.0-alpha] — 2026-10-30

Fifth alpha release: network game between PCs and Android consoles, and the look of the 1997 3dfx
edition.

### Added

- Network game for 2 to 6 players (PC or Android console), one player per machine, on the local
  network or over the Internet, with the 1997 game's own rules (single race, time limit and chase
  modes, host restart, players leaving). MULTI PLAYER → NETWORK GAME opens a lobby: NAME, CREATE A
  GAME, local network games found automatically, or an ADDRESS to join over the Internet (typed on
  the keyboard, the on-screen keyboard on Android, or with the gamepad).
  - Over the Internet: remote cars are smoothed on screen, car updates drop to 30 per second on a
    slow link, packets are compressed, and the session page shows the round trip and packet loss.
  - Clear messages: game not found, game already started, other version, port already in use, host
    has left. A host that vanishes in a race is noticed within seconds.
  - The host opens or forwards UDP port 17970 on their router to play over the Internet.
  - Tested between a PC and an Android console (Odin 2 Portal) on home Wi-Fi: lobby, race, pause,
    host restart, players leaving.

- OPTIONS → 3DFX (3D renderer): the rendering differences of the 1997 3dfx edition, one per line or
  all at once with PRESET, checked side by side against the original 3dfx game:
  - EFFECTS: the 3dfx effect pictures, with glowing additive smoke, sparks and glints.
  - SCENERY: the tracks' redrawn details of the 3dfx edition (painted sea on Snake Island, foliage
    and banners on Lost Ruins, clouds, fences, flags, street lamp cones in Tokyo).
  - RAIN: Moosejaw Falls' own rain as thin blue-to-white glowing streaks.
  - SHADOWS: the game's shadows as soft half-transparent shapes.
  - COLOURS: 16-bit dithered colours, like a Voodoo card.

### Known limitations

- Network game tested between a PC and an Android console on the same Wi-Fi network, not yet
  between two PCs nor over the Internet with real players.
- Android: same-screen multiplayer not yet tested on a device; game files must be copied to the
  device by hand.
- The 3dfx look was compared with the original 3dfx game on still pictures and short drives, not
  over full played races.

### Fixed

- Android: the game no longer closes when it comes back after being sent to the background (home
  screen, settings).
- Android: the network pause menu no longer flickers (one frame in two was black).
- The idle credits no longer start in the network lobby or while a network game is open, where
  they hid the game choices.

## [0.4.0-alpha] — 2026-10-29

Fourth alpha release: same-screen multiplayer for up to six players, reflections and wet roads.

### Added

- Same-screen multiplayer for up to six players with a 3D engine: two at most on the keyboard (its
  left and right halves), the others on gamepads. MULTI PLAYER → SPLIT SCREEN: each gamepad joins or
  leaves with Y, the left half of the keyboard with one of its keys; then everyone picks a car at the
  same time, each in their own frame. Views split and merge with the race: players close together
  share a view, the ones who pull away get their own (1 to 6 views), with a small J1 to J6 marker
  above each car, sized by distance. The software engine keeps the original two-player game.
- Player settings (OPTIONS → PLAYERS, Select on the join screen, PLAYERS line of the pause menu):
  device, a control for each action captured on the player's own device, default controls, gearbox
  and automatic acceleration, saved as `playerN_*` keys. Whoever pauses drives the pause menu with
  their own device.

- New graphics options, off by default, greyed out without DYNAMIC lighting:
  - REFLECTIONS (OFF / ON): each surface shines according to its material (glossy car paint, water,
    slightly shiny asphalt, matte rock and grass). With added rain or storm, the ground gets wet:
    darker, glossy asphalt and puddles. On a wet road, headlights, tail lights, street lamps and the
    cars themselves are mirrored in long streaks, like on a real road at night in the rain. The sea
    and the game's animated water mirror the scenery too, rain or not.
  - REFLECTIONS can be set to FULL: real screen-space reflections of the scenery, cars and lamps on the
    wet road (smooth streaks) and on puddles and water (sharp), instead of light streaks only.
  - RAIN RIPPLES (OFF / ON, with REFLECTIONS and added rain or storm): raindrops hit the wet road and
    the water, each one spreading two or three fine rings of its own size that fade out.
  - SURFACE RELIEF (OFF / ON): rocks, verges and the road gain real volume from their own textures,
    fading out smoothly in the distance.

- Pause menu: a new OPTIONS line opens the graphics enhancements, applied at once without leaving
  the race.
- FPS COUNTER (OFF / ON): a small, discreet frame rate counter in the top right corner.
- SMOOTH INTERFACE (OFF / ON): menus, texts and gauges with rounded pixel staircases and soft edges,
  at the same size.

### Changed

- The settings file `fun_tracks_recomp.ini` uses English keys and values (`engine=software`,
  `weather=rain`, `reflections=full`…). It is created with all its default values when missing; an
  existing file keeps your choices and comments, its former French names being translated
  automatically.
- Menus with a 3D engine use the whole screen at the same scale: the graphics options show 14 lines
  instead of 6, in two aligned columns. Scroll arrows sit in their own row, only when lines are hidden on that
  side, and no longer overlap the title. Menus no longer wrap around from the last line to the first.
  ENGINE is the first line of the graphics options, and long labels no longer overlap their value.
- Night: the flashing beacons light their surroundings while they flash, and the turbo stars glow.
- Faster graphics enhancements on large screens: rain drops lit once per drop instead of once per
  pixel, and lamps entirely behind the camera skipped.
- Car lights at night look photo-realistic: headlights only dazzle when facing the camera (from behind
  you see their warm beam on the road), tail lights glow red from behind, and brake lights fade in and
  out like real bulbs, three to four times brighter, lighting the road behind the car.
- Car lights sit exactly on the lights drawn on each car, with their own number, size and shape: the
  police car's twin headlights, the jeep's three stacked tail lights, the school bus's round tail
  lights and roof marker lights, the long tail light strips of the black car. Each light glows over
  its drawing, round or straight-edged, following the bodywork in perspective.
- Added rain looks more like real rain: drops only show by the light they catch, so at night they
  glitter in the headlight beams; close to the camera they are blurred and almost transparent, and
  their streaks vary in length and strength.

### Known limitations

- No network multiplayer.
- Android: same-screen multiplayer not yet tested on a device; game files must be copied to the
  device by hand.

### Fixed

- Weather effects no longer repeat: rain ripples fall anywhere on the ground (no grid pattern) and
  no longer replay the same drops every 100 seconds; each rain drop and snowflake takes a new place
  every time it falls; rain ripples, drops on the camera and lightning differ from one game to the
  next.
- Night lights: the glow of car lights was hidden by the bodywork up close, or shown as large blobs
  below the lights from afar.
- Night lights: a car's headlights no longer switch off at once when it drops out of the screen
  behind the camera; car lights now fade out with distance.
- Menu background race: the cars were squashed after the menus grew taller.
- Pause menu: the OPTIONS line was cut at the bottom of the panel.
- Menus: coming back from a race could leave them in black and white.
- Weather on the camera: two drops could swallow each other over and over and grow until they hid
  the whole screen.
- Wet road: no more stair-shaped grey patches or visible triangles; puddles have round edges, wet
  tyres stay dark and the reflection streaks are smooth.

## [0.3.0-alpha] — 2026-10-28

Third alpha release: 3D graphics enhancements (textures, anti-aliasing, weather, lighting, night).

### Added

- 3D graphics enhancements, as new lines at the end of the graphics options (all off by default,
  greyed out in software, saved in `fun_tracks_recomp.ini`):
  - FILTERING (SHARP / SMOOTH): textures smoothed without blurring their colours together.
  - MIPMAPS and ANISOTROPIC (up to 16×): no more shimmering in the distance, the road stays sharp
    up to the horizon.
  - SHARPENING (LOW / MEDIUM): restores crispness to the 3D scene; the HUD is untouched.
  - ANTI-ALIASING (OFF / FXAA / MSAA 4X): smooths the jagged, stair-stepped edges of the 3D scene
    (road borders, start banner). MSAA 4X fixes the edges exactly; FXAA is lighter but also softens
    the game's high-contrast textures a little. The HUD and menus stay sharp.
  - TEXTURES (ORIGINAL / HD 2X / HD 4X): HD texture packs. `tools/upscale_textures.py` builds them
    from your game files in about a minute (pixel-art upscaling, no invented details);
    `tools/dump_textures.py` extracts the original pages if you want to retouch them. Animated
    textures (water) are never replaced and keep moving.
  - WEATHER (ORIGINAL / RAIN / STORM / SNOW): rain, storms with lightning, or snow on any track. It
    is scenery only: races and the AI are unchanged.
  - WEATHER ON CAMERA (OFF / ON, with an added weather): rain and snow hit the camera lens, like in
    real rainy racing footage. Drops are soft, out-of-focus blobs that distort the scene behind
    them; heavy ones slide down, merge and leave a wet trail, faster and more often the faster you
    drive; snowflakes land as white blurs and melt into water. The HUD stays sharp.
  - LIGHTING (ORIGINAL / DYNAMIC) and SHADOWS (ORIGINAL / SIMPLE / DETAILED): a sun per track that
    shades the scenery, and real shadows for cars (and the whole scenery in DETAILED).
  - TIME OF DAY (ORIGINAL / DAY / DUSK / NIGHT): a real night, with headlights lighting the road,
    discreet tail lights, brake lights that glow on the road behind a braking car, and lit street
    lamps, all with a soft glow. Markers (the arrow above your car, car names) stay bright at night.

### Changed

- 3D renderer rebuilt on a cleaner base: the game now tells the renderer exactly which data it may
  read and when it is freed, which parts of the picture are interface, and which full-screen effects
  to apply, instead of the renderer guessing them. About 20% less time per frame in 3D.
- The menu transitions (entry, exit and race start) now cover the whole screen in 3D, and the live
  demo keeps running behind them instead of turning black.

### Known limitations

- No network multiplayer.
- Android: one player only; game files must be copied to the device by hand.

### Fixed

- 3D renderer: the game could crash now and then when going back to the menus after a race (for
  example after QUIT, then starting another race). The cause is fixed.
- 3D renderer, Tokyo Bullet: the street lamp halos now show, as in the original game.
- 3D renderer: the race opening circle has a soft edge again, and it darkens the HUD outside the
  circle, as in the original game.

- 3D renderer: after playing several tracks, the scenery could stay black, and cars or their
  tyres could vanish until the renderer was switched (F11). Tracks now load fully every time.
- 3D renderer, Tokyo Bullet: large white patches no longer cover the screen when the camera
  passes close to a street lamp glow.
- 3D renderer: cars no longer sink into the ground.
- 3D renderer, Yodel Peaks: the drifting mist no longer has a pink tint.
- 3D renderer: the pause menu text on Snake Island is drawn cleanly.
- 3D renderer: no more thin line above "TOTAL TIME".
- 3D renderer: leaving the menus for a race no longer shows a black box over the live demo.

## [0.2.0-alpha] — 2026-10-27

Second alpha release: widescreen, six languages, live menu demo.

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
- Live demo behind the menus (3D only): instead of the original recorded video, a real race on
  Moosejaw Falls (Canada) driven by six AI cars, without HUD, filmed with changing camera shots
  (crane, chase, front, high, orbit) like the original demo; the team credits still scroll over
  it. A new race starts when one ends.
- New LIVE DEMO line in the graphics options (ON or OFF, greyed out in software), saved in
  `fun_tracks_recomp.ini` (`demo = oui` or `non`).

### Changed

- Settings that have no effect with the chosen renderer are greyed out: resolution, mip-mapping
  and perspective polygons in 3D, aspect in software.
- In 3D, races always use the high-resolution interface layout (sharper HUD); the keypad + and −
  keys no longer change the resolution there. The resolution setting still applies to the
  software renderer.
- Menus keep the size they have at the game resolution, like the pause menu: in 3D they take the
  middle of the screen with the live demo all around; in software they follow the chosen
  resolution.
- The game keeps running when its window loses focus (it used to freeze).

### Known limitations

- No network multiplayer.
- Android: one player only; game files must be copied to the device by hand.

### Fixed

- 3D renderer: a crash that could happen when leaving a race back to the main menu.
- Menu scroll arrows no longer show a blue box around them.
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

[0.9.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.9.0-alpha
[0.8.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.8.0-alpha
[0.7.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.7.0-alpha
[0.6.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.6.0-alpha
[0.5.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.5.0-alpha
[0.4.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.4.0-alpha
[0.3.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.3.0-alpha
[0.2.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.2.0-alpha
[0.1.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.1.0-alpha
