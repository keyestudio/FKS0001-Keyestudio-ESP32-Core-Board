### Project 9 Digitale Buizen Display

**1. Beschrijving**

Deze 4-cijferige buisdisplay is een apparaat dat wordt gebruikt om tellingen of tijd weer te geven, en kan cijfers van 0 ~ 9 en eenvoudige letters tonen. Het bestaat uit vier digitale buizen, elk met zeven lichtgevende diodes (LED).

Bovendien kunnen meerdere functies worden gerealiseerd door hun pinnen aan te sluiten op de Arduino ontwikkelbord, zoals tijdregistratie en het opslaan van enkele spellen.

**2. Werking**

![](media/A33.png)

TM1650 maakt gebruik van het IIC-protocol en gebruikt twee buslijnen (SDA en SCL).

**Data Commando:** 0x48.  
Dit commando vertelt de TM1650 om de digitale buizen te verlichten in plaats van toetsen te scannen.

**Display Commando:**

![](media/A34.png)

In feite is het één byte data waarbij verschillende bits verschillende functies vertegenwoordigen.  
**bit[6:4]:** Stel de helderheid van de LED in. Let op dat 000 de helderste stand aangeeft.  
**bit[3]:** Bepaalt of er een decimale punt is.  
**bit[0]:** Bepaalt of het display aan moet staan.

**Digitale Buis Aan**  
Een voorbeeld: Helderheid niveau 8 zonder punt betekent 0x05.  
Stappen: Startsignaal — Verstuur 0x48 — Slave-apparaat ontvangt — Verstuur 0x05 — Slave-apparaat ontvangt — Eindsignaal  
Na het inschakelen hoeft 0x48 niet herhaaldelijk te worden verzonden, omdat de functie van de digitale buis bevestigd is.  
Daarnaast kunnen helderheid en weergavemethoden met meerdere data op één plek worden opgesomd, zodat het overzichtelijk en ruimtebesparend is.

**Digitale Buis Uit**  
Stappen: Startsignaal — Verstuur 0x48 — Slave-apparaat ontvangt — Verstuur 0x00 — Slave-apparaat ontvangt — Eindsignaal

**Digitale Buis Toont Cijfers**  
We vertellen eerst de TM1650 om cijfers op de vooraf bepaalde buis weer te geven. Daarna wordt het cijfer getoond. De acht bits corresponderen met acht segmenten, waarbij 1 betekent aan en 0 uit. Als er twijfel is over de corresponderende relatie, kunt u bit voor bit in een lus aanzetten.

Bijvoorbeeld, wanneer bit 1 aan is en 8 toont, is de data 0x68. Als er een punt is, wordt 8 ook weergegeven bij het verzenden van 0x7f.  
Stappen: Startsignaal — Verstuur 0x68 — Slave-apparaat ontvangt — Verstuur 0x7f — Slave-apparaat ontvangt — Eindsignaal  
Resultaat: 8 wordt weergegeven op Bit 1.

Voor het gemak kan een array worden gemaakt met corresponderende waarden voor 0~9. Na verdere verbetering kan het cijfers weergeven, helderheid aanpassen, de decimale punt verschuiven en buizen bedienen.

**3. Aansluitschema**

![](media/A35.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.1 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
    DigitalTube.displayFloatNum(9999);   //Values or variables added to the parentheses can be displayed through the digital tube 
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, toont de digitale buisdisplay "9999", zoals hieronder weergegeven.

![](media/A36.png)

**6. Uitgebreide Code**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.2 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  for(int num=0; num<10000; num++)
  {   //Als num minder is dan 10000, wordt num met 1 verhoogd per cyclus
    DigitalTube.displayFloatNum(num);   //Waarden of variabelen in de haakjes kunnen via de digitale buis worden weergegeven
    delay(100);
  }
}
```

**7. Testresultaat**

Na het uploaden van de code toont de digitale buis de cijfers 1~9999 via een "for" lus.