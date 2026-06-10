### Projekt 22 Geräuschmesser

**1. Beschreibung**

Der Arduino-Geräuschmesser stellt das Tonsignal als eine Reihe von Punkten dar, die in Muster umgewandelt und auf einer Punktmatrix angezeigt werden.

**2. Schaltplan**

![](media/B63.png)

**3. Testcode**

1. Ziehen Sie die Basisblöcke und initialisieren Sie das Display. Setzen Sie den Pin CS auf IO15 und die Helligkeit auf 3. Fügen Sie dann einen Variablenblock hinzu, wählen Sie int und benennen Sie ihn als „item“ mit einer Anfangszuweisung von 0.

2. Fügen Sie einen Variablenblock hinzu und benennen Sie ihn als „item“. Verwenden Sie eine Map-Funktion, um den gelesenen Schallwertbereich von 0-4095 auf 0-7 zu konvertieren, wobei der angenommene Maximalwert des Schalls 800 beträgt.

![](media/B64.png)

3. Löschen Sie das Display.

4. Programmieren Sie eine Bedingung. Wenn die Variable item größer als -1 ist, zeigt die Punktmatrix (x0:0  y0:0 x1:1  y1:0) in roter Farbe an.

![](media/B65.png)

5. Wiederholen Sie Schritt 4, aber die Bedingung lautet, ob item größer als 0 ist. Wenn ja, leuchten die Punkte bei (x0:1  y0:0  x1:1  y1:1) auf. Bauen Sie analog dazu Codeblöcke mit Bezug auf die folgenden Koordinaten.

6. Aktualisieren Sie abschließend das Display.

**Referenzkoordinaten:**

![](media/B66.png)

![](media/B67.png)

**Vollständiger Code:**

![](media/B68.png)

**4. Testergebnis**

Nach dem Anschluss der Verkabelung und dem Hochladen des Codes wird die Geräuschpegelanzeige auf der Punktmatrix wie unten gezeigt dargestellt.

![](media/B69.png)![](media/B70.png)![](media/B69.png)![](media/B70.png)