### Projekt 7 Aktiver Summer

**1. Beschreibung**

Ein aktiver Summer ist eine Komponente, die als Alarm, Erinnerung oder Unterhaltungsgerät verwendet wird und einen zuverlässigen Ton erzeugt.

Darüber hinaus ermöglicht er die Erzeugung hochgradig kontrollierbarer Töne, wodurch unsere Projekte interessanter werden.

**2. Funktionsprinzip**

![](media/A82.png)

Ein aktiver Summer integriert einen Multivibrator, daher erzeugt er nur bei Gleichspannung Ton. Pin 1 des Summers ist mit VCC verbunden und Pin 2 wird von einem Triod gesteuert. Wenn für die Basis (Pin 1) des Triods ein hoher Pegel anliegt, verbinden sich Kollektor (Pin 3) und Emitter (Pin 2) mit GND, und der Summer gibt einen Ton von sich.

Umgekehrt, wenn wir der Basis einen niedrigen Pegel geben, werden die übrigen Pins getrennt, sodass der Summer still bleibt.

**3. Schaltplan**

![](media/A83.png)

**4. Testcode**

Wenn das Entwicklungsboard einen hohen Pegel ausgibt, gibt der Summer einen Ton von sich. Wenn es einen niedrigen Pegel ausgibt, hört der Summer auf zu klingeln.

1. Ziehen Sie die beiden grundlegenden Codeblöcke.

![](media/A84.png)

2. Ziehen Sie die folgenden Blöcke aus dem Bereich „Buzzer“ und setzen Sie den IO5-Pin auf HIGH. Stellen Sie dann die Verzögerungszeit auf 1s ein.

![](media/A85.png)

3. Ziehen Sie die folgenden Blöcke aus dem Bereich „Buzzer“ und setzen Sie den IO5-Pin auf LOW. Stellen Sie dann die Verzögerungszeit auf 1s ein.

![](media/A86.png)

**Vollständiger Code：**

![](media/A87.png)

**5. Testergebnis**

Nach dem Hochladen des Codes und dem Einschalten gibt der Summer 1s lang einen Ton von sich und bleibt 1s still.

**6. Codeerklärung**

Buzzer-Ausgabeblock. Zuerst definieren wir den Pin als IO5 und setzen dann die Ausgabe auf „HIGH“ oder „LOW“. Der Summer piept bei HIGH, während er bei LOW still bleibt.

![](media/A88.png)