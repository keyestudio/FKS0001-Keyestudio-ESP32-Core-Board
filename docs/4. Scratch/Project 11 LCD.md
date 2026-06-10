### Project 11 LCD

**1. Beschrijving**

Arduino I2C 1602 LCD is een veelgebruikt hulpprogramma voor MCU-ontwikkelborden om verbinding te maken met externe sensoren en modules. Het beschikt over een 16-bits brede tekenset, een 2-regelig LCD-scherm en instelbare helderheid. Deze programmeerbare module is handig voor het bewerken, weergeven en beheren van gegevens. Daarnaast kan het niet alleen tekens en cijfers weergeven, maar ook sensorwaarden, zoals temperatuur, vochtigheid of drukwaarde.

Vanwege de bruikbaarheid wordt het display veel toegepast in diverse gebieden, waaronder slimme thuisproducten, industriële monitorsystemen, robotbesturingssystemen en automotive elektronicasystemen.

**2. Werking**

![](media/A129.png)

Het werkt volgens hetzelfde principe als IIC-communicatie. Onderliggende functies zijn verpakt in bibliotheken zodat je ze direct kunt aanroepen. Als je hierin geïnteresseerd bent, kun je de onderliggende stuurprincipes verder bestuderen.

**3. Aansluitschema**

![](media/A130.png)

**4. Testcode**

1. Sleep de twee basiscodeblokken.

![](media/A131.png)

2. Sleep het blok “init LCD” uit “LCD” en stel het I2C-adres in op 0x27.

![](media/A132.png)

3. Sleep het blok "LCD back light" en zet deze op AAN. Tekens zijn moeilijk leesbaar zonder achtergrondverlichting.

![](media/A133.png)

4. Sleep een "LCD cursor position" blok en stel x in op 3 en y op 0. Voeg een "LCD print" blok toe en typ “keyestudio” in het lege veld.

![](media/A134.png)

5. Sleep een "LCD cursor position" en stel x in op 2 en y op 1. Voeg een "LCD print" toe en typ “Hello,world!” in het lege veld.

![](media/A135.png)

**Volledige code：**

![](media/A136.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, zet het LCD aan en “Hello, world!” en “keyestudio!” worden op het LCD weergegeven.

Als de tekens onduidelijk zijn, stel dan de achtergrondverlichtingspotentiometer af met een kleine sleufschroevendraaier.

![](media/A137.png)

**6. Code-uitleg**

1. Stel het IIC-communicatieadres in. In dit project is het adres van LCD 1602 0x27.

![](media/A138.png)

2. Bedien de achtergrondverlichting van het LCD. De weergegeven tekens zijn veel duidelijker te zien als de achtergrondverlichting aan staat.

![](media/A139.png)

3. Stel de cursorpositie in. Dit geeft een nauwkeurige positie via de x- en y-as. Mogelijke waarden zijn X: 0-15 en Y: 0-1.

![](media/A140.png)

4. Print tekens op het LCD. Het lege veld kan worden gevuld met tekens of variabelen, wat handig is voor het weergeven van waarden van sensoren en modules.

![](media/A141.png)

5. Laat de cursor knipperen op de weergavepositie. Standaard is de cursor inactief.

![](media/A142.png)