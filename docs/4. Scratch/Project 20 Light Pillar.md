### Project 20 Lichtzuil

**1. Beschrijving**

De weerstand (minder dan 1KΩ) van de fotoweerstand varieert met het licht, waardoor het de helderheid van de dotmatrix kan regelen. Bij het aansturen verbinden we deze weerstand met een analoge pin op de board om de verandering in weerstand te monitoren. Op deze manier regelt het licht automatisch de helderheid van het display.

Daarnaast wordt de fotoweerstand veel toegepast in ons dagelijks leven. Bijvoorbeeld, een gordijn dat automatisch opent of sluit afhankelijk van de lichtintensiteit buiten.

**2. Werking**

![](media/B43.png)

Wanneer het volledig donker is, is de weerstand gelijk aan 0.2MΩ en nadert de spanning op het signaalknooppunt (punt 2) 0V. Hoe sterker het licht, hoe kleiner de weerstand en spanning zullen zijn.

**3. Aansluitschema**

![](media/B44.png)

**4. Testcode**

De analoge waarde van de fotoweerstand kan worden uitgelezen:

1. Sleep de twee basisblokken. Plaats het baudrate-instelblok ertussen en stel deze in op 9600.

2. Voeg een "serial print" blok toe in de "forever" lus met de modus "warp".

3. Sleep een "lees de waarde" blok van “Light” naar het "serial print" blok en stel de pin in op IO33.

![](media/B45.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De analoge waarde wordt weergegeven binnen het bereik van 0-4095.

![](media/B46.png)

**6. Uitbreidingscode**

In dit uitbreidingsproject gebruiken we de fotoweerstand om de omgevingslichtintensiteit te meten. De middelste twee kolommen zijn opgenomen in dit experiment om de lichtintensiteit weer te geven. Hoe lichter het is, hoe meer LED's oplichten. Dit vormt een "lichtzuil".

**Aansluitschema:**

![](media/B47.png)

1. Sleep de twee basisblokken.

2. Initialiseer in "Matrix" het dotmatrixdisplay en stel pin CS in op IO15. Voeg een "helderheid instellen" blok toe en stel deze in op 3.

![](media/B48.png)

3. Sleep een "variabele" blok. Stel het bereik in op Local, het type op int en de naam op light.

![](media/B49.png)

4. Ken een map-functie toe aan de variabele. Voeg "lees de waarde van light IO33" van "Light" toe aan de waarde van de map-functie, met bereik van (0,4095) naar (0,7).

![](media/B50.png)

5. Zoek de volgende blokken in "Matrix". Maak eerst het display leeg, en teken vervolgens lijnen op het display bij de punten (x0:3  y0:0, x1:3  y1: variabele light) en (x0:4  y0:0, x1:4  y1: variabele light). Vernieuw tenslotte het matrixdisplay.

![](media/B51.png)

**Volledige code:**

![](media/B52.png)

**7. Code-uitleg**

Lees de analoge waarde van de fotoweerstand uit door de pin in te stellen.

![](media/B53.png)