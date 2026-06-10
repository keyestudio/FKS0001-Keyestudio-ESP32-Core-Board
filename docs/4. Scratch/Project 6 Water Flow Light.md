### Project 6 Waterstroom Licht

**1. Beschrijving**

Dit eenvoudige waterstroom lichtproject helpt je bij het leren van elektronische verpakking. In dit project zullen we LEDs aansturen om de kleur te veranderen met een bepaalde snelheid via een Arduino board.

**2. Bedradingsschema**

![](media/A74.png)

**3. Testcode**

Een waterstroom licht bestaat uit een stroom van LED-verlichting van links naar rechts.

1. Sleep de twee basis codeblokken.

![](media/A75.png)

2. Stel de pinmodus in op “output”.

![](media/A76.png)

3. Sleep de volgende blokken uit het "LED" gedeelte en zet de IO15 pin op LOW, de IO12 pin op HIGH. Stel vervolgens de vertragingstijd in op 0,2s.

![](media/A77.png)

4. Sleep de volgende blokken uit het "LED" gedeelte en zet de IO12 pin op LOW, de IO13 pin op HIGH. Stel vervolgens de vertragingstijd in op 0,2s.

![](media/A78.png)

5. Sleep de volgende blokken uit het "LED" gedeelte en zet de IO13 pin op LOW, de IO14 pin op HIGH. Stel vervolgens de vertragingstijd in op 0,2s.

![](media/A79.png)

6. Sleep de volgende blokken uit het "LED" gedeelte en zet de IO14 pin op LOW, de IO15 pin op HIGH. Stel vervolgens de vertragingstijd in op 0,2s.

   ![](media/A80.png)

**Volledige code：**

![](media/A81.png)

**4. Testresultaat**

Na het uploaden van de code en het inschakelen, lichten de LEDs op van links naar rechts.