Date: 2026-01-31
Tags: {
#W
}

Diese Formelsammlung basiert auf dem Thema [[Kreisbewegungen]]
### Dauer

$$
T = \frac{t}{n} = \frac{\text{dazu benötigte Zeit}}{\text{Anzahl der Umläufe}}
$$
$$
T = \frac{1}{f} \quad f = \frac{1}{T}
$$
$$
f = \frac{U}{t} =\frac{\text{Umdrehungen}}{\text{dazu benötigte Zeit}}
$$

### Winkelgeschwindigkeit

$$
\omega  = \frac{\Delta \varphi}{\Delta t} = \frac{\text{Winkeländerung}}{\text{Zeitintervall}} 
$$
$$
\omega  = \frac{360^{\circ}}{T} = \frac{2\pi}{T} = \frac{2\pi}{\frac{1}{f}} = 2\pi \cdot f
$$
$$\omega_{1}= \frac{20}{10s} = 2s^{-1} = 2 \cdot \frac{1}{s}$$
$$
\omega_{2}=\frac{2\pi \cdot U}{60} \qquad | \quad \text{Bei U Umdrehungen pro Minute}
$$
$$
\omega = \frac{v}{r}
$$
### Bahngeschwindigkeit
$$
v = \frac{s}{t} = \frac{2\pi \cdot r}{T} = 2\pi \cdot r \cdot f 
$$
$$
v = \frac{s}{t} \qquad | \quad s = r \cdot \varphi 
$$
$$
v = \frac{r \cdot \varphi}{t} \qquad | \quad\omega = \frac{\varphi}{t}
$$
$$
v = r \cdot \omega 
$$
$$
v_{1}= \frac{2 \pi \cdot 5m}{10s} = \pi \frac{m}{s}
$$

Aufpassen ob man den Winkel (DEG) in Grad oder Bogenmaß (RAD) berechnet

$$
360^{\circ} = 2\pi
$$
$$
90^{\circ} = \frac{\pi}{2}

$$
### Zentripetalkraft

$$
F_{z} = \frac{m \cdot v^2}{r}\quad\text{mit}\quad v=\omega \cdot r
$$
$$
F_{z} = \frac{m \cdot (\omega \cdot r)^2}{r}=m\cdot \omega ^2\cdot r
$$
$$
F_{z}=m\cdot a_{z}
$$
#### Edge cases

###### v mit m, r, F

$$
F_{z}=\frac{m\cdot v^2}{r}\quad|\cdot r\quad|:m\quad|\sqrt{-}
$$
$$
v=\sqrt{ F_{z}\cdot \frac{r}{m} }
$$
###### U mit F, r, m

$$
F_{z}=m\cdot \omega^2\cdot r
$$
$$
F_{z}=m\cdot(\frac{2\pi \cdot U}{60})^2\cdot r\quad|:(r\cdot m)
$$
$$
\frac{F_{z}}{r\cdot m}=(\frac{2\pi \cdot U}{60})^2\quad|\sqrt{ - }
$$
$$
\sqrt{ \frac{F_{z}}{r\cdot m} }=\frac{2\pi \cdot U}{60}\quad|\cdot 60\quad|:2\pi
$$
$$
\frac{60}{2\pi}\cdot\sqrt{ \frac{F_{z}}{r\cdot m} }=U
$$
### Zentripetalbeschleunigung

$$
a_{z}=\frac{v^2}{r}=\frac{(w\cdot r)^2}{r}=\omega^2\cdot r
$$


# References