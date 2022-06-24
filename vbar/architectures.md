# Architekturen

```{note}
Die in diesem Abschnitt betrachteten spatio-temporal Convolutional-Varianten sind alle im Rahmen des Residualen-Lernens zu betrachten.
Des Weiteren werden nur "Vanilla-Blocks" (bsp. ohne Bottlenecks) verwendet. Ein Block besteht dabei aus 2 Convolutional-Schichten oder -Layer, sowie einer Aktivierungsfunktion nach den Beiden.
Für die Klassifizierung ist ein fully-connected Layer verantwortlich.
```
## Variablen

Unseren Input-Tensor

$x = 3 \times L \times H \times W$

wobei 

- $L$ der Anzahl der Frames des Ausschnittes entspricht,
- $H$ und $W$ für die Höhe und Breite eines Frames stehen und
- $3$ für die Farbkanälen steht.

Den Tensor $z_i$ wird über den i-ten Convolutional-Block des Residualen-Netzwerkes berechnet. Der Output des i-ten Blockes entspricht demnach

$z_i = z_{i-1} + F(z_{i-1};\theta _i)$

wobei 

- $F(;\theta _i)$ die Komposition von 2 Convolutions, mit den Gewichten $\theta _i$ und Aktivierungsfunktionen, implementiert.

## R2D: 2D Convolutions über Ausschnitt

## F-R2D: 2D Convolutions über Frames

## R3D: 3D Convolutions