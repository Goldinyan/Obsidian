# Heap in C

## Eigenschaften
- Manuelle Speicherverwaltung (malloc, calloc, realloc, free)
- Flexibel, dynamisch, aber langsamer als Stack
- Fragmentierung möglich
- Speicher bleibt bestehen, bis er explizit freigegeben wird

## Lebensdauer
- Variablen leben über Funktionsgrenzen hinweg
- Ideal für große oder dynamische Datenstrukturen

## Typische Fehler
- Memory Leak (free vergessen)
- Double Free
- Use‑After‑Free
- Dereferenzieren von NULL-Pointern

## Beispiel
```c
int *p = malloc(sizeof(int));
if (!p) {
    // Fehlerbehandlung
}
*p = 10;
free(p);
```

## Merksatz
Heap = flexibel, manuell, langlebig, fehleranfällig.
