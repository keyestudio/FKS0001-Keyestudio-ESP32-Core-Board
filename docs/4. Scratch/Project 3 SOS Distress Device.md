### Project 3 SOS Noodapparaat

**1. Beschrijving**

Het SOS-apparaat kan noodsignalen uitzenden, wat overeenkomt met het principe van de Morse-code. Het is handig voor noodgevallen.

**2. Aansluitschema**

![](media/A36.png)

**3. Testcode**

Wat we eerst moeten verduidelijken is hoe het SOS-noodlicht knippert: de LED knippert snel 3 keer voor “S” en langzaam 3 keer voor “O”.

Vervolgens regelen we het aantal knipperingen en de duur via de "for" lus en stellen we de intervaltijd tussen letters in.

1. Sleep de twee codeblokken.

![](media/A37.png)

2. Sleep het volgende blok uit het onderdeel "Pins" en stel de IO5 pin in als output.

![](media/A38.png)

**Letter "S"**

3. Sleep het volgende blok uit het onderdeel "Control" en stel het in op 3 keer, omdat "S" betekent 3 keer knipperen.

![](media/A39.png)

4. Sleep de volgende blokken uit het onderdeel "LED" en zet de IO5 pin op HIGH. Stel daarna de vertraging in op 0,15s.

![](media/A40.png)

5. Sleep de volgende blokken uit het onderdeel "LED" en zet de IO5 pin op LOW. Stel daarna de vertraging in op 0,1s.

![](media/A41.png)

**Letter O**

6. Volg de vorige stappen om de volgende codeblokken te maken. Pas de HIGH-uitgang aan naar een vertraging van 0,4s en LOW naar 0,2s.

![](media/A42.png)

**Letter S**

7. Voer stap 3, 4 en 5 opnieuw uit.

![](media/A43.png)

8. Voeg aan het einde een vertraging van 5s toe, en "SOS" zal elke 5s herhalen.

   ![](media/A44.png)

**Volledige code：**

![](media/A45.png)

**4. Testresultaat**

Na het uploaden van de code knippert de LED respectievelijk 3 keer snel en langzaam.