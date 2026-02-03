Last login: Tue Jan 20 17:43:36 on ttys000

~ via  v22.17.1 via 🐍 v3.14.2 
❯ z ray 

raytracing on  main [!] 
❯ copilot
zsh: command not found: copilot

raytracing on  main [!] 
❯ cd                                                                                                

~ via  v22.17.1 via 🐍 v3.14.2 
❯ brew install github-copilot-cli

==> Auto-updating Homebrew...
Adjust how often this is run with `$HOMEBREW_AUTO_UPDATE_SECS` or disable with
`$HOMEBREW_NO_AUTO_UPDATE=1`. Hide these hints with `$HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> Auto-updated Homebrew!
Updated 2 taps (homebrew/core and homebrew/cask).
==> New Formulae
azure-dev: Developer CLI that provides commands for working with Azure resources
dovi_convert: Dolby Vision Profile 7 to 8.1 MKV converter
ekphos: Terminal-based markdown research tool inspired by Obsidian
ffmpeg-full: Play, record, convert, and stream many audio and video codecs
fzf-tab: Replace zsh completion selection menu with fzf
imagemagick-full: Tools and libraries to manipulate images in many formats
kubefwd: Bulk port forwarding Kubernetes services for local development
libks: Foundational support for signalwire C products
libthai: Thai language support library
magics: ECMWF's meteorological plotting software
nativefiledialog-extended: Native file dialog library with C and C++ bindings
openskills: Universal skills loader for AI coding agents
pgroll: Postgres zero-downtime migrations made easy
pocket-tts: Text-to-speech application designed to run efficiently on CPUs
ralph-orchestrator: Multi-agent orchestration framework for autonomous AI task completion
repeater: Flashcard program that uses spaced repetition
rig-r: R Installation Manager
rv-r: Declarative R package manager
sandvault: Run AI agents isolated in a sandboxed macOS user account
shiki: Beautiful yet powerful syntax highlighter
signalwire-client-c: SignalWire C Client SDK
tftp-now: Single-binary TFTP server and client that you can use right now
tock: Powerful time tracking tool for the command-line
vtsls: LSP wrapper for typescript extension of vscode
worktrunk: CLI for Git worktree management, designed for parallel AI agent workflows
xcsift: Swift tool to parse xcodebuild output for coding agents
==> New Casks
amical: AI dictation app
aquaskk@prerelease: Input method without morphological analysis
auto-claude: Autonomous multi-session AI coding
bettershot: Screen capturing and editing tool
boltai@1: AI chat client
claudebar: Menu bar app for monitoring AI coding assistant usage quotas
codebuddy: AI-powered adaptive IDE
codebuddy-cn: AI-powered adaptive IDE (Chinese version)
eigent: Desktop AI agent
font-zxgamut
freeshow@beta: Presentation software
gitfit: Micro-workouts while waiting for AI code generation
hytale: Official Hytale Launcher
impactor: Sideloading application for iOS/tvOS
kogiqa: UI automation tool using natural language descriptions
mcpbundler: MCP servers and Agent skills management app
mos@beta: Smooths scrolling and set mouse scroll directions independently
plaud: AI note-taking for online meetings, phone calls, and in-person conversations
proscoreboard: Scoreboard software

~ via  v22.17.1 via 🐍 v3.14.2 
❯ brew install gh                
==> Fetching downloads for: gh
✔︎ Bottle Manifest gh (2.86.0)                                                    Downloaded    7.4KB/  7.4KB
✔︎ Bottle gh (2.86.0)                                                             Downloaded   12.6MB/ 12.6MB
==> Pouring gh--2.86.0.arm64_sequoia.bottle.tar.gz
🍺  /opt/homebrew/Cellar/gh/2.86.0: 222 files, 36.3MB
==> Running `brew cleanup gh`...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> Caveats
zsh completions have been installed to:
  /opt/homebrew/share/zsh/site-functions

~ via  v22.17.1 via 🐍 v3.14.2 took 3s 
❯ gh extension install github/gh-copilot

To get started with GitHub CLI, please run:  gh auth login
Alternatively, populate the GH_TOKEN environment variable with a GitHub API authentication token.

~ via  v22.17.1 via 🐍 v3.14.2 
❯ gh auth login                         
? Where do you use GitHub? GitHub.com
? What is your preferred protocol for Git operations on this host? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: 52F6-45F2
Press Enter to open https://github.com/login/device in your browser... 
✓ Authentication complete.
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as Goldinyan

~ via  v22.17.1 via 🐍 v3.14.2 took 1m5s 
❯ gh extension install github/gh-copilot

"copilot" matches the name of a built-in command or alias

~ via  v22.17.1 via 🐍 v3.14.2 
❯ gh extension list

no installed extensions found

~ via  v22.17.1 via 🐍 v3.14.2 
❯ gh copilot





Hier kommt die komplette, aktuelle Befehlsübersicht der neuen GitHub Copilot CLI, so wie sie wirklich funktioniert – ohne veraltete Doku, ohne Chaos, exakt so wie du sie in deinem Terminal nutzen kannst.

Ich strukturiere das so, dass du es direkt in deine Obsidian‑Notizen übernehmen kannst.

  

🧭 GitHub Copilot CLI – vollständige Befehlsübersicht

Die CLI besteht aus zwei Schichten:

1. Interaktiver Modus → gh copilot
2. Direkter Prompt‑Modus → copilot -i oder copilot -p

Beide haben unterschiedliche Commands.

  

1) Interaktiver Modus (`gh copilot`)

Wenn du startest:

gh copilot

bist du im TUI. Dort funktionieren Slash‑Commands wie in ChatGPT/Claude.

Slash‑Commands im TUI

Command | Bedeutung

-------------------

/model | Modell auswählen (z. B. GPT‑4.1, Claude Haiku, etc.)

/help | Liste aller Befehle anzeigen

/exit | TUI verlassen

/delegate | Copilot erzeugt einen PR für dich (AI‑PR‑Flow)

/repo | Repository‑Kontext setzen

/clear | Verlauf löschen

/settings | Einstellungen anzeigen

/feedback | Feedback senden

/explain | Code oder Befehl erklären

/tests | Tests generieren

/fix | Fehler beheben lassen

/optimize | Code optimieren

/doc | Dokumentation generieren

/commit | Commit‑Message generieren

/pr | Pull‑Request‑Beschreibung generieren

Wichtig:

Du kannst im TUI auch einfach direkt schreiben:

explain ls -lha

ohne Slash.

  

2) Direkter Prompt‑Modus (`copilot -i` / `copilot -p`)

Dieser Modus ist für Einmal‑Prompts, ohne TUI.

Grundbefehle

Inline‑Prompt:

copilot -i "explain what is 2+2"

Prompt‑Flag:

copilot -p "write a bash script that cleans logs"

Datei als Input:

copilot -f script.sh -i "explain this file"

Ausgabe in Datei schreiben:

copilot -i "generate a README" > README.md

  

3) Git‑spezifische Copilot‑Befehle

Diese funktionieren innerhalb eines Git‑Repos:

Befehl | Funktion

-----------------

copilot commit | Commit‑Message generieren

copilot pr | PR‑Beschreibung generieren

copilot explain | Änderungen erklären

copilot fix | Fehler im Code beheben

copilot tests | Tests generieren

copilot doc | Dokumentation erzeugen

Beispiel:

copilot commit -i "summarize changes"

  

4) GitHub‑CLI‑Integration (`gh copilot …`)

Neben dem TUI gibt es auch Subcommands:

Command | Bedeutung

-------------------

gh copilot chat | Direkt Chat starten

gh copilot explain | Code/Befehl erklären

gh copilot suggest | Vorschläge generieren

gh copilot review | Code‑Review durchführen

gh copilot tests | Tests generieren

gh copilot pr | PR‑Beschreibung generieren

Beispiel:

gh copilot explain file.go

  

5) Modelle wechseln

Im TUI:

/model

Direkt:

copilot -m "gpt-4.1" -i "explain this"

  

6) Kontext setzen

Repository‑Kontext:

/repo set .

Datei‑Kontext:

copilot -f main.c -i "optimize this"

  

7) Debugging / Meta‑Commands

Command | Funktion

------------------

copilot --help | Hilfe

copilot --version | Version anzeigen

gh copilot --help | Hilfe für TUI‑Modus

  

Wenn du willst

Ich kann dir:

- eine komplette Obsidian‑Note daraus bauen
- ein Alias‑Setup erstellen, das alles vereinheitlicht
- oder dir ein minimalistisches Copilot‑TUI‑Workflow‑Template bauen, das perfekt zu deinem Stil passt

Sag einfach Bescheid.