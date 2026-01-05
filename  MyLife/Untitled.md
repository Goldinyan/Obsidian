Hier ist eine **kompakte, saubere Obsidian‑Note**, perfekt als dauerhafte Referenz.  
Format ist direkt copy‑paste‑fähig.

---

# 📌 Pointer‑Zugriff in C (Kurzreferenz)

## 🎯 Grundprinzip
Ein Pointer zeigt auf einen Wert.  
Um den Wert zu ändern, musst du **dereferenzieren**.

---

## 🔹 Primitive Typen (`int`, `bool`, `float`, …)

### Schreiben/Lesen:
```c
*p = value;
value = *p;
```

### Beispiel:
```c
bool *quit = &did_quit;
*quit = true;
```

---

## 🔹 Struct‑Pointer

### Zugriff auf Felder:
```c
ptr->field
```

### Bedeutung:
```c
ptr->field   ==   (*ptr).field
```

Der `->`‑Operator **dereferenziert automatisch** und greift dann auf das Feld zu.

### Beispiel:
```c
state->meta.lost = true;
state->snake.body[0].x++;
```

---

## 🔹 Merksatz (ultrakompakt)

- **Primitive Werte:** `*p = value;`
- **Struct‑Felder:** `p->field = value;`
- **`->` = syntaktischer Zucker für `(*p).field`**

---

## 🔹 Minimalbeispiele

### Primitive:
```c
void set_flag(bool *flag) {
    *flag = true;
}
```

### Struct:
```c
void update(game_state_t *s) {
    s->meta.time++;
    s->snake.body[0].y--;
}
```

---

Wenn du willst, kann ich dir auch eine zweite Note machen:  
**„Pointer in 60 Sekunden“** oder **„Pointer‑Fehler, die jeder macht“**.