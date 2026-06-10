### Project 19  Dimmen van Lamp

**1. Beschrijving**

De dimlamp past de helderheid van een LED aan via een potentiometer en een Arduino-controller. De helderheid is afhankelijk van de weerstandwaarde, die kan worden uitgelezen en aangepast door de uiteinden van de potentiometer te verbinden met digitale of analoge pinnen op het bord.  
Bovendien wordt dit systeem toegepast om de spanning of stroom van andere apparaten zoals ventilatoren, lampen en verwarmers te regelen.

**2. Werking**

![](media/B32.png)

In wezen is een potentiometer een element dat de waarde van de weerstand kan veranderen. Volgens de wet van Ohm (U=I*R) beïnvloedt de weerstand de spanning. Onze potentiometer is 10K.

In dit project is de maximale weerstand 10K. Het ESP32-bord verdeelt de spanning van 3V gelijkmatig in 4095 delen (3/4095=0.0007326007326). De analoge spanning wordt verkregen door de uitgelezen waarde te vermenigvuldigen met 0.0007326007326.

**3. Aansluitschema**

![](media/B33.png)

**4. Testcode**

De analoge waarde van de potentiometer kan worden uitgelezen:

1. Sleep de twee basisblokken. Plaats het blok voor het instellen van de baudrate ertussen en stel deze in op 9600.

2. Voeg een "serial print" blok toe in de "forever" lus en selecteer "warp" als printmodus.

3. Sleep een "lees de waarde" blok van “pot” naar de serial print en stel de pin in op IO33.

![](media/B34.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor, stel je de baudrate in op 9600 en wordt de analoge waarde weergegeven binnen het bereik van 0-4095.

![](media/B35.png)

**6. Uitbreidingscode**

We gaan de helderheid van de LED regelen via een potentiometer. Zoals we weten, wordt dit beïnvloed door PWM. De range van de analoge waarde is echter 0-4095, terwijl die van PWM 0-255 is. Daarom is een "map(value, fromLow, fromHigh, toLow, toHigh)" functie nodig.

**Aansluitschema：**

![](media/B36.png)

1. Sleep de twee basisblokken.  
2. Voeg een variabeleblok toe en stel deze in als lokaal. Selecteer "int" als type en noem het "pot".

![](media/B37.png)

3. Sleep een "map" functie van “Data” en plaats deze op de toewijzingspositie. Stel de waarde van "map" in op "lees de waarde van pot IO33", met het bereik van (0,4095) naar (0,255).

![](media/B38.png)

4. Voeg tenslotte een "LED analogWrite" blok toe. Stel de pin in op IO25 en de analoge waarde op de variabele "pot".

![](media/B39.png)

**Volledige code:**

![](media/B40.png)

**7. Code-uitleg**

1. **map** functie. Het bereik van de analoge waarde kan worden omgezet van 0-4095 naar 0-255.

![](media/B41.png)

2. Lees de analoge waarde van de potentiometer door de pin in te stellen.

![](media/B42.png)