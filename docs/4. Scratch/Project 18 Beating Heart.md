### Project 18 Kloppend Hart

**1. Beschrijving**

In dit project wordt een kloppend hart weergegeven via een Arduino board, een 8X8 dot matrix display, een printplaat en enkele elektronische componenten. Door te programmeren kun je de klopsnelheid, de afmeting van het hart en de helderheid ervan regelen.

**2. Aansluitschema**

![](media/B24.png)

**3. Testcode**

1. Sleep de twee basisblokken.

2. Initialiseer het dot matrix display. Stel de CS-pin in op IO15 en de helderheid op 3. Plaats deze twee uitvoeringen tussen de basisblokken.

De volgende uitvoeringen bevinden zich allemaal in het "forever" blok.

3. Maak het display leeg. Laat het display lijnen tekenen en stel het coördinatensysteem en de oorsprong in zoals hieronder. Vernieuw daarna het display om het kleinere hart te tonen met een vertraging van 1s.

![](media/B25.png)

![](media/B26.png)

4. Herhaal stap 3 maar teken lijnen zoals op de onderstaande afbeelding om een groter hart te tonen.

![](media/B27.png)

![](media/B28.png)

**Volledige code:**

![](media/B29.png)

**4. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code worden de twee hartgroottes afwisselend weergegeven.

![](media/B30.png)![](media/B31.png)