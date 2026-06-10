### Projekt 25 Ultraschall-Entfernungsmesser

**1. Beschreibung**

Dieser Ultraschall-Entfernungsmesser misst die Entfernung von Hindernissen, indem er Schallwellen aussendet und dann das Echo empfängt. Das heißt, die Entfernung ist kein unmittelbarer Wert, sondern ein beobachteter Wert, der durch eine theoretische Berechnung der Zeitdifferenz zwischen Sender und Empfänger ermittelt wird.

Ultraschall kann die Form von Objekten erkennen, automatische Türen steuern sowie Fließgeschwindigkeit und Druck schätzen.

Außerdem unterstützt er die Zusammenarbeit mit Computern. Dadurch kann der gemessene Wert über ein Arduino-Board an Computer übertragen werden.

Im Alltag wird er häufig für Motoren, Servos und LEDs sowie Systeme (automatische Navigation, Steuerungs- und Sicherheitsüberwachungssysteme) eingesetzt.

**2. Funktionsprinzip**

![](media/B91.png)

Wie allgemein bekannt ist, handelt es sich bei Ultraschall um eine Art unhörbares Schallwellensignal mit hoher Frequenz. Ähnlich wie eine Fledermaus misst dieses Modul die Entfernung von Hindernissen, indem es die Zeitdifferenz zwischen Wellenemission und Echoempfang berechnet.

- **Maximale Entfernung:** 3M

- **Minimale Entfernung:** 5cm

- **Erfassungswinkel:** ≤15°

**3. Schaltplan**

![](media/B92.png)

**4. Testcode**

Im „forever“-Block zwei „serial print“-Blöcke anlegen und einen „read distance“-Block aus „Ultrasonic“ ziehen. Den trig-Pin auf IO13 und den echo-Pin auf IO14 setzen, beide in cm. Eine Verzögerung von 0,5s nicht vergessen.

![](media/B93.png)

**5. Testergebnis**

Nach Anschluss der Verkabelung und Hochladen des Codes den seriellen Monitor öffnen, Baudrate auf 9600 einstellen, und der serielle Port beginnt, die Distanzwerte auszugeben.

![](media/B94.png)

**6. Wissensvertiefung**

Lassen Sie uns einen Entfernungsmesser bauen.

Wir zeigen Zeichen auf dem LCD 1602 an. Programmieren Sie, dass „Keyestudio“ bei (3,0) und „distance:“ bei (0,1) angezeigt wird, gefolgt vom Distanzwert bei (9,1).

Wenn der Wert kleiner als 100 (oder 10) ist, bleibt ein Rest der dritten (bzw. zweiten) Stelle erhalten. Daher ist eine „if“-Abfrage notwendig, um eine bestimmte Bedingung zu prüfen.

**Schaltplan：**

![](media/B95.png)

**Code：**

1. Ziehen Sie die zwei Basisblöcke.

2. Initialisieren Sie im „LCD“ das LCD. Ziehen Sie einen „LCD print“-Block und fügen Sie den Zeichenstring „Keyestudio“ hinzu (dies kann auch außerhalb des „forever“-Blocks erfolgen, da diese Anzeige fest ist). Fügen Sie einen „variable“-Block hinzu, setzen Sie den Typ auf int und benennen Sie ihn „distance“ mit einer Anfangszuweisung von 0.

![](media/B96.png)

3. Weisen Sie der Variablen „distance“ den Wert von „read distance“ zu. Stellen Sie das LCD so ein, dass „Distance：“ ausgegeben wird, gefolgt vom Distanzwert (und wir müssen die vorangehenden Zeichen im Voraus berechnen, um den Cursor entsprechend zu setzen).

![](media/B97.png)

4. Erstellen Sie einen Block zum „Löschen von Anzeige-Resten“, wenn die Anzahl der angezeigten Stellen abnimmt. Zuerst wird eine Bedingung verwendet, um zu prüfen, ob die Distanz kleiner als 100 (oder 10) ist. Falls ja, wird an der Stelle der dritten (bzw. zweiten) Stelle ein Leerzeichen ausgegeben, um die vorherige Anzeige zu löschen. Zum Schluss nicht vergessen, eine Verzögerung von 0,5s hinzuzufügen.

![](media/B98.png)

**Vollständiger Code:**

![](media/B99.png)

**7. Code-Erklärung**

Liest die Entfernung aus, nachdem trig-Pin und echo-Pin gesetzt wurden. Die Einheit des angezeigten Werts ist optional (cm oder inch).

![](media/B100.png)