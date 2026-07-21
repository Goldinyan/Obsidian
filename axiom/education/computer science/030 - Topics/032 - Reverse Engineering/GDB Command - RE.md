Date: 2025-12-21
Tags: {
#F 
[[%Command]]
[[%Terminal]]
[[%Reverse Engineering]]
[[%Cyber Security]]
[[%Binary]]
[[%LowLevel]]
}


```bash
# Installation (gef via git)
git clone https://github.com/hugsy/gef.git
echo "source /path/to/gef.py" >> ~/.gdbinit
```

## 🧠 Grundlagen
```bash
gdb ./binary         # Start mit Binary
start                # Startet main()
break <func|addr>    # Breakpoint setzen
run / args           # Ausführen mit args
continue / c         # Weiterlaufen
next / n             # Nächste Zeile (kein Sprung in Funktionen)
step / s             # Nächste Zeile (springt in Funktionen)
finish               # Funktion verlassen
quit                 # Beenden
```

## 🧵 Stack & Speicher
```bash
info registers       # Register anzeigen
x/10gx $rsp          # Stack anzeigen (hex, 8-byte aligned)
x/s $rsp             # String am Stack
x/20xw <addr>        # Speicher dumpen (wordweise)
x/20xb <addr>        # Byteweise dumpen
x/20i <addr>         # Disassembly ab Adresse
```

## 🧩 GEF Shortcuts
```bash
context              # Zeigt Stack, Code, Register
hexdump <addr>       # Hexdump ab Adresse
dereference <addr>   # Zeigt was ein Pointer zeigt
telescope $rsp       # Stack visualisiert
vmmap                # Speicherbereiche
canary               # Stack Canary anzeigen
```

## 🔍 Analyse
```bash
info functions       # Alle Funktionen
info files           # Geladene Dateien
info frame           # Aktueller Stackframe
backtrace / bt       # Callstack anzeigen
disas <func>         # Funktion disassemblieren
```

## 🧪 Interaktiv
```bash
set var x = 0x1234   # Variable setzen
print x              # Variable anzeigen
display x            # Bei jedem Stop anzeigen
watch x              # Watchpoint setzen
```

## 🧷 Tipps
- `gef config` → GEF konfigurieren
- `gef save` → Einstellungen speichern
- `gef restore` → Einstellungen laden
- Nutze `telescope` für Stack-Strings
- Nutze `canary` für Buffer Overflow Checks

