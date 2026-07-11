Hier ist dein kompaktes, auf Produktivität getrimmtes **`cloc` Cheat Sheet**. Perfekt zum Kopieren oder für deine Notizen.

## 🚀 Die absoluten Basics

|**Befehl**|**Beschreibung**|
|---|---|
|`cloc .`|Scannt das **aktuelle Verzeichnis** (inkl. Unterordner).|
|`cloc [ordner]`|Scannt einen **spezifischen Ordner** (z. B. `cloc src/`).|
|`cloc [datei.ts]`|Zählt die Zeilen einer **einzelnen Datei**.|

## 🛠️ Wichtige Filter & Ignorieren (Praxis-Beispiele)

Beim Scannen von Web- oder Softwareprojekten willst du generierten Code und Abhängigkeiten fast immer ausschließen:

### 1. Ordner ignorieren (`--exclude-dir`)

Schließt Ordner wie `node_modules` oder Build-Artefakte komplett aus:

Bash

```
cloc . --exclude-dir=node_modules,.git,.next,dist,build
```

### 2. Bestimmte Dateiendungen ignorieren (`--exclude-ext`)

Wenn du beispielsweise die gigantischen JSON- oder Markdown-Dateien nicht in der Statistik haben willst:

Bash

```
cloc . --exclude-ext=json,md
```

### 3. Nur eine bestimmte Sprache zählen (`--include-lang`)

Ignoriert alles andere und zeigt dir z. B. nur deinen TypeScript- oder C++-Code:

Bash

```
cloc . --include-lang=TypeScript
cloc . --include-lang="C++,C Header"
```

## 📊 Erweiterte Ausgaben

### Einzelne Dateien auflisten (`--by-file`)

Zeigt dir die Statistik **aufgelistet nach jeder einzelnen Datei** anstatt nur die Summe pro Sprache (perfekt, um "Code-Monster" zu finden):

Bash

```
cloc . --by-file
```

### Ergebnisse exportieren

Du kannst das Ergebnis direkt in eine Datei schreiben lassen, um es abzuspeichern:

Bash

```
cloc . --md --out=report.md      # Als Markdown-Tabelle
cloc . --json --out=report.json  # Als JSON-Datenstruktur
cloc . --csv --out=report.csv    # Für Excel / Tabellen
```

## 💡 Profi-Tricks

- **Git-Commits vergleichen:** Du willst wissen, wie viele Zeilen Code sich zwischen zwei Git-Commits oder Branches verändert haben?
    
    Bash
    
    ```
    cloc --git --diff main feature-branch
    ```
    
- **Aus einer komprimierten Datei lesen:** `cloc` kann direkt in `.tar.gz` oder `.zip` Archive schauen, ohne dass du sie vorher entpacken musst:
    
    Bash
    
    ```
    cloc projekt.zip
    ```