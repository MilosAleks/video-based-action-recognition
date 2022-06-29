# Einführung

## Der Begriff "Action"

Der Begriff der Aktion (ff., eng. Action) kann definiert werden nach Lan et. al {cite}'NIPS2010_2b44928a' als eine "einfache, atomare Bewegung, die von einer einzelnen Person ausgeführt wird." Hingegen sind Aktivitäten auf ein komplexeres Szenario bezogen, an dem u.a. eine Gruppe von Menschen beteiligt ist. Dies ist keine Standardterminologie und oft werden Begriffe wie Action, Activities von vielen Forschern austauschbar angewandt {cite}'MOESLUND200690'.
Ebenso gibt es keine gut-akzeptierte Nomenklatur oder Kategorisierung für Actions oder Activities.
Konsequent führt dies zur Frage, was ist denn eine bzw. welche Aktionen fallen den unter dieser Definition.

![move_and_action](img/Concept_of_moveme_and_action_hierarchy.png)
{cite}'ahad2011computer'

Basis dieser Kategorisierung ist Vecchio et al. {cite}'article2'. Es sollen (menschliche) Bewegungsabläufe - in diesem Kontext Aktivitäten in ihre Bauteile zerlegt werden. Dies ist definierte als *movemes*. Dabei handelt es sich um ein abstraktes Alphabet für recht primitive Bewegungen. So können aus einer Reihe von movemes eine Action konstruiert. In seiner Dissertation erweitert Fanti {cite}'article', interpretiert er verschiedene (menschliche) Bewegung in einer 3-stufigen Hierarchie und stellt diese wie in Abbildung 1 auf.
## Action Recognition

![computer_vision](img/Computer_Vision.png)

Die Action Recognition (dt. Handlungserkennung) ist ein Feld der Computer Vision. Es soll aus realen Bildern Semantik extrahiert werden, um Modelle generieren zu können. 
Unter Action Recognition versteht man den Versuch, festzustellen, ob die Eingabedaten ein bestimmtes Objekt, ein bestimmtes Merkmal oder eine bestimmte Aktivität enthalten oder ihnen ähneln. In der Computer Vision besteht Action Recognition darin, eine Action Recognition-Komponente aus einem Video oder einer Bildszene zu entschlüsseln. Auf Menschen bezogen, ist Action Recognition die Aufgabe zu erkennen, wann eine Person in einem Bild oder video eine bestimmte Handlung ausführt. 
Dazu gehört die Tatsache, dass Handlungen dynamisch sind und in der Regel nicht einfach durch die Betrachtung einzelner Zeitpunkte erkannt werden können. Die Erkennung von Handlungen wird außerdem durch die Unterschiede zwischen Menschen und sogar zwischen den Instanzen einer einzelnen Person erschwert. Schließlich erfordert eine erfolgreiche Handlungserkennung entweder eine explizite oder implizite Entfernung des Hintergrunds; Bewegungen im Hintergrund sind ablenkend und sollten ignoriert werden {cite}'inproceedings'. 
## Anwendungsbereiche von Action Recognition

![application_realm_ar](img/Application_realm_AR.png)

Das Verstehen von Bewegungen oder Aktivitäten aus Bildern und Videosequenzen ist eine sehr wichtige, aber schwierige Aufgabe. Das Gebiet der Handlungs- und Aktivitätsdarstellung und -erkennung ist recht gut erforscht {cite}'inproceedings2' aber noch nicht sehr ausgereift für viele Anwendungen im realen Leben. Die Erkennung der Identität von Personen sowie der Aktionen, Aktivitäten und Verhaltensweisen, die von einer oder mehreren Personen in Videosequenzen ausgeführt werden, ist für verschiedene Anwendungen sehr wichtig. Diverse Anwendungen sind bereits auf dieses Ziel ausgerichtet, um Videos richtig zu verstehen, z.B. in

- Intelligente Videoüberwachung,
- Mixed Reality
- Mensch-Computer-Interaktion,
- Gesichtsanalyse,
- Objektverfolgung,
- Sport-Analytics
- usw. 
## Ansätze von Action Recogintion 

Action Recognition ist ein Feld der Computer Vision und kann in mehrere Kategorien unterteilt werden

Es gibt verschiedene Ansätze für die Erkennung und Analyse von Handlungen und Aktivitäten.

Action Classifcation wird versucht, einem gegebenen Bild oder Video die richtige Bezeichnung (z. B. "Kochen", "Schreiben" usw.) zuzuordnen.
Action Localization wird versucht, anhand einer bestimmten Aktion und eines Videos den richtigen Ort und Zeitstempel im Video zu ermitteln, an dem die Aktion ausgeführt wird.

Pose Estimation 

Apperance-based methoeds

Motion-based methods 

Space-time methods 
