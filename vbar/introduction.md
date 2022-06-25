# Introduction

Hier Einleitungstext und Grundlagen (eventuell neues Kapitel ??) ...

[Sports-1M Datensatz](https://paperswithcode.com/dataset/sports-1m)

Der Begriff der Aktion (ff., eng. Action) folgt keiner universelle Terminologie aber kann angenähert werden nach Lan et. al als eine "einfache, atomare Bewegung, die von einer einzelnen Person ausgeführt wird." Konsequent führt dies zur nächsten Frage, nämlich was ist denn eine bzw. welche Aktionen fallen den unter dieser Definition



![move_and_action](img/Concept_of_moveme_and_action_hierarchy.png){cite}'ahad2011computer'


Die Aufgaben von 

## Kategorien von Action Recognition
## Anwendung von Action Recognition

## Stand der Technik von Action Recognition 

In dieser Vortrag geht es speziell um Video-Basierte Action Recognition. Doch ist es erstmals wichtig zu klären, was das Inputsignal im Deep Learning Kontext ist. 
Notwendigerweiser nehmen Images und Videos als Inputs Anwendung in dieser Domäne. Es gilt diese Begriff voneinander bedingt voneinander zu differenzieren.
Ein Image $I$ ist ein 2D-Signal bestehend aus spatialen (räumlichen) Komponenten:

$I = x \times y$ 

wobei 

- $x$, $y$ den spatialen Koordinaten eines Signals entsprechen.

Formell ist ein Video ein 3D-Signal $V$ bestehend aus spatialen (räumlichen) und temporalen (zeitlichen) Kompontenten:

$V =  x \times y \times t$

wobei

- $x$, $y$ den spatialen Koordinaten eines Signals entsprechen,
- $t$ die temporale Koordinate eines Signals entspricht.

Je nachdem ob $t$ präsent ist, ist das Signal ein Video oder ein Image. Somit können wir Videos als eine zeitlich aufeinanderfolgende Reihe von Images verstehen. Gerade für Daten mit einer gitterartigen Topologie und Raum-Zeit Beziehung wie Bilder eignen sich Convolutional Neural Networks (CNN) sehr gut als Stand der Technik. Das erste CNN wurde von Lecun et. al (1998) unter der Bezeichnung "LetNet-5" vorgestellt.

![LeNet-5](img/LeNet-5.png){cite}'lecun-gradientbased-learning-applied-1998'

Ein CNN folgt einem hierarchischen Modell, das wie ein Trichter ein Netzwerk aufbaut und schließlich eine vollständig verbundene Schicht hervorbringt, in der alle Neuronen miteinander verbunden sind und die Ausgabe verarbeitet wird.
Ein CNN besteht im Grunde genommen aus: 

- Input Layer
- Convolutional Layer
- Pooling Layer
- Fully Connected Layers 
- Output Layer



![AlexNet](img/AlexNetArchitecture.png){cite}'NIPS2012_c399862d'

Mit der Einführung des AlexNet, einer CNN-Architektur hat der Bereich der Standbilderkennung große Fortschritte gemacht hat.
Im Vergleich dazu, gibt es zurzeit bemerkenswert signifikanten Funde im Bereich der videobasierten Erkennung. 

## Herausforderungen von Action Recognition

Videoverständnis ist eines der zentralen Probleme im Bereich von Computer Vision der letzten Jahrzehnte 

the main challenge of recognizing actions across video frames is the caputure of spatio-temporal context 

## Spatial - Temporale Kohärenz
"Die langsame Merkmalsanalyse und verwandte Algorithmen gehen von der Annahme aus, dass sich die wichtigsten erklärenden Faktoren im Laufe der Zeit langsam ändern oder dass es zumindest einfacher ist, die wahren, zugrunde liegenden erklärenden Faktoren vorherzusagen als Rohbeobachtungen wie Pixelwerte." {cite}'GoodBengCour16'


 Um den Inhalt eines Videos effektiv beschreiben zu können, müssen die Objekte und Ereignisse in den Bildsequenzen, aus denen das Video besteht, erkannt werden. Modernste Computer-Vision-Tools bieten die Möglichkeit, Objekte und ihre Eigenschaften in Bildern zu erkennen und zu identifizieren [59, 60]. Die robuste und genaue Erkennung von Ereignissen, die in Bildsequenzen auftreten, ist jedoch nach wie vor ein Problem. Dies ist nicht überraschend, da die kognitiven Grundlagen für das Verständnis von Ereignissen viel komplizierter sind. Es erfordert die Anwendung komplexer raum-zeitlicher Konzepte.

