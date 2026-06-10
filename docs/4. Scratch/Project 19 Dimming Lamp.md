### Projekt 19  Dimmbares Licht

**1. Beschreibung**

Die dimmbare Lampe passt die Helligkeit der LED über ein Potentiometer und einen Arduino-Controller an. Die Helligkeit hängt vom Widerstandswert ab, der durch Anschluss der Enden des Potentiometers an digitale oder analoge Pins auf dem Board ausgelesen und eingestellt werden kann.  
Darüber hinaus wird dieses System zur Steuerung der Spannung oder des Stroms anderer Geräte wie Lüfter, Glühbirnen und Heizungen verwendet.

**2. Funktionsprinzip**

![](media/B32.png)

Im Wesentlichen ist ein Potentiometer ein Bauelement, das den Widerstandswert verändern kann. Nach dem Ohmschen Gesetz (U=I*R) beeinflusst der Widerstand die Spannung. Unser Potentiometer hat 10K.

In diesem Projekt beträgt der maximale Widerstand 10K. Das ESP32-Board teilt die Spannung von 3V gleichmäßig in 4095 Teile (3/4095=0.0007326007326). Die analoge Spannung wird durch Multiplikation des ausgelesenen Werts mit 0.0007326007326 erhalten.

**3. Schaltplan**

![](media/B33.png)

**4. Testcode**

Der analoge Wert des Potentiometers kann ausgelesen werden:

1. Ziehen Sie die zwei Basisblöcke. Setzen Sie den Baudraten-Block dazwischen und stellen Sie ihn auf 9600 ein.

2. Fügen Sie im „forever“-Loop einen „serial print“-Block hinzu und wählen Sie „warp“ als Druckmodus.

3. Ziehen Sie einen „read the value“-Block vom „pot“ zum serial print und setzen Sie den Pin auf IO33.

![](media/B34.png)

**5. Testergebnis**

Nach Anschluss der Verkabelung und Hochladen des Codes öffnen Sie den seriellen Monitor, stellen die Baudrate auf 9600 ein, und der analoge Wert wird im Bereich von 0-4095 angezeigt.

![](media/B35.png)

**6. Erweiterungscode**

Wir steuern die Helligkeit der LED über ein Potentiometer. Wie bekannt, wird dies durch PWM beeinflusst. Der Bereich des analogen Werts liegt jedoch bei 0-4095, während der von PWM bei 0-255 liegt. Daher wird eine „map(value, fromLow, fromHigh, toLow, toHigh)“-Funktion benötigt.

**Schaltplan：**

![](media/B36.png)

1. Ziehen Sie die zwei Basisblöcke.
2. Fügen Sie einen Variablenblock hinzu und setzen Sie ihn auf lokal. Wählen Sie „int“ als Typ und benennen Sie ihn „pot“.

![](media/B37.png)

3. Ziehen Sie eine „map“-Funktion aus „Data“ und setzen Sie sie an die Zuweisungsstelle. Setzen Sie den Wert von „map“ auf „read the value of pot IO33“, dessen Bereich von (0,4095) auf (0,255) abgebildet wird.

![](media/B38.png)

4. Fügen Sie abschließend einen „LED analogWrite“-Block hinzu. Setzen Sie den Pin auf IO25 und den analogen Wert auf die Variable „pot“.

![](media/B39.png)

**Vollständiger Code:**

![](media/B40.png)

**7. Code-Erklärung**

1. **map**-Funktion. Der Bereich des analogen Werts kann von 0-4095 auf 0-255 umgerechnet werden.

![](media/B41.png)

2. Liest den analogen Wert des Potentiometers durch Setzen des Pins aus.

![](media/B42.png)