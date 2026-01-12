Date: 2026-01-11
Tags: {
#W 
[[%Makefile]]
[[%Compiler]]
[[%SDL]]
}


# Compiling SDL & Makefile




## Minimal-Form:
```bash
gcc main.c -o game -I/opt/homebrew/include/SDL2 -L/opt/homebrew/lib -lSDL2
```

## Meaning of the flags:

Base C Flags can be seen here [[Compiling - C]].
-I<path> -> adds an include path
-L<path> -> Libary path

| Modul       | Purpose                    | Flag            |
|-------------|---------------------------|---------------|
| SDL2        | Core-Libary            | -lSDL2        |
| SDL2_ttf    | TrueType‑Fonts            | -lSDL2_ttf    |
| SDL2_image  | PNG/JPG/BMP loading | -lSDL2_image  |
| SDL2_mixer  | Audio                     | -lSDL2_mixer  |
| SDL2main | SDL-Main Wrapper (required for Windows) | -lSDL2main |
|SDL2_net| Network | -lSDL2_net|
|SDLK2_gfx | Primitive Shapes, Rotating, Zooming| -lSDL2_gfx


## Makefile

```bash
CC = gcc
CFLAGS = -Wall -Wextra -std=c11 -Iinclude -I/opt/homebrew/include
LDFLAGS = -L/opt/homebrew/lib -lSDL2

SRC = $(wildcard src/*.c)
OBJ = $(patsubst src/%.c, object_files/%.o, $(SRC))

TARGET = program

all: $(TARGET)

$(TARGET): $(OBJ)
	$(CC) $(OBJ) -o $(TARGET) $(LDFLAGS)

object_files/%.o: src/%.c
	@mkdir -p object_files
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f object_files/*.o $(TARGET)


```


# References