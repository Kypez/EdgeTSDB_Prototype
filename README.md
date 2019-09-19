# EdgeTSDB_Prototype_Simulated_Sensor_Ingestion_to_InfluxDB

Dieser Prorotyp ist eine JSON-Datei für den Import in die Open-Source Entwicklungsumgebung Node-Red. Der Prototyp dient dazu, da um das Systemverhalten der Zeitreihendatenbank InfluxDB auf einem Raspberry Pi als Einzelkonton bei mehrfacher paralellel schreiblast und gleichzeitigen Datenabfragen zu evaluieren. Dabei wurde das Node-Red Framework verwendet, um mehrere Datenquellen mit einer InfluxDB-Datenbank zu verbinden und das Schreiben verschiedener Sensordatentypen in InfluxDB durch entsprechende Ausgabenodes zu simulieren. 

Der Zweck des Prototyps ist es eine Berwertung des Lastmanagements bei InfluxDB zu ermöglichen. Mittels InfluxDB werden 60 Datenquellen erzeugt und 60 paralelle Datenströme über den ofiziellen Konnektor in die Datenbank InfluxDB eingespeist.

Damit der Prototyp funktionert werden folgende Nodes werden vorausgesetzt, die nicht vorinstalliert sind:
- Sensehat Node
- InfluxDB Node

Die Funktionsweise des Prototyps kann wie folgt beschrieben werden: 
Es wurde eine Node-Red-Instanz mit 60 Ausgabe-Nodes erstellt, um die Anzahl der Sensoren einer modernen Werkzeugmaschine zu simulieren (DMG Mori 2016)

Die Sensehat-Nodes wurden verwendet, um das Sensor-Erweiterungsmodul für den Raspberry Pi zu simulieren. Jeder Node kann simulierte Daten verschiedener Sensoren (z. B. Temperatur oder Beschleunigung) mit einer vorgegebenen Abtastrate erzeugen. Jeder datenerzeugende Node ist mit dem aufnehmenden InfluxDB-Node verbunden und ein simultanes Schreiben in die vorkonfigurierte InfluxDB-Datenbank wird ermöglicht.

Von den 60 Ausgabe-Nodes wurden 54 Nodes so konfiguriert, um Temperaturdaten als exemplarische Sensormessung in industriellen Prozessen zu simulieren. Fünf Nodes lieferten die Daten zur Rotationsintensität eines Werkzeugs (z. B. einer Spindel in einer Werkzeugmaschine). Zusätzlich wurde ein Node konfiguriert, um Twitter-Nachrichten zu erfassen und in InfluxDB auf dem Edge-Gerät zu schreiben. Dadurch wurden Fehlermeldungen vom Überwachungssystem einer Werkzeugmaschine simuliert (Martinviita 2018). Alle Sensordaten wurden mit einer Abtastrate von 1 Sekunde konfiguriert. Obwohl diese Abtastrate nicht als hochfrequent eingestuft werden kann, sind schnellere Abtastraten bei den verwendeten Sensehat-Nodes (Node-Red 2018) nicht möglich.

Die in InfluxDB gespeicherten Daten werden sporadisch durch Abfragen ganzer Zeitreihen von der Analyseanwendung Grafana abgefragt, um die Lese-/Schreibunabhängigkeit von InfluxDB zu simulieren und bei aktiven Schreibvorgängen gleichzeitige Abfragen zu testen.

