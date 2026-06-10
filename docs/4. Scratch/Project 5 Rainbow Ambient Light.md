### Project 5 Regenboog Sfeerverlichting

**1. Beschrijving**

2812RGB LED is een programmeerbare kleurrijke dromerige lamp, waarvan kleur, helderheid en ritme verstelbaar zijn. Deze regenboog sfeerverlichting kan naar wens worden gebruikt als dynamische decoratie. Of je kunt het laten "dansen met muziek". Belangrijk is dat het kan worden verbeterd als alarm. De ingebouwde sensor detecteert de omgeving om gebruikers te waarschuwen door de kleur, helderheid en het ritme te veranderen.

**2. Werking**

![](media/A53.png)

Het dataprotocol gebruikt een communicatiemodus van enkelvoudige lijn return-to-zero code. Nadat de pixel is gereset bij inschakeling, ontvangt de DIN-terminal data van de controller. De eerst binnenkomende 24bit data wordt door de eerste pixel uitgelezen en naar het interne dataregister gestuurd.

De resterende data wordt versterkt door een versterkingscircuit en via de DOUT-poort doorgestuurd naar de volgende gekoppelde pixel.  
Tijdens het doorgeven via pixels neemt het signaal elke keer met 24bit af.

Daarnaast gebruikt de pixel automatische vormgeving en doorstuurtechnologie, waardoor het aantal gekoppelde pixels alleen wordt beperkt door de signaaltransmissiesnelheid.

**3. Aansluitschema**

![](media/A54.png)

**4. Testcode**

Laten we leren hoe we de 2812 RGB kunnen aansteken en de kleuren kunnen instellen.

1. Sleep de twee codeblokken.

![](media/A55.png)

2. Sleep het volgende blok uit het onderdeel "RGB LED" en stel de pin in op IO15 en het aantal LED's op 6.

![](media/A56.png)

3. Sleep het volgende blok uit het onderdeel "RGB LED" en stel de helderheid in op 20.

![](media/A57.png)

4. Sleep de volgende blokken en stel het aantal LED's in op 0, 1, 2, 3, 4 en 5, kies vervolgens rood, groen, blauw, geel, paars en wit als kleuren.

![](media/A58.png)

5. Voeg het volgende blok toe.

![](media/A59.png)

**Volledige code:**

![](media/A60.png)

**5. Testresultaat**

Na het uploaden van de code, het aansluiten van de bedrading en het inschakelen, zullen de LED's oplichten in verschillende kleuren, zoals hieronder weergegeven:

![](media/A61.png)

**6. Kennisuitbreiding**

In dit uitbreidingsproject maken we een mini lichtshow!

Nest vier "herhaal" blokken en voeg een "variabele +" toe in elk, en zet de corresponderende variabelen aan het einde van elke lus terug naar 0.

![](media/A62.png)

Plaats de bovenstaande drie variabelen in het "RGB" blok zodat deze kleurwaarden worden aangestuurd. Voeg daarna een verfrissingsmodule toe.

![](media/A63.png)

Plaats de RGB in een "toon kleur" blok om kleuren weer te geven. Definieer ook een variabele item om de weergegeven LED te regelen.

![](media/A64.png)

De "voor altijd" module wordt gebruikt om de RGB LED's te besturen, die zullen cyclus van 0-5 om geleidelijk elke lamp aan te steken.

![](media/A65.png)

**Volledige code**

![](media/A66.png)

**7. Code-uitleg**

1. Stel het aantal 2812 RGB in. Een ontwikkelbord pin kan meerdere 2812 RGB LED's aansturen, dus we moeten het aantal vooraf instellen en de aangesloten pin selecteren.

![](media/A67.png)

2. Stel de helderheid van 2812 RGB in. Voer een helderheidswaarde in tussen 0-255, waarbij 255 het helderst is.

![](media/A68.png)

3. Dit blok schakelt alle 2812 RGB's uit.

![](media/A69.png)

4. Bestuur de weergave van 2812 RGB's. We kunnen de velden invullen om de aan te steken LED en de kleur te regelen nadat de pin is geselecteerd. Bijvoorbeeld, "0 tot 0" betekent dat alleen de eerste LED oplicht. Na het uploaden van de code zal de eerste LED in de ingestelde kleur aan gaan.

**OPMERKING:** De twee velden kunnen ook met variabelen worden ingevuld, zodat een lichtshow kan worden gevormd.

![](media/A70.png)

5. Stel de kleur van 2812 RGB's in. De weergegeven kleur kan worden aangepast door de waarden van rood, groen en blauw. We kunnen dit blok toevoegen in de kleurinstellingen van 2812 RGB.

![](media/A71.png)

6. Hiermee kan een enkele 2812 RGB worden aangestuurd door het nummer van de LED in te voeren en de kleur te selecteren.

![](media/A72.png)

7. De 2812 RGB toont de ingestelde kleur pas na verversen.

![](media/A73.png)