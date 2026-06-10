### Project 17 Inbraakalarm

**1. Beschrijving**

Dit inbraakalarmsysteem kan indringers in huizen of kleine kantoren detecteren en de bewoner waarschuwen om tijdig maatregelen te nemen.

In dit project bewaakt de sensor een bepaald gebied. Een apparaat op de Arduino-board zal een LED laten oplichten en een buzzer laten piepen als er beweging wordt gedetecteerd in die zone. Bovendien is de gevoeligheid instelbaar voor een nauwkeurigere detectie.

In feite kenmerkt deze module zich door praktische bruikbaarheid, eenvoudige installatie en lage kosten. Naast thuis en kantoor is het ook toepasbaar in fabrieken, magazijnen en markten, wat in grote mate de eigendomsveiligheid beschermt.

**2. Werking**

![](media/B14.png)

Het menselijk lichaam (37°C) zendt altijd infraroodstraling uit met een golflengte van 10μm, wat ongeveer overeenkomt met die van de sensor.

Hierdoor kan deze module menselijke beweging detecteren. Als er beweging is, geeft de PIR-sensor ongeveer 3 seconden een hoog signaal en daarna een laag signaal.

**3. Aansluitschema**

![](media/B15.png)

**4. Testcode**

1. Voeg de twee basisblokken toe en sleep een "baud rate" blok van “Serial” ertussen. Stel de seriële baudrate in op 9600.

![](media/B16.png)

2. Voeg een "if else" blok toe. Plaats een "read PIR motion sensor" blok in het zeshoekige vak en stel de interface in op IO5, zodat het kan bepalen of er menselijke beweging is. Voeg twee "serial print" blokken toe na "then" en "else" en stel beide modi in op "warp". Als de voorwaarde waar is, print dan “Someone Invaded”. Anders print “No one”, en voeg daarna een vertraging van 1s toe.

![](media/B17.png)

**Volledige code:**

![](media/B18.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. Wanneer de sensor beweging detecteert, print de seriële poort "Someone Invaded", anders print het “No One”.

![](media/B19.png)

**6. Uitbreidingscode**

Laten we een inbraakalarm maken. Wanneer de PIR-sensor een mens detecteert, gaat de LED aan en geeft de buzzer geluid. Anders gaat de LED uit en blijft de buzzer stil.

**Stroomschema：**

![](media/B20.png)

**Aansluitschema：**

![](media/B21.png)

**Code：**

![](media/B22.png)

**7. Code-uitleg**

Wanneer de PIR menselijke bewegingen detecteert, geeft deze een hoog signaal. Daarom kunnen we bepalen of er beweging is door de pin van de ontwikkelboard die met deze sensor is verbonden uit te lezen.

![](media/B23.png)