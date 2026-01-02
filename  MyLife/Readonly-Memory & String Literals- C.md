Date: 2026‑01‑02  
Tags: { 
#F 
[[%C]]
[[%Memory]]
}

## String literals reside in read‑only memory

In C, the expression

```c
"hello"
```

creates a string literal.  
The compiler stores this literal in a read‑only memory segment (typically `.rodata`).  
This memory must not be modified.

Example:

```c
char *s = "hello";
```

`s` points to the literal stored in read‑only memory.

```
s ──► ['h' 'e' 'l' 'l' 'o' '\0']   (read‑only)
```

## Writing to a string literal causes a segmentation fault

```c
char *s = "hello";
s[0] = 'H';   // segmentation fault
```

Reason:

- `s[0]` is equivalent to `*(s + 0)`
- The write targets read‑only memory
- The operating system blocks the write → segmentation fault

## Correct, writable alternative

If the string must be modifiable, create a **copy** in writable memory:

```c
char s[] = "hello";   // array, not read‑only
s[0] = 'H';           // valid
```

This creates a local array containing a writable copy of the literal.

## Key rule

- `char *s = "text";` → points to read‑only memory → not modifiable  
- `char s[] = "text";` → creates a writable array → modifiable
