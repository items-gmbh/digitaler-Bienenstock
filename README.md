# Der digitale Bienenstock mit LoRaWAN - zwei Bauvarianten <br><br> ![Logo items GmbH](https://itemsnet.de/wp-content/uploads/2019/11/itemsLogo.png)
Dieses Github-Repository erklärt den Aufbau von zwei verschiedenen digitalen Bienenstocken auf der Basis von LoRaWAN.<br>
Zu diesem Projekt gibt es folgenden Blogbeitrag der items Gmbh zum nachlesen:<br>
https://itemsnet.de/itemsblogging/der-digitale-bienenstock/ <br>

- [Waagenbau](#waagenbau)<br>
- [Variante 1: LoRa - Nodes](#variante-1-lora---nodes)<br>
  - [Verwendete Sensoren](#verwendete-sensoren)<br>
  - [Dragino LSN50 v2](#dragino-lsn50-v2)<br>
  - [Bedienungsanleitung Dragino LSN50 v2](#bedienungsanleitung)<br>
  - [Benötigtest Material](#benötigtes-material)<br>
  - [Anpassung des Source-Codes](#anpassung-des-source-codes)<br>
  - [Pin-Belegung](#pin-belegung)<br>
  - [Positionierung der Sensoren](#positionierung-der-sensoren)<br>
- [Variante 2: Selbstbau - Variante](#variante-2-selbstbau---variante)
  - [Software](#software)<br>
  - [Materialliste](#materialliste)<br>
  - [Aufbau der Sensoren](#aufbau-der-sensoren)<br>
  - [Platzierung der Sensoren](#platzierung-der-sensoren)<br> 

## Waagenbau
Beide Varianten benötigen eine Waage, mit der die Gewichtsmessung des Bienenstocks durchgeführt wird.
Hiverize.org stellt eine Anleitung für eine mögliche Waage zur Verfügung.
Diese ist zu finden unter:
https://hiverize.org/eine-stockwaage-bauen/

![Waage](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Waage.jpg)

## Variante 1: LoRa - Nodes

### Verwendete Sensoren:
* Dragino LSN50 v2
* Dragino LHT65
* Bosche H40a Wägezelle

### Dragino LSN50 v2:
Für die Gewichtsmessung und eine zusätzliche Temperaturmessung wird der LSN50 v2 verwendet.
#### Bedienungsanleitung:
https://www.dragino.com/downloads/downloads/LSN50-LoRaST/LSN50_LoRa_Sensor_Node_UserManual_v1.7.3.pdf

#### Benötigtes Material:
* LSN50 v2
* HX711
* Bosche H40a 
* DS18B20 Temperaturfühler
* Rahmenmaterial für die Waage
* wasserdichte Kabeldurchführung

#### Anpassung des Source-Codes
Zu Beachten ist, dass füpr eine erfolgreiche Gewichtsmessung der ursprüngliche Code des LSN50 v2 angepasst werden muss.
Die Gewichtsmessung ist dort auf 5 kg beschränkt.

![weight.c Code](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/weight_code.png)

Der veränderte Source-Code wird in diesem Repository zur Verfügung gestellt (EU868.hex).
Das Dragino-Wiki erläutert, wie der LSN50 v2 mit neuer Firmware bespielt werden kann: <br>
https://wiki.dragino.com/index.php?title=Firmware_Upgrade_Trouble_Shooting

#### Pin-Belegung
In diesem Projekt wird der Modus 5 des LSN50v2 benötigt.<br>
Dieser Modus ermöglicht eine Gewichtsmessung und zusätzlich noch eine Temperaturmessung.<br>
Die Pin-Belegung für den LSN50 v2 und den verwendeten Sensoren ist in den folgenden zwei Tabellen abgebildet.<br>
LSN50 v2 | HX711      
---------|------------
+5 V|VCC
GND|GND
PA11|SCK
PB12|DT

LSN50 v2 | DS18B20
---------|---------
VCC      | VCC
GND      | GND
PB3      | DT

Die nächste Abbildung zeigt, wie die Wägezelle an dem HX711 angeschlossen werden muss.

![HX711-Pinout](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Load_Cell_Pinout.png)
<br>Bildquelle: https://circuits4you.com/2016/11/25/hx711-arduino-load-cell/ <br>

Zu beachten ist, dass in diesem Projekt ein HX711 von Sparkfun getestet wurde.
Dieser ADC hat in diesem Aufbau nicht funktioniert. Aus diesem Grund wurde auf eine billigere Version gewechselt.
Mit der günstigeren Variante gab es keine weiteren Probleme mehr.

#### Positionierung der Sensoren
Der Dragino LHT65-Sensor wurde in diesem Beispiel auf den Rähmchen des Honigraums platziert.<br>
Zu beachten ist, dass aufgrund der Dicke des Sensors eine leere Zarge aufgesetzt wurde.<br><br>
![LHT65 Platzierung](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/LHT65.jpg)

## Variante 2: Selbstbau - Variante
Die Selbstbau-Variante basiert auf dem Heltec CubeCell.<br>
Dieses Entwicklerboard unterstützt LoRaWAN und hat zusätzlich noch eine Solar-Management-System eingebaut. <br>
### Software
Die Software für diese Variante des digitalen Bienenstöcks basiert auf dem GitHub Projekt von Jörg Keller: <br>
https://github.com/joergkeller/beehive-sensor <br><br>

In diesem Projekt ist auch eine Excel-Datei beigefügt, die für die Kalibrierung der Waage notwendig ist.
Außerdem werden dort die wesentlichen Verkabelungen für das Heltec CubeCell aufgeführt.

### Materialliste
Die folgende Tabelle listet die Materialien, die in diesem Projekt verwendet wurden.

Produkt         | Anzahl
----------------|-------
Heltec CubeCell | 1
Bosche Wägezelle H40a | 1
HX711 | 1
DHT22 AM2302 | 1
DS18B20 | 5
18650 Li-Ion Akku | 1
Solarzelle | 1
18650 Halterung | 1
JST 1,25 Stecker | 1
Rahmenmaterial Waage | 1
Elektronik Gehäuse | 1
Kabelverschraubung | 1
Flachbandkabel | 1
4-Poliges Kabel | 1
Steckplatine | 1
6-Polige Pfostenbuchse | 15
LED | 1
Drahtbrücken |
Lötzinn|
Widerstand 4,7 kΩ | 1
Widerstand 10 kΩ | 1

### Aufbau der Sensoren
Der Aufbau der Sensoren stammt aus einer Anleitung von Hiverize.org: <br>
https://hiverize.org/einbautemperatursensor/ <br>
Zusätzlich zu den Temperatursensoren wurde am Ende des Flachbandkabels noch der DHT22/AM2302 Temperatur- und Luftfeuchtigkeitssensor angebracht.<br><br>

![Temperatursensoren](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Eigenbau3.jpg)<br>


### Platzierung der Sensoren
Im folgenden Bild ist erkenntlich, wie die Temperatursensoren in dem Bienenstock platziert wurden.<br>

![Platzierung der Sensoren](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Eigenbau1.jpg) <br>

Das folgende Bild zeigt die Verkabelung am Heltec CubeCell. <br>
Das Steckboard im rechten, oberen Eck stellt das Flachbandkabel mit den Temperatursensoren dar. <br><br>

![Fritzing](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Fritzing.png) <br>

Bei Fragen gerne eine Mail an: <br>
l.weber@itemsnet.de
