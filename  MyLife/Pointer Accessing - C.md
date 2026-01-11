Date: 2026-01-11
Tags: {
#W
}


# Pointer Accessing - C

##### A pointer points to a value, and to change this value you have to dereference.

---

## Primitive Types (`int`, `bool`, `float`, …)

### Reading & Writing:
```c
*p = value;
value = *p;
```

### Example:
```c
bool *quit = &did_quit;
*quit = true;
```

---

## Struct‑Pointer

### Accessing:
```c
ptr->field
```

### Meaning:
```c
ptr->field   ==   (*ptr).field
```

The -> dereferences automatically and accesses the field

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



# References