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

# Fun Tracks — ricompilato

Fun Tracks (1997) è un gioco di corse con visuale dall'alto, con piccole auto giocattolo su
piste sterrate, campi di mais e canyon. Questo progetto ricostruisce il gioco Windows originale a
partire dal suo codice C decompilato, così che funzioni in modo nativo sui sistemi di oggi.

Questo repository contiene solo le **versioni pubblicate** (Windows 64 bit e Android). Versione
attuale: **alpha** — aspettatevi dei bug.

## Come è stata fatta questa ricompilazione

1. **Decompilazione.** L'eseguibile originale (`FUN_WIN.EXE`, compilato nel 1997 con Microsoft
   Visual C++ 4.2) è stato riportato in C leggibile, routine per routine. Ogni routine viene
   ricompilata con lo stesso compilatore del 1996 e confrontata con il codice macchina originale:
   stesso flusso, stesso comportamento e, per la maggior parte, byte per byte. Avanzamento di
   questo lavoro:
   [monitoraggio della decompilazione](https://karlos-fr.github.io/fun-tracks-decomp-progress/).
2. **Ricompilazione.** Questo codice C è stato poi portato in un progetto moderno, compilato con
   i compilatori di oggi a 64 bit. Il gioco vero e proprio (gare, auto, IA, menu) è il codice
   decompilato; è stato sostituito solo ciò che parlava con Windows 95: DirectDraw, DirectSound e
   DirectInput hanno lasciato il posto a SDL3, e un nuovo renderer GPU disegna l'immagine in 3D.
3. **Verifiche.** Un sistema di test gioca partite predefinite con orologio e tastiera fissi e
   registra ogni fotogramma (immagine, tempi di gara, posizione delle auto). Le stesse partite
   vengono rigiocate sull'eseguibile originale per il confronto, e ogni modifica deve lasciare
   queste registrazioni identiche.
4. **L'IA, dichiarata.** Questo lavoro è stato fatto con agenti di programmazione IA: **OpenAI
   Codex** e **Anthropic Claude** (Claude Code). Leggono l'assembly, scrivono e testano il codice
   C e gli strumenti; una persona guida il progetto, gioca, prova e decide. Nulla viene accettato
   sulla fiducia: ogni passo è verificato dai confronti qui sopra.

## Principali novità

Rispetto al gioco originale del 1997:

- **Renderer 3D su GPU** (Direct3D 12 su Windows, Vulkan su Android), accanto al renderer
  software originale; F11 passa dall'uno all'altro.
- **Schermo panoramico** in 3D: le gare riempiono gli schermi 16:9 e 21:9, l'interfaccia di gara
  si sposta ai bordi dello schermo.
- **Demo dal vivo nei menu**: dietro i menu, una vera gara guidata dall'IA del gioco e ripresa
  con inquadrature che cambiano, al posto del video registrato.
- **Sei lingue** integrate nel gioco (inglese, tedesco, italiano, spagnolo, svedese, francese),
  scelte in base alla lingua del sistema o nelle opzioni.
- **Versione Android** per console portatili, con controlli da gamepad.
- **Multigiocatore sullo stesso schermo** in 3D fino a sei giocatori (metà della tastiera e
  gamepad): le visuali si dividono e si riuniscono secondo la gara, ognuno sceglie la sua auto e
  configura i suoi comandi.
- **Miglioramenti grafici** in 3D, tutti facoltativi: texture levigate, mipmap, filtro
  anisotropo, nitidezza, antialiasing, pacchetti di texture HD, pioggia, temporale e neve
  (anche sull'obiettivo), luci e ombre dinamiche e una vera notte con i fari.
- **Musica del CD** riprodotta da file OGG.
- **La stessa fisica ovunque**: le gare danno esattamente gli stessi calcoli su ogni piattaforma.

Elenco completo, versione per versione:
[CHANGELOG.md](../CHANGELOG.md) (in inglese).

## Serve il gioco originale

**Qui non è incluso alcun file del gioco originale.** Bisogna possedere una copia del gioco PC
originale (Fun Tracks, 1997) e usare i file della sua cartella di installazione (quella che
contiene `fun_win.btz`, `LEVELS`, `CARS`...).

Per trovare il gioco completo, partite dalla sua pagina su
[Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1172&fic=liens).

Facoltativo: la musica del CD può essere riprodotta da file OGG chiamati `Music/track02.ogg`,
`Music/track03.ogg`... nella cartella del gioco (estratti dal vostro CD).

## Installazione — Windows 64 bit

Requisiti: Windows 10 o 11 (64 bit), una scheda grafica con DirectX 12.

1. Scaricate `FunTracks-…-windows-x64.zip` dalla pagina
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases).
2. Estraete `FunTracks.exe` e `fun_tracks_recomp.ini` nella cartella del gioco Fun Tracks.
3. Avviate `FunTracks.exe`.

Tastiera come nel gioco originale. Alt+Invio: schermo intero / finestra. F11: renderer 3D /
renderer originale.

## Installazione — Android

Requisiti: Android 10 o successivo, dispositivo ARM a 64 bit. Pensato per console portatili con
tasti (provato sull'AYN Odin 2 Portal); serve un gamepad.

1. Scaricate `FunTracks-…-android-arm64.apk` dalla pagina
   [Releases](https://github.com/Karlos-fr/fun-tracks-recomp-releases/releases) e installatelo
   (consentite l'installazione di app da origini sconosciute).
2. Avviate il gioco una volta, poi chiudetelo: così viene creata la sua cartella dati.
3. Collegate il dispositivo a un PC con un cavo USB e copiate **il contenuto** della cartella del
   gioco Fun Tracks in `Android/data/com.karlos.funtracks/files/` sul dispositivo
   (oppure: `adb push <cartella del gioco>/. /sdcard/Android/data/com.karlos.funtracks/files/`).
4. Avviate il gioco.

Per usare il renderer 3D, copiate anche `fun_tracks_recomp.ini` (dallo zip per Windows) in quella
cartella.

Gamepad: levetta / croce direzionale per sterzare e muoversi nei menu, A per accelerare o
confermare, B per frenare o tornare indietro, X turbo, LB / RB marce, Y vista posteriore, Start
pausa. I tasti si cambiano nella pagina dei comandi del gioco.

## Limiti noti (alpha)

- Niente multigiocatore in rete.
- Multigiocatore sullo stesso schermo non ancora provato su Android.
