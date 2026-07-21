
# Raycasting: Warum diese zwei Zeilen einen Strahl erzeugen

```c
x_draw += step * cos(ray.angle);
y_draw += step * sin(ray.angle);
```

## Grundprinzip
Ein Punkt wird in jeder Schleifeniteration um einen kleinen Vektor verschoben. Dieser Vektor zeigt in die Richtung des Winkels `ray.angle`. Dadurch entsteht eine gerade Linie.

---

## Richtung durch Winkel
- `cos(angle)` liefert die horizontale Komponente  
- `sin(angle)` liefert die vertikale Komponente  
Beides zusammen ergibt einen Richtungsvektor.

---

## Schrittweise Bewegung
Mit konstantem `step` (z. B. 1):

- Startpunkt: `(x_start, y_start)`
- Jede Iteration verschiebt den Punkt um denselben Richtungsvektor
- Dadurch entsteht eine gleichmäßige, gerade Linie

---

## Geometrischer Hintergrund
Die Bewegung entspricht einer parametrischen Geraden:

```
x(t) = x0 + t * cos(angle)
y(t) = y0 + t * sin(angle)
```

mit t = 1, 2, 3, …

---

## Warum `step` konstant bleibt
Die Linie entsteht durch die fortlaufende Veränderung von `x_draw` und `y_draw`.  
Ein wachsender `step` würde Punkte überspringen und die Linie ungleichmäßig machen.

---

## Kurzfassung
Ein Strahl entsteht, weil in jeder Iteration derselbe Richtungsvektor `(cos(angle), sin(angle))` zum aktuellen Punkt addiert wird. Dadurch wächst die Linie gleichmäßig in Richtung des Winkels.
