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

Den Tensor $z_i$ wird über den $i$-ten Convolutional-Block des Residualen-Netzwerkes berechnet. Der Output des $i$-ten Blockes entspricht demnach

$z_i = z_{i-1} + F(z_{i-1};\theta _i)$

wobei 

- $F(;\theta _i)$ die Komposition von 2 Convolutions, mit den Gewichten $\theta _i$ und Aktivierungsfunktionen, implementiert.

## R2D: 2D Convolutions über Ausschnitt

Da bei 2D CNN's für Videos die temporale Anordnung der Frames nicht beachtet wird, werden diese wie Kanäle behandelt.
Der 4D Input-Tensor entspricht demnach einem 3D Input-Tensor.
Der Output $z_i$ des $i$-ten Blockes ist auch ein 3D Tensor. Dessen Größe ist

$N_i \times H_i \times W_i$

wobei

- $N_i$ der Anzahl der im verwendeten Convolution-Filter im $i$-ten Block entspricht und
- $H_i$ und $W_i$ die spatial Dimensionen, die durch Pooling oder Striding abnehmen können, sind.

Jeder Filter ist 3D und mit der Größe

$N_{i-1} \times d \times d$

wobei

- $d$ für die räumliche Breite und Höhe steht.

```{note}
Die Convolution der 3D Filter sind nur über die räumlichen Dimensionen (und dementsprechend 2D) des vorhergehenden Tensors $z_{i-1}$. Jeder Filter hat nur einen Kanal als Output, wodurch bereits nach der ersten Convolution-Schicht temporale Schlüsse nicht mehr nachzuvollziehen sind. Entsprechend ist in diesem Netz kein temporales Striding erforderlich.
```

## F-R2D: 2D Convolutions über Frames

## R3D: 3D Convolutions