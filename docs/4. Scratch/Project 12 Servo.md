### Projekt 12 Servo

**1. Beschreibung**

Dieser Servo zeichnet sich durch hohe Leistung und hohe Präzision mit einem maximalen Drehwinkel von 180° aus. Mit nur 9g Gewicht ist er perfekt geeignet für jede Miniatur-Anwendung in verschiedenen Einsatzbereichen. Darüber hinaus verfügt er über eine kurze Anlaufzeit, geringe Geräuschentwicklung und hohe Stabilität.

**2. Funktionsprinzip**

**Winkelbereich:** 180° (360°, 180° und 90°)

**Betriebsspannung:** 3,3V oder 5V

**Pin:** Drei Drähte

![](media/A143.png)

**GND:** Masse (braun)

**VCC:** Ein roter Pin, der mit +5V (3,3V) verbunden wird

**S:** Ein oranger Signalleitungs-Pin, der über PWM-Signal gesteuert wird

![](media/A144.png)

**Steuerprinzip:** Der Drehwinkel wird über das Tastverhältnis des PWM-Signals gesteuert. Theoretisch beträgt der Standard-PWM-Zyklus 20ms (50Hz), daher sollte die Pulsbreite im Bereich von 1ms bis 2ms liegen. Tatsächlich liegt die Pulsbreite jedoch zwischen 0,5ms und 2,5ms, was einem Winkel von 0° bis 180° entspricht. Beachten Sie, dass bei gleichem Signal der Drehwinkel je nach Servo-Hersteller variieren kann.

**3. Schaltplan**

![](media/A145.png)

**4. Testcode**

1. Ziehen Sie die beiden Basisblöcke und setzen Sie einen „Variable“-Block dazwischen. Stellen Sie den Variablentyp auf int, den Namen auf angle und weisen Sie den Anfangswert 0 zu.

![](media/A146.png)

2. **Servo dreht sich allmählich von 0° bis 180°:** 

Fügen Sie einen Wiederholungsblock hinzu und setzen Sie die Wiederholungsanzahl auf 180 (180 Winkel). Ziehen Sie einen „Variable ändern“-Block und einen „Servo“-Block hinein. Benennen Sie die Variable „angle“ und wählen Sie den Modus „++“. Stellen Sie den Servo-PIN auf IO4 und den Winkel auf die benannte Variable ein. Vergessen Sie nicht, eine Verzögerung von 15ms einzufügen.

![](media/A147.png)

3. **Servo dreht sich allmählich von 180° bis 0°:** Wiederholen Sie Schritt 2, setzen Sie jedoch den Variablenmodus auf „--“.

![](media/A148.png)

**Vollständiger Code:**

![](media/A149.png)

**5. Testergebnis**

Nach Anschluss der Verkabelung und Hochladen des Codes beginnt der Servo, sich von 0° bis 180° und anschließend von 180° bis 0° zu drehen.

**6. Code-Erklärung**

1. Setzt die Werte des Servos. Servo-Pin und Drehwinkel können durch Parameter in diesem Block gesteuert werden.

![](media/A150.png)

2. Liest den aktuellen Winkel des Servos aus.

![](media/A151.png)