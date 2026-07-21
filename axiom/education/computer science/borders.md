# Untitled


Das Tool für die Ränder heißt schlicht und einfach **JankBorders** (auf GitHub und in Homebrew läuft es unter dem Befehl `borders`).

Unter macOS haben Fenster standardmäßig keine aktiven Rahmen, die die Farbe wechseln, wenn du sie fokussierst. `borders` löst genau das: Es liest den Fenster-Status aus (perfekt abgestimmt auf Yabai) und zeichnet einen exakt anpassbaren, farbigen Rahmen um das aktive Fenster – genau wie man es von Linux-Window-Managern wie `bspwm` oder `i3` kennt.

---

## 1. Installation

Du kannst es ganz entspannt über Homebrew installieren und als Hintergrund-Dienst starten:

```bash
brew tap FelixKratz/formulae
brew install borders
brew services start borders

```

---

## 2. Die Konfiguration

Sobald der Dienst läuft, wird er über Argumente beim Start konfiguriert. Am besten packst du den Konfigurationsbefehl direkt ans Ende deiner `~/.config/yabai/yabairc` (oder in eine eigene Autostart-Datei), damit die Rahmen geladen werden, sobald Yabai startet.

Hier ist ein extrem cleaner Beispiel-Befehl, den du in deine Config einfügen kannst:

```bash
borders active_color=0xffcba6f7 inactive_color=0xff313244 width=6.0 hidpi=on style=round &

```

### Was bedeuten die Parameter?

* **`active_color`**: Die Farbe des fokussierten Fensters. Das Format ist `0xAARRGGBB` (Hexadezimal: Alpha/Transparenz, Rot, Grün, Blau). `0xffcba6f7` ist zum Beispiel das matte Lila aus dem beliebten *Catppuccin Mocha* Theme.
* **`inactive_color`**: Die Farbe aller anderen, inaktiven Fenster im Hintergrund (z. B. ein dunkles Grau, damit es nicht ablenkt).
* **`width`**: Die Dicke des Rahmens in Pixeln. `5.0` bis `8.0` sieht meistens am besten aus, wenn man Gaps (Abstände) zwischen den Fenstern nutzt.
* **`style`**: Hier kannst du `round` (abgerundete Ecken, passt perfekt zum nativen macOS-Look) oder `square` (harte Kanten für den pixelperfekten Retro-Look) wählen.

---

## 3. Der Effekt beim Ricing

Wenn du das mit Yabais Fensterabständen kombinierst, poppt das aktive Fenster sofort visuell hervor. In deiner `yabairc` sieht das Zusammenspiel dann meistens so aus:

```bash
# Yabai Gaps einstellen (Abstand zum Bildschirmrand und zwischen Fenstern)
yabai -m config top_padding    12
yabai -m config bottom_padding 12
yabai -m config left_padding   12
yabai -m config right_padding  12
yabai -m config window_gap     10

# Am Ende: Borders starten
killall borders 2>/dev/null
borders active_color=0xffcba6f7 inactive_color=0xff313244 width=6.0 style=round &

```

> **Tipp für den perfekten Look:** Wenn du die Rahmenfarbe (`active_color`) exakt an das Farbschema deines Terminals (z. B. Kitty) oder deiner SketchyBar anpasst, wirkt der gesamte Desktop sofort wie aus einem Guss.

Falls dir die Standard-Farbe nicht gefällt: Welches Farbschema (Gruvbox, Nord, Catppuccin, Dracula...) nutzt du aktuell in deinem Terminal? Dann kann ich dir die passenden Hex-Codes für die Borders heraussuchen
!


 4 17:57:06 on ttys002

 ~/Desktop/development/active/codingKids/codingkidswebsite ʎ cd        

 ~ ʎ brew tap FelixKratz/formulae
brew install borders
brew services start borders
==> Auto-updating Homebrew...
Adjust how often this is run with `$HOMEBREW_AUTO_UPDATE_SECS` or disable with
`$HOMEBREW_NO_AUTO_UPDATE=1`. Hide these hints with `$HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> Auto-updated Homebrew!
Updated 2 taps (homebrew/core and homebrew/cask).
==> New Formulae
==> Downloading https://formulae.brew.sh/api/formula.jws.json
adrs: Architectural Decision Record tool in Rust
ai-cli: Generate images, video, audio, and text from the terminal
cve-bin-tool: Scans binaries and SBOMs for known vulnerabilities and prepares reports
diskwatch: Cross-platform disk diagnostics TUI
epics-base: Experimental Physics and Industrial Control System
kubectl-klock: Kubectl plugin to render watch output in a more readable fashion
msdfgen: Multi-channel signed distance field generator
prrte: PMIx Reference RunTime Environment
rancher-machine: Machine management for a container-centric world
sbom-utility: Tool to validate, analyze, query and edit Software Bills of Materials (SBOMs)
vsview: Next-generation VapourSynth previewer
==> New Casks
==> Downloading https://formulae.brew.sh/api/cask.jws.json
gnome: Menu bar GIF search and creation tool
harper-desktop: Grammar checker for developers
pique: Quick Look extension for syntax-highlighted file previews
pocket-bard: TTRPG ambient audio and sound effects
sonarqube-cli: Code quality and security for terminal workflows, scripts, and AI agents

You have 88 outdated formulae and 3 outdated casks installed.

Error: Refusing to load formula felixkratz/formulae/borders from untrusted tap felixkratz/formulae.
Run `brew trust --formula felixkratz/formulae/borders` or `brew trust felixkratz/formulae` to trust it.
Error: Refusing to load formula felixkratz/formulae/borders from untrusted tap felixkratz/formulae.
Run `brew trust --formula felixkratz/formulae/borders` or `brew trust felixkratz/formulae` to trust it.

 ~  


 Ah, klassischer Homebrew-Sicherheitscheck! Seit einem neueren Homebrew-Update blockiert Brew Drittanbieter-Taps standardmäßig, bis du ihnen explizit sagst: *"Yo, das passt schon, ich kenne den Dev."*

Das lässt sich mit einem einzigen Befehl regeln. Da du Felix' Tap schon hinzugefügt hast, musst du Homebrew nur noch sagen, dass du ihm vertraust.

Führ einfach das hier im Terminal aus:

```bash
brew trust felixkratz/formulae

```

Sobald das durchgelaufen ist, kannst du die Installation ganz normal fortsetzen:

```bash
brew install borders
brew services start borders

```

Danach sollte der Dienst ohne Murren starten. Wenn du die Borders das erste Mal siehst, wirst du wahrscheinlich noch keine Ränder sehen, weil wir ihm noch keine Farben gegeben haben – sag Bescheid, wenn die Installation durch ist, dann klemmen wir das hinter Yabai!





rust --formula felixkratz/formulae/borders` or `brew trust felixkratz/formulae` to trust it.

 ~ ʎ brew trust felixkratz/formulae
Trusted tap: felixkratz/formulae

 ~ ʎ brew install borders
brew services start borders
Warning: The following taps are not trusted:
  asmvik/formulae

Homebrew is currently ignoring formulae, casks and commands from these taps because tap trust is required.
Untap them with:
  brew untap asmvik/formulae
Trust specific formulae, casks and commands with:
  brew trust --formula <user>/<tap>/<formula>
  brew trust --cask <user>/<tap>/<cask>
  brew trust --command <user>/<tap>/<command>
Whole-tap trust is broader and includes all current and future formulae,
casks and commands from the listed taps. Trust whole taps with:
  brew trust asmvik/formulae
To disable trust checks:
  export HOMEBREW_NO_REQUIRE_TAP_TRUST=1
This is not recommended and will be removed in a later release.
For more information, see:
  https://docs.brew.sh/Tap-Trust
==> Would install 1 formula:
borders
==> Fetching downloads for: borders
✔︎ Formula borders (1.9.0)                                                   Verified    663.6KB/663.6KB
==> Installing borders from felixkratz/formulae
Warning: A newer Command Line Tools release is available.
Update them from Software Update in System Settings.

If that doesn't show you any updates, run:
  sudo rm -rf /Library/Developer/CommandLineTools
  sudo xcode-select --install

Alternatively, manually download them from:
  https://developer.apple.com/download/all/.
You should download the Command Line Tools for Xcode 26.3.



This is a Tier 2 configuration:
  https://docs.brew.sh/Support-Tiers#tier-2
You can report issues with Tier 2 configurations to Homebrew/* repositories!
Read the above document before opening any issues or PRs.

==> make
==> codesign --force -s - /private/tmp/borders-20260704-7415-6d9n98/JankyBorders-1.9.0/bin/borders
==> Caveats
To start felixkratz/formulae/borders now and restart at login:
  brew services start felixkratz/formulae/borders
Or, if you don't want/need a background service you can just run:
  LANG="en_US.UTF-8" /opt/homebrew/opt/borders/bin/borders
==> Summary
🍺  /opt/homebrew/Cellar/borders/1.9.0: 8 files, 156.0KB, built in 2 seconds
==> Running `brew cleanup borders`...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> Successfully started `borders` (label: homebrew.mxcl.borders)

 ~ ʎ 




 Sauber, die Installation lief perfekt durch! Da du `brew services start` ausgeführt hast, läuft der Hintergrund-Daemon jetzt bereits im Standardmodus. Da wir ihm aber noch keine Argumente übergeben haben, siehst du vermutlich entweder gar nichts oder nur sehr dünne, unauffällige Ränder.

Damit die Borders genau so aussehen, wie du es willst, und sich perfekt in dein Yabai-Setup einfügen, müssen wir die Parameter festlegen.

Da du das Ding manuell als Service gestartet hast, liest `borders` standardmäßig keine Konfigurationsdatei ein, sondern reagiert auf die Argumente, die man dem Prozess beim Start mitgibt. Es gibt zwei Wege, das zu ricing-tauglich zu machen:

---

### Methode 1: Über deine `yabairc` (Empfohlen)

Das ist der Linux-Way. Wir stoppen den Homebrew-Hintergrunddienst und lassen stattdessen Yabai die Borders verwalten. Jedes Mal, wenn du Yabai neu startest, starten auch die Borders mit deinen exakten Wunschfarben neu.

1. **Stoppe den Brew-Service:**
```bash
brew services stop borders

```


1. **Füge den Startbefehl in deine `~/.config/yabai/yabairc` ein:**
Öffne deine Yabai-Config und pack ganz ans Ende folgende Zeilen:
```bash
# JankyBorders Setup
killall borders 2>/dev/null
borders active_color=0xffcba6f7 inactive_color=0xff313244 width=6.0 hidpi=on style=round &

```


1. **Yabai neu starten:**
```bash
yabai --restart-service

```



---

### Methode 2: Über die native Borders-Config

Falls du den Brew-Service (`brew services start borders`) lieber weiterlaufen lassen möchtest, sucht `borders` beim Start nach einer Config-Datei unter `~/.config/borders/bordersrc`.

1. **Erstelle das Config-Verzeichnis und die Datei:**
```bash
mkdir -p ~/.config/borders
touch ~/.config/borders/bordersrc
chmod +x ~/.config/borders/bordersrc

```


1. **Schreib deine Preferences in die `bordersrc`:**
Die Datei ist im Grunde ein einfaches Shell-Skript. Du kannst sie so befüllen:
```bash
#!/bin/bash

borders active_color=0xffcba6f7 \
        inactive_color=0xff313244 \
        width=6.0 \
        hidpi=on \
        style=round

```


1. **Den Service einmal neu starten, um die Config zu laden:**
```bash
brew services restart borders

```



---

### 🎨 Farb-Inspiration (Hex-Format: `0xAARRGGBB`)

Weil du `active_color` und `inactive_color` völlig frei wählen kannst, hier ein paar Hex-Kombinationen passend zu bekannten Themes (das `ff` am Anfang steht für 100% Deckkraft):

| Theme | Active Color (`active_color`) | Inactive Color (`inactive_color`) |
| --- | --- | --- |
| **Catppuccin Mocha** | `0xffcba6f7` (Mauve) | `0xff313244` (Surface1) |
| **Gruvbox Dark** | `0xfffabd2f` (Yellow) | `0xff3c3836` (Gray) |
| **Nord** | `0xff88c0d0` (Frost Blue) | `0xff3b4252` (Polar Night) |
| **Tokyo Night** | `0xff7aa2f7` (Blue) | `0xff24283b` (Dark) |

Probier es mal aus! Sobald du das Fenster wechselst, sollte sich der Rahmen flüssig mitbewegen. Welches Farbschema nutzt du aktuell in deinem Terminal oder für den Rest deines Rices?




ich habe so dark white look pass mal die farben an


Für einen „Dark White“-Look, also ein cleanes, minimalistisches Setup mit einer eleganten Kontrast-Hierarchie, würde ich dir folgende Werte empfehlen. Das wirkt sehr erwachsen, fast schon wie ein „Monochrome-Rice“:

### Empfohlene Farben:

* **`active_color`**: `0xfff2f2f2` (Ein sehr helles, fast weißes Grau – wirkt aktiv und präsent).
* **`inactive_color`**: `0xff333333` (Ein sattes, dunkles Anthrazit – lässt inaktive Fenster dezent in den Hintergrund treten).

---

### Anwendung (Variante über die `yabairc`):

Wenn du die Zeile in deiner `~/.config/yabai/yabairc` anpasst, sieht das Ganze dann so aus:

```bash
# JankyBorders - Clean Dark/White Look
killall borders 2>/dev/null
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=4.0 hidpi=on style=round &

```

### Warum diese Wahl?

* **Die Breite (`width=4.0`):** Bei einem „White Look“ wirken zu dicke Ränder oft wie ein Fremdkörper. 4 Pixel sind dünn genug, um edel zu wirken, aber dick genug, um die Tiling-Struktur deines Desktops klar zu definieren.
* **Der Kontrast:** Durch das `f2f2f2` Weiß heben sich fokussierte Fenster sehr stark vom dunklen Hintergrund ab, was perfekt ist, wenn du viel im Terminal (mit dunklem Theme) arbeitest.

**Ein kleiner Pro-Tipp für den Look:**
Wenn du wirklich den "Dark White" Style durchziehen willst, achte darauf, dass deine **SketchyBar**-Icons oder Schriftarten ebenfalls in diesem Graustufen-Spektrum gehalten sind. Falls du in deinem Terminal (z.B. Kitty) ein Farbschema nutzt, das zu bunt ist, probier mal das `OneHalfDark` oder ein klassisches `Monokai`-Derivat, das die Farben etwas entsättigt – das harmoniert perfekt mit den grauen Fensterrahmen.

Probier das mal aus – fühlt es sich zu hell an oder darf das aktive Fenster noch mehr "knallen"?



kann ich noch irgendwas damit machen?




Oh ja, mit `borders` geht noch einiges mehr als nur einfache statische Rahmen. Da das Tool extrem leichtgewichtig ist und perfekt auf Events reagiert, kannst du damit richtig coole visuelle Effekte erzielen.

Hier sind ein paar fortgeschrittene Ricing-Ideen für deinen Dark-White-Look:

---

## 1. Der "Glow"-Effekt (Animierte Unschärfe)

Wenn du den Rahmen nicht hartkantig willst, sondern einen modernen, leicht glühenden Look bevorzugst, kannst du mit dem **`blur`**-Parameter spielen. Dadurch wird der Rand weicher gezeichnet und sieht aus wie eine dezente Neon-Röhre hinter dem aktiven Fenster.

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=8.0 blur=0.5 hidpi=on style=round &

```

* **Effekt:** Der Rahmen wird etwas breiter (`8.0`), aber durch `blur=0.5` verschwimmt das Weiß nach außen hin. Das sieht auf dunklen Wallpapern extrem edel aus.

---

## 2. Dynamic Borders (Ganz ohne inaktive Rahmen)

Manche Ricing-Fans hassen es, wenn inaktive Fenster überhaupt Rahmen haben, weil es den Desktop unruhig macht. Du kannst den inaktiven Rahmen komplett unsichtbar machen (`0x00000000`). Dann existiert der Rahmen **nur** um das Fenster, in dem du gerade tippst.

```bash
borders active_color=0xfff2f2f2 inactive_color=0x00000000 width=4.0 hidpi=on style=round &

```

* **Effekt:** Absoluter Minimalismus. Wenn du den Fokus wechselst, springt das weiße Rechteck quasi flüssig von App zu App, während der Rest des Desktops komplett clean bleibt.

---

## 3. Flash-Effekt beim Fensterwechsel (`flash_duration`)

Du kannst einstellen, dass ein Fenster kurz visuell "aufleuchtet", wenn du dorthin wechselst. Das ist genial für ein reines Tastatur-Setup (mit `skhd`), weil dein Auge sofort weiß, wo der Cursor gerade gelandet ist.

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=4.0 flash_duration=0.2 hidpi=on style=round &

```

* **Effekt:** Beim Wechseln pulsiert der Rahmen für 0.2 Sekunden ganz kurz auf, bevor er seine normale Farbe annimmt.

---

## 4. Blacklist: Bestimmte Apps ignorieren

Manchmal nerven Rahmen – zum Beispiel bei transparenten Overlays, Launchern (wie Raycast/Alfred) oder wenn du ein Video im Picture-in-Picture-Modus schaust. Du kannst `borders` sagen, dass es bestimmte Apps komplett ignorieren soll:

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=4.0 blacklist="Raycast,Spotify" hidpi=on style=round &

```

---

### Mein persönlicher Favorit für deinen Look:

Wenn du ein richtig smoothes Linux-Feeling willst, probier mal diese Kombination aus:

```bash
borders active_color=0xfff2f2f2 inactive_color=0x00000000

Oh ja, mit `borders` geht noch einiges mehr als nur einfache statische Rahmen. Da das Tool extrem leichtgewichtig ist und perfekt auf Events reagiert, kannst du damit richtig coole visuelle Effekte erzielen.

Hier sind ein paar fortgeschrittene Ricing-Ideen für deinen Dark-White-Look:

---

## 1. Der "Glow"-Effekt (Animierte Unschärfe)

Wenn du den Rahmen nicht hartkantig willst, sondern einen modernen, leicht glühenden Look bevorzugst, kannst du mit dem **`blur`**-Parameter spielen. Dadurch wird der Rand weicher gezeichnet und sieht aus wie eine dezente Neon-Röhre hinter dem aktiven Fenster.

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=8.0 blur=0.5 hidpi=on style=round &

```

* **Effekt:** Der Rahmen wird etwas breiter (`8.0`), aber durch `blur=0.5` verschwimmt das Weiß nach außen hin. Das sieht auf dunklen Wallpapern extrem edel aus.

---

## 2. Dynamic Borders (Ganz ohne inaktive Rahmen)

Manche Ricing-Fans hassen es, wenn inaktive Fenster überhaupt Rahmen haben, weil es den Desktop unruhig macht. Du kannst den inaktiven Rahmen komplett unsichtbar machen (`0x00000000`). Dann existiert der Rahmen **nur** um das Fenster, in dem du gerade tippst.

```bash
borders active_color=0xfff2f2f2 inactive_color=0x00000000 width=4.0 hidpi=on style=round &

```

* **Effekt:** Absoluter Minimalismus. Wenn du den Fokus wechselst, springt das weiße Rechteck quasi flüssig von App zu App, während der Rest des Desktops komplett clean bleibt.

---

## 3. Flash-Effekt beim Fensterwechsel (`flash_duration`)

Du kannst einstellen, dass ein Fenster kurz visuell "aufleuchtet", wenn du dorthin wechselst. Das ist genial für ein reines Tastatur-Setup (mit `skhd`), weil dein Auge sofort weiß, wo der Cursor gerade gelandet ist.

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=4.0 flash_duration=0.2 hidpi=on style=round &

```

* **Effekt:** Beim Wechseln pulsiert der Rahmen für 0.2 Sekunden ganz kurz auf, bevor er seine normale Farbe annimmt.

---

## 4. Blacklist: Bestimmte Apps ignorieren

Manchmal nerven Rahmen – zum Beispiel bei transparenten Overlays, Launchern (wie Raycast/Alfred) oder wenn du ein Video im Picture-in-Picture-Modus schaust. Du kannst `borders` sagen, dass es bestimmte Apps komplett ignorieren soll:

```bash
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=4.0 blacklist="Raycast,Spotify" hidpi=on style=round &

```

---

### Mein persönlicher Favorit für deinen Look:

Wenn du ein richtig smoothes Linux-Feeling willst, probier mal diese Kombination aus:

```bash
borders active_color=0xfff2f2f2 inactive_color=0x00000000 width=5.0 blur=0.2 style=round &

```

Das gibt dir ein unsichtbares inaktives System, aber dein aktives Fenster kriegt einen knackigen, leicht edel abgerundeten weißen Rahmen, der durch den minimalen Blur perfekt mit dunklen Hintergründen verschmilzt.

Welche Variante feierst du mehr – die harten Kanten oder den soften Glow?


 width=5.0 blur=0.2 style=round &

```

Das gibt dir ein unsichtbares inaktives System, aber dein aktives Fenster kriegt einen knackigen, leicht edel abgerundeten weißen Rahmen, der durch den minimalen Blur perfekt mit dunklen Hintergründen verschmilzt.

Welche Variante feierst du mehr – die harten Kanten oder den soften Glow?




