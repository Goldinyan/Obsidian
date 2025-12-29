
### 1. Komplette Overkill‑Formel für Obsidian

$$
\frac{
\displaystyle
\int_{0}^{\pi} \left( \sin^4 x + \cos^4 x \right)\,dx
+
\sum_{k=1}^{4} \ln(k!)
-
\prod_{n=1}^{3} \left( n + \frac{1}{n} \right)
+
\sqrt[3]{(e^{i\pi}+1)^2 + 8}
}{
\displaystyle
\Gamma\!\left(\tfrac{5}{2}\right)
+
\zeta(2)
}
$$

---

### 2. Teil A – Das Integral

$$
\int_{0}^{\pi} \left( \sin^4 x + \cos^4 x \right)\,dx
$$

Wir benutzen zuerst eine Umformung:

$$
\sin^4 x + \cos^4 x
=
(\sin^2 x + \cos^2 x)^2 - 2\sin^2 x \cos^2 x
$$

Da

$$
\sin^2 x + \cos^2 x = 1
$$

wird das zu:

$$
\sin^4 x + \cos^4 x = 1 - 2\sin^2 x \cos^2 x
$$

Jetzt schreiben wir den Term mit 
$$\sin^2 x \cos^2 x $$ um. 

Aus

$$
\sin(2x) = 2\sin x \cos x
$$

folgt

$$
\sin^2(2x) = 4\sin^2 x \cos^2 x
$$

also

$$
\sin^2 x \cos^2 x = \frac{1}{4}\sin^2(2x)
$$

Einsetzen:

$$
\sin^4 x + \cos^4 x
=
1 - \frac{1}{2}\sin^2(2x)
$$

Jetzt das Integral:

$$
\int_0^\pi \left( \sin^4 x + \cos^4 x \right)\,dx
=
\int_0^\pi \left( 1 - \frac{1}{2}\sin^2(2x) \right)\,dx
$$

Aufteilen:

$$
= \int_0^\pi 1\,dx - \frac{1}{2}\int_0^\pi \sin^2(2x)\,dx
$$

Das erste Integral:

$$
\int_0^\pi 1\,dx = \pi
$$

Für das zweite nutzen wir

$$
\sin^2 u = \frac{1 - \cos(2u)}{2}
$$

mit \(u = 2x\):

$$
\sin^2(2x) = \frac{1 - \cos(4x)}{2}
$$

Dann:

$$
\int_0^\pi \sin^2(2x)\,dx
=
\int_0^\pi \frac{1 - \cos(4x)}{2}\,dx
=
\frac{1}{2}\int_0^\pi (1 - \cos(4x))\,dx
$$

Integration:

$$
\int 1\,dx = x,
\qquad
\int -\cos(4x)\,dx = -\frac{1}{4}\sin(4x)
$$

also:

$$
\int_0^\pi \sin^2(2x)\,dx
=
\frac{1}{2}\left[ x - \frac{1}{4}\sin(4x) \right]_0^\pi
$$

Grenzen:

$$
\sin(4\pi) = 0, \quad \sin(0) = 0
$$

also:

$$
\int_0^\pi \sin^2(2x)\,dx = \frac{1}{2}(\pi - 0) = \frac{\pi}{2}
$$

Zurück ins Hauptintegral:

$$
\int_0^\pi (\sin^4 x + \cos^4 x)\,dx
=
\pi - \frac{1}{2}\cdot \frac{\pi}{2}
=
\pi - \frac{\pi}{4}
=
\frac{3\pi}{4}
$$

**Ergebnis Teil A:**

$$
\int_0^\pi (\sin^4 x + \cos^4 x)\,dx = \frac{3\pi}{4}
$$

---

### 3. Teil B – Die Summe

$$
\sum_{k=1}^{4} \ln(k!)
$$

Ausschreiben:

$$
\sum_{k=1}^{4} \ln(k!)
=
\ln(1!) + \ln(2!) + \ln(3!) + \ln(4!)
$$

Fakultäten:

$$
1! = 1,\quad 2! = 2,\quad 3! = 6,\quad 4! = 24
$$

also:

$$
\ln(1) + \ln(2) + \ln(6) + \ln(24)
$$

Da

$$
\ln(1) = 0
$$

wird das zu:

$$
\ln(2) + \ln(6) + \ln(24)
$$

Logarithmenregel:

$$
\ln(a) + \ln(b) = \ln(a\cdot b)
$$

also:

$$
\ln(2) + \ln(6) = \ln(12)
$$
$$
\ln(12) + \ln(24) = \ln(12\cdot 24) = \ln(288)
$$

**Ergebnis Teil B:**

$$
\sum_{k=1}^{4} \ln(k!) = \ln(288)
$$

---

### 4. Teil C – Das Produkt

$$
\prod_{n=1}^{3} \left( n + \frac{1}{n} \right)
$$

Ausschreiben:

$$
\prod_{n=1}^{3} \left( n + \frac{1}{n} \right)
=
\left(1 + 1\right)\left(2 + \frac{1}{2}\right)\left(3 + \frac{1}{3}\right)
$$

Einsetzen:

$$
1 + 1 = 2
$$
$$
2 + \frac{1}{2} = \frac{5}{2}
$$
$$
3 + \frac{1}{3} = \frac{10}{3}
$$

Also:

$$
2 \cdot \frac{5}{2} \cdot \frac{10}{3}
$$

Zuerst:

$$
2 \cdot \frac{5}{2} = 5
$$

Dann:

$$
5 \cdot \frac{10}{3} = \frac{50}{3}
$$

**Ergebnis Teil C:**

$$
\prod_{n=1}^{3} \left( n + \frac{1}{n} \right) = \frac{50}{3}
$$

---

### 5. Teil D – Die Kubikwurzel

$$
\sqrt[3]{(e^{i\pi}+1)^2 + 8}
$$

Euler:

$$
e^{i\pi} = -1
$$

Also:

$$
e^{i\pi} + 1 = -1 + 1 = 0
$$

Dann:

$$
(e^{i\pi}+1)^2 + 8 = 0^2 + 8 = 8
$$
$$
\sqrt[3]{8} = 2
$$

**Ergebnis Teil D:**

$$
\sqrt[3]{(e^{i\pi}+1)^2 + 8} = 2
$$

---

### 6. Teil E – Der Zähler komplett

Zähler:

$$
\frac{3\pi}{4} + \ln(288) - \frac{50}{3} + 2
$$

Das ist genau das, was wir aus A, B, C, D zusammengesetzt haben.

---

### 7. Teil F – Der Nenner

Nenner:

$$
\Gamma\!\left(\tfrac{5}{2}\right) + \zeta(2)
$$

#### Gammafunktion

Rekursionsformel:

$$
\Gamma(x+1) = x\,\Gamma(x)
$$

Bekannt:

$$
\Gamma\!\left(\tfrac{1}{2}\right) = \sqrt{\pi}
$$

Dann:

$$
\Gamma\!\left(\tfrac{3}{2}\right)
= \tfrac{1}{2}\,\Gamma\!\left(\tfrac{1}{2}\right)
= \tfrac{1}{2}\sqrt{\pi}
$$
$$
\Gamma\!\left(\tfrac{5}{2}\right)
= \tfrac{3}{2}\,\Gamma\!\left(\tfrac{3}{2}\right)
= \tfrac{3}{2}\cdot \tfrac{1}{2}\sqrt{\pi}
= \tfrac{3}{4}\sqrt{\pi}
$$

#### Zetafunktion

$$
\zeta(2) = \sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
$$

Also:

$$
\Gamma\!\left(\tfrac{5}{2}\right) + \zeta(2)
=
\frac{3}{4}\sqrt{\pi} + \frac{\pi^2}{6}
$$

---

### 8. Endform der gesamten Rechnung


$$
\frac{
\frac{3\pi}{4} + \ln(288) - \frac{50}{3} + 2
}{
\frac{3}{4}\sqrt{\pi} + \frac{\pi^2}{6}
}
$$
