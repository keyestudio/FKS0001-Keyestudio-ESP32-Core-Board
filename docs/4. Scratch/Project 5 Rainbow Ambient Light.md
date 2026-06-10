### Projekt 5 Regenbogen-Umgebungslicht

**1. Beschreibung**

2812RGB LED ist ein programmierbares, farbenfrohes, traumhaftes Licht, dessen Farbe, Helligkeit und Rhythmus einstellbar sind. Dieses Regenbogen-Umgebungslicht kann nach Belieben als dynamische Dekoration verwendet werden. Oder Sie können es steuern, um „mit Musik zu tanzen“. Wichtig ist, dass es als Alarm verbessert werden kann. Sein eingebauter Sensor erkennt die Umgebung und warnt den Benutzer durch Änderung von Farbe, Helligkeit und Rhythmus.

**2. Funktionsprinzip**

![](media/A53.png)

Das Datenprotokoll verwendet den Kommunikationsmodus des einkanaligen Return-to-Zero-Codes. Nach dem Zurücksetzen des Pixels bei Stromzufuhr empfängt der DIN-Anschluss Daten vom Controller. Die zuerst ankommenden 24-Bit-Daten werden vom ersten Pixel extrahiert und in das interne Datenregister gesendet.

Die verbleibenden Daten werden von einer Verstärkerschaltung verstärkt und über den DOUT-Anschluss an das nächste kaskadierte Pixel weitergeleitet.  
Beim Durchlaufen der Pixel verringert sich das Signal jeweils um 24 Bit.

Außerdem verwendet das Pixel eine automatische Formungs- und Weiterleitungstechnologie, sodass die Anzahl der kaskadierten Pixel nur durch die Signalübertragungsgeschwindigkeit begrenzt ist.

**3. Schaltplan**

![](media/A54.png)

**4. Testcode**

Lernen wir, wie man 2812 RGB einschaltet und seine Farben einstellt.

1. Ziehen Sie die beiden Codeblöcke.

![](media/A55.png)

2. Ziehen Sie den folgenden Block aus dem Bereich „RGB LED“ und stellen Sie den Pin auf IO15 und die Anzahl der LEDs auf 6 ein.

![](media/A56.png)

3. Ziehen Sie den folgenden Block aus dem Bereich „RGB LED“ und stellen Sie die Helligkeit auf 20 ein.

![](media/A57.png)

4. Ziehen Sie die folgenden Blöcke und stellen Sie die Anzahl der LEDs auf 0, 1, 2, 3, 4 und 5 ein, wählen Sie dann die Farben Rot, Grün, Blau, Gelb, Lila und Weiß.

![](media/A58.png)

5. Fügen Sie den folgenden Block hinzu.

![](media/A59.png)

**Vollständiger Code:**

![](media/A60.png)

**5. Testergebnis**

Nach dem Hochladen des Codes, dem Verbinden der Verkabelung und dem Einschalten leuchten die LEDs in verschiedenen Farben, wie unten gezeigt:

![](media/A61.png)

**6. Wissensvertiefung**

In diesem Erweiterungsprojekt erstellen wir eine Mini-Lichtshow!

Verschachteln Sie vier „wiederhole“-Blöcke und fügen Sie darin jeweils eine „Variable +“ hinzu, dann setzen Sie die entsprechenden Variablen am Ende jeder Schleife auf 0 zurück.

![](media/A62.png)

Setzen Sie die oben genannten drei Variablen in den „RGB“-Block, damit diese Farbwerte gesteuert werden. Fügen Sie dann ein Aktualisierungsmodul hinzu.

![](media/A63.png)

Setzen Sie das RGB in einen „Farbe anzeigen“-Block, um die Farben darzustellen. Definieren Sie eine Variable, um die angezeigte LED zu steuern.

![](media/A64.png)

Das „für immer“-Modul wird verwendet, um die RGB-LEDs zu steuern, die von 0 bis 5 durchlaufen und nacheinander jede LED einschalten.

![](media/A65.png)

**Vollständiger Code**

![](media/A66.png)

**7. Code-Erklärung**

1. Stellen Sie die Anzahl der 2812 RGB ein. Ein Entwicklungsboard-Pin kann mehrere 2812 RGB LEDs steuern, daher müssen wir die Anzahl im Voraus einstellen und den angeschlossenen Pin auswählen.

![](media/A67.png)

2. Stellen Sie die Helligkeit der 2812 RGB ein. Geben Sie den Helligkeitswert im Bereich von 0-255 ein, wobei 255 die höchste Helligkeit ist.

![](media/A68.png)

3. Dieser Block schaltet alle 2812 RGBs aus.

![](media/A69.png)

4. Steuern Sie die Anzeige der 2812 RGBs. Wir können die Felder ausfüllen, um die leuchtende LED und deren Farbe nach Auswahl des Pins zu steuern. Zum Beispiel bedeutet „0 bis 0“, dass nur die erste LED leuchtet. Nach dem Hochladen des Codes leuchtet die erste LED in der eingestellten Farbe.

**HINWEIS:** Die beiden Felder können auch mit Variablen gefüllt werden, sodass eine Lichtshow erstellt werden kann.

![](media/A70.png)

5. Stellen Sie die Farbe der 2812 RGBs ein. Die angezeigte Farbe kann durch die Werte für Rot, Grün und Blau moduliert werden. Wir können diesen Block in den Farbeinstellungen der 2812 RGB hinzufügen.

![](media/A71.png)

6. Es kann eine einzelne 2812 RGB-Anzeige gesteuert werden, indem die LED-Nummer eingegeben und die Farbe ausgewählt wird.

![](media/A72.png)

7. Die 2812 RGB zeigt die eingestellte Farbe erst nach dem Aktualisieren an.

![](media/A73.png)