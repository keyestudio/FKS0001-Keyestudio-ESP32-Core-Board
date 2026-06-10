### Projekt 4 Ampel

**1. Beschreibung**

Das Ampelmodul ist ein Gerät zur Steuerung des Verkehrs von Fußgängern und Fahrzeugen. Es umfasst eine rote, eine gelbe und eine grüne Lampe, die unterschiedliche Anweisungen bedeuten.

**Rot für Stopp:** Fußgänger und Fahrzeuge halten an.

**Gelb für Vorsicht:** Fußgänger und Fahrzeuge bereiten sich auf das Anhalten vor. Wenn die Fahrt bereits im Gange ist, sollte die Geschwindigkeit reduziert werden.

**Grün für Weiterfahren:** Fußgänger und Fahrzeuge fahren unter Beachtung der Verkehrsregeln weiter.

In diesem Projekt können Sie Arduino verwenden, um Code zur Steuerung der Ampel zu schreiben. Zum Beispiel können Sie die Dauer jeder Lampe und die Zeitintervalle dazwischen einstellen. Außerdem können Sie einen Timer hinzufügen, um die Lichtfarben nach Zeitplan zu ändern.

**2. Schaltplan**

![](media/A46.png)

**3. Testcode**

Wir simulieren einfach die Ampel: Die grüne LED leuchtet 5 Sekunden, die gelbe LED blinkt 3 Mal und die rote LED leuchtet 5 Sekunden. Dies wird in einer Schleife wiederholt.

Das Blinken der gelben LED kann mit der for()-Anweisung aus Projekt 3 realisiert werden. Somit müssen wir nur die Leuchtdauer einstellen, um eine Ampel zu vervollständigen.

1. Ziehen Sie die zwei Codeblöcke.

![](media/A47.png)

2. Stellen Sie den Pin-Modus auf „output“ ein.

![](media/A48.png)

3. Ziehen Sie die folgenden Blöcke aus dem Bereich „LED“ und setzen Sie den IO27-Pin auf HIGH und dann auf LOW. Stellen Sie anschließend die Verzögerungszeit auf 5 Sekunden ein.

![](media/A49.png)

4. Ziehen Sie die folgenden Blöcke aus dem Bereich „Control“ und setzen Sie die Wiederholungsanzahl auf 3, dann setzen Sie den IO26-Pin auf HIGH und danach auf LOW. Stellen Sie die Verzögerungszeit auf 0,5 Sekunden ein.

![](media/A50.png)

5. Wiederholen Sie Schritt 3 und setzen Sie den Pin auf IO25.

![](media/A51.png)

**Vollständiger Code：**

![](media/A52.png)

**4. Testergebnis**

Nach dem Hochladen des Codes leuchtet die grüne LED 5 Sekunden, die gelbe LED blinkt 3 Mal und die rote LED leuchtet 5 Sekunden.