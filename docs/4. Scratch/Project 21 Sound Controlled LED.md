### Project 21 Geluidsgestuurde LED

**1. Beschrijving**

Een geluidsgestuurde LED is een apparaat dat geluid detecteert om daarmee de helderheid van een LED te regelen. Het bestaat uit een Arduino-board en enkele componenten. Het kan worden aangesloten op meerdere sensoren zoals microfoons. Het zet geluid om in een veranderend spanningssignaal dat door de Arduino wordt ontvangen om de LED aan en uit te schakelen.

**2. Werkingsprincipe**

![](media/B54.png)

Bij het detecteren van geluid trilt de elektretfilm in de microfoon, wat de capaciteit verandert en een subtiele spanningsverandering genereert.

Vervolgens gebruiken we de LM386-chip om een geschikte schakeling te bouwen die het gedetecteerde geluid tot 200 keer versterkt, wat kan worden aangepast met een potentiometer. Draai deze met de klok mee om de versterking te vergroten.

**3. Aansluitschema**

![](media/B55.png)

**4. Testcode**

Zoek het blok "lees de waarde" in “Sound” en print de gelezen geluidssignalen op de seriële poort. Stel de blokken als volgt samen. Let erop dat je geen vertraging toevoegt bij het gebruik van de geluidsensor.

![](media/B56.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De analoge waarde wordt weergegeven.

![](media/B57.png)

**6. Uitbreidingscode**

De veelvoorkomende gangverlichting is een soort geluidsgestuurde verlichting. Tegelijkertijd bevat deze ook een fotoweerstand.

Hier bouwen we een model waarbij een LED alleen door geluid wordt beïnvloed. Wanneer het analoge volume boven 100 komt, gaat de LED 2 seconden aan en daarna weer uit.

**Stroomschema:**

![](media/B58.png)

**Aansluitschema:**

![](media/B59.png)

**Code:**

1. Sleep twee basisblokken.

2. Sleep een "if else" blok en vul het zeshoekige veld met een item＞100 blok. Stel de waarde in op "lees de waarde van geluid IO33". Als de voorwaarde waar is, geeft de LED een HIGH-signaal op pin IO25 met een vertraging van 2 seconden; anders geeft hij een LOW-signaal op dezelfde pin zonder vertraging.

![](media/B60.png)

**Volledige code:**

![](media/B61.png)

**7. Code-uitleg**

Lees de waarde van geluid door de bijbehorende pin in te stellen.

![](media/B62.png)  
### Project 22 Geluidsmeter

**1. Beschrijving**

De Arduino geluidsmeter zet het geluidssignaal om in een reeks stippen, die worden weergegeven als patronen op een dotmatrix.

**2. Aansluitschema**

![](media/B63.png)

**3. Testcode**

1. Sleep de basisblokken en initialiseer het display. Stel de pin CS in op IO15 en de helderheid op 3. Voeg vervolgens een variabeleblok toe, selecteer int en noem deze "item" met een initiële waarde van 0.

2. Voeg een variabeleblok toe en noem deze "item". Gebruik een map-functie om de gelezen geluidswaarde van het bereik 0-4095 om te zetten naar 0-7, waarbij de veronderstelde maximale geluidswaarde 800 is.

![](media/B64.png)

3. Maak het display leeg.

4. Programmeer een voorwaarde. Als de variabele item groter is dan -1, toont de dotmatrix (x0:0  y0:0 x1:1  y1:0) in de kleur rood.

![](media/B65.png)

5. Herhaal stap 4, maar controleer of item groter is dan 0. Als dat zo is, lichten de stippen op (x0:1  y0:0  x1:1  y1:1). Bouw op dezelfde manier codeblokken op volgens de volgende coördinaten.

6. Vernieuw tenslotte het display.

**Referentiecoördinaten:**

![](media/B66.png)

![](media/B67.png)

**Volledige code:**

![](media/B68.png)

**4. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code wordt het geluidsniveau weergegeven op de dotmatrix, zoals hieronder te zien is.