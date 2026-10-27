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

# Fun Tracks — recompilado

Fun Tracks (1997) es un juego de carreras con vista cenital, con pequeños coches de juguete en
pistas de tierra, campos de maíz y cañones. Este proyecto reconstruye el juego original de
Windows a partir de su código C descompilado, para que funcione de forma nativa en los sistemas
actuales.

Este repositorio solo aloja las **versiones publicadas** (Windows de 64 bits y Android). Versión
actual: **alfa**; habrá errores.

## Cómo se hizo esta recompilación

1. **Descompilación.** El ejecutable original (`FUN_WIN.EXE`, compilado en 1997 con Microsoft
   Visual C++ 4.2) se volvió a convertir en C legible, rutina por rutina. Cada rutina se compila
   de nuevo con el mismo compilador de 1996 y se compara con el código máquina original: el
   mismo flujo, el mismo comportamiento y, en la mayoría de los casos, byte a byte. Progreso de
   este trabajo:
   [seguimiento de la descompilación](https://karlos-fr.github.io/fun-tracks-decomp-progress/).
2. **Recompilación.** Después, ese código C se llevó a un proyecto moderno, compilado con los
   compiladores actuales en 64 bits. El juego en sí (carreras, coches, IA, menús) es el código
   descompilado; solo se sustituyó lo que hablaba con Windows 95: DirectDraw, DirectSound y
   DirectInput dieron paso a SDL3, y un nuevo motor de GPU dibuja la imagen en 3D.
3. **Comprobaciones.** Un banco de pruebas juega partidas guionizadas con reloj y teclado fijos y
   registra cada fotograma (imagen, tiempos de carrera, posición de los coches). Las mismas
   partidas se vuelven a jugar en el ejecutable original para comparar, y cada cambio debe dejar
   esos registros idénticos.
4. **IA, sin ocultarlo.** Este trabajo se hizo con agentes de programación con IA: **OpenAI
   Codex** y **Anthropic Claude** (Claude Code). Leen el ensamblador, escriben y prueban el código
   C y las herramientas; una persona dirige el proyecto, juega, prueba y decide. Nada se acepta a
   ciegas: cada paso se verifica con las comparaciones anteriores.

## Novedades principales

Respecto al juego original de 1997:

- **Motor 3D por GPU** (Direct3D 12 en Windows, Vulkan en Android), junto al motor por software
  original; F11 cambia entre ambos.
- **Pantalla panorámica** en 3D: las carreras llenan pantallas 16:9 y 21:9, y la interfaz de
  carrera pasa a los bordes de la pantalla.
- **Demo en vivo en los menús**: detrás de los menús, una carrera real conducida por la IA del
  juego y filmada con planos de cámara cambiantes, en lugar del vídeo grabado.
- **Seis idiomas** integrados en el juego (inglés, alemán, italiano, español, sueco, francés),
  elegidos según el idioma del sistema o en las opciones.
- **Versión para Android** para consolas portátiles, con mando.
- **Música del CD** reproducida desde archivos OGG.
- **La misma física en todas partes**: las carreras calculan exactamente lo mismo en cada
  plataforma.

Lista completa, versión por versión:
[CHANGELOG.md](../CHANGELOG.md) (en inglés).

## Se necesita el juego original

**Aquí no se incluye ningún archivo del juego original.** Hay que tener una copia del juego de
PC original (Fun Tracks, 1997) y usar los archivos de su carpeta de instalación (la que contiene
`fun_win.btz`, `LEVELS`, `CARS`...).

Para encontrar el juego completo, empieza por su página en
[Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1172&fic=liens).

Opcional: la música del CD puede reproducirse desde archivos OGG llamados `Music/track02.ogg`,
`Music/track03.ogg`... en la carpeta del juego (extraídos de tu CD).

## Instalación — Windows de 64 bits

Requisitos: Windows 10 u 11 (64 bits), una tarjeta gráfica con DirectX 12.

1. Descarga `FunTracks-…-windows-x64.zip` desde la página
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases).
2. Extrae `FunTracks.exe` y `fun_tracks_recomp.ini` en la carpeta de tu juego Fun Tracks.
3. Ejecuta `FunTracks.exe`.

Teclado como en el juego original. Alt+Intro: pantalla completa / ventana. F11: motor 3D / motor
original.

## Instalación — Android

Requisitos: Android 10 o posterior, dispositivo ARM de 64 bits. Pensado para consolas portátiles
con botones (probado en la AYN Odin 2 Portal); hace falta un mando.

1. Descarga `FunTracks-…-android-arm64.apk` desde la página
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) e instálalo
   (permite instalar aplicaciones de orígenes desconocidos).
2. Abre el juego una vez y ciérralo: así se crea su carpeta de datos.
3. Conecta el dispositivo a un PC con un cable USB y copia **el contenido** de la carpeta de tu
   juego Fun Tracks en `Android/data/com.karlos.funtracks/files/` en el dispositivo
   (o: `adb push <carpeta del juego>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Abre el juego.

Para usar el motor 3D, copia también `fun_tracks_recomp.ini` (del zip de Windows) en esa carpeta.

Mando: stick / cruceta para girar y moverse por los menús, A para acelerar o confirmar, B para
frenar o volver, X turbo, LB / RB marchas, Y vista trasera, Start pausa. Los botones se cambian
en la página de controles del juego.

## Limitaciones conocidas (alfa)

- Sin multijugador en red.
- Un solo jugador en Android.
