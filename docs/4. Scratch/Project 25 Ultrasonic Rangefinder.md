### Project 25 Ultrasone Afstandsmeter

**1. Beschrijving**

Deze ultrasone afstandsmeter meet de afstand van obstakels door geluidsgolven uit te zenden en vervolgens de echo te ontvangen. Met andere woorden, de afstand is geen directe waarde, maar een waargenomen waarde door een theoretische berekening van het tijdsverschil tussen zender en ontvanger.

Ultrasoon kan de vorm van objecten detecteren, automatische deuren aansturen en de stroomsnelheid en druk inschatten.

Bovendien ondersteunt het samenwerking met computers. Hierdoor kan de gemeten waarde via een Arduino-board naar computers worden verzonden.

In het dagelijks leven wordt het veel gebruikt voor motoren, servo’s en LED’s evenals systemen (automatische navigatie-, controle- en beveiligingsmonitoringsystemen).

**2. Werkingsprincipe**

![](media/B91.png)

Zoals we allemaal weten, is ultrasoon een soort onhoorbare geluidsgolf met een hoge frequentie. Vergelijkbaar met een vleermuis meet deze module de afstand van obstakels door het tijdsverschil te berekenen tussen het uitzenden van de golf en het ontvangen van de echo.

- **Maximale afstand:** 3M

- **Minimale afstand:** 5cm

- **Detectiehoek:** ≤15°

**3. Aansluitschema**

![](media/B92.png)

**4. Testcode**

In het "forever" blok, bouw twee "serial print" blokken en sleep een "read distance" blok uit “Ultrasonic”. Stel de trig pin in op IO13 en de echo pin op IO14, beide in cm. Vergeet niet een vertraging van 0,5s toe te voegen.

![](media/B93.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De seriële poort begint dan de afstandswaarde te printen.

![](media/B94.png)

**6. Kennisuitbreiding**

Laten we een afstandsmeter maken.

We tonen tekens op een LCD 1602. Programmeer om "Keyestudio" te tonen op (3,0) en “distance:” op (0,1) gevolgd door de afstandswaarde op (9,1).

Wanneer de waarde kleiner is dan 100 (of 10), blijft er een rest van het derde (of het tweede) cijfer zichtbaar. Daarom is een "if" controle nodig om een bepaalde conditie te bepalen.

**Aansluitschema：**

![](media/B95.png)

**Code：**

1. Sleep de twee basisblokken.

2. Initialiseer in "LCD" het LCD. Sleep een “LCD print” blok en voeg de tekenreeks “Keyestudio” toe (dit kan ook buiten het "forever" blok geplaatst worden omdat deze weergave vast is). Voeg een "variable" blok toe, stel het type in op int en noem het "distance" met een initiële waarde van 0.

![](media/B96.png)

3. Ken de gelezen afstandswaarde toe aan de variabele "distance". Stel het LCD in om “Distance：” te printen gevolgd door de afstandswaarde (en we moeten de eerder weergegeven tekens vooraf berekenen om de cursor erachter te plaatsen).

![](media/B97.png)

4. Bouw een "clear display residue" blok wanneer het aantal weergegeven cijfers afneemt. We gebruiken eerst een conditie om te controleren of de afstand kleiner is dan 100 (of 10). Als dat zo is, wordt er een spatie geprint op de rest van het derde (of tweede) cijfer om de vorige weergave te wissen. Vergeet tot slot niet een vertraging van 0,5s toe te voegen.

![](media/B98.png)

**Volledige code:**

![](media/B99.png)

**7. Code-uitleg**

Lees de afstand uit nadat de trig pin en echo pin zijn ingesteld. De eenheid van de weergegeven waarde is optioneel (cm of inch).

![](media/B100.png)