### Projekt 15 Responder

**1. Beschreibung**

Dieser programmierbare Responder empfängt Signale über ein Arduino-Entwicklungsboard und eine Gruppe von Tasten und bewertet die Richtigkeit der Antworten über eine LED. Er ist ein gutes Objekt, um die Reaktionsfähigkeit der Schüler zu trainieren und ihre Aufmerksamkeit auf Fragen zu lenken. Wenn die Antwort richtig ist, erhält der Teilnehmer viele Punkte.

Außerdem vereinfacht er die Handhabung von Antwortgebern für Lehrer und reduziert Antwortchaos. Er kann sogar das Interesse der Schüler am Lernen fördern.

**2. Flussdiagramm**

![](media/A184.png)

**3. Schaltplan**

![](media/A185.png)

**4. Testcode**

1. Ziehen Sie die zwei Basisblöcke und setzen Sie einen „Variable“-Block dazwischen. Stellen Sie den Variablentyp auf int und den Namen auf item mit einer Anfangszuweisung von 0 ein. Setzen Sie den LED-Pin auf „output“ und den Tasten-Pin auf „input“.

![](media/A186.png)

2. Fügen Sie einen „LED output“-Block hinzu, definieren Sie den Pin als IO27 und setzen Sie die Ausgabe auf HIGH.  
3. Ziehen Sie einen „if“-Block und fügen Sie die Bedingung „interface IO19 button was be pushed?“ hinzu.

![](media/A187.png)

4. Fügen Sie eine Variablenzuweisung und vier LED-Ausgabeblöcke unter „then“ hinzu. Dabei benennen wir die Variable „item“ mit der Zuweisung „0“ und setzen alle Ausgänge an den Pins 12, 13, 14 und 27 jeweils auf LOW (Der Responder funktioniert nur, wenn alle LEDs aus sind). Vergessen Sie auch nicht eine Verzögerung von 0,2 s.

![](media/A188.png)

5. Fügen Sie einen „repeat until“-Block hinzu und setzen Sie „until“ auf „item = 1“, wie unten gezeigt. Wenn item = 1 ist, wird die Schleife verlassen.

![](media/A189.png)

6. Ziehen Sie einen weiteren „if“-Block und setzen Sie die Bedingung „Interface IO16 button was be pushed?“. Fügen Sie unter „then“ einen „LED output“-Block hinzu und setzen Sie die Ausgabe auf HIGH am Pin IO12. Fügen Sie außerdem eine „set item variable by 1“-Anweisung hinzu, um diesen Bedingungsblock zu verlassen.

![](media/A190.png)

7. Wiederholen Sie Schritt 6, setzen Sie jedoch das Interface auf IO17 und den LED-Pin auf IO13.

![](media/A191.png)

8. Führen Sie Schritt 6 erneut aus, setzen Sie das Interface auf IO18 und den LED-Pin auf IO14.

![](media/A192.png)

**Vollständiger Code:**

![](media/A193.png)

**5. Testergebnis**

Verbinden Sie die Verkabelung und laden Sie den Code hoch. Die Antworten der Teilnehmer sind nur gültig, wenn die rote LED aus ist (rote Taste gedrückt).

Wenn jemand seine Taste (gelb, grün oder blau) drückt, leuchtet die entsprechende LED sowie die rote Gegen-LED auf. Bis dahin können die übrigen LEDs beim Drücken der Tasten nicht eingeschaltet werden. Die Antwortaktion kann nur ausgeführt werden, wenn die rote Taste erneut gedrückt wird.

**6. Code-Erklärung**

1. Bedingungsschleifenmodul. Wenn die Bedingungen im Rautenfeld des Moduls erfüllt sind, wird die Schleife verlassen.

![](media/A194.png)

2. Der „=“-Block wird verwendet, um zu prüfen, ob zwei Werte gleich sind.

![](media/A195.png)