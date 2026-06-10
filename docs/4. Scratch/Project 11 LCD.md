### Projekt 11 LCD

**1. Beschreibung**

Arduino I2C 1602 LCD ist ein häufig verwendetes Hilfsgerät für MCU-Entwicklungsboards zur Verbindung mit externen Sensoren und Modulen. Es verfügt über ein 16 Zeichen breites, 2-zeiliges LCD-Display und eine einstellbare Helligkeit. Dieses programmierbare Modul ist praktisch für die Datenbearbeitung, Anzeige und Verwaltung. Außerdem kann es nicht nur Zeichen und Zahlen, sondern auch Sensorwerte wie Temperatur, Luftfeuchtigkeit oder Druck anzeigen.

Aufgrund seiner Vielseitigkeit wird das Display in vielen Bereichen eingesetzt, darunter Smart-Home-Produkte, industrielle Überwachungssysteme, Robotersteuerungssysteme und Automobilelektroniksysteme.

**2. Funktionsprinzip**

![](media/A129.png)

Es basiert auf dem gleichen Prinzip wie die IIC-Kommunikation. Die zugrundeliegenden Funktionen sind in Bibliotheken verpackt, sodass Sie sie direkt aufrufen können. Wenn Sie daran interessiert sind, können Sie sich die zugrundeliegenden Treiberprinzipien näher ansehen.

**3. Schaltplan**

![](media/A130.png)

**4. Testcode**

1. Ziehen Sie die beiden grundlegenden Codeblöcke.

![](media/A131.png)

2. Ziehen Sie den Block „init LCD“ aus „LCD“ und setzen Sie die I2C-Adresse auf 0x27.

![](media/A132.png)

3. Ziehen Sie den Block „LCD back light“ und stellen Sie ihn auf ON. Ohne Hintergrundbeleuchtung sind die Zeichen schwer lesbar.

![](media/A133.png)

4. Ziehen Sie einen Block „LCD cursor position“ und setzen Sie x auf 3 und y auf 0. Fügen Sie einen „LCD print“-Block hinzu und geben Sie „keyestudio“ in das Feld ein.

![](media/A134.png)

5. Ziehen Sie einen weiteren „LCD cursor position“-Block und setzen Sie x auf 2 und y auf 1. Fügen Sie einen „LCD print“-Block hinzu und geben Sie „Hello,world!“ in das Feld ein.

![](media/A135.png)

**Vollständiger Code:**

![](media/A136.png)

**5. Testergebnis**

Nach dem Anschluss der Verkabelung und dem Hochladen des Codes schalten Sie das LCD ein, und „Hello, world!“ sowie „keyestudio!“ werden auf dem LCD angezeigt.

Wenn die Zeichen unscharf sind, justieren Sie bitte das Hintergrundbeleuchtungspotentiometer mit einem kleinen Schlitzschraubendreher.

![](media/A137.png)

**6. Codeerklärung**

1. Setzen Sie die IIC-Kommunikationsadresse. In diesem Projekt ist die Adresse des LCD 1602 0x27.

![](media/A138.png)

2. Steuern Sie die LCD-Hintergrundbeleuchtung. Die angezeigten Zeichen sind viel klarer sichtbar, wenn die Hintergrundbeleuchtung eingeschaltet ist.

![](media/A139.png)

3. Setzen Sie die Cursorposition. Diese wird genau über die Achsen x und y angegeben. Mögliche Werte sind X: 0-15 und Y: 0-1.

![](media/A140.png)

4. Drucken Sie Zeichen auf dem LCD. Das Feld kann mit Zeichen oder Variablen gefüllt werden, was praktisch ist, um Werte von Sensoren und Modulen anzuzeigen.

![](media/A141.png)

5. Lassen Sie den Cursor an der Anzeigeposition blinken. Standardmäßig ist der Cursor inaktiv.

![](media/A142.png)