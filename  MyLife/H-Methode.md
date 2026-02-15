---
id: "H-Methode"
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
Source:
---
## Herleitung der H‑Methode (Differentialrechnung)

Die H‑Methode ist die klassische Herleitung der **Ableitung** über den **Differenzenquotienten**.


### Ziel

Wir wollen die **Steigung der Tangente** an einer Funktion f(x) im Punkt $x_0$ bestimmen.

Diese Steigung nennen wir:

$$ f^\prime(x_0) $$



# **Idee: Steigung über zwei Punkte**

Die Steigung einer Geraden zwischen zwei Punkten $(x_0, f(x_0))$ und $(x_0 + h, f(x_0 + h))$ ist:

$$ m(h) = \frac{f(x_0 + h) - f(x_0)}{h} $$

Das ist die **Sekantensteigung**.
Höhenänderung durch Breitenänderung



# **3. Problem: Die Tangente ist ein Grenzfall**

Die Tangente entsteht, wenn der zweite Punkt **immer näher an den ersten rückt**.

Das heißt: $( h \to 0 )$



# **4. Definition der Ableitung (H‑Methode)**

Die Steigung der Tangente ist der Grenzwert der Sekantensteigung:

$$ f^\prime(x_0) = \lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h} $$

Das ist die **H‑Methode**.

---

# **5. Warum funktioniert das?**

- Für **h ≠ 0** ist die Formel eine normale Steigung zweier Punkte.
- Wenn **h → 0**, rückt der zweite Punkt unendlich nah an x_0.
- Die Sekante wird zur **Tangente**.
- Der Grenzwert ist die **exakte momentane Steigung**.

---

# **6. Beispiel: `\(⁠f(x) = x^2\)`**

Wir setzen ein:

[ f^\prime(x_0) = \lim_{h \to 0} \frac{(x_0 + h)^2 - x_0^2}{h} ]

Ausmultiplizieren:

[ (x_0 + h)^2 = x_0^2 + 2x_0 h + h^2 ]

Einsetzen:

[ \frac{x_0^2 + 2x_0 h + h^2 - x_0^2}{h} ]

Kürzen:

[ = \frac{2x_0 h + h^2}{h} ]

[ = 2x_0 + h ]

Grenzwert:

[ \lim_{h \to 0} (2x_0 + h) = 2x_0 ]

Damit:

[ f^\prime(x) = 2x ]

---

# **7. Zusammenfassung**

|**Schritt**|**Bedeutung**|
|---|---|
|1|Zwei Punkte wählen: ￼ und ￼|
|2|Sekantensteigung bilden|
|3|Grenzwert für ￼ nehmen|
|4|Ergebnis ist die Ableitung = Tangentensteigung|

---

Wenn du willst, rechne ich dir:

- ein **weiteres Beispiel** durch
- die **H‑Methode für eine konkrete Funktion**
- die **Herleitung der Ableitungsregeln** aus der H‑Methode
- oder ich formuliere dir eine **kompakte Version für Obsidian**

Sag einfach Bescheid, wohin du weiter willst.