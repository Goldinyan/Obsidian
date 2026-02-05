Date: 2026-01-03
Tags: {
#F 
[[%Mathematics]]
[[%MathFunctions]]
[[%Integral]]
}


# Integral Basics


Integrale werden benutzt, um die Fläche zu berechnen, die zwischen dem Graphen einer Funktion und der x-Achse im Bereich $x \to y$ liegt.

$$
\int^{y}_{x}f(x)dx
$$
Das $\mathrm{d}x$ zeigt an, nach welcher Variable integriert wird. Es markiert nicht das Ende der Funktion, sondern gehört als Bestandteil zum Integralzeichen.

Integrieren ist die Umkehrung der [[Ableitung Basics]] und stellt die Stammfunktion wieder her. Dafür benötigen wir die Ableitungsregeln.

Lass uns zwei Beispiele durchgehen.

## Beispiel 1:
$$
\int^{4}_{0}x\, \mathrm{d}x
$$
Um die Stammfunktion zu bilden, erhöhen wir den Exponenten um eins und teilen durch den neuen Exponenten. Falls ein Vorfaktor vorhanden ist, wird er wie gewohnt mit dem Zähler multipliziert.

Beispiele:
$$
x^3 \rightarrow \frac{1}{4}x^4
$$
$$
x \rightarrow \frac{1}{2}x^2
$$
$$
3x \rightarrow \frac{3}{2}x^2
$$


## Allgemeine Regel:

- Exponenten um eains erhöhen
- Durch den neuen Exponenten teilen.
- Vorfaktoren wie gewohnt mit dem Zähler multiplizieren

$$
\int x^{n}\,\mathrm{d}x = \frac{1}{n+1}x^{n+1} + C
$$

Für bestimmte Integrale entfällt das +C. Nachdem die Stammfunktion gebildet wurde, setzt man die Grenzen ein und subtrahiert:

$$
\left[\frac{1}{2}x^{2}\right]_{0}^{4}

= \frac{1}{2}4^{2} - \frac{1}{2}0^{2}

= 8
$$

## 2. Beispiel:

$$
\int^{1}_{0}4x^2+x \; \mathrm{d}x
$$

$$
\frac{4}{3}x^3 + \frac{1}{2}x^2
$$
$$
\left[\frac{4}{3}x^{3}+\frac{1}{2}x^{2}\right]_{0}^{1}

= \left(\frac{4}{3}\cdot 1^{3}+\frac{1}{2}\cdot 1^{2}\right)

\;-\;

\left(\frac{4}{3}\cdot 0^{3}+\frac{1}{2}\cdot 0^{2}\right)
$$
$$
= \frac{4}{3} + \frac{1}{2}
$$
$$
= \frac{11}{6}
$$

# References