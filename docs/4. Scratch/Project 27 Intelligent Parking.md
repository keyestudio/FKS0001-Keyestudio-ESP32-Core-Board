### Project 27 Intelligent Parkeren

**1. Beschrijving**

Dit intelligente parkeersysteem detecteert en optimaliseert de parkeerpositie via een ultrasone sensor. Met dit systeem wordt verkeerd parkeren in grote mate voorkomen.

Allereerst moet je de sensor rondom de parkeerplaats installeren. Vervolgens detecteert deze de afstand tussen de auto en de randen en stuurt de informatie naar de ontwikkelkaart om de auto automatisch naar de optimale parkeerpositie te laten aanpassen.

**2. Stroomschema**

![](media/B104.png)

**3. Aansluitschema**

![](media/B105.png)

**4. Testcode**

Ken de gedetecteerde afstandswaarde toe aan een variabele en bepaal of deze groter is dan de ingestelde drempelwaarde. Zo ja, lichten de corresponderende lijnen op de dotmatrix op. Op deze manier kan een afstand worden weergegeven door lijnen te verlichten.

**Referentiecoördinaten:**

![](media/B106.png)

**Volledige code:**

![](media/B107.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, worden lijnen weergegeven op de dotmatrix. Als de gedetecteerde afstand minder is dan 50 cm, zijn er minder lijnen zichtbaar.

![](media/B108.png)![](media/B109.png)