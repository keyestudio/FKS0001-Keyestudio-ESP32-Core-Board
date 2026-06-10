### Projekt 14 Zähler

**1. Beschreibung**

Der Arduino 4-Bit Digitalrohrzähler kann Zahlen im Bereich von 0~9999 erfassen. Er verfügt über eine Anzeige-Geschwindigkeit, Zählmodus-Anpassung sowie eine Rücksetzfunktion. Dieses Modul wird häufig in Echtzeit-Zählern (wie Tastenbetätigung und DC-Motor-Drehzahlzählung), Spiel- und Versuchsausrüstung eingesetzt.

**2. Flussdiagramm**

![](media/A172.png)

**3. Schaltplan**

![](media/A173.png)

**4. Testcode**

1. Ziehen Sie die beiden Grundblöcke.

![](media/A174.png)

2. Stellen Sie den Tasten-Pin auf „input“.

![](media/A175.png)

3. Fügen Sie einen „Variable“-Block hinzu. Setzen Sie den Variablentyp auf int und den Namen auf item. Weisen Sie 0 als Anfangswert zu.

![](media/A176.png)

4. Ziehen Sie einen „if“-Block aus „Control“ (er wird nur ausgeführt, wenn die Bedingung erfüllt ist). Legen Sie einen „Button pressed“-Block aus „Button“ in das Bedingungsfeld (das sechseckige) und setzen Sie den Pin auf IO19. Ziehen Sie einen „variable mode“-Block und setzen Sie ihn nach „then“, definieren Sie ihn als „item“ und stellen Sie den Modus auf „++“.

![](media/A177.png)

5. Wiederholen Sie Schritt 4, setzen Sie jedoch die Schnittstelle auf IO18 und den Modus auf „– –“.

![](media/A178.png)

6. Ziehen Sie einen weiteren „if“-Block aus „Control“ und definieren Sie die Bedingung „wurde die Taste an Schnittstelle IO17 gedrückt?“. Legen Sie nach „then“ einen Variablen-Setzblock und setzen Sie die Variable auf 0.

![](media/A179.png)

7. Ziehen Sie einen „if“-Block aus „Control“. Finden Sie den „＞“-Block in „Operators“ und füllen Sie das linke Feld mit „variable item“ und das rechte mit „9999“. Legen Sie ebenfalls nach „then“ einen Variablen-Setzblock und setzen Sie die Variable auf 0.

![](media/A180.png)

8. Ziehen Sie einen „TM1650 display“-Block aus „Digital tube“ und setzen Sie die angezeigte Zeichenfolge auf den „variable item“-Block. Vergessen Sie abschließend nicht, eine Verzögerung von 0,2 s hinzuzufügen.

![](media/A181.png)

**Vollständiger Code:**

![](media/A182.png)

**5. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes drücken Sie die grüne Taste, um 1 zu addieren, die gelbe, um 1 zu subtrahieren, und die rote, um zurückzusetzen.

**6. Code-Erklärung**

Der **">"**-Block wird verwendet, um zwischen zwei Werten zu vergleichen. Diese beiden Felder können entweder mit Zahlen oder Variablen belegt werden.

![](media/A183.png)