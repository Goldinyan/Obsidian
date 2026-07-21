# Untitled

Ja, das kannst du über ein Tool namens **Knip** (oder alternativ **ts-prune**) machen. Das sind Werkzeuge zur statischen Code-Analyse, die genau dafür gebaut wurden, ungenutzte Dateien ("Dead Code"), verwaiste Imports und ungenutzte NPM-Packages in Next.js/TypeScript-Projekten zu finden.

Hier ist der schnellste Weg, um ungenutzte Dateien zu filtern:

---

### Methode 1: Der sauberste Weg mit **Knip** (Empfohlen)

Knip ist extrem mächtig für Next.js-Projekte, da es versteht, welche Dateien Root-Pages (`page.tsx`) sind und welche Komponenten nirgends importiert werden.

**1. Installieren:**

```bash
npm install -D knip typescript

```

**2. Ausführen:**
Du kannst Knip direkt im Terminal laufen lassen. Der `--production` Flag sorgt dafür, dass nur dein echter App-Code (ohne Test-Dateien oder Config-Skripte) gescannt wird:

```bash
npx knip --production

```

**3. Das Ergebnis:**
Knip gibt dir im Terminal eine saubere Liste aus, aufgeteilt nach:

* `Unused files` (Dateien, die von nirgendwo importiert werden ➡️ **Das ist das, was du suchst**)
* `Unused exports` (Funktionen/Typen, die exportiert, aber nie importiert werden)
* `Unused dependencies` (NPM-Pakete in der `package.json`, die du löschen kannst)

---

### Methode 2: Der schnelle VS Code Trick (Ohne Installation)

Wenn du keine Tools installieren willst, kannst du die VS Code Suche missbrauchen, um nach Dateien zu filtern, deren Name nirgendwo im Code auftaucht:

1. Drücke `Strg + Shift + F` (Windows) oder `Cmd + Shift + F` (Mac), um die **globale Suche** zu öffnen.
2. Gib den Namen einer verdächtigen Komponente ein (z. B. `AvatarView`).
3. Wenn als einziges Ergebnis die Datei selbst auftaucht (`export default function AvatarView...`), weißt du sofort, dass sie nirgendwo importiert wird.

### Methode 3: Für TypeScript-Spezifisches (**ts-prune**)

Falls Knip dir zu viele Infos ausgibt und du *nur* ungenutzte TypeScript-Exporte sehen willst:

```bash
npx ts-prune

```

Das listet dir jede Datei und die dazugehörige Zeile auf, die ungenutzt im Projekt herumliegt.:w
