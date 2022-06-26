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

Wir nehmen, um die Modelle zu trainieren, $L$ konsekutive Bilder eines Videos. Im Rahmen dieser Arbeit experimentieren wir dafür mit 8 und 16 Frame-Clips ($L$ = 8 oder $L$ = 16).

Batch-Normalization wird in allen Schichten verwendet.
Wir verwenden eine Batch-Größe von 32 Clips pro GPU.
Wir teilen die Lernrate, die initial 0.01 ist, alle 10 Epochen durch 10.
Der Trainings-Prozess umfasst 45 Epochen.

Wir erhalten die Clip-Top-1-Accuracy und Video-Top-1-Accuracy.
Für die Video-Top-1-Accuracy werden die mittleren Ausschnitte von 10 Clips, die aus einem Video entnommen werden, verwendet. Der Durchschnitt dieser 10 Clip-Vorhersagen entspricht dann der Video-Prediction.
