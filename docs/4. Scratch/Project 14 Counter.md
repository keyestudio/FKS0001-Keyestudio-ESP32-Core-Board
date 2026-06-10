### Project 14 Teller

**1. Beschrijving**

De Arduino 4-bit digitale buisteller kan getallen binnen 0~9999 registreren. Het beschikt over aanpasbare weergavesnelheid, telmodus en resetfunctie. Deze module wordt veel toegepast in realtime tellers (zoals het tellen van knopdrukken en DC-motorrotaties), gaming en experimentele apparatuur.

**2. Stroomschema**

![](media/A172.png)

**3. Aansluitschema**

![](media/A173.png)

**4. Testcode**

1. Sleep de twee basisblokken.

![](media/A174.png)

2. Stel de knop-pin in op “input”.

![](media/A175.png)

3. Voeg een "variabele" blok toe. Stel het variabeltype in op int en noem het item. Wijs 0 toe als beginwaarde.

![](media/A176.png)

4. Sleep een "if" blok uit “Control” (dit wordt alleen uitgevoerd als de voorwaarde waar is). Plaats een “Button pressed” blok uit “Button” in het voorwaardenvakje (de zeshoek) en stel de pin in op IO19. Sleep een "variable mode" blok en plaats dit na "then", definieer het als "item" en zet de modus op "++".

![](media/A177.png)

5. Herhaal stap 4, maar stel de interface in op IO18 en de modus op "– –".

![](media/A178.png)

6. Sleep nog een "if" blok uit “Control” en definieer de voorwaarde als "interface IO17 button was be pushed?". Plaats een variabele-instelblok na "then" en zet de "variabele op 0".

![](media/A179.png)

7. Sleep een "if" blok uit “Control”. Zoek het "＞" blok in “Operators” en vul het linker vak met "variable item" en het rechter met "9999". Plaats ook een variabele-instelblok na "then" en zet de "variabele op 0".

![](media/A180.png)

8. Sleep een "TM1650 display" blok uit "Digital tube" en stel de weergegeven string in op het "variable item" blok. Vergeet tot slot niet een vertraging van 0,2s toe te voegen.

![](media/A181.png)

**Volledige code:**

![](media/A182.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, druk op de groene knop om met 1 te verhogen, geel om met 1 te verlagen en rood om te resetten.

**6. Code-uitleg**

Het **">"** blok wordt gebruikt om een vergelijking tussen twee waarden te maken. Deze twee velden kunnen worden ingevuld met getallen of variabelen.

![](media/A183.png)