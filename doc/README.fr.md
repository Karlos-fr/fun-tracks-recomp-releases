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

# Fun Tracks — recompilé

Fun Tracks (1997) est un jeu de course vu de dessus, avec de petites voitures jouets sur des
pistes de terre, dans les champs de maïs et les canyons. Ce projet reconstruit le jeu Windows
d'origine à partir de son code C décompilé, pour qu'il tourne nativement sur les systèmes
actuels.

Ce dépôt héberge seulement les **versions publiées** (Windows 64 bits et Android). Version
actuelle : **alpha** — des bugs sont à prévoir.

## Comment cette recompilation a été faite

1. **Décompilation.** L'exécutable d'origine (`FUN_WIN.EXE`, compilé en 1997 avec Microsoft
   Visual C++ 4.2) a été retraduit en C lisible, routine par routine. Chaque routine est
   recompilée avec le même compilateur de 1996 et comparée au code machine d'origine : même
   enchaînement, même comportement, et pour la plupart octet pour octet. Avancement de ce
   travail : [suivi de la décompilation](https://karlos-fr.github.io/fun-tracks-decomp-progress/).
2. **Recompilation.** Ce code C a ensuite été repris dans un projet moderne, compilé avec les
   compilateurs actuels en 64 bits. Le jeu lui-même (courses, voitures, IA, menus) est le code
   décompilé ; seul ce qui parlait à Windows 95 a été remplacé : DirectDraw, DirectSound et
   DirectInput ont laissé place à SDL3, et un nouveau moteur GPU dessine l'image en 3D.
3. **Vérifications.** Un harnais de test joue des parties scriptées avec une horloge et un
   clavier fixes, et enregistre chaque image (image, temps de course, position des voitures).
   Les mêmes parties sont rejouées sur l'exécutable d'origine pour comparer, et chaque
   changement doit laisser ces enregistrements identiques.
4. **L'IA, assumée.** Ce travail a été fait avec des agents de programmation IA : **OpenAI
   Codex** et **Anthropic Claude** (Claude Code). Ils lisent l'assembleur, écrivent et testent le
   code C et les outils ; un humain mène le projet, joue, teste et décide. Rien n'est accepté
   sur parole : chaque étape est vérifiée par les comparaisons ci-dessus.

## Principaux ajouts

Par rapport au jeu d'origine de 1997 :

- **Moteur 3D GPU** (Direct3D 12 sous Windows, Vulkan sous Android), à côté du moteur logiciel
  d'origine ; F11 passe de l'un à l'autre.
- **Écran large** en 3D : les courses remplissent les écrans 16:9 et 21:9, l'interface de course
  va sur les bords de l'écran.
- **Démo live dans les menus** : derrière les menus, une vraie course pilotée par l'IA du jeu et
  filmée avec des plans de caméra variés, à la place de la vidéo enregistrée.
- **Six langues** intégrées au jeu (anglais, allemand, italien, espagnol, suédois, français),
  choisies d'après la langue du système ou dans les options.
- **Version Android** pour les consoles portables, jouable à la manette.
- **Musique du CD** jouée depuis des fichiers OGG.
- **La même physique partout** : les courses donnent exactement les mêmes calculs sur toutes les
  plateformes.

Liste complète, version par version :
[CHANGELOG.md](../CHANGELOG.md) (en anglais).

## Il faut le jeu original

**Aucun fichier du jeu original n'est fourni ici.** Il faut posséder une copie du jeu PC
d'origine (Fun Tracks, 1997) et utiliser les fichiers de son dossier d'installation (celui qui
contient `fun_win.btz`, `LEVELS`, `CARS`...).

Pour trouver le jeu complet, partez de sa page sur
[Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1172&fic=liens).

Facultatif : la musique du CD peut être jouée depuis des fichiers OGG nommés
`Music/track02.ogg`, `Music/track03.ogg`... dans le dossier du jeu (extraits de votre CD).

## Installation — Windows 64 bits

Configuration : Windows 10 ou 11 (64 bits), une carte graphique compatible DirectX 12.

1. Téléchargez `FunTracks-…-windows-x64.zip` depuis la page
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases).
2. Extrayez `FunTracks.exe` et `fun_tracks_recomp.ini` dans le dossier de votre jeu Fun Tracks.
3. Lancez `FunTracks.exe`.

Clavier comme dans le jeu d'origine. Alt+Entrée : plein écran / fenêtre. F11 : moteur 3D /
moteur d'origine.

## Installation — Android

Configuration : Android 10 ou plus récent, appareil ARM 64 bits. Pensé pour les consoles
portables à boutons (testé sur l'AYN Odin 2 Portal) ; une manette est nécessaire.

1. Téléchargez `FunTracks-…-android-arm64.apk` depuis la page
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) et installez-le
   (autorisez l'installation d'applications de sources inconnues).
2. Lancez le jeu une fois, puis fermez-le : cela crée son dossier de données.
3. Branchez l'appareil à un PC par câble USB et copiez **le contenu** du dossier de votre jeu
   Fun Tracks dans `Android/data/com.karlos.funtracks/files/` sur l'appareil
   (ou : `adb push <dossier du jeu>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Lancez le jeu.

Pour utiliser le moteur 3D, copiez aussi `fun_tracks_recomp.ini` (depuis le zip Windows) dans ce
dossier.

Manette : stick / croix pour diriger et se déplacer dans les menus, A pour accélérer ou valider,
B pour freiner ou revenir, X turbo, LB / RB vitesses, Y vue arrière, Start pause. Les boutons se
changent dans la page des touches du jeu.

## Limites connues (alpha)

- Pas de multijoueur en réseau.
- Un seul joueur sur Android.
