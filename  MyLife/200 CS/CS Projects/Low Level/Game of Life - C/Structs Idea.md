Date: 2026-01-01
Tags: {
#W 
[[%Projects]]
[[Game of Life - C]]
}


# Structs Idea


```c
typedef struct {
  int width;
  int height;
  unsigned char *cells; // 0 -> tot, 1 -> lebend 
  // unsigned char, weil klein 1 byte 
} grid_t;

typedef struct { 
  grid_t current;
  grid_t next;
} world_state_t;
```

I will now explain in detail, how this struct operates in this game and why I choose it. First width and height is the indicator of the grid, and customizable, leading to a better user experience. 

I needed a way to dynamically load a 2D Array responsible for the grid, which is not possible, so I went with creating a pointer of a 1D Array, allocating it in a dynamic way:
```c
cells = calloc(width * height, sizeof(unsigned char));
```

Therefore creating an Array with 20 values (width = 5; height = 4): 

```
Index:   0 1 2 3 4   5 6 7 8 9   10 11 12 13 14   15 16 17 18 19
cell:  (0,0)...    (0,1)...     (0,2)...         (0,3)...
```
A 2D coordinate (x, y) can be read by converting it into an index, and using this index to access the Array:

```c
index = y * width + x;
return g->cells[y * g->width + x];
```

Acquiring the index this way, allows us to structure the rest of the projects in a comfortable way:
```c
inline unsigned char grid_get(const grid_t *g, int x, int y) {
    return g->cells[y * g->width + x];
}

inline void grid_set(grid_t *g, int x, int y, unsigned char value) {
    g->cells[y * g->width + x] = value;
}
```

Both functions only do one thing, calculating the index and returning or writing the value, making the 1D-Array logically a 2D-Array

Another question one might have is
# 3. Warum wir zwei Grids haben (`current` und `next`)

Während du das Game of Life aktualisierst, darfst du **den aktuellen Zustand nicht überschreiben**, bevor du alle Zellen berechnet hast.

Beispielproblem:

- Du berechnest Zelle (0,0) neu  
- Du überschreibst sie  
- Jetzt hat Zelle (0,1) falsche Nachbarn, weil du schon etwas verändert hast

Darum:

- `current` = alter Zustand  
- `next` = neuer Zustand, der gerade berechnet wird  

---

# 4. Warum wir am Ende tauschen

Nach jedem Schritt:

```c
grid_t tmp = *cur;
*cur = *next;
*next = tmp;
```

Das bedeutet:

- `next` wird zum neuen `current`  
- das alte `current` wird zum neuen `next` (leer, bereit für den nächsten Schritt)

Wir tauschen nur die **Pointer und Metadaten**, nicht den Inhalt.  
Das ist extrem effizient.

---

# 5. Kompakte Gesamtlogik

```c
// Lesen
alive = grid_get(cur, x, y);

// Berechnen
new_value = ...;

// Schreiben
grid_set(next, x, y, new_value);

// Am Ende
swap(current, next);
```

Damit bleibt:

- `current` immer unverändert während der Berechnung  
- `next` enthält den neuen Zustand  
- der Tausch macht den neuen Zustand zum aktuellen  

---

Wenn du willst, kann ich dir jetzt:

- das Rendering bauen  
- ein Startmuster setzen  
- oder den kompletten `main()`‑Loop schreiben.