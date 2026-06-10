### Projekt 23 Smart Cup

**1. Beschreibung**

In diesem Projekt verwenden wir hauptsächlich das Arduino-Entwicklungsboard, um einen programmierbaren Smart Cup zu erstellen, der die Temperatur der inneren Flüssigkeit über eine RGB-Anzeige anzeigt. Die Helligkeit des Lichts kann durch das Einstellen eines Temperaturschwellenwerts gesteuert werden. Wird der Schwellenwert überschritten, wird das Licht heller. Andernfalls wird es dunkler.

Der Smart Cup hilft den Benutzern, die Temperatur ihres Trinkwassers besser zu kontrollieren und effektiv Überhitzung oder Einfrieren zu verhindern.

**2. Funktionsprinzip**

![](media/B71.png)

Die zugehörigen Einstellungen im DHT11 werden vom Hersteller bereitgestellt, sodass Sie nur die Daten gemäß dem Sequenzdiagramm nacheinander lesen und verarbeiten müssen.

Außerdem sind die relevanten Codes in unseren Bibliotheken verpackt, was es Ihnen erleichtert, Pins einzustellen und Werte auszulesen.

**3. Schaltplan**

![](media/B72.png)

**4. Testcode**

1. Ziehen Sie zwei Basisblöcke. Fügen Sie das Modul für die serielle Baudrate hinzu und setzen Sie die Baudrate auf 9600.

2. Ziehen Sie das DHT-Modul aus „Temperatur und Luftfeuchtigkeit“ und setzen Sie den Pin auf IO26, den Modus auf dht11.

![](media/B73.png)

3. Fügen Sie das Modul für serielle Ausgabe ohne Zeilenumbruch hinzu und setzen Sie die Ausgabe auf „RH:“, dann folgen Sie den untenstehenden Schritten und fügen eine Verzögerung von 1s hinzu.

**Vollständiger Code:**

![](media/B74.png)

**5. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes klicken Sie auf ![](media/B75.png), um den seriellen Monitor zu öffnen, stellen die Baudrate auf 9600 ein, und die Temperatur- und Luftfeuchtigkeitswerte werden angezeigt.

![](media/B76.png)

**6. Erweiterungscode**

In diesem Erweiterungsexperiment erstellen wir einen Smart Cup, der die Flüssigkeitstemperatur anzeigen kann. Wir teilen 100 in vier Bereiche auf, wobei jede LED einen Bereich repräsentiert:

- **Rote LED:** 100-75°C

- **Gelbe LED:** 75-50°C

- **Grüne LED:** 50-25°C

- **Blaue LED:** 25-0°C

- **Flussdiagramm：**

![](media/B77.png)

**Schaltplan：**

![](media/B78.png)

**Code：**

1. Ziehen Sie zwei Basisblöcke. Stellen Sie dann die 4 LED-Pins auf „output“, den DHT11-Pin auf IO26, den Modus auf dht11 und den Variablennamen auf temp ein.

![](media/B79.png)

2. Weisen Sie den Temperaturwert des DHT11 der Variablen temp zu.

![](media/B80.png)

3. Verwenden Sie „if else“, um die Variable temp zu prüfen. Wenn die Bedingungen erfüllt sind, wird die entsprechende LED eingeschaltet, andernfalls ausgeschaltet.

**Vollständiger Code:**

![](media/B81.png)

**7. Codeerklärung**

1. In diesem Codeblock kann die markierte Zahl in das Feld eingetragen werden, sodass mehrere Temperatur- und Luftfeuchtigkeitssensoren angeschlossen werden können. Nach dem Einstellen von Pin und Modus kann der Wert ausgelesen werden. In diesem Projekt setzen wir den Modus auf DHT11.

![](media/B82.png)

2. Codeblock zum Auslesen von Temperatur und Luftfeuchtigkeit.

![](media/B83.png)