### Projekt 2 Atmende LED

**1. Beschreibung**

Die Arduino atmende LED nutzt den programmierbaren PWM an Bord, um eine analoge Wellenform auszugeben. Nach dem Einschalten kann die Helligkeit der LED durch den Tastgrad der Wellenform angepasst werden, um schließlich den Effekt einer atmenden LED zu realisieren.

Auf diese Weise kann Umgebungslicht simuliert werden, indem die LED-Helligkeit über die Zeit verändert wird. Außerdem kann die atmende LED eine farbenfrohe Mini-Leuchte bilden, die eine ruhige und warme Atmosphäre schafft.

**2. Was ist PWM?**

PWM steuert analoge Ausgänge auf digitale Weise, indem der Tastgrad der Welle (ein Signal, das zyklisch zwischen hohem und niedrigem Pegel wechselt) angepasst wird.

Für Arduino sind digitale Ausgangsports LOW und HIGH, die jeweils 0V und 5V entsprechen. Allgemein definieren wir LOW als 0 und HIGH als 1. Arduino gibt innerhalb von 1 Sekunde 500 Signale mit 0 oder 1 aus. Wenn sie „1“ sind, wird 5V ausgegeben. Umgekehrt, wenn sie alle 0 sind, beträgt die Ausgabe 0V. Oder wenn sie 010101010101... sind, beträgt der durchschnittliche Ausgang 2,5V.

Mit anderen Worten beeinflusst das Verhältnis von 0 und 1 die Spannung, je mehr 0- und 1-Signale pro Zeiteinheit ausgegeben werden, desto genauer ist die Steuerung.

![](media/A21.png)

**3. Schaltplan**

![](media/A22.png)

**4. Testcode**

Wir verwenden eine „for“-Schleife, um eine Variable von 0 bis 255 zu erhöhen, und definieren diese Variable als PWM-Ausgang (analogWrite(pin, value)). Übrigens kann eine Verzögerungszeit die Steuerung der Leuchtdauer der LED verstärken. Anschließend verwenden wir eine weitere „for“-Schleife, um sie von 255 auf 0 mit einer Verzögerung zu verringern, um den Dimmvorgang der LED zu steuern.

1. Ziehen Sie die beiden Codeblöcke.

![](media/A23.png)

2. Ziehen Sie den folgenden Block aus dem Bereich „Variablen“ und definieren Sie den Namen als „item“ mit einer Anfangszuweisung von „0“. Setzen Sie diesen Block in den „forever“-Block.

![](media/A24.png)

3. Ziehen Sie den folgenden Block aus dem Bereich „Steuerung“ und setzen Sie ihn auf 255 Wiederholungen, was dem Maximalwert von PWM entspricht.

![](media/A25.png)

4. Ziehen Sie den folgenden Block aus dem Bereich „Variablen“, setzen Sie „item“ als zu änderndes Objekt und stellen Sie den Modus auf „++“.

![](media/A26.png)

5. Ziehen Sie den folgenden Block aus dem Bereich „LED“ und setzen Sie den LED-Pin auf IO5. Fügen Sie dann einen „Variable“-Block hinzu und füllen Sie das Feld mit „item“.

![](media/A27.png)

6. Ziehen Sie den folgenden Block aus dem Bereich „Steuerung“ und setzen Sie die Zeit auf 0,01s, also 10ms.

![](media/A28.png)

7. Erstellen Sie gemäß den vorherigen Schritten einen weiteren Codeblock mit dem einzigen Unterschied, dass der Variablenmodus „– –“ ist.

![](media/A29.png)

**Vollständiger Code:**

![](media/A30.png)

**5. Testergebnis**

Nach dem Hochladen des Codes können wir sehen, dass die LED allmählich dunkler wird. Sie „atmet“ gleichmäßig.

**6. Code-Erklärung**

1. Dieser Block wird verwendet, um den nutzbaren Bereich der Variable, den Variablentyp, den Namen und den Anfangswert festzulegen.

![](media/A31.png)

2. Die Wiederholungsanzahl kann im Feld dieses Wiederholungsblocks zugewiesen werden.

![](media/A32.png)

3. Geben Sie einen Variablennamen in das Feld ein, und sein Wert wird bei jeder Ausführung des Codes um 1 erhöht. „++“ kann zu „– –“ geändert werden.

![](media/A33.png)

4. Geben Sie einen Variablennamen in das Feld ein, und sein Wert wird bei jeder Ausführung des Codes um 1 verringert. „– –“ kann zu „++“ geändert werden.

![](media/A34.png)

5. Dies ist ein PWM-Ausgabemodul, und das weiße Feld zeigt den Wert des ausgegebenen PWM an.

![](media/A35.png)