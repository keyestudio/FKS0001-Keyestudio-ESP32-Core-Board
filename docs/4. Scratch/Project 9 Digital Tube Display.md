### Project 9 Digitale Buizen Display

**1. Beschrijving**

Deze 4-cijferige buisdisplay is een apparaat dat wordt gebruikt om tellingen of tijd weer te geven, en kan cijfers van 0 ~ 9 en eenvoudige letters tonen. Het bestaat uit vier digitale buizen, elk met zeven lichtgevende diodes (LED).

Bovendien kunnen meerdere functies worden gerealiseerd door hun pinnen aan te sluiten op de Arduino ontwikkelbord, zoals tijdregistratie en sommige spelopslag.

**2. Werkingsprincipe**

![](media/A96.png)

TM1650 maakt gebruik van het IIC-protocol en gebruikt twee buslijnen (SDA en SCL).

De code wordt geleverd in onze blokken, en de digitale buis zal nummers weergeven via deze code.

**3. Aansluitschema**

![](media/A97.png)

**4. Testcode**

Om nummers op het display te tonen, hoef je alleen maar een "TM 1650 display" blok uit "Digitale buis" te slepen en de nummerreeks in te stellen op 9999.

![](media/A98.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, toont het digitale buisdisplay "9999", zoals hieronder weergegeven.

![](media/A99.png)

**6. Uitgebreide Code**

Laten we wat moeilijkere bewerkingen doen. In plaats van statische nummers, laten we het dynamische nummers tonen.

De volgende code bestuurt de buizen om 1~9999 weer te geven.

1. Sleep de twee basiscodeblokken.

![](media/A100.png)

2. Sleep het volgende blok uit "Variabelen". Stel het type in op int en de naam op item, en wijs 0 toe als beginwaarde.

![](media/A101.png)

3. Sleep het volgende blok uit "Besturing" en stel het in op 9999 keer.

![](media/A102.png)

4. Sleep een "variabele modus" uit "Variabelen", definieer de naam als item en stel de modus in op "++".

5. Sleep een "TM 1650 display" blok uit "Digitale buis" en vervang de stringwaarde door variabele item. Voeg er een vertraging van 0,5s aan toe.

![](media/A103.png)

6. Voeg een "stel variabele in" blok toe na het "herhaal" blok. Stel de item variabele in op 0. Anders zal de item waarde buiten het displaybereik vallen na 9999 herhalingen.

![](media/A104.png)

**Volledige Code：**

![](media/A105.png)

**7. Code Uitleg**

1. Stel de displaystring in. Typ direct de nummers of letters die je wilt weergeven in het lege veld.

![](media/A106.png)

2. Stel de AAN of UIT status van deze TM 1650 digitale buis in. Elke buis kan afzonderlijk worden bestuurd.

![](media/A107.png)

3. Het is mogelijk om het display te wissen of te gebruiken als een hoofdschakelaar om de digitale buis aan of uit te zetten.

![](media/A108.png)