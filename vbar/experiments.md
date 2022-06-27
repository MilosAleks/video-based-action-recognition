# Experimente

```{note}
Die Datensets, auf welchen die verschiedenen Architekturen trainiert werden, entsprechen [Kinetics](https://www.deepmind.com/open-source/kinetics) und [Sports-1M](https://cs.stanford.edu/people/karpathy/deepvideo/). Diese umfassen eine ausreichende Größe, sodass auch tiefe Modelle von Grund auf trainiert werden können.
Da ein *gutes* Video-Modell auch effektives Transfer-Lernen (auf andere Datensets) unterstützen sollte, ziehen wir die Datensets [UCF101](https://www.crcv.ucf.edu/research/data-sets/ucf101/) und [HMDB51](https://serre-lab.clps.brown.edu/resource/hmdb-a-large-human-motion-database/) dazu, auf die Modelle entsprechend fine-tuned werden sollen.
```

## Setup

### Netzwerk Architektur

Die Experimente werden auf Deep-Residual-Netze, durch deren Einfachheit und Leistungspotential, beschränkt.
Es existieren 2 R3D Architekturen (3D ResNet) für das Experiment. 
Die erste Architektur umfasst 18, und die Zweite 34 Schichten.

Der Input der Netze bestehen aus RGB-Frames mit einer Größe von 112 x 112.
Downsampling wird in der ersten Schicht, in Form von Striding von $1 \times 2 \times 2$ (spatial) und in den Schichten 3, 4 und 5 $2 \times 2 \times 2$ (spatio-temporal) verwendet.

Von den beschriebenen R3D Modellen leiten wir die Architekturen für R2D, MC$x$, RMC$x$ und R(2+1)D ab, indem die 3D Convolutionen entsprechend mit 2D, Mixed-Convolutions, Reversed-Mixed-Convolutions und R(2+1)D Convolutions ersetzt werden.

In den Architekturen, in welchen 3D durch 2D Convolutions ersetzten werden (z.B in RMC$x$), wird das 3D Downsampling (spatio-temporal) entsprechend nur noch 2D (spatial). 
Dieser Unterschied führt zu Aktivierung-Tensoren unterschiedlicher Größe (temporal) in der finalen Schicht, bis zu welcher unabh. davon in allen Netzwerken ein spatio-temporales Average-Pooling implementiert wird.
Die Klassifizierung erfolgt dann mittels einem fully-connected Layer, dessen Dimension der Anzahl der Klassen entspricht (z.B 400 für Kinetik).

### Training und Evaluation

Für einen ersten Versuch verwenden wir Kinetics. 
Hierfür teilen wir das Set entsprechend für das Training und die Validierung.
Um die Netze fair bewerten zu können, erhalten diese alle 18 Schichten und werden von Grund auf, mit dem selben Input, trainiert.

Das der Input, sprich die Frames der Videos, die erwünschte Größe erreichen, werden diese erst entsprechend auf eine Größe von $128 \times 171$ verkleinert. Hiernach schneiden wir die Frames, per Zufall, auf die Input-Größe von $112 \times 112$ zu.

Wir nehmen, um die Modelle zu trainieren, $L$ konsekutive Bilder eines Videos. Im Rahmen dieser Arbeit experimentieren wir dafür mit 8 und 16 Frame Clips ($L$ = 8 oder $L$ = 16).

Batch-Normalization wird in allen Schichten verwendet.
Wir verwenden eine Batch-Größe von 32 Clips pro GPU.
Wir teilen die Lernrate, die initial 0.01 ist, alle 10 Epochen durch 10.
Der Trainings-Prozess umfasst 45 Epochen.

Wir erhalten die Clip-Top-1-Accuracy und Video-Top-1-Accuracy.
Für die Video-Top-1-Accuracy werden die mittleren Ausschnitte von 10 Clips, die aus einem Video entnommen werden, verwendet. Der Durchschnitt dieser 10 Clip-Vorhersagen entspricht dann der Video-Prediction.

```{note}
Top-1-Accuracy ist die konventionelle Accuracy/ Genauigkeit, sprich die Modellantwort (mit der höchsten Wahrscheinlichkeit) muss die erwartete Antwort sein.
```

### Vergleich der spatio-temporal Convolutions

*Die in diesem Abschnitt verwendeten Zahlen und Erkenntnisse sind der anschließenden Tabelle entnommen.*

Es besteht ein deutlicher Unterschied in der Performance der 2D (R2D und F-R2D) und 3D oder vermischten Residual Netzen (MC$x$ und R-MC$x$). Die 2D Architekturen schneiden im Schnitt bis zu 4% bei 8-Frame Clips und bis zu 6.5%, wenn die Modelle mit 16 Frame-Clips als Input trainiert wurden, schlechter ab. 
Hieraus schließen wir, dass das Modellieren von Bewegungen, von Bedeutung ist (wie in MC$x$ beschrieben).

Der Unterschied besteht darin, dass im Vergleich zu den 3D oder MC$x$ Modellen, welche die temporalen Informationen beibehalten, R2D diese Informationen innerhalb des ersten Blockes komprimiert (und entsprechend eliminiert), während F-R2D Bildmerkmale direkt aus Einzelbildern berechnet.

```{note}
Alle Modelle/ Architekturen (innerhalb derselben Einstellung) bekommen den identischen Input und verarbeiten entsprechend alle Bilder eines Clips (8 oder 16).
```

Inmitten der 3D Architekturen, erzielte R(2+1)D die beste Accuracy. So schnitt diese bei 8-Frame Clips um 2 - 3.5% besser, und bei 16-Frame Clips um bis zu 4.75% besser als R3D, MC$x$ oder R-MC$x$ ab.
Demnach ist das Auftrennen der Convolutions in Raum- und Zeit-Komponenten besser als das direkte Modellieren beider Komponenten oder das Vermischen der Architekturen (3D und 2D).
Zudem übertrifft R(2+1)D auch die 2D Architekturen (R2D und F-R2D) um 5-6% in der 8-Frame-, und um 6-10% in der 16-Frame-Einstellung.

Die nächste Abbildung stellt für die verschiedenen Formen von Convolutionen die Video-Top-1-Accuracy im Vergleich zu deren Berechnungskomplexität (FLOPs) dar:

![Accuracy für Handlungserkennung für verschiedene Formen von Convolutions mit deren Berechnungskomplexität](img/acc_flop.png)

Die linke Seite des Schaubildes (a) beinhaltet die Modelle, die mt 8-Frame-Clips trainiert wurden. Rechts (b) sind die Modelle für die entsprechenden 16-Frame-Clips ersichtlich.
R2D ist demnach das effizienteste Netzwerk, besitzt aber auch die schlechtesten Accuracy. So ist es, indem es alle temporalen Informationen in der ersten Schicht komprimiert, 7x schneller als die andere 2D Architektur F-R2D. 
Hinsichtlich der Accuracy schneiden die beiden Architekturen fast identisch ab (8-Frames: <1%, 16-Frames 1.5%).
Da wie beschrieben, R2D alle temporalen Informationen eliminiert, schneidet es mit einer zunehmender Anzahl an Frames schwächer ab.

Interessanterweise ist R-MC3 effizienter als F-R2D (alle Bilder werden unabh. voneinander verarbeitet), da die Architektur Downsampling (Temporales-Striding) implementiert.
Dementsprechend ist R-MC2 *teurer*, da es Downsampling erst ab der 3. Schicht verwendet (R-MC3 ab der 2. Schicht).

Während R(2+1) fast die identische Anzahl an Parametern und Berechnungskomplexität wie R3D hat, erzielt die Architektur eine bessere Accuracy (3-5%).

*Why are (2+1)D convolutions better than 3D?*

...

![Accuracy für Handlungserkennung für verschiedene Formen von Convolutions auf dem Kinetics Datenset](img/comp_accuracy.png)