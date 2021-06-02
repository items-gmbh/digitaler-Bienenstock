# Der digitale Bienenstock mit LoRaWAN - zwei Bauvarianten

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
Das Dragino-Wiki erläutert, wie der LSN50 v2 mit neuer Firmware bespielt werden kann:
https://wiki.dragino.com/index.php?title=Firmware_Upgrade_Trouble_Shooting

#### Pin-Belegung
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

![HX711-Pinout](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/Load_Cell_Pinout.png)
<br>Bildquelle: https://circuits4you.com/2016/11/25/hx711-arduino-load-cell/

#### Positionierung der Sensoren
Der Dragino LHT65-Sensor wurde in diesem Beispiel auf den Rähmchen des Honigraums platziert.<br>
Zu beachten ist, dass aufgrund der Dicke des Sensors eine leere Zarge aufgesetzt wurde.<br><br>
![LHT65 Platzierung](https://github.com/items-gmbh/digitaler-Bienenstock/blob/main/Abbildungen/LHT65.jpg)


#### Bedienungsanleitung:
https://www.dragino.com/downloads/downloads/LSN50-LoRaST/LSN50_LoRa_Sensor_Node_UserManual_v1.7.3.pdf

## Variante 2: Selbstbau - Variante
### Materialliste

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
Widerstasnd 4,7 kΩ | 1
