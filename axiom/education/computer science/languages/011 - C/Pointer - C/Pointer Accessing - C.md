Date: 2026-01-11
Tags: {
#W
[[%C]]
[[%Pointers]]
}

# Pointer Accessing - C

##### A pointer points to a value, and to change this value you have to dereference.

---
## Memorization 

- **Primitive Types:** `*p = value;`
- **Struct‑Fields:** `p->field = value;`
- **`->` = synthetic Sugar for`(*p).field`**

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

### Example:
```c
state->meta.lost = true;
state->snake.body[0].x++;
```




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





# References