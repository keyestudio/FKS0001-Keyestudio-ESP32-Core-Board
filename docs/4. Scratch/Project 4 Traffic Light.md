### Project 4 Verkeerslicht

**1. Beschrijving**

De verkeerslichtmodule is een apparaat dat wordt gebruikt om de route van voetgangers en voertuigen te regelen. Het bevat een rood, geel en groen licht, die verschillende instructies impliceren.

**Rood voor Stop:** Voetgangers en voertuigen stoppen met doorgaan.

**Geel voor Voorzichtigheid:** Voetgangers en voertuigen maken zich klaar om te stoppen. Als het rijden al bezig is, moet de snelheid laag zijn.

**Groen voor Doorgaan:** Voetgangers en voertuigen gaan door met inachtneming van de verkeersregels.

In dit project kun je Arduino gebruiken om code te schrijven om verkeerslichten te bedienen. Bijvoorbeeld, stel de duur van elk licht en de intervaltijd ertussen in. Daarnaast kun je ook een timer toevoegen om de lichtkleuren volgens een schema te wijzigen.

**2. Aansluitschema**

![](media/A46.png)

**3. Testcode**

We simuleren eenvoudig de verkeerslichten: het groene LED licht gaat 5s aan, het gele LED knippert 3 keer, en het rode LED gaat 5s aan. En we stellen dit in om te herhalen.

Het knipperen van het gele LED kan gebruikmaken van de for()-statement die we in project 3 hebben genoemd. Dus hoeven we alleen de verlichtingstijd in te stellen om een verkeerslichtcyclus te voltooien.

1. Sleep de twee codeblokken.

![](media/A47.png)

2. Stel de pinmodus in op “output”

![](media/A48.png)

3. Sleep de volgende blokken uit het "LED"-gedeelte en stel de IO27 pin in op HIGH en daarna LOW. Stel vervolgens de vertragingstijd in op 5s.

![](media/A49.png)

4. Sleep de volgende blokken uit het "Control"-gedeelte en stel het aantal herhalingen in op 3, stel dan de IO26 pin in op HIGH en daarna LOW. Stel de vertragingstijd in op 0,5s.

![](media/A50.png)

5. Herhaal stap 3, en stel de pin in op IO25.

![](media/A51.png)

**Volledige code：**

![](media/A52.png)

**4. Testresultaat**

Na het uploaden van de code zal het groene LED 5s branden, het gele LED 3 keer knipperen, en het rode LED 5s aan zijn.