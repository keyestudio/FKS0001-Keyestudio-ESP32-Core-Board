### Project 22 Geluidsmeter

**1. Beschrijving**

De Arduino geluidsmeter zet het geluidssignaal om in een reeks stippen, die worden omgezet in patronen weergegeven op een dotmatrix.

**2. Aansluitschema**

![](media/B63.png)

**3. Testcode**

1. Sleep de basisblokken en initialiseer het display. Stel de pin CS in op IO15 en de helderheid op 3. Voeg vervolgens een variabeleblok toe, selecteer int en noem deze "item" met een initiële waarde van 0.

2. Voeg een variabeleblok toe en noem deze "item". Gebruik een map-functie om de gelezen geluidswaarde van het bereik 0-4095 om te zetten naar 0-7, waarbij de veronderstelde maximale geluidswaarde 800 is.

![](media/B64.png)

3. Maak het display leeg.

4. Programmeer een voorwaarde. Als de variabele item groter is dan -1, toont de dotmatrix (x0:0  y0:0 x1:1  y1:0) in de kleur rood.

![](media/B65.png)

5. Herhaal stap 4, maar controleer of item groter is dan 0. Zo ja, dan lichten de stippen op (x0:1  y0:0  x1:1  y1:1). Op dezelfde manier bouw je codeblokken op met de volgende coördinaten als referentie.

6. Vernieuw tenslotte het display.

**Referentiecoördinaten:**

![](media/B66.png)

![](media/B67.png)

**Volledige code:**

![](media/B68.png)

**4. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code wordt het geluidsniveau weergegeven op de dotmatrix, zoals hieronder te zien is.

![](media/B69.png)![](media/B70.png)![](media/B69.png)![](media/B70.png)