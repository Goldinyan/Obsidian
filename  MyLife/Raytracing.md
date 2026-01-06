Ich fasse dir das **kompakt, klar und ohne unnötige Mathematik** zusammen.  
Du wirst danach **genau verstehen**, warum diese zwei Zeilen:

```c
x_draw += step * cos(ray.angle);
y_draw += step * sin(ray.angle);
```

einen **strahlenförmigen Lichtstrahl** erzeugen.

---

# 🔥 **Warum funktioniert das?**  
Weil du hier **einen Punkt immer wieder ein kleines Stück in eine bestimmte Richtung verschiebst**.

Diese Richtung wird durch den Winkel `ray.angle` bestimmt.

---

# 1. **Ein Winkel beschreibt eine Richtung**

Ein Winkel in 2D sagt dir:

- **cos(angle)** → wie weit du in X‑Richtung gehst  
- **sin(angle)** → wie weit du in Y‑Richtung gehst  

Das ist eine fundamentale Eigenschaft des Einheitskreises.

---

# 2. **cos und sin liefern eine Richtungs‑Einheit**

Wenn du dir einen Kreis vorstellst:

- `cos(angle)` ist die horizontale Komponente  
- `sin(angle)` ist die vertikale Komponente  

Beispiel:

| Winkel | cos | sin | Richtung |
|--------|-----|-----|----------|
| 0°     | 1   | 0   | nach rechts |
| 90°    | 0   | 1   | nach unten |
| 180°   | -1  | 0   | nach links |
| 270°   | 0   | -1  | nach oben |

---

# 3. **Du gehst in jeder Schleifeniteration einen kleinen Schritt weiter**

```c
double step = 1;
x_draw += step * cos(ray.angle);
y_draw += step * sin(ray.angle);
```

Das bedeutet:

- du startest bei `x_start, y_start`
- du gehst **1 Pixel** in Richtung `angle`
- dann nochmal 1 Pixel
- dann nochmal
- usw.

Dadurch entsteht eine **gerade Linie**.

---

# 4. **Die while‑Schleife verlängert den Strahl**

```c
while (!reached_end_of_screen && !object_hit) {
    x_draw += step * cos(ray.angle);
    y_draw += step * sin(ray.angle);
    draw_pixel(x_draw, y_draw);
}
```

Das heißt:

- solange der Strahl nicht den Bildschirm verlässt  
- und nicht ein Objekt trifft  
- wird er **immer weiter verlängert**

---

# 5. **Du zeichnest jeden Zwischenpunkt**

```c
SDL_Rect ray_point = {x_draw, y_draw, 1, 1};
SDL_FillRect(surface, &ray_point, color);
```

Dadurch wird der Strahl sichtbar.

---

# 6. **Warum ist das so simpel?**

Weil du **keine Linie berechnest**.  
Du **gehst einfach immer weiter in dieselbe Richtung**.

Das ist der einfachste Raycasting‑Algorithmus überhaupt.

---

# 7. **Was passiert geometrisch?**

Du erzeugst eine parametrisierte Linie:

\[
x(t) = x_0 + t \cdot \cos(\theta)
\]
\[
y(t) = y_0 + t \cdot \sin(\theta)
\]

Mit `t = 1, 2, 3, 4, ...`.

Das ist die Standardform einer Geraden in 2D.

---

# 8. **Warum funktioniert das für jeden Winkel?**

Weil `cos` und `sin` immer eine Richtung auf dem Kreis definieren.

Du gehst also nicht:

- in X **oder** Y  
- sondern in X **und** Y gleichzeitig  

→ dadurch entsteht eine diagonale Bewegung.

---

# 9. **Warum sieht es wie ein Lichtstrahl aus?**

Weil du:

- viele Strahlen erzeugst (`RAYS_NUMBER`)
- jeder Strahl einen anderen Winkel hat
- alle Strahlen vom selben Punkt starten

Das ergibt einen **Fächer aus Linien**, also Licht.

---

# 🔥 **Kurzfassung in einem Satz**

> Du nimmst einen Startpunkt und verschiebst ihn in jeder Schleifeniteration um einen kleinen Vektor, der durch `cos(angle)` und `sin(angle)` bestimmt wird. Dadurch entsteht eine gerade Linie in Richtung des Winkels.

---

Wenn du willst, kann ich dir das auch:

- **grafisch erklären**  
- **mit ASCII‑Diagrammen zeigen**  
- **in 5 Zeilen Minimal‑Code reduzieren**  
- **mit Debug‑Ausgabe visualisieren**  

Sag einfach Bescheid.Du **musst `step` nicht erhöhen**, damit der Strahl weiterläuft.  
Das ist genau der Punkt, den viele am Anfang falsch einschätzen.

Ich erkläre dir das **kompakt und absolut klar**, ohne unnötige Mathematik.

---

# 🔥 Warum der Strahl weiterläuft, obwohl `step` konstant bleibt

Du machst in jeder Schleifeniteration:

```c
x_draw += step * cos(angle);
y_draw += step * sin(angle);
```

Wenn `step = 1` ist, bedeutet das:

- **x_draw wird jedes Mal um denselben Wert erhöht**
- **y_draw wird jedes Mal um denselben Wert erhöht**

Beispiel:  
Winkel = 0° → cos = 1, sin = 0

```
Iteration 1: x = x + 1
Iteration 2: x = x + 1
Iteration 3: x = x + 1
Iteration 4: x = x + 1
...
```

Das ergibt eine **gerade Linie nach rechts**.

---

# 🔹 Der Trick: Du erhöhst nicht `step`, sondern **x_draw und y_draw**

`step` ist nur die **Schrittgröße**.

Die Bewegung entsteht dadurch, dass du **x_draw und y_draw immer weiter veränderst**.

---

# 🔹 Beispiel mit einem schrägen Winkel

Nehmen wir 45°:

- cos(45°) ≈ 0.707  
- sin(45°) ≈ 0.707  

Dann passiert:

```
Iteration 1: x += 0.707, y += 0.707
Iteration 2: x += 0.707, y += 0.707
Iteration 3: x += 0.707, y += 0.707
Iteration 4: x += 0.707, y += 0.707
...
```

Das ergibt eine **diagonale Linie**.

---

# 🔹 Warum das eine Linie ergibt

Weil du jedes Mal **denselben Richtungsvektor** addierst:

\[
(\cos(\theta), \sin(\theta))
\]

Das ist wie:

- immer wieder **den gleichen Schritt** in die gleiche Richtung machen  
- dadurch entsteht eine **gerade Linie**

---

# 🔥 Kurzfassung

> Der Strahl wird länger, weil du `x_draw` und `y_draw` in jeder Schleife veränderst.  
> `step` bleibt gleich, aber die Position ändert sich jedes Mal.

---

# 🔹 Wenn du `step` erhöhen würdest…

Dann würde der Strahl **immer schneller** werden:

```
step = 1
step = 2
step = 3
step = 4
```

Dann würdest du **Punkte überspringen**, und die Linie wäre **löchrig**.

Darum lässt man `step` konstant.

---

Wenn du willst, kann ich dir das auch als **ASCII‑Diagramm** zeigen, oder dir eine **Debug‑Version** bauen, die jeden Schritt ausgibt.