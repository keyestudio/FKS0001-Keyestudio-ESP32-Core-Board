### Projekt 29 IR-Fernbedienung

**1. Beschreibung**

Die IR-Fernbedienung verwendet IR-Signale zur Steuerung von LEDs, was den Prozess der LED-Steuerung erheblich vereinfacht.

**2. Funktionsprinzip**

![](media/B113.png)

In diesem Projekt verwenden wir häufig einen Träger von etwa 38K zur Modulation.

Das IR-Fernbediensystem umfasst Modulation, Aussendung und Empfang. Es sendet Daten durch Modulation, was die Übertragungseffizienz verbessert und den Stromverbrauch reduziert.

Im Allgemeinen liegt die Frequenz der Trägermodulation im Bereich von 30kHz bis 60kHz (meist 38kHz). Die Tastverhältnis der Rechteckwelle beträgt 1/3, wie unten gezeigt, und wird durch den 455kHz Quarzoszillator auf der Senderseite bestimmt.  
Eine ganzzahlige Frequenzteilung ist für den Quarzoszillator an dieser Stelle erforderlich, und der Frequenzfaktor beträgt üblicherweise 12. Daher gilt: 455kHz ÷ 12 ≈ 37,9kHz ≈ 38kHz.

38kHz Träger (vollständiges) Aussendediagramm:

![](media/B114.jpg)

- **Trägerfrequenz:** 38kHz

- **Wellenlänge:** 940nm

- **Empfangswinkel:** 90°

- **Steuerabstand:** 6M

**Schaltplan der Fernbedienungstasten:**

![](media/B115.png)

**3. Anschlussdiagramm**

![](media/B116.png)

**4. Testcode**

1. Ziehen Sie die zwei Basisblöcke.

2. Finden und ziehen Sie den Block „IR remote init“ aus „IR Remote“ und setzen Sie den Pin auf IO19. Fügen Sie einen „baud rate“-Block aus „serial“ hinzu und stellen Sie ihn auf 9600 ein.

![](media/B117.png)、

3. Ziehen Sie einen „if“-Block und füllen Sie die Bedingung mit „Received data“. Nur wenn das IR-Modul Daten empfängt, werden die Codeblöcke im „if“ ausgeführt.

![](media/B118.png)

4. Ziehen Sie einen weiteren „if“-Block und setzen Sie die Bedingung auf „Read the data ＞ 0“. Nur wenn diese Bedingung erfüllt ist, beginnt der serielle Port mit der Ausgabe der Daten.

   Dieser Sensor arbeitet so schnell, dass der Code beim Drücken der Steuertasten zweimal oder öfter ausgeführt werden kann. Beim zweiten Mal eines gleichen Befehls wird jedoch der Wert 0 gesendet, daher ist ein „>“-Block notwendig, um Duplikate zu vermeiden.

![](media/B119.png)

5. Fügen Sie nach „then“ einen „serial print“-Block hinzu. Stellen Sie ihn so ein, dass die gelesenen Daten vom „IR remote“-Modul im Modus „warp“ ausgegeben werden.

![](media/B120.png)

6. Vergessen Sie am Ende nicht, die Daten nach der Ausführung zu aktualisieren.

![](media/B121.png)

**Vollständiger Code:**

![](media/B122.png)

**5. Testergebnis**

Nach dem Anschluss der Verkabelung und dem Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein. Drücken Sie die Taste auf der Fernbedieneinheit, und Sie sehen den Wert in Hexadezimalform.

![](media/B123.png)

**6. Erweiterungscode**

In diesem Erweiterungscode steuern wir eine Lampe mit einem IR-Fernbedienungsschalter. Drücken Sie OK, um die LED einzuschalten, und drücken Sie erneut, um sie auszuschalten.

Um diese wiederholbare Funktion zu realisieren, ist die Variable „item“ im gesamten Code unerlässlich. Beim ersten Mal ist item = 0, sodass die Codes im „else“-Block ausgeführt werden, um 1 als neuen Wert zuzuweisen. Beim zweiten Mal, wenn item = 1 ist, wird hingegen der „if“-Block ausgeführt, um den Wert abwechselnd wieder auf 0 zu setzen.

**Anschlussdiagramm:**

![](media/B124.png)

**Code:**

![](media/B125.png)

**7. Codeerklärung**

1. Initialisieren Sie das IR-Fernbedienungsmodul nach der Einstellung seines Empfangspins.

![](media/B126.png)

2. Prüfen Sie, ob der Sensor Daten empfangen hat. Falls ja, werden die zugehörigen Codeblöcke ausgeführt.

![](media/B127.png)

3. Lesen Sie die empfangenen Daten von der IR-Fernbedienung aus.

![](media/B128.png)

4. Aktualisieren Sie die empfangenen Daten nach jedem vollständigen Empfangsvorgang.

![](media/B129.png)