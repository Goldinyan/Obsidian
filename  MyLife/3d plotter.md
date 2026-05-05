---
id: 3d plotter
aliases:
Topic:
Related:
Tags:
  - w
Date: 2026-05-04T16:58:00
Updated:
Source:
---
# 3d plotter

Verstanden, wenn das Projekt wächst und Features wie ein rotierbares Koordinatensystem, Grid-Rendering und komplexe mathematische Operationen dazukommen, reicht eine flache Struktur nicht mehr aus. Wir brauchen eine **Sub-Modul-Struktur** im Core.

Hier ist der "Deep Dive" Tree. Ich habe die Logik so aufgeteilt, dass die Mathematik von der Geometrie getrennt ist:

### Der erweiterte Projekt-Tree

Plaintext

```
3D_Function_Plotter/
├── CMakeLists.txt
├── extern/                      # Bibliotheken (GLM, ImGui, GLFW, Glad)
├── core/
│   ├── CMakeLists.txt
│   ├── include/core/
│   │   ├── math/                # Die reine Mathematik
│   │   │   ├── lexer.hpp        # Zerlegt String in Tokens
│   │   │   ├── parser.hpp       # Baut den Abstract Syntax Tree (AST)
│   │   │   ├── expression.hpp   # Basisklasse für Rechenoperationen
│   │   │   └── function_3d.hpp  # Kapselt f(x,y)
│   │   ├── geometry/            # Von Mathe zu Punkten/Linien
│   │   │   ├── mesh.hpp         # Speichert Vertices & Indices
│   │   │   ├── generator.hpp    # Erzeugt das Funktions-Mesh
│   │   │   └── axis_grid.hpp    # Erzeugt die Linien für X, Y, Z Achsen
│   │   └── utils/
│   │       └── logger.hpp       # Debugging-Hilfe
│   └── src/
│       ├── math/ (parser.cpp, lexer.cpp, etc.)
│       └── geometry/ (generator.cpp, axis_grid.cpp)
│
├── app/
│   ├── CMakeLists.txt
│   ├── assets/
│   │   └── shaders/
│   │       ├── function.vert    # Shader für die Fläche
│   │       ├── function.frag
│   │       ├── line.vert        # Shader für das Koordinatensystem
│   │       └── line.frag
│   ├── include/app/
│   │   ├── input_handler.hpp    # Verarbeitet Maus (Rotation) & Keyboard
│   │   ├── camera.hpp           # Berechnet View- & Projection-Matrix
│   │   ├── renderer/
│   │   │   ├── shader.hpp       # Lädt/Kompiliert GLSL
│   │   │   └── scene.hpp        # Hält alle Objekte (Mesh, Achsen)
│   │   └── ui_layer.hpp         # ImGui Interface
│   └── src/
│       ├── main.cpp
│       ├── camera.cpp
│       └── input_handler.cpp
│
└── tests/                       # WICHTIG: Teste den Parser separat!
```

---

### Warum diese Aufteilung bei Komplexität hilft:

#### 1. `core/math` (Der Gehirnschmalz)

Wenn du `sin(x) * cos(y)` parsen willst, ist das ein klassischer Compiler-Bau-Task.

- **Lexer:** Erkennt Symbole (`sin`, `(`, `+`).
    
- **Parser:** Baut einen Baum auf. Das ist wichtig, damit du die Funktion im Loop Millionen Mal pro Sekunde für verschiedene $x/y$-Werte aufrufen kannst, ohne den String jedes Mal neu zu lesen.
    

#### 2. `core/geometry` (Das Skelett)

Hier wird die Rotation vorbereitet.

- **axis_grid.hpp:** Du willst nicht nur die Funktion sehen, sondern auch ein Gitter. Das Gitter ist ein eigenes Objekt mit eigenen Vertices.
    
- **Generator:** Hier entscheidest du über die Auflösung (z.B. $200 \times 200$ Quadrate).
    

#### 3. `app/camera.hpp` & `input_handler.hpp` (Die Rotation)

Das ist die Antwort auf dein "Rotation"-Bedürfnis.

- Die Kamera hält eine **View-Matrix**.
    
- Der `input_handler` registriert Mausbewegungen (Delta X/Y).
    
- Diese Bewegung füttert die Kamera, die eine neue Matrix berechnet:
    
    $$View = Translation \cdot Rotation_X \cdot Rotation_Y$$
    
- Diese Matrix schickst du an den Shader in `assets/shaders/`.
    

#### 4. `app/renderer/scene.hpp`

Anstatt alles in die `main.cpp` zu klatschen, verwaltet die `Scene` alle Objekte. Sie sagt: "Zeichne zuerst das Koordinatensystem (Linien-Shader) und dann die mathematische Fläche (Flächen-Shader)".

### Ein wichtiger Hinweis zur Performance:

Da du einen Plotter baust, wird der User oft die Funktion ändern. Wenn das passiert, muss das Mesh im Core neu generiert werden. Durch die Trennung kannst du im Core ein **"Dirty-Flag"** setzen:

1. User ändert Text -> `math/parser` validiert.
    
2. `geometry/generator` baut neues Mesh im Hintergrund.
    
3. `app/renderer` bemerkt das neue Mesh und lädt es hoch (VBO Update).
    

Soll ich dir mal zeigen, wie so ein **`Camera`** Header aussehen müsste, damit die Rotation butterweich läuft?