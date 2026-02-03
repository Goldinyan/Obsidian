
# Arrayzugriff in C: echtes Array vs. malloc-Pointer

## 1. Gemeinsamer Punkt: Indexzugriff
Der Ausdruck

```c
int_array[5]
```

ist immer äquivalent zu:

```c
*(int_array + 5)
```

Der Indexoperator ist reine Pointer-Arithmetik. C führt keine Bounds-Checks durch.

---

## 2. Unterschied: Speicherherkunft

### Heap (malloc)

```c
int *int_array = malloc(1024);  // 1024 Bytes
int_array[5] = 50;
```

- Speicher kommt vom Heap  
- Muss mit `free` freigegeben werden  
- Compiler kennt die Anzahl der Elemente nicht  
- Interpretation der Bytes als `int[]` liegt beim Programmierer

Wenn `sizeof(int) == 4`, passen 256 Elemente hinein.

---

### Stack (echtes Array)

```c
int int_array[256];
int_array[5] = 50;
```

- Feste Größe, Teil des Typs  
- Compiler kennt die Elementanzahl  
- Keine Freigabe nötig  
- Speicher liegt typischerweise auf dem Stack

---

## 3. Unterschied: sizeof

```c
int int_array[256];
sizeof(int_array);     // 256 * sizeof(int)

int *p = malloc(1024);
sizeof(p);             // sizeof(int*) (z. B. 8)
```

Bei Arrays liefert `sizeof` die gesamte Arraygröße.  
Bei malloc-Pointern liefert `sizeof` nur die Pointergröße.

---

## 4. Fazit

- Der Zugriff `int_array[5]` funktioniert in beiden Fällen identisch.  
- Ein echtes Array hat feste Größe und Typinformation.  
- Ein malloc-Pointer hat nur Speicher, aber keine Größeninformation.  

Wenn du willst, kann ich dir auch eine Version mit Diagrammen oder eine noch kompaktere Referenz erstellen.