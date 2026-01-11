

## Minimal-Form:
```bash
gcc main.c -o game -I/opt/homebrew/include/SDL2 -L/opt/homebrew/lib -lSDL2
```

## Meaning of the flags:

Base C Flags can be seen here [[Compiling - C]].

-I<path> -> adds an include path
-L<path> -> Libary path

-lSDL2 -> links SDL2
-lSDL2_ttf -> links SDL2_ttf
-lSDL2_image -> links 
