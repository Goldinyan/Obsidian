# SKHD problem


# Post-Mortem: `skhd` Fehleranalyse & Lösung

## 1. Das Kernproblem

Der macOS Tastatur-Shortcut-Daemon `skhd` lief scheinbar im Hintergrund, reagierte jedoch auf keinerlei Tasteneingaben (`alt - h/j/k/l`), um den Window-Manager `yabai` anzusteuern. Beim Versuch, das Programm manuell im Terminal zu starten, brach es ab.

### Ursprünglicher Fehler-Output:

```bash
~ ʎ skhd
skhd: could not lock pid-file! abort..
```

---

## 2. Die Fehlversuche (Und warum sie fehlschlugen)

### Ansatz A: Homebrew Service-Neustart (`brew services restart`)

* **Versuch:** Den Dienst über den Standard-Paketmanager neu starten.
* **Problem:** Homebrew verweigerte den Dienst aufgrund eines Tippfehlers im Repository-Namen (`koejeishiya` mit `j` statt `koekeishiya` mit `k`). Nach Behebung des Tippfehlers stellte sich heraus, dass die Formel gar kein `plist`-Skript für Homebrew besitzt.
* **Outputs:**
```bash
# Tippfehler
Error: Refusing to load formula koekeishiya/formulae/skhd from untrusted tap...

# Nach dem Beheben des Vertrauens-Fehlers
Error: Invalid usage: Formula `skhd` has not implemented #plist, #service or provided a locatable service file.
```



### Ansatz B: Symlinks & Manuelles Starten mit `--start-service`

* **Versuch:** `skhd` mit dem Flag `-c` auf die richtige Konfigurationsdatei zwingen.
* **Problem:** `skhd` akzeptiert das Flag `--start-service` nicht, wenn gleichzeitig manuell eine Config-Datei übergeben wird. Zudem blockierte der alte Prozess weiterhin das System.
* **Output:**
```bash
skhd: unrecognized option `--start-service'
skhd: could not lock pid-file! abort..
```



---

## 3. Die eigentlichen Ursachen (Root Causes)

Durch Analyse der Prozessliste (`ps aux | grep skhd`) und Untersuchung des Dateisystems wurden drei fatale Fehler entdeckt:

1. **Ein Zombie-Prozess blockierte das System:** Seit Montagabend lief eine alte, eingefrorene Instanz von `skhd` (PID `25116`), die die Sperrdatei (`/tmp/skhd.pid`) besetzte und verhinderte, dass neue Instanzen geladen wurden.
2. **Falsches Home-Verzeichnis:** Der Zombie-Prozess suchte stur unter `/Users/ansgar/...`. Das tatsächliche Benutzerverzeichnis auf dem Mac hieß jedoch `/Users/ansgarseifert/...`. `skhd` lud folglich eine nicht-existente, leere Konfiguration.


---

## 4. Die endgültige Lösung (Schritt für Schritt)



### Schritt 1: Den Zombie-Prozess terminieren

Der alte Prozess von Montag sowie die blockierende PID-Sperrdatei wurden rigoros gelöscht:

```bash
kill -9 25116
rm -f /tmp/skhd.pid
```

### Schritt 2: Pfad-Verknüpfung (Symlink) erstellen

Um den Pfadkonflikt zwischen `ansgar` und `ansgarseifert` dauerhaft zu lösen, wurde eine symbolische Verknüpfung angelegt, damit `skhd` die Datei immer findet:

```bash
ln -s /Users/ansgarseifert/.config/skhd ~/.config/skhd
```

### Schritt 3: Dienst sauber neu starten

Nachdem der Weg frei war, reichte der integrierte Befehl, um den Daemon frisch im System zu registrieren:

```bash
skhd --start-service
```

### Finaler Erfolgs-Output (`ps aux | grep skhd`):

```text
ansgarseifert    45889   ...   8:46AM   ... /opt/homebrew/bin/skhd
```

*Ergebnis:* Ein brandneuer Prozess (PID `45889`) läuft stabil mit der korrekten, reparierten Konfiguration. Die Keybinds funktionieren wieder einwandfrei.

