# Changelog

All notable changes to the Fun Tracks recompilation are listed here, newest first.

## [Unreleased] — next alpha

### Added

- OPTIONS → ATMOSPHERE (3D renderer): weather, weather on the camera, rain ripples, time of day and
  the new SKY line, gathered in one sub-menu.
- SKY (with DYNAMIC lighting): a real sky behind the scenery instead of the plain background, seen
  as soon as the camera is low: blue with drifting clouds by day, a red sunset at dusk, stars at
  night, grey and overcast in the rain; each track keeps its own light. Water, wet roads, puddles
  and cars reflect it.
- Puddles under added rain or storm (with REFLECTIONS): mirror-like water with irregular edges and
  a soaked fringe of darker asphalt, reflecting the sky and the scenery.
- Splashes: cars running through puddles throw side sheets and a rear spray of drops that fall and
  bounce, leaving a veil of mist behind the wheels.

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

[0.5.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.5.0-alpha
[0.4.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.4.0-alpha
[0.3.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.3.0-alpha
[0.2.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.2.0-alpha
[0.1.0-alpha]: https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases/tag/v0.1.0-alpha
