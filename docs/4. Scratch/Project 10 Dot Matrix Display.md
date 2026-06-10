### Project 10 Dot Matrix Display

**1. Beschrijving**

Deze module bestaat uit een 8x8 LED dot matrix met één besturingspin voor elke rij en kolom om de helderheid van de LED aan te passen. Door verbinding te maken met een Arduino board, wordt de helderheid van de LED geregeld om karakters en figuren weer te geven via Arduino-programmering. Op deze manier kunnen eenvoudige karakters, cijfers en figuren worden weergegeven. Het kan ook worden toegepast in spelmachines of schermen.

![](media/A109.png)

MAX7219 is een IC met SPI-communicatie en kan worden gebruikt om de 8x8 dot matrix te besturen. De MAX7219 SPI-communicatie is geïntegreerd in onze bibliotheken en kan direct worden aangeroepen.

**2. Aansluitschema**

![](media/A110.png)

**3. Testcode**

1. Sleep de twee basis codeblokken.

![](media/A111.png)

2. Sleep een "init matrix display" uit “Matrix” en stel CS in op IO15. DIN en CLK zijn respectievelijk vaste pinnen op IO23 en IO18.

![](media/A112.png)

3. Sleep een "set brightness" blok en stel deze in op 3.

![](media/A113.png)

4. Sleep een "image" blok en kies het hart-icoon.

![](media/A114.png)

5. Voeg aan het einde een "refresh" blok toe.

![](media/A115.png)

**Volledige code：**

![](media/A116.png)

**4. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, wordt er een hart weergegeven op de dot matrix, zoals hieronder getoond.

![](media/A117.png)

**5. Code-uitleg**

1. Stel de CS-pin in. In de code is DIN vastgezet op io23 en SLK op io18, terwijl de CS-pin optioneel is. Voor gemakkelijke bedrading kiezen we io15.

![](media/A118.png)

2. Teken pixels. Dit codeblok schakelt pixels op de dot matrix aan of uit via de x- en y-as, met rood voor aan en zwart voor uit.

![](media/A119.png)

3. Teken lijn. Plaats de lijn met twee groepen coördinaten, ook met rood voor aan en zwart voor uit.

![](media/A120.png)

4. Toon karakters. We hebben karakterbibliotheken toegevoegd, dus je hoeft alleen een letter te typen om deze op de dot matrix weer te geven. Daarnaast moet het in combinatie met een "rotation 180°" blok worden gebruikt.

![](media/A121.png)

5. Toon cijfers. Op dezelfde manier hoef je alleen een cijfer te typen om het op de dot matrix weer te geven, en ook dit moet in combinatie met een "rotation 180°" blok worden gebruikt.

![](media/A122.png)

6. Toon scrollende tekenreeksen. In combinatie met een "rotation 180°" blok worden de opgegeven scrollende tekenreeksen weergegeven na het instellen van de snelheid.

![](media/A123.png)

7. Toon afbeelding. Voor het gemak hebben we enkele emotie-iconen geïntegreerd die direct geselecteerd kunnen worden.

![](media/A124.png)

8. Toon vulkleuren. Je kunt instellen op zwart (LED uit) of rood (LED aan).

![](media/A125.png)

9. Vernieuw het display. De dot matrix moet worden ververst als er iets wordt weergegeven. Anders kan er een fout optreden.

![](media/A126.png)

10. Stel de helderheid in. Je kunt de helderheid verlagen tijdens het debuggen om je ogen te sparen.

![](media/A127.png)

11. Stel rotatiehoeken in. Voor hoge compatibiliteit met meer code moeten sommige data en iconen worden geroteerd om een omgekeerde weergave te voorkomen. Daarom is een "rotation 180°" blok noodzakelijk in de code.

![](media/A128.png)