#Da läuft der Tailwind v4 Oxide-Compiler im Language Server Amok und frisst dir die CPU weg. Das passiert ganz gerne mal, wenn Neovim oder deine IDE im Hintergrund mehrere Instanzen triggert oder sich beim Scannen von Verzeichnissen verschluckt.

Da du auf dem Mac unterwegs bist, kannst du alle diese Prozesse am schnellsten mit **`pkill`** und einem Pattern-Matching auf den Skriptnamen wegräumen.

Hier sind die Befehle für dein Terminal:

### 1. Die präzise Variante (Empfohlen)

Hiermit killst du gezielt alle Node-Prozesse, die `oxide-helper` im Pfad aufweisen, ohne andere laufende Node-Instanzen (wie deinen Next.js-Dev-Server) zu gefährden:

```bash
pkill -f oxide-helper

```

*Der Flag `-f` sorgt dafür, dass das Muster auf die vollständige Argumentenliste (den gesamten Pfad) angewendet wird, nicht nur auf den Prozessnamen `node` selbst.*

---

### 2. Die "Tabula Rasa"-Variante

Falls der Language-Server danach immer noch hängt oder von Editoren wiederbelebt wird, kannst du radikal den gesamten Tailwind-Language-Server abschießen:

```bash
pkill -f @tailwindcss/language-server

```

---

### 3. Auf Nummer sicher gehen

Wenn du vor dem KIllen erst sehen willst, welche PIDs (Prozess-IDs) genau getroffen werden, kannst du das mit `pgrep` überprüfen:

```bash
pgrep -fl oxide-helper

```

> **Tipp für Neovim/deine IDE:** Wenn die Prozesse direkt nach dem Killen wieder spawnen und deine CPU direkt wieder hochjagt, liegt das meistens an einem hängenden LSP-Client. In Neovim hilft dann oft ein kurzes `:LspRestart` oder das Schließen des Editors, bevor du den `pkill`-Befehl feuerst. Untitled

