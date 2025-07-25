# Dokumentation Ablauf Projektarbeit
*Datum:* _Stand: 01. Juni 2025_  
*Autor:* Erik Ziechmann

## Erste Einrichtung MRT
_nur einmal am Anfang_

1. Geräte Manager COM Port herausfinden
2. PuTTy mit der COM Adresse (hier COM5) öffnen
3. IP addr show eingeben
4. Inet Adresse beschreibt Adresse von Board

Wenn die Adresse in Internet aufgerufen wird, gibt es ein bearbeitungsmenü in dem auch feste IPs zugewiesen werden können

1. In marcos_client/ local_config.py.example (example löschen danach -> nur noch local_config.py)
2. IP hier anpassen in die herausgefundene (172.16.8.107)
3. fpa_clk_freq_MHz 125 auskommentieren und 122.88 reinschreiben
4. grad_board muss ocra1 sein
5. In marcos_experiments/ mri_config.py.examles (examle löschen -> nur noch mri_config.py)
6. grad_max_Hz_per_m muss nur = 10.9e6 sein, andere auskommentieren
7. In marcos_experiments/ external.py.examples (example löschen -> nur noch external.py)
8. flocra_pulseq muss aus git gezogen werden (https://github.com/catkira/flocra-pulseq.git). Hier pulseq_1.4


## Ablauf Einrichtung MRT
_jedes mal vor Nutzung des MRTs_

1. Terminal aufrufen
2. Ubuntu auswählen (oben)
3. Folgende Befehle ausführen  
- cd git
- cd marcos_pack/ (https://github.com/catkira/marcos_pack.git)
- cd marcos_extras/ (https://github.com/vnegnev/marcos_extras.git)
- ./marcos_setup.sh 172.16.8.107 rp-122 (alt: 172.16.8.254)
- angezeigten Befehl kopieren und ausführen
4. VS Code öffnen und nun ist es möglich Code auszuführen
5. (eventuell Befehle danach: cd git, git remote)

**Wichtig:** beim ersten einrichten und ertem zugriff auf Konsole ssh-copy-ip root@172.16.8.107 (passwort ist root)

## Einrichtung des Codes

1. Visual Studio Code öffnen
2. Marcos Client öffnen (https://github.com/catkira/marcos_client.git)
4. Test loopback code öffnen -> Ergebnisse mit loop schauen (RX1 und Tx physisch verbunden)
5. Danach können Sequenzen laufen


## Wichtige Bibliotheken

numpy
matplotlib
msgpack
PyQt5
scipy
external



## Erste Einrichtung am Oszilloskop

Gradient Chanel 1 auf Oszilloskop 2
TxGate auf auf Oszilloskop 1


Mit oszilloskop richtig einstellen und loopback laufen lassen zum testen

Gespeichert in Marcos pack 



## Aufgaben für die nächste Woche

_Stand 14.05.2025_ : Einführung in Projektorientiertes Arbeiten schreiben (Aufbau seq und m file 
Und Grundlagen echo Sequenzen. Lernen selbst Sequenzen zu erstellen und sich anzuschauen und verstehen was das bedeutet. Schonmal dem Ablauf und das Erstellen von seq Dateien anschauen und auf eigenem Rechner importieren und implementieren. Gradient spoiling ignorieren 
(Schonmal lesen). ) 

_Stand 22.05.2025_ : Warnings herausfinden und beheben   

_Stand 18.07.2025_ : C3, c9, c34, c17 müssen größer werden auf PCB Board für Tx, Coil, Rx


## Spule physisch auf Frequenz des MRTs einstellen

50 Ohm Lamourfrequenz ist das Ziel
Mit dem Gaußmeter Feldstärke messer wird die Feldstärke des MRTs gemessen

Jetzt soll eine kleine Spule auf die gleiche Stärke gebracht werden

Spektrum analysator wird zur kleinen Spulen einstellung genutzt
Dafür verschiedene Kondensatoren mit verschiedenen Größen auf den Aufbau der kleinen Spule gelötet um einen bestimmten MHz Wert zu erhalten:

https://de.wikipedia.org/wiki/Gyromagnetisches_Verh%C3%A4ltnis
42,577
42,577   ×   0,04639 = 1,97514 MHz

Dahin muss die Resonanz auf einem smith chart geschoben werden mit dem Kapazitäten
Die kapazitäten anpassen damit und austauschen damit der smithchart auf 1 kommt und die spule an die resonanzfrequenz angepasst wird.

Die Kondensator regler haben dabei einen Wert von 6-110 pF

Einzelne 1x 47
1x 22 + 101


weitere schaltung: 
transmit receive switch

s21 richtung stellt richtung von port dar



C3, c9, c34, c17 müssen größer werden

lambda/4 Spule 
3.9 uH 
1.6 nF
