### Projekt 28 Intelligentes Tor

**1. Beschreibung**

Das intelligente Tor ist ein intelligentes Parksystem, das MCU und Ultraschallsensor integriert und das Tor automatisch entsprechend der Entfernung der Fahrzeuge steuert, um die Fahrzeugzufahrt besser zu kontrollieren.

Wenn eine bestimmte Entfernung erreicht wird, empfängt die MCU das Signal vom Sensor und schätzt die Entfernung anhand der Signalstärke. Wenn sich ein Fahrzeug nähert oder entfernt, öffnet oder schließt die MCU das Tor über einen Servo.

**2. Flussdiagramm**

![](media/B110.png)

**3. Schaltplan**

![](media/B111.png)

**4. Testcode**

Definieren Sie eine Variable „distance“ mit der Zuweisung des vom Ultraschallmodul erfassten Entfernungswerts.

Vergleichen Sie anschließend den Entfernungswert mit 30 cm. Wenn er kleiner als 30 cm ist, dreht sich der Servo für 5 s auf 180°. Andernfalls kehrt der Servo auf 0° zurück.

![](media/B112.png)

**5. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes dreht sich der Servo für 5 s auf 180°, wenn die erkannte Entfernung weniger als 30 cm beträgt. Andernfalls dreht sich der Servo auf 0°.