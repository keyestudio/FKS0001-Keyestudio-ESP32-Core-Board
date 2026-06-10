### Project 1 LED Knipperen

**1. Beschrijving**

LED knipperen is een eenvoudig project ontworpen voor beginners. Je hoeft alleen een LED op de Arduino board te installeren en de code te uploaden via de Arduino IDE. Dit project versterkt het begrip van het Arduino conceptuele kader en het gebruik van methoden voor beginners.

**2. Werking**

![](media/A7.png)

**LED:** Over het algemeen kan de beperkte uitgangsstroom van IO-poorten zorgen voor een lage helderheid van de LED, daarom wordt een NPN-transistor (Q2) in het circuit gebruikt als schakelaar. In dit geval zal de LED oplichten als de basis(pin 1) van de transistor op een hoog niveau staat. Omgekeerd gaat de LED uit wanneer de basis laag is.

**Transistor schakelaar:** Kort gezegd, de LED licht op wanneer de basis(pin 1) op een hoog niveau staat. Tegelijkertijd zijn de collector(pin 3) en emitter(pin 2) verbonden, en vervolgens gaat VCC via een stroombegrenzende weerstand naar de LED en uiteindelijk naar GND, wat een circuit vormt. Omgekeerd gaat de LED uit wanneer de basis laag is. In dit geval zijn de collector en emitter niet verbonden en gaat de LED uit.

**3. Aansluitschema**

![](media/A8.png)

**4. Testcode**

Volgens de bovenstaande principes kunnen we de LED aansturen via de niveaus van de pinnen op de ontwikkelboard.

1. Sleep het volgende blok in het onderdeel "Events".

![](media/A9.png)

2. Sleep het volgende blok in het onderdeel "Control".

![](media/A10.png)

3. Sleep het volgende blok in het onderdeel "Pins" en stel de IO5 pin in als output.

   ![](media/A11.png)

4. Sleep het volgende blok in het onderdeel "LED" en stel de IO5 pin in op HIGH.

![](media/A12.png)

5. Sleep het volgende blok in het onderdeel "Control".

![](media/A13.png)

6. Sleep de volgende blokken en stel de IO5 pin in op LOW.

![](media/A14.png)

**Volledige code：**

![](media/A15.png)

**5. Testresultaat**

Na het uploaden van de code en het inschakelen van de voeding zal de LED 1 seconde aan zijn en 1 seconde uit.

**6. Code-uitleg**

<p style="color:red;">Opmerking: De pinmodus moet worden ingesteld op "output" bij gebruik van de LED-module.<p>

1. Codeblokken worden niet uitgevoerd als het volgende blok niet aanwezig is.

![](media/A16.png)

2. Codeblokken in het volgende blok worden in een lus uitgevoerd.

![](media/A17.png)

3. Dit is een module die wordt gebruikt om de pinmodus in te stellen (voor het aansturen van LED en buzzer op “output” modus, en het uitlezen van sensormodules op “input”).

![](media/A18.png)

4. Dit is een module die wordt gebruikt om de pin en de niveaus ("HIGH" en "LOW") in te stellen.

![](media/A19.png)

5. Dit is een module die wordt gebruikt om de vertragingstijd in te stellen.

![](media/A20.png)