### Projekt 6 Wasserflusslicht

**1. Beschreibung**

Dieses einfache Wasserflusslicht-Projekt hilft Ihnen, die elektronische Verpackung zu erlernen. In diesem Projekt steuern wir LEDs, um die Farbe mit einer bestimmten Geschwindigkeit über ein Arduino-Board zu ändern.

**2. Schaltplan**

![](media/A74.png)

**3. Testcode**

Ein Wasserflusslicht besteht aus einem LED-Lichtstrom von links nach rechts.

1. Ziehen Sie die beiden grundlegenden Codeblöcke.

![](media/A75.png)

2. Stellen Sie den Pin-Modus auf „output“ ein.

![](media/A76.png)

3. Ziehen Sie die folgenden Blöcke aus dem Bereich „LED“ und setzen Sie den IO15-Pin auf LOW, den IO12-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 0,2 s ein.

![](media/A77.png)

4. Ziehen Sie die folgenden Blöcke aus dem Bereich „LED“ und setzen Sie den IO12-Pin auf LOW, den IO13-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 0,2 s ein.

![](media/A78.png)

5. Ziehen Sie die folgenden Blöcke aus dem Bereich „LED“ und setzen Sie den IO13-Pin auf LOW, den IO14-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 0,2 s ein.

![](media/A79.png)

6. Ziehen Sie die folgenden Blöcke aus dem Bereich „LED“ und setzen Sie den IO14-Pin auf LOW, den IO15-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 0,2 s ein.

   ![](media/A80.png)

**Vollständiger Code：**

![](media/A81.png)

**4. Testergebnis**

Nach dem Hochladen des Codes und dem Einschalten leuchten die LEDs von links nach rechts auf.