### Project 2 Ademend LED

**1. Beschrijving**

Arduino ademend LED maakt gebruik van on-board programmeerbare PWM om een analoge golfvorm uit te voeren. Na het inschakelen kan de helderheid van de LED worden aangepast via de duty cycle van de golfvorm om uiteindelijk het effect van een ademend LED te realiseren.

Op deze manier kan omgevingslicht worden gesimuleerd door de helderheid van de LED in de tijd te veranderen. Ook kan een ademend LED een kleurrijk mini-licht vormen om een rustige en warme sfeer te creëren.

**2. Wat is PWM?**

PWM bestuurt analoge output via digitale middelen, waarmee de duty cycle van de golf (een signaal dat cyclisch wisselt tussen hoog niveau en laag niveau) kan worden aangepast.

Voor Arduino zijn digitale poorten met spanningsuitgang LOW en HIGH, die respectievelijk overeenkomen met 0V en 5V. Over het algemeen definiëren we LOW als 0 en HIGH als 1. Arduino zal binnen 1s 500 signalen van 0 of 1 uitsturen. Als ze "1" zijn, wordt 5V uitgegeven. Omgekeerd, als ze allemaal 0 zijn, is de uitgang 0V. Of als ze 010101010101... zijn, is de gemiddelde uitgang 2,5V.

Met andere woorden, de verhouding van 0 en 1 in de output beïnvloedt de spanningswaarde; hoe meer 0- en 1-signalen per tijdseenheid worden uitgegeven, hoe nauwkeuriger de regeling zal zijn.

![](media/A21.png)

**3. Aansluitschema**

![](media/A22.png)

**4. Testcode**

We gebruiken een "for"-lus om een variabele te verhogen van 0 tot 255, en definiëren deze variabele als PWM-uitgang (analogWrite(pin, value)). Tussen haakjes kan een vertragingstijd de controle van de LED-verlichtingstijd versterken. Vervolgens gebruiken we een andere "for"-lus om de variabele te verlagen van 255 tot 0 met een vertragingstijd om het dimproces van de LED te regelen.

1. Sleep de twee codeblokken.

![](media/A23.png)

2. Sleep het volgende blok uit het onderdeel "Variabelen" en definieer de naam als "item" met een initiële waarde "0". Plaats dit blok in het "voor altijd" blok.

![](media/A24.png)

3. Sleep het volgende blok uit het onderdeel "Besturing" en stel het in op 255 keer, wat de maximale waarde van PWM is.

![](media/A25.png)

4. Sleep het volgende blok uit het onderdeel "Variabelen", zet "item" als het te wijzigen object en stel de modus in op "++".

![](media/A26.png)

5. Sleep het volgende blok uit het onderdeel “LED” en stel de LED-pin in op IO5. Voeg vervolgens een "variabele" blok toe en vul deze met "item".

![](media/A27.png)

6. Sleep het volgende blok uit het onderdeel "Besturing" en stel de tijd in op 0,01s, dat is 10ms.

![](media/A28.png)

7. Bouw volgens de vorige stappen een ander codeblok met als enige verschil de variabele modus "– –".

![](media/A29.png)

**Volledige code:**

![](media/A30.png)

**5. Testresultaat**

Na het uploaden van de code zien we dat de LED geleidelijk dimt. Hij "ademt" gelijkmatig.

**6. Code-uitleg**

1. Dit blok wordt gebruikt om het bruikbare bereik van de variabele, het variabeltype, de naam en de initiële waarde in te stellen.

![](media/A31.png)

2. Het aantal herhalingen kan worden ingevuld in het lege veld van dit herhaalblok.

![](media/A32.png)

3. Voer een variabelenaam in het lege veld in en de waarde wordt bij elke uitvoering met 1 verhoogd. "++" kan worden gewijzigd in "– –".

![](media/A33.png)

4. Voer een variabelenaam in het lege veld in en de waarde wordt bij elke uitvoering met 1 verlaagd. "– –" kan worden gewijzigd in "++".

![](media/A34.png)

5. Dit is een PWM-uitgangsmoduul, en het witte vak is de waarde van de uitgevoerde PWM.

![](media/A35.png)