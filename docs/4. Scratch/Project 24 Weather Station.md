### Project 24 Weerstation

**1. Beschrijving**

Dit weerstation registreert de omgevings-temperatuur en vochtigheidswaarde via een Arduino board en een temperatuur- en vochtigheidssensor.

Bovendien maakt het mogelijk om temperatuur- en vochtigheidswaarden aan te passen op basis van omgevingsparameters om zo comfortabele omgevingscondities te bereiken.

**2. Aansluitschema**

![](media/B84.png)

**3. Testcode**

1. Voeg twee basismodules toe. Initialiseer de LCD 1602 en zet de achtergrondverlichting van de LCD 1602 AAN (vergeet niet de LCD aan te zetten). Stel de pin van dht in op IO26 en de modus op dht11. Stel twee int-variabelen in, “RH“ en “temp“, op 0.

![](media/B85.png)

2. Wijs de vochtigheidswaarde toe aan de variabele RH, en de temperatuurwaarde aan de variabele temp.

![](media/B86.png)

3. Stel de LCD-weergavepositie in op x: 0 en y: 0. Voeg de lcd-weergavemodule toe en stel het weergegeven teken in op "humidity:". Voeg de lcd-weergavemodule opnieuw toe en voeg de variabele RH toe aan het witte vak.

![](media/B87.png)

4. Herhaal stap 3, maar stel y in op 1 en het weergegeven teken op “temperature:”, en voeg de variabele temp toe aan het witte vak.

![](media/B88.png)

**Volledige code:**

![](media/B89.png)

**4. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, zal het LCD-scherm direct de omgevingsvochtigheid en temperatuurwaarde weergeven.

![](media/B90.png)