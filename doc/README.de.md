<p align="center">
  <img src="../images/header.png" alt="Fun Tracks Recomp" width="760" />
</p>

<p align="center">
  <a href="../README.md"><img src="../images/flags/flag-gb.svg" alt="" width="18" height="12" /> English</a>
  /
  <a href="README.de.md"><img src="../images/flags/flag-de.svg" alt="" width="18" height="12" /> Deutsch</a>
  /
  <a href="README.it.md"><img src="../images/flags/flag-it.svg" alt="" width="18" height="12" /> Italiano</a>
  /
  <a href="README.es.md"><img src="../images/flags/flag-es.svg" alt="" width="18" height="12" /> Español</a>
  /
  <a href="README.sv.md"><img src="../images/flags/flag-se.svg" alt="" width="18" height="12" /> Svenska</a>
  /
  <a href="README.fr.md"><img src="../images/flags/flag-fr.svg" alt="" width="18" height="12" /> Français</a>
</p>

https://github.com/user-attachments/assets/8c41af54-9f3b-44e0-af5b-05ec92f7762c

# Fun Tracks — neu kompiliert

Fun Tracks (1997) ist ein Rennspiel aus der Vogelperspektive mit kleinen Spielzeugautos auf
Feldwegen, in Maisfeldern und Canyons. Dieses Projekt baut das ursprüngliche Windows-Spiel aus
seinem dekompilierten C-Code neu auf, damit es nativ auf heutigen Systemen läuft.

Dieses Repository enthält nur die **Veröffentlichungen** (Windows 64-Bit und Android). Aktuelle
Version: **Alpha** — mit Fehlern ist zu rechnen.

## Wie diese Neukompilierung entstand

1. **Dekompilierung.** Die ursprüngliche Programmdatei (`FUN_WIN.EXE`, 1997 mit Microsoft
   Visual C++ 4.2 erstellt) wurde Routine für Routine in lesbares C zurückübersetzt. Jede Routine
   wird mit demselben Compiler von 1996 erneut übersetzt und mit dem ursprünglichen Maschinencode
   verglichen: gleicher Ablauf, gleiches Verhalten, und die meisten sogar Byte für Byte.
   Fortschritt dieser Arbeit:
   [Dekompilierungs-Tracker](https://karlos-fr.github.io/fun-tracks-decomp-progress/).
2. **Neukompilierung.** Dieser C-Code wurde dann in ein modernes Projekt übernommen und mit
   heutigen Compilern in 64-Bit gebaut. Das Spiel selbst (Rennen, Autos, KI, Menüs) ist der
   dekompilierte Code; ersetzt wurde nur, was mit Windows 95 sprach: DirectDraw, DirectSound und
   DirectInput wichen SDL3, und ein neuer GPU-Renderer zeichnet das 3D-Bild.
3. **Prüfungen.** Ein Test-Harness spielt geskriptete Partien mit fester Uhr und Tastatur und
   zeichnet jedes Bild auf (Bild, Rennzeiten, Positionen der Autos). Dieselben Partien werden zum
   Vergleich mit der ursprünglichen Programmdatei abgespielt, und jede Änderung muss diese
   Aufzeichnungen unverändert lassen.
4. **KI, offen gesagt.** Diese Arbeit entstand mit KI-Programmieragenten: **OpenAI Codex** und
   **Anthropic Claude** (Claude Code). Sie lesen den Assemblercode, schreiben und testen den
   C-Code und die Werkzeuge; ein Mensch leitet das Projekt, spielt, testet und entscheidet.
   Nichts wird ungeprüft übernommen: Jeder Schritt wird durch die obigen Vergleiche kontrolliert.

## Wichtigste Neuerungen

Im Vergleich zum Originalspiel von 1997:

- **GPU-3D-Renderer** (Direct3D 12 unter Windows, Vulkan unter Android), neben dem
  ursprünglichen Software-Renderer; F11 schaltet zwischen beiden um.
- **Breitbild** in 3D: Rennen füllen 16:9- und 21:9-Bildschirme, die Rennanzeige wandert an die
  Bildschirmränder.
- **Live-Demo im Menü**: Hinter den Menüs läuft ein echtes Rennen, gesteuert von der KI des
  Spiels und mit wechselnden Kameraeinstellungen gefilmt, statt des aufgezeichneten Videos.
- **Sechs Sprachen** im Spiel (Englisch, Deutsch, Italienisch, Spanisch, Schwedisch,
  Französisch), nach der Systemsprache oder in den Optionen gewählt.
- **Android-Version** für Handheld-Konsolen, mit Gamepad-Steuerung.
- **CD-Musik** aus OGG-Dateien.
- **Überall dieselbe Physik**: Rennen rechnen auf jeder Plattform exakt gleich.

Vollständige Liste, Version für Version:
[CHANGELOG.md](../CHANGELOG.md) (auf Englisch).

## Das Originalspiel wird benötigt

**Hier ist keine Datei des Originalspiels enthalten.** Du brauchst eine Kopie des
ursprünglichen PC-Spiels (Fun Tracks, 1997) und die Dateien seines Installationsordners (der
Ordner mit `fun_win.btz`, `LEVELS`, `CARS`...).

Um das vollständige Spiel zu finden, beginne mit seiner Seite bei
[Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1172&fic=liens).

Optional: Die CD-Musik kann aus OGG-Dateien namens `Music/track02.ogg`, `Music/track03.ogg`...
im Spielordner abgespielt werden (von deiner CD gerippt).

## Installation — Windows 64-Bit

Voraussetzungen: Windows 10 oder 11 (64-Bit), eine Grafikkarte mit DirectX 12.

1. Lade `FunTracks-…-windows-x64.zip` von der Seite
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) herunter.
2. Entpacke `FunTracks.exe` und `fun_tracks_recomp.ini` in deinen Fun-Tracks-Spielordner.
3. Starte `FunTracks.exe`.

Tastatur wie im Originalspiel. Alt+Eingabe: Vollbild / Fenster. F11: 3D-Renderer /
ursprünglicher Renderer.

## Installation — Android

Voraussetzungen: Android 10 oder neuer, 64-Bit-ARM-Gerät. Gedacht für Handheld-Konsolen mit
Tasten (getestet auf der AYN Odin 2 Portal); ein Gamepad ist nötig.

1. Lade `FunTracks-…-android-arm64.apk` von der Seite
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) herunter und
   installiere es (Installation aus unbekannten Quellen erlauben).
2. Starte das Spiel einmal und schließe es wieder: Dabei entsteht sein Datenordner.
3. Verbinde das Gerät per USB-Kabel mit einem PC und kopiere **den Inhalt** deines
   Fun-Tracks-Spielordners nach `Android/data/com.karlos.funtracks/files/` auf dem Gerät
   (oder: `adb push <Spielordner>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Starte das Spiel.

Für den 3D-Renderer kopiere auch `fun_tracks_recomp.ini` (aus dem Windows-Zip) in diesen Ordner.

Gamepad: Stick / Steuerkreuz zum Lenken und für die Menüs, A zum Beschleunigen oder Bestätigen,
B zum Bremsen oder Zurückgehen, X Turbo, LB / RB Gänge, Y Rückansicht, Start Pause. Die Tasten
lassen sich auf der Tastenseite des Spiels ändern.

## Bekannte Einschränkungen (Alpha)

- Kein Netzwerk-Mehrspielermodus.
- Nur ein Spieler unter Android.
