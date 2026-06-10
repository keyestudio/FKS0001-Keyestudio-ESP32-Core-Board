### Projekt 13 Mini Lampe

**1. Beschreibung**

In diesem Projekt steuern wir eine Lampe über Arduino UNO und einen Taster. Wenn wir den Taster drücken, ändert sich der Zustand der Lampe (AN oder AUS).

**2. Funktionsprinzip**

![](media/A152.png)

Wenn der Taster losgelassen wird, liefert eine Spannung VCC, die durch R29 fließt, ein hohes Signal am S-Anschluss. Beim Drücken werden Pin 1 und 3 sowie Pin 2 und 4 verbunden, und die Spannung an S1 geht auf GND als niedriges Signal. In diesem Moment verhindert R29 einen Kurzschluss zwischen VCC und GND.

**3. Schaltplan**

![](media/A153.png)

**4. Testcode**

1. Fügen Sie zwei Grundblöcke hinzu.

![](media/A154.png)

2. Ziehen Sie einen „baud rate“-Block aus „Serial“ und stellen Sie ihn auf 9600 ein.

![](media/A155.png)

3. Ziehen Sie dann einen „print“-Block aus „Serial“, geben Sie „Key status:“ in das Feld ein und stellen Sie ihn auf „no-warp“.

![](media/A156.png)

4. Stellen Sie den IO15-Pin auf „input“.

![](media/A157.png)

5. Ziehen Sie einen weiteren „Serial print“-Block aus „Serial“ und stellen Sie den Modus auf „warp“. Fügen Sie einen „state value of button“-Block aus „Button“ hinzu und setzen Sie den Pin auf IO15.

![](media/A158.png)

**Vollständiger Code:**

![](media/A159.png)

**5. Testergebnis**

Nach dem Verbinden der Schaltung und Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein.  
Wenn wir den Taster drücken, zeigt der serielle Port „Key status: 0“ an; wenn wir den Taster loslassen, zeigt der serielle Port „Key status: 1“ an.

![](media/A160.png)

**6. Wissensvertiefung**

Als nächstes steuern wir die LED über den Zustand des Tasters.

**Flussdiagramm：**

![](media/A161.png)

**Schaltplan：**

![](media/A162.png)

**Code:**

1. Ziehen Sie zwei Grundblöcke.

![](media/A163.png)

2. Stellen Sie den LED-Pin auf „output“ und den Taster-Pin auf „input“.

![](media/A164.png)

3. Ziehen Sie einen „if else“-Block aus „Control“. Fügen Sie nach „if“ einen „button pin“-Block aus „Button“ hinzu und setzen Sie den Pin auf IO15. Legen Sie unter „if“ einen „LED output“-Block mit HIGH und unter „else“ einen weiteren mit LOW. Beide LED-Pins sind IO4.

![](media/A165.png)

**Vollständiger Code:**

![](media/A166.png)

**8. Code-Erklärung**

**Hinweis: Der Pin-Modus muss auf „input“ gesetzt werden, wenn das Taster-Modul verwendet wird.**

1. Prüft, ob der Taster gedrückt ist. Wenn ja, ergibt dieser Block true.

![](media/A167.png)

2. Liest den Wert des Tasters aus. Wenn der Taster nicht gedrückt ist, ist der Wert 1, sonst 0.

![](media/A168.png)

3. Wenn die Bedingung im Hexagon wahr ist, wird der „if“-Block ausgeführt. Andernfalls läuft das Programm gemäß dem „else“-Block.

![](media/A169.png)

4. Setzt die Baudrate. Bitte stellen Sie sicher, dass die serielle Baudrate mit der des seriellen Monitors übereinstimmt, sonst wird nichts ausgegeben. Übliche Baudraten sind 9600 und 115200, hier verwenden wir 9600.

![](media/A170.png)

5. Gibt Zeichen im seriellen Monitor aus. Die ausgegebenen Wörter sind die, die Sie im Feld eingeben. Außerdem gibt es drei Druckmodi: warp, no-warp und HEX (hexadezimal).

![](media/A171.png)