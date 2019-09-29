# EdgeTSDB_Prototype_Simulated_Sensor_Ingestion_to_InfluxDB

Dieser Prorotyp ist eine JSON-Datei für den Import in die Open-Source Entwicklungsumgebung Node-Red. Der Prototyp dient dazu, da um das Systemverhalten der Zeitreihendatenbank InfluxDB auf einem Raspberry Pi zu testen. Die Installation stellt einen Einzelknoten dar, welcher mehrfacher paralellen Schreiblast und gleichzeitigen Datenabfragen ausgesetzt ist. So wird ein industrielles Edge-Gerät zur Aufnahme von industriellen Sensordaten simuliert. Dabei wurde das Node-Red Framework verwendet, um mehrere Datenquellen mit einer InfluxDB-Datenbank zu verbinden und das Schreiben verschiedener Sensordatentypen in InfluxDB durch entsprechende Ausgabenodes zu simulieren. 

Der Zweck des Prototyps ist es eine Berwertung des Lastmanagements bei InfluxDB zu ermöglichen. Mittels InfluxDB werden 60 Datenquellen erzeugt und 60 paralelle Datenströme über den ofiziellen Konnektor in die Zeitreihendatenbank InfluxDB eingespeist.

Damit der Prototyp funktionert werden folgende Nodes vorausgesetzt, die in der Grundinstallation von Node-Red nichit enthalten sind:
- Sensehat Node
- InfluxDB Node

Die Funktionsweise des Prototyps kann wie folgt beschrieben werden: 
Es wurde eine Node-Red-Instanz mit 60 Ausgabe-Nodes erstellt, um die Anzahl der Sensoren einer modernen Werkzeugmaschine zu simulieren (Am Beispiel einer DMG Mori Maschine aus dem Jahr 2016)

Die Sensehat-Nodes wurden verwendet, um das Sensor-Erweiterungsmodul für den Raspberry Pi zu simulieren. Jeder Node kann simulierte Daten verschiedener Sensoren (z. B. Temperatur oder Beschleunigung) mit einer vorgegebenen Abtastrate erzeugen. Jeder datenerzeugende Node ist mit dem aufnehmenden InfluxDB-Node verbunden und ein simultanes Schreiben in die vorkonfigurierte InfluxDB-Datenbank wird ermöglicht.

Von den 60 Ausgabe-Nodes wurden 54 Nodes so konfiguriert, um Temperaturdaten als exemplarische Sensormessung in industriellen Prozessen zu simulieren. Fünf Nodes lieferten die Daten zur Rotationsintensität eines Werkzeugs (z. B. einer Spindel in einer Werkzeugmaschine). Zusätzlich wurde ein Node konfiguriert, um Twitter-Nachrichten zu erfassen und in InfluxDB auf dem Edge-Gerät zu schreiben. Dadurch wurden Fehlermeldungen vom Überwachungssystem einer Werkzeugmaschine simuliert (Martinviita 2018). Alle Sensordaten wurden mit einer Abtastrate von 1 Sekunde konfiguriert. Obwohl diese Abtastrate nicht als hochfrequent eingestuft werden kann, sind schnellere Abtastraten bei den verwendeten Nodes für die Simulation des Sensehataufsatzes nicht möglich.

Der Prototyp wurde auf folgendem System aufgebaut:
Raspberry Pi 3B
16GB SD-Karte
Noobs -> Raspbian OS & update
InfluxDB ARM Installation (http://blog.centurio.net/2018/10/28/howto-install-influxdb-and-grafana-on-a-raspberry-pi-3/)
Grafana ARM Installation (http://blog.centurio.net/2018/10/28/howto-install-influxdb-and-grafana-on-a-raspberry-pi-3/)
Node-Red Installation & update

--------------------------

This prorotype is a JSON file for import into the open source development environment Node-Red. The prototype is used to evaluate the system behavior of the InfluxDB time series database on a Raspberry Pi, which is exposed to multiple parallel write loads and simultaneous data queries. This is how we simulate and industrial edge device for recording industrial sensor data as a single node. The Node-Red Framework was used to connect several data sources to an InfluxDB database and to simulate the writing of different sensor data types in InfluxDB by corresponding output codes. 

The purpose of the prototype is to enable an evaluation of the load management in InfluxDB. Using InfluxDB, 60 data sources are generated and 60 parallel data streams are streamed into the InfluxDB timeseries database via the official connector.

In order for the prototype to work, the following nodes are required to be installed, as they are not contained in the typical installation of Node-Red:
- Sensehat Node
- InfluxDB Node

The functionality of the prototype can be described as follows: 
A Node Red instance with 60 output nodes was created to simulate the number of sensors of a modern machine tool (Example of a DMG Mori Machine from 2016).

The Sensehat nodes were used to simulate the sensor extension module for the Raspberry Pi. Each node can generate simulated data from different sensors (e.g. temperature or acceleration) at a given sampling rate. Each data generating node is connected to the receiving InfluxDB node and allows simultaneous writing to the preconfigured InfluxDB database.

Of the 60 output nodes, 54 were configured to simulate temperature data as exemplary sensor measurements in industrial processes(Sensehat nodes). Five Sensehat nodes provided data on the rotation intensity of a tool (e.g. a spindle in a machine tool). In addition, a node was configured to capture Twitter messages and write them to InfluxDB on the Edge device. This simulated error messages from a machine tool monitoring system. All sensor data was configured with a sampling rate of 1 second. Although this sampling rate cannot be classified as high frequency, faster sampling rates are not possible with the simulated Sensehat nodes which were used.


The prototype was built on the following system:
Raspberry Pi 3B
16GB SD-Card
Noobs -> Raspbian OS & update
InfluxDB ARM installation (http://blog.centurio.net/2018/10/28/howto-install-influxdb-and-grafana-on-a-raspberry-pi-3/)
Grafana ARM installation (http://blog.centurio.net/2018/10/28/howto-install-influxdb-and-grafana-on-a-raspberry-pi-3/)
Node-Red installation & update
