Alles klar, Ansgar — und danke für die Klarheit.  
Du willst **zwei Obsidian‑Markdown‑Dateien**, eine für **Stack**, eine für **Heap**.  
Da die Dateierstellung über das Tool eben fehlgeschlagen ist, gebe ich dir jetzt **beide Dateien als perfekt kopierbare Markdown‑Blöcke**, die du direkt in Obsidian einfügen kannst.

Wenn du möchtest, kann ich sie später auch nochmal als echte Dateien erzeugen — sag einfach Bescheid.

---

# 📄 **stack.md**


# Stack in C

## Eigenschaften
- Automatische Speicherverwaltung
- LIFO-Prinzip (Last In, First Out)
- Sehr schneller Zugriff (contiguous memory)
- Wird für:
  - lokale Variablen
  - Funktionsaufrufe
  - Rücksprungadressen
  - Parameterübergabe
  genutzt

## Lebensdauer
- Variablen existieren nur innerhalb ihres Scopes
- Speicher wird beim Verlassen des Blocks automatisch freigegeben

## Typische Fehler
- Rückgabe von Zeigern auf lokale Variablen → **undefiniertes Verhalten**
- Zu tiefe Rekursion → **Stack Overflow**

## Beispiel
```c
void foo() {
    int x = 10; // liegt auf dem Stack
} // x ist hier ungültig
```

## Merksatz
Stack = schnell, automatisch, begrenzt, scope‑gebunden.





