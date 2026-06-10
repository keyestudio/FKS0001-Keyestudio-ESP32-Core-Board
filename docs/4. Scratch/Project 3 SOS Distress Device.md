### Projekt 3 SOS Notsignalgerät

**1. Beschreibung**

Das SOS-Gerät kann Notsignale aussenden, die dem Prinzip des Morse-Codes entsprechen. Es ist praktisch für Notfälle.

**2. Schaltplan**

![](media/A36.png)

**3. Testcode**

Zuerst sollten wir klären, wie das SOS-Notsignal blinkt: Die LED blinkt schnell 3-mal für „S“ und langsam 3-mal für „O“.

Anschließend steuern wir die Blinkanzahl und -dauer über eine "for"-Schleife und legen die Pausenzeit zwischen den Buchstaben fest.

1. Ziehen Sie die beiden Codeblöcke.

![](media/A37.png)

2. Ziehen Sie den folgenden Block aus dem Bereich "Pins" und setzen Sie den IO5-Pin auf Ausgang.

![](media/A38.png)

**Buchstabe „S“**

3. Ziehen Sie den folgenden Block aus dem Bereich "Control" und setzen Sie ihn auf 3-mal, da „S“ für 3-maliges Blinken steht.

![](media/A39.png)

4. Ziehen Sie die folgenden Blöcke aus dem Bereich "LED" und setzen Sie den IO5-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 0,15 s ein.

![](media/A40.png)

5. Ziehen Sie die folgenden Blöcke aus dem Bereich "LED" und setzen Sie den IO5-Pin auf LOW. Stellen Sie dann die Verzögerungszeit auf 0,1 s ein.

![](media/A41.png)

**Buchstabe O**

6. Orientieren Sie sich an den vorherigen Schritten, um die folgenden Codeblöcke zu erstellen. Ändern Sie die HIGH-Ausgabe auf eine Verzögerung von 0,4 s und LOW auf 0,2 s.

![](media/A42.png)

**Buchstabe S**

7. Führen Sie die Schritte 3, 4 und 5 erneut aus.

![](media/A43.png)

8. Fügen Sie am Ende eine Verzögerung von 5 s hinzu, damit sich „SOS“ alle 5 s wiederholt.

   ![](media/A44.png)

**Vollständiger Code:**

![](media/A45.png)

**4. Testergebnis**

Nach dem Hochladen des Codes blinkt die LED jeweils 3-mal schnell und langsam.