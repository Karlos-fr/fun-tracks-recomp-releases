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

# Fun Tracks — omkompilerat

Fun Tracks (1997) är ett racingspel sett uppifrån, med små leksaksbilar på grusbanor, i
majsfält och kanjoner. Det här projektet bygger upp det ursprungliga Windows-spelet igen från
dess dekompilerade C-kod, så att det körs direkt på dagens system.

Det här repot innehåller bara **utgåvorna** (Windows 64-bitars och Android). Nuvarande version:
**alfa** — räkna med buggar.

## Så gjordes omkompileringen

1. **Dekompilering.** Den ursprungliga programfilen (`FUN_WIN.EXE`, byggd 1997 med Microsoft
   Visual C++ 4.2) översattes tillbaka till läsbar C, rutin för rutin. Varje rutin kompileras
   igen med samma kompilator från 1996 och jämförs med den ursprungliga maskinkoden: samma
   flöde, samma beteende, och de flesta byte för byte. Arbetets framsteg:
   [dekompileringens framstegssida](https://karlos-fr.github.io/fun-tracks-decomp-progress/).
2. **Omkompilering.** C-koden flyttades sedan till ett modernt projekt, byggt med dagens
   kompilatorer i 64 bitar. Själva spelet (lopp, bilar, AI, menyer) är den dekompilerade koden;
   bara det som pratade med Windows 95 byttes ut: DirectDraw, DirectSound och DirectInput
   ersattes av SDL3, och en ny GPU-renderare ritar 3D-bilden.
3. **Kontroller.** En testmiljö spelar förinspelade partier med fast klocka och tangentbord och
   sparar varje bildruta (bild, lopptider, bilarnas positioner). Samma partier spelas upp på den
   ursprungliga programfilen för jämförelse, och varje ändring måste lämna inspelningarna
   identiska.
4. **AI, öppet redovisat.** Arbetet gjordes med AI-programmeringsagenter: **OpenAI Codex** och
   **Anthropic Claude** (Claude Code). De läser assemblerkoden, skriver och testar C-koden och
   verktygen; en människa leder projektet, spelar, testar och bestämmer. Inget godtas på tro:
   varje steg kontrolleras med jämförelserna ovan.

## Viktigaste tilläggen

Jämfört med originalspelet från 1997:

- **GPU-baserad 3D-renderare** (Direct3D 12 på Windows, Vulkan på Android), bredvid den
  ursprungliga mjukvarurenderaren; F11 växlar mellan dem.
- **Bredbild** i 3D: loppen fyller 16:9- och 21:9-skärmar och loppets visning flyttas till
  skärmens kanter.
- **Livedemo i menyerna**: bakom menyerna körs ett riktigt lopp som styrs av spelets AI och
  filmas med växlande kameravinklar, i stället för den inspelade videon.
- **Sex språk** inbyggda i spelet (engelska, tyska, italienska, spanska, svenska, franska),
  valda efter systemets språk eller i inställningarna.
- **Android-version** för handhållna konsoler, med handkontroll.
- **Flerspelarläge på samma skärm** i 3D för upp till sex spelare (tangentbordshalvor och
  handkontroller): vyerna delas och slås ihop efter loppet, var och en väljer sin bil och ställer
  in sina kontroller.
- **Grafikförbättringar** i 3D, alla valfria: utjämnade texturer, mipmaps, anisotropisk
  filtrering, skärpa, kantutjämning, HD-texturpaket, regn, åska och snö (även på
  kameralinsen), dynamiskt ljus och skuggor samt en riktig natt med strålkastare.
- **CD-musik** spelas upp från OGG-filer.
- **Samma fysik överallt**: loppen räknar exakt likadant på alla plattformar.

Fullständig lista, version för version:
[CHANGELOG.md](../CHANGELOG.md) (på engelska).

## Originalspelet behövs

**Ingen fil från originalspelet ingår här.** Du måste äga en kopia av det ursprungliga PC-spelet
(Fun Tracks, 1997) och använda filerna i dess installationsmapp (mappen som innehåller
`fun_win.btz`, `LEVELS`, `CARS`...).

För att hitta hela spelet, börja på dess sida hos
[Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1172&fic=liens).

Valfritt: CD-musiken kan spelas upp från OGG-filer med namnen `Music/track02.ogg`,
`Music/track03.ogg`... i spelmappen (rippade från din CD).

## Installation — Windows 64-bitars

Krav: Windows 10 eller 11 (64-bitars), ett grafikkort med DirectX 12.

1. Ladda ner `FunTracks-…-windows-x64.zip` från sidan
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases).
2. Packa upp `FunTracks.exe` och `fun_tracks_recomp.ini` i din Fun Tracks-spelmapp.
3. Starta `FunTracks.exe`.

Tangentbord som i originalspelet. Alt+Enter: helskärm / fönster. F11: 3D-renderare /
ursprunglig renderare.

## Installation — Android

Krav: Android 10 eller senare, 64-bitars ARM-enhet. Gjord för handhållna konsoler med knappar
(testad på AYN Odin 2 Portal); en handkontroll behövs.

1. Ladda ner `FunTracks-…-android-arm64.apk` från sidan
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) och installera
   den (tillåt installation av appar från okända källor).
2. Starta spelet en gång och stäng det: då skapas dess datamapp.
3. Anslut enheten till en PC med en USB-kabel och kopiera **innehållet** i din Fun Tracks-spelmapp
   till `Android/data/com.karlos.funtracks/files/` på enheten
   (eller: `adb push <spelmapp>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Starta spelet.

För att använda 3D-renderaren, kopiera också `fun_tracks_recomp.ini` (från Windows-zippen) till
den mappen.

Handkontroll: spak / styrkors för att styra och röra sig i menyerna, A för att gasa eller
bekräfta, B för att bromsa eller gå tillbaka, X turbo, LB / RB växlar, Y backspegel, Start paus.
Knapparna kan ändras på spelets sida för kontroller.

## Kända begränsningar (alfa)

- Inget flerspelarläge över nätverk.
- Flerspelarläge på samma skärm ännu inte testat på Android.
