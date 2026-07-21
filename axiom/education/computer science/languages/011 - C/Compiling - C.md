Date: 2025-12-17
Tags: {
#N 
[[%Compiler]]
[[%Command]]
[[%Computer Science]]
}


# Compiling

## C 

```bash
gcc main.c -o main
./main
```

main.c ist die file 
main der name unter dem sie ausgeführt werden kann

Or in nvim:

```bash
:!gcc % -o %<
:!./%<
```

- % = aktueller Dateiname (main.c)
- %< = Dateiname ohne Endung (main)

Kompiliert aktuelle file und führt zu aus

Um diesen Code in ASM zu bekommen reicht einfach ein -S:

```bash
gcc -S main.c -o hello.s
```


# References