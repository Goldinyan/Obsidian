Hier ist ein kompakter, sachlicher Abschnitt mit **kurzen, präzisen C‑Codebeispielen**, die typische Ursachen für Segmentation Faults demonstrieren. Stil und Struktur passen zu deinem Obsidian‑Dokument.

---

# Häufige Ursachen für Segmentation Faults in C  
Date: 2026-01-02  
Tags: { #W }

## 1. Zugriff über einen Nullpointer

```c
int *p = NULL;
*p = 10;   // seg fault
```

---

## 2. Array out of bounds

```c
int a[3] = {1,2,3};
a[10] = 5;   // seg fault (undefined behavior)
```

---

## 3. Pointer-Arithmetik außerhalb des gültigen Bereichs

```c
int a[5] = {0};
int *p = a + 100;
*p = 1;      // seg fault
```

---

## 4. Use-after-free

```c
int *p = malloc(sizeof(int));
free(p);
*p = 10;     // seg fault
```

---

## 5. Double free

```c
int *p = malloc(4);
free(p);
free(p);     // seg fault
```

---

## 6. Schreiben in readonly-Speicher (String-Literal)

```c
char *s = "hello";
s[0] = 'H';   // seg fault
```

---

## 7. Dereferenzieren eines uninitialisierten Pointers

```c
int *p;   // uninitialized, contains garbage
*p = 5;   // seg fault
```

---

## 8. Stack overflow durch unendliche Rekursion

```c
void f(void) {
    f();   // eventually seg fault
}
```

---

## 9. Zugriff auf bereits zerstörte automatische Variable (dangling pointer)

```c
int *make_ptr(void) {
    int x = 10;
    return &x;   // returns pointer to dead stack memory
}

int main(void) {
    int *p = make_ptr();
    *p = 5;       // seg fault
}
```

---

Wenn du willst, kann ich dir daraus auch eine noch kompaktere Referenzseite oder eine Version mit kurzen Erklärungen pro Beispiel erstellen.