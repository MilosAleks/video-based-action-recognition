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
Der Input der Netze sind Clips, bestehend aus $L$ RGB-Frames mit einer Größe von 112 x 112.