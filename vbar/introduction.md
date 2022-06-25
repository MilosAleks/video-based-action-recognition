# Introduction

Hier Einleitungstext und Grundlagen (eventuell neues Kapitel ??) ...

<<<<<<< HEAD
[Sports-1M Datensatz](https://paperswithcode.com/dataset/sports-1m)

Der Begriff der Aktion (ff., eng. Action) folgt keiner universelle Terminologie aber kann angenähert werden nach Lan et. al als eine "einfache, atomare Bewegung, die von einer einzelnen Person ausgeführt wird." Konsequent führt dies zur nächsten Frage, nämlich was ist denn eine bzw. welche Aktionen fallen den unter der Definition von Lan et. al? 


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

- $x$, $y$ den spatialen Koordinaten eines Signals entspricht.

Formell ist ein Video ein 3D-Signal $V$ bestehend aus spatialen (räumlichen) und temporalen (zeitlichen) Kompontenten:

$V =  x \times y \times t$

wobei

- $x$, $y$ den spatialen Koordinaten eines Signals entspricht,
- $t$ die temporale Koordinate eines Signals entspricht.

Je nachdem ob $t$ präsent ist, ist das Signal ein Video oder ein Image. Somit können wir Videos als eine zeitlich aufeinanderfolgende Reihe von Images verstehen. 


=======
Die Definition einer Aktion (eng./ff. Action) nach Lan et. al ist als eine einfache, atomare Bewegung, die von einer einzelnen Person ausgeführt wird. Darauffolgenden ist eine Aktivität (eng. Activity) die sich auf ein komplexeres Szenario bezieht, an dem eine Gruppe von Menschen beteiligt ist
>>>>>>> 08bf9fda89bf8d3e0e6ea4f149de5c24a3532e2a

![AlexNet](img/AlexNetArchitecture.png){cite}'NIPS2012_c399862d'

Mit der Einführung des AlexNet, einer CNN-Architektur hat der Bereich der Standbilderkennung große Fortschritte gemacht hat.
Im Vergleich dazu, gibt es zurzeit bemerkenswert signifikanten Funde im Bereich der videobasierten Erkennung. 

## Herausforderungen von Action Recognition

Videoverständnis ist eines der zentralen Probleme im Bereich von Computer Vision der letzten Jahrzehnte 

the main challenge of recognizing actions across video frames is the caputure of spatio-temporal context 

## Qou Vadis, Action Recognition? 

## Spatial - Temporale Kohärenz
"Die langsame Merkmalsanalyse und verwandte Algorithmen gehen von der Annahme aus, dass sich die wichtigsten erklärenden Faktoren im Laufe der Zeit langsam ändern oder dass es zumindest einfacher ist, die wahren, zugrunde liegenden erklärenden Faktoren vorherzusagen als Rohbeobachtungen wie Pixelwerte." {cite}'GoodBengCour16'


 Um den Inhalt eines Videos effektiv beschreiben zu können, müssen die Objekte und Ereignisse in den Bildsequenzen, aus denen das Video besteht, erkannt werden. Modernste Computer-Vision-Tools bieten die Möglichkeit, Objekte und ihre Eigenschaften in Bildern zu erkennen und zu identifizieren [59, 60]. Die robuste und genaue Erkennung von Ereignissen, die in Bildsequenzen auftreten, ist jedoch nach wie vor ein Problem. Dies ist nicht überraschend, da die kognitiven Grundlagen für das Verständnis von Ereignissen viel komplizierter sind. Es erfordert die Anwendung komplexer raum-zeitlicher Konzepte.

Die Zerlegung eines Videos ergibt folgende Teile
    Spatial Komponent
    Temporaler Komponent

