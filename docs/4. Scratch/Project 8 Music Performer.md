### Project 8 Muziekuitvoerder

**1. Beschrijving**

In dit project gebruiken we een versterkerluidspreker om muziek af te spelen. Deze luidspreker kan niet alleen eenvoudige liedjes afspelen, maar ook uitvoeren wat jij wilt. Zo kun je andere interessante codes in het project programmeren om schitterende leerresultaten te bereiken.

**2. Werking**

![](media/A89.png)

Het elektrische signaal wordt ingevoerd vanaf pin 1 van RP1 (regelt de signaalsterkte, wat ook het geluidsvolume is).  
Na koppeling in C4 en het passeren van R5 bereikt het signaal de IN- pin van 8002B, waar het operationeel wordt versterkt en naar de BEE1 luidspreker wordt uitgegeven.

**3. Aansluitschema**

![](media/A90.png)

**4. Testcode**

![](media/A91.png)

**5. Testresultaat**

Na het uploaden van de code en het inschakelen speelt de versterker cirkelvormig muziektonen af met de bijbehorende frequenties: DO, Re, Mi, Fa, So, La, Si.

**6. Kennisuitbreiding**

Laten we het een verjaardagsliedje laten spelen. We hebben al enkele liedjes toegevoegd in de bibliotheek, zodat je deze muziekblokken direct uit "Music" kunt slepen.

**Code:**

![](media/A92.png)

**7. Code-uitleg**

1. Stel de toonfrequentie in. Na het instellen van de pin kunnen we de frequentie selecteren om muziek te componeren.

![](media/A93.png)

2. Muziekmodule, voor gebruiksgemak hebben we 6 muziekstukken geïntegreerd in de code, dus hoeven we alleen de pin in te stellen en de muziek te selecteren.

![](media/A94.png)

3. Stop-module, we hoeven alleen de corresponderende pin in te stellen om de muziek te stoppen.

![](media/A95.png)