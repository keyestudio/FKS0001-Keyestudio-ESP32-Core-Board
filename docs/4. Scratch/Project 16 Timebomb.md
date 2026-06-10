### Project 16 Timebomb

**1. Beschrijving**

Dit project geeft je de mogelijkheid om een interessant timebomb-spel te ervaren.

In dit project stelt de dot matrix je timebomb voor, terwijl de digitale buis de resterende tijd weergeeft. Knoppen kunnen niet alleen de bom bedienen, maar ook de tijd instellen. Je kunt een aftelling instellen om deze bom te regelen, en hij ontploft wanneer de aftelling voorbij is. Daarnaast wordt een buzzer gebruikt als alarm.

Hoe dan ook, door te programmeren met meerdere sensoren kan je algehele vermogen tot logisch denken worden verbeterd.

**2. Stroomschema**

![](media/B1.png)

**3. Aansluitschema**

![](media/B2.png)

**4. Testcode**

1. Sleep de twee basisblokken.

![](media/B3.png)

2. Stel de knop-pin in op “input”.

![](media/B4.png)

3. Voeg een "init matrix display" blok toe uit "Matrix" en stel de pin CS in op IO15. Daarna volgt een "brightness" blok met de waarde 3 en een "variable" blok (stel het variabeltype in op int en de naam op item, wijs 0 toe als beginwaarde).

![](media/B5.png)

4. Sleep in "Matrix" een "fill color" blok en selecteer "black" (d.w.z. alle LED’s uit om de vorige weergave te wissen). Voeg een "display image" toe om een glimlachend gezicht te definiëren. Plaats vervolgens een refresh-blok om het display te vernieuwen.

![](media/B6.png)

5. Sleep een "if" blok en vul het conditievak met "interface IO33 button was be pushed?". Voeg na "then" een "variable mode" blok toe en stel de naam in op item en de modus op "++".

![](media/B7.png)

6. Herhaal de handeling van stap 5, maar stel de interface in op IO32 en de modus op "--".

![](media/B8.png)

7. Sleep een "if" blok om te controleren of pin IO26 is ingedrukt. In deze "if" voegen we een repeat-blok toe en stellen de voorwaarde in op "item" = 0.

In de "repeat until" lus plaats je een "variable mode" en stel je "item" in op "--", zoals hieronder weergegeven. Sleep een "TM1650 display" blok uit "Digital tube" en definieer de weergegeven string als "variable item" blok. Voeg daarna een "buzzer output" blok toe en stel de output in op HIGH op pin IO27 gevolgd door een vertraging van 0,5s. Herhaal de laatste procedure maar stel de output in op LOW.

![](media/B9.png)

8. Programmeer een andere lus en definieer de voorwaarde als "interface IO25 button was be pushed?". De volgende uitvoeringen vinden in deze lus plaats. Plaats een "TM1650 display" blok en definieer de weergegeven string als "variable item" blok. Herhaal vervolgens stap 4, maar stel hier het beeld in op een huilend gezicht.

![](media/B10.png)

9. Sleep een "if then" blok en vul het lege veld met de voorwaarde: item ＞ 9999. Voeg in dit conditieblok de instructie toe "set item variable by 0".

![](media/B11.png)

10. Sleep een "TM1650 display" uit "Digital tube" en definieer de weergegeven string als "variable item". Vergeet ook niet een vertraging van 0,2s toe te voegen.

![](media/B12.png)

**Volledige code:**

![](media/B13.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, druk je op de blauwe knop om tijd toe te voegen, groen om te verminderen en rood om te resetten. Druk op de gele knop om af te tellen. Wanneer de tijd om is, ontploft de bom.