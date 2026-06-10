### Projekt 1 LED Blinken

**1. Beschreibung**

LED-Blinken ist ein einfaches Projekt, das für Einsteiger konzipiert ist. Sie müssen nur eine LED auf dem Arduino-Board installieren und den Code in der Arduino IDE hochladen. Dieses Projekt festigt das Verständnis des Arduino-Konzeptes und die Anwendung von Methoden für Einsteiger.

**2. Funktionsprinzip**

![](media/A7.png)

**LED:** Allgemein gesprochen kann die begrenzte Ausgangsstromstärke der IO-Ports eine geringe Helligkeit der LED verursachen, daher wird im Schaltkreis ein NPN-Transistor (Q2) als Schalter eingesetzt. In diesem Fall leuchtet die LED, wenn die Basis (Pin 1) des Transistors auf hohem Pegel ist. Im Gegensatz dazu geht die LED aus, wenn die Basis auf niedrigem Pegel ist.

**Transistorschalter:** Kurz gesagt, die LED leuchtet, wenn die Basis (Pin 1) auf hohem Pegel ist. Gleichzeitig sind Kollektor (Pin 3) und Emitter (Pin 2) verbunden, und VCC fließt über einen strombegrenzenden Widerstand zur LED und schließlich zu GND, wodurch ein Stromkreis entsteht. Im Gegensatz dazu geht die LED aus, wenn die Basis auf niedrigem Pegel ist. In diesem Fall sind Kollektor und Emitter getrennt und die LED ist aus.

**3. Schaltplan**

![](media/A8.png)

**4. Testcode**

Nach den vorherigen Prinzipien können wir die LED über die Pegel der Pins auf dem Entwicklungsboard steuern.

1. Ziehen Sie den folgenden Block im Bereich „Events“ hinein.

![](media/A9.png)

2. Ziehen Sie den folgenden Block im Bereich „Control“ hinein.

![](media/A10.png)

3. Ziehen Sie den folgenden Block im Bereich „Pins“ hinein und setzen Sie den IO5-Pin auf output.

   ![](media/A11.png)

4. Ziehen Sie den folgenden Block im Bereich „LED“ hinein und setzen Sie den IO5-Pin auf HIGH.

![](media/A12.png)

5. Ziehen Sie den folgenden Block im Bereich „Control“ hinein.

![](media/A13.png)

6. Ziehen Sie die folgenden Blöcke hinein und setzen Sie den IO5-Pin auf LOW.

![](media/A14.png)

**Vollständiger Code：**

![](media/A15.png)

**5. Testergebnis**

Nach dem Hochladen des Codes und dem Einschalten wird die LED 1 Sekunde lang leuchten und 1 Sekunde lang aus sein.

**6. Code-Erklärung**

<p style="color:red;">Hinweis: Der Pin-Modus muss auf „output“ gesetzt werden, wenn das LED-Modul verwendet wird.<p>

1. Codeblöcke werden nicht ausgeführt, wenn der folgende Block nicht vorhanden ist.

![](media/A16.png)

2. Codeblöcke im folgenden Block werden in einer Schleife ausgeführt.

![](media/A17.png)

3. Dies ist ein Modul, das den Pin-Modus einstellt (LED und Summer für „output“-Modus steuern, und Sensor-Modul lesen für „input“).

![](media/A18.png)

4. Dies ist ein Modul, das den Pin und die Pegel („HIGH“ und „LOW“) einstellt.

![](media/A19.png)

5. Dies ist ein Modul, das die Verzögerungszeit einstellt.

![](media/A20.png)