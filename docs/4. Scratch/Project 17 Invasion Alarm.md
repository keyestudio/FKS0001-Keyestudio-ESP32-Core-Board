### Projekt 17 Invasionsalarm

**1. Beschreibung**

Dieses Invasionsalarmsystem kann Eindringlinge in Häusern oder kleinen Büros erkennen und den Besitzer rechtzeitig warnen, Maßnahmen zu ergreifen.

In diesem Projekt überwacht der Sensor einen bestimmten Bereich. Ein Gerät auf dem Arduino-Board löst aus, dass eine LED aufleuchtet und ein Summer warnt, wenn in dieser Zone eine Bewegung erkannt wird. Außerdem ist die Empfindlichkeit einstellbar, um eine genauere Erkennung zu ermöglichen.

Im Grunde zeichnet sich dieses Modul durch Praktikabilität, einfache Installation und geringe Kosten aus. Neben Haus und Büro eignet es sich auch für Fabriken, Lagerhäuser und Märkte, was in großem Maße den Schutz des Eigentums gewährleistet.

**2. Funktionsprinzip**

![](media/B14.png)

Der menschliche Körper (37°C) strahlt immer Infrarotstrahlung mit einer Wellenlänge von 10μm ab, die der vom Sensor erfassten Wellenlänge entspricht.

Aus diesem Grund kann dieses Modul Bewegungen von Menschen erkennen. Wenn eine Bewegung vorliegt, gibt der PIR-Sensor für etwa 3 Sekunden ein High-Signal aus und danach ein Low-Signal.

**3. Schaltplan**

![](media/B15.png)

**4. Testcode**

1. Fügen Sie die zwei Grundblöcke hinzu und ziehen Sie einen „baud rate“-Block aus „Serial“ dazwischen. Stellen Sie die serielle Baudrate auf 9600 ein.

![](media/B16.png)

2. Fügen Sie einen „if else“-Block hinzu. Setzen Sie einen „read PIR motion sensor“-Block in das sechseckige Feld und stellen Sie die Schnittstelle auf IO5 ein, damit erkannt wird, ob eine menschliche Bewegung vorliegt. Fügen Sie zwei „serial print“-Blöcke nach „then“ und „else“ hinzu und stellen Sie beide Modi auf „warp“. Wenn die Bedingung erfüllt ist, wird „Someone Invaded“ ausgegeben. Andernfalls wird „No one“ ausgegeben, gefolgt von einer Verzögerung von 1 Sekunde.

![](media/B17.png)

**Vollständiger Code:**

![](media/B18.png)

**5. Testergebnis**

Nach Anschluss der Verkabelung und Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein. Wenn der Sensor eine Bewegung erkennt, gibt der serielle Port „Someone Invaded“ aus, andernfalls „No One“.

![](media/B19.png)

**6. Erweiterungscode**

Lassen Sie uns einen Invasionsalarm bauen. Wenn der PIR-Sensor einen Menschen erkennt, leuchtet die LED und der Summer gibt einen Ton von sich. Im Gegensatz dazu geht die LED aus und der Summer bleibt still.

**Flussdiagramm：**

![](media/B20.png)

**Schaltplan：**

![](media/B21.png)

**Code：**

![](media/B22.png)

**7. Code-Erklärung**

Wenn der PIR menschliche Bewegungen erkennt, gibt er ein High-Signal aus. Daher können wir durch Auslesen des Pins am Entwicklungsboard, der mit diesem Sensor verbunden ist, feststellen, ob eine Bewegung vorliegt.

![](media/B23.png)