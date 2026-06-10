### Projekt 27 Intelligentes Parken

**1. Beschreibung**

Dieses intelligente Parksystem erkennt und optimiert die Parkposition mittels eines Ultraschallsensors. Mit diesem System wird falsches Parken weitgehend vermieden.

Zuerst müssen Sie den Sensor rund um den Parkplatz installieren. Anschließend erkennt er den Abstand zwischen dem Auto und den Begrenzungen und sendet die Informationen an das Entwicklungsboard, um das Auto automatisch auf die optimale Parkposition zu steuern.

**2. Flussdiagramm**

![](media/B104.png)

**3. Schaltplan**

![](media/B105.png)

**4. Testcode**

Weisen Sie den erfassten Distanzwert einer Variablen zu und prüfen Sie, ob dieser größer als der eingestellte Schwellenwert ist. Falls ja, leuchten entsprechende Linien auf der Punktmatrix auf. So kann eine Entfernung durch das Beleuchten von Linien dargestellt werden.

**Referenzkoordinaten:**

![](media/B106.png)

**Vollständiger Code:**

![](media/B107.png)

**5. Testergebnis**

Nach dem Anschluss der Verkabelung und dem Hochladen des Codes werden Linien auf der Punktmatrix angezeigt. Wenn der erkannte Abstand weniger als 50 cm beträgt, werden weniger Linien angezeigt.

![](media/B108.png)![](media/B109.png)