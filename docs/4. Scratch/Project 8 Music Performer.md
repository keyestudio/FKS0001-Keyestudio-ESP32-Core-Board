### Projekt 8 Musikspieler

**1. Beschreibung**

In diesem Projekt verwenden wir einen Leistungsverstärker-Lautsprecher, um Musik abzuspielen. Dieser Lautsprecher kann nicht nur einfache Lieder wiedergeben, sondern auch das ausführen, was Sie wünschen. Somit können Sie im Projekt weitere interessante Codes programmieren, um hervorragende Lernergebnisse zu erzielen.

**2. Funktionsprinzip**

![](media/A89.png)

Das elektrische Signal wird an Pin 1 von RP1 eingespeist (regelt die Signalstärke, was auch die Lautstärke des Tons ist).  
Nach der Kopplung in C4 und dem Durchlaufen von R5 erreicht das Signal den IN- Pin des 8002B, wo es operativ verstärkt und an den BEE1 Lautsprecher ausgegeben wird.

**3. Schaltplan**

![](media/A90.png)

**4. Testcode**

![](media/A91.png)

**5. Testergebnis**

Nach dem Hochladen des Codes und dem Einschalten spielt der Verstärker zyklisch Musiknoten mit den entsprechenden Frequenzen: DO, Re, Mi, Fa, So, La, Si.

**6. Wissensvertiefung**

Lassen Sie uns ein Geburtstagslied abspielen. Wir haben bereits einige Lieder in der Bibliothek hinzugefügt, sodass Sie diese Musikblöcke direkt aus „Music“ ziehen können.

**Code:**

![](media/A92.png)

**7. Codeerklärung**

1. Stellen Sie die Tonfrequenz ein. Nach der Einstellung des Pins können wir die Frequenz auswählen, um Musik zu komponieren.

![](media/A93.png)

2. Musikmodul: Zur Vereinfachung haben wir 6 Musikstücke im Code integriert, somit müssen wir nur den Pin einstellen und die Musik auswählen.

![](media/A94.png)

3. Stop-Modul: Wir müssen nur den entsprechenden Pin einstellen, um die Musik zu stoppen.

![](media/A95.png)