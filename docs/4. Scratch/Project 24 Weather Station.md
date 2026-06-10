### Projekt 24 Wetterstation

**1. Beschreibung**

Diese Wetterstation erfasst die Umgebungstemperatur und den Feuchtigkeitswert über ein Arduino-Board und einen Temperatur- und Feuchtigkeitssensor.

Außerdem ermöglicht sie die Anpassung der Temperatur- und Feuchtigkeitswerte entsprechend den Umweltparametern, um angenehme Umweltbedingungen zu erreichen.

**2. Schaltplan**

![](media/B84.png)

**3. Testcode**

1. Fügen Sie zwei Basismodule hinzu. Initialisieren Sie das LCD 1602 und schalten Sie die Hintergrundbeleuchtung des LCD 1602 ein (denken Sie daran, das LCD einzuschalten). Setzen Sie den Pin des dht auf IO26 und den Modus auf dht11. Setzen Sie zwei int-Variablen „RH“ und „temp“ auf 0.

![](media/B85.png)

2. Weisen Sie der Variable RH den Feuchtigkeitswert und der Variable temp den Temperaturwert zu.

![](media/B86.png)

3. Setzen Sie die LCD-Anzeigeposition auf x: 0 und y: 0. Fügen Sie das LCD-Anzeigemodul hinzu und setzen Sie das Anzeigewort auf „humidity:“. Fügen Sie das LCD-Anzeigemodul erneut hinzu und fügen Sie die Variable RH in das weiße Feld ein.

![](media/B87.png)

4. Wiederholen Sie Schritt 3, setzen Sie jedoch y: 1 und das Anzeigewort auf „temperature:“ und fügen Sie die Variable temp in das weiße Feld ein.

![](media/B88.png)

**Vollständiger Code:**

![](media/B89.png)

**4. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes zeigt das LCD direkt den Umgebungsfeuchtigkeits- und Temperaturwert an.

![](media/B90.png)