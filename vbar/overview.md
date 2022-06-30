# Überblick

```{note}
Die Inhalte basieren auf/ entsprechen den Erkenntnissen dieses [Papers](https://arxiv.org/abs/1711.11248).
```

![Intro  Video](img/intro.gif)
<!-- https://raw.githubusercontent.com/open-mmlab/mmaction2/master/resources/mmaction2_overview.gif -->
 
Die Motivation der Arbeit, sich mit der Handlungserkennung von Videoinhalten zu befassen, beruht darauf, dass mittels 2D CNN's in diesem Bereich bereits *ordentliche* Fortschritte erzielt werden konnten (bspw. mittels der einzelnen Frames von Videos).

Mittels 3D CNN's soll dies im Rahmen des Residual-Lernens weiter verbessert werden. Hierfür sollen 3D Convolutional-Filter in Raum- und Zeit-Komponenten unterteilt werden.
Auf eine Diskussion der verschiedenen Formen dieses Auftrennens, folgen entsprechende Erkenntnisse zur Handlungserkennung für Videos.

Die Studie schließt mit dem Entwurf einer Architektur ab, mittels welcher Handlungen aus Videos mit einer mindestens genauso, oder höheren Accuracy, als bisher (sprich: state of the art) erkannt werden können.