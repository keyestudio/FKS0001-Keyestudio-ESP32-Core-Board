### Project 13 Mini Lamp

**1. Beschrijving**

In dit project gaan we een lamp bedienen via Arduino UNO en een knop. Wanneer we de knop indrukken, verandert de status van de lamp (AAN of UIT).

**2. Werkingsprincipe**

![](media/A152.png)

Wanneer de knop losgelaten wordt, zorgt een spanning VCC die door R29 loopt voor een hoog niveau op de S-terminal. Wanneer ingedrukt, worden pin 1 en 3, pin 2 en 4 verbonden en komt de spanning op S1 op GND als een laag niveau. Op dat moment voorkomt R29 een kortsluiting tussen VCC en GND.

**3. Aansluitschema**

![](media/A153.png)

**4. Testcode**

1. Voeg twee basisblokken toe.

![](media/A154.png)

2. Sleep een "baud rate" uit “Serial” en stel deze in op 9600.

![](media/A155.png)

3. Sleep vervolgens een "print" blok uit “Serial”, typ “Key status:” in het lege veld en stel het in op "no-warp".

![](media/A156.png)

4. Stel de IO15 pin in op “input”.

![](media/A157.png)

5. Sleep nog een “Serial print” blok uit “Serial” en stel de modus in op "warp". Voeg een "state value of button" toe uit “Button” en stel de pin in op IO15.

![](media/A158.png)

**Volledige code:**

![](media/A159.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600.  
Wanneer we de knop indrukken, print de seriële poort "Key status: 0"; wanneer we de knop loslaten, print de seriële poort "Key status: 1".

![](media/A160.png)

**6. Kennisuitbreiding**

Vervolgens gaan we de LED aansturen via de status van de knoppen.

**Stroomschema:**

![](media/A161.png)

**Aansluitschema:**

![](media/A162.png)

**Code:**

1. Sleep twee basisblokken.

![](media/A163.png)

2. Stel de LED-pin in op “output” en de knop-pin op “input”.

![](media/A164.png)

3. Sleep een "if else" blok uit “Control”. Voeg een "button pin" blok toe uit “Button” na "if" en stel de pin in op IO15. Plaats een "LED output" blok onder "if" en stel de output in op HIGH, en plaats een ander onder "else" en stel deze in op LOW. Beide LED-pinnen zijn IO4.

![](media/A165.png)

**Volledige code:**

![](media/A166.png)

**8. Code-uitleg**

**Opmerking: Pin-modus moet op "input" worden gezet bij gebruik van de knopmodule.**

1. Controleer of de knop is ingedrukt. Zo ja, dan geeft dit blok true terug.

![](media/A167.png)

2. Lees de knopwaarde uit. Wanneer de knop niet is ingedrukt, is de waarde 1. Anders is deze 0.

![](media/A168.png)

3. Als de voorwaarde in het zeshoekige blok waar is, wordt het "if" blok uitgevoerd. Anders draait het programma het "else" blok.

![](media/A169.png)

4. Stel de baudrate in. Zorg ervoor dat de seriële baudrate overeenkomt met die van de seriële monitor, anders wordt er niets geprint. De meest gebruikte baudrates zijn 9600 en 115200, hier stellen we 9600 in.

![](media/A170.png)

5. Print tekens op de seriële monitor. De geprinte tekst is wat je in het lege veld typt. Daarnaast zijn er drie printmodi: warp, no-warp en HEX (hexadecimaal).

![](media/A171.png)