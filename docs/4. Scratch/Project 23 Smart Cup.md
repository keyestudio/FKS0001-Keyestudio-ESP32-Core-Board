### Project 23 Slimme Beker

**1. Beschrijving**

In dit project gebruiken we voornamelijk het Arduino-ontwikkelbord om een programmeerbare slimme beker te maken, die de temperatuur van de binnenste vloeistof weergeeft via een RGB-indicator. De helderheid van het licht kan worden geregeld door een temperatuurgrens in te stellen. Als de drempel wordt overschreden, wordt het licht helderder. Anders wordt het donkerder.

De slimme beker helpt gebruikers beter de temperatuur van hun drinkwater te controleren en voorkomt effectief oververhitting of bevriezing.

**2. Werkingsprincipe**

![](media/B71.png)

De relevante instellingen voor de DHT11 worden door de fabrikanten geleverd, dus je hoeft alleen de data volgens het volgordediagram netjes uit te lezen en te verwerken.

Daarnaast zijn de bijbehorende codes verpakt in onze bibliotheken, wat het gemakkelijk maakt om pinnen in te stellen en waarden uit te lezen.

**3. Aansluitschema**

![](media/B72.png)

**4. Testcode**

1. Sleep twee basisblokken. Voeg het seriële baudrate-module toe en stel de baudrate in op 9600.

2. Sleep het DHT-module uit “Temperatuur en vochtigheid” en stel de pin in op IO26, modus op dht11.

![](media/B73.png)

3. Voeg een seriële printmodule toe zonder regelafbreking, stel de print in op “RH:”, volg daarna de onderstaande stappen en voeg een vertraging van 1s toe.

**Volledige code:**

![](media/B74.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, klik![](media/B75.png)om de seriële monitor te openen, stel de baudrate in op 9600, en de temperatuur- en vochtigheidswaarden worden weergegeven.

![](media/B76.png)

**6. Uitbreidingscode**

In dit uitbreidingsexperiment maken we een slimme beker die de vloeistoftemperatuur kan weergeven. We verdelen 100 in vier delen waarbij elke LED een deel vertegenwoordigt:

- **Rode LED:** 100-75°C

- **Gele LED:** 75-50°C

- **Groene LED:** 50-25°C

- **Blauwe LED:** 25-0°C

**Stroomschema:**

![](media/B77.png)

**Aansluitschema:**

![](media/B78.png)

**Code:**

1. Sleep twee basisblokken. Stel vervolgens de 4 LED-pinnen in op “output”, de DHT11-pin op IO26, modus op dht11 en de variabelenaam op temp.

![](media/B79.png)

2. Ken de temperatuurwaarde van DHT11 toe aan de variabele temp.

![](media/B80.png)

3. Gebruik "if else" om de variabele temp te beoordelen. Als aan de voorwaarden wordt voldaan, gaat de corresponderende LED aan, anders gaat deze uit.

**Volledige code:**

![](media/B81.png)

**7. Code-uitleg**

1. In dit codeblok kan het gemarkeerde nummer in het lege veld worden ingevuld zodat meerdere temperatuur- en vochtigheidssensoren kunnen worden aangesloten. Na het instellen van de pin en modus kan de waarde worden uitgelezen. In dit project stellen we de modus in op DHT11.

![](media/B82.png)

2. Codeblok voor het uitlezen van temperatuur en vochtigheid.

![](media/B83.png)