### Project 11 LCD

**1. Beschrijving**

Arduino I2C 1602 LCD is een veelgebruikt hulpprogramma voor MCU-ontwikkelborden om verbinding te maken met externe sensoren en modules. Het beschikt over een 16-bits brede tekenset, een 2-regelig LCD-scherm en instelbare helderheid. Deze programmeerbare module is handig voor het bewerken, weergeven en beheren van gegevens. Daarnaast kan het niet alleen tekens en cijfers weergeven, maar ook sensorwaarden, zoals temperatuur, vochtigheid of drukwaarden.

Vanwege de bruikbaarheid wordt het display veel toegepast in verschillende gebieden, waaronder slimme thuisproducten, industriële monitorsystemen, robotbesturingssystemen en automotive elektronicasystemen.

**2. Werking**

![](media/A44.png)

Het werkt volgens hetzelfde principe als IIC-communicatie. Onderliggende functies zijn verpakt in bibliotheken zodat je ze direct kunt aanroepen. Als je hierin geïnteresseerd bent, kun je de onderliggende stuurprincipes verder bestuderen.

**3. Aansluitschema**

![](media/A45.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 11 LCD
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); // set the LCD address to 0x27 for a 16 chars and 2 line display

void setup()
{
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();		//Turn on the LCD backlight 
    lcd.setCursor(2,0);		//Set the display position 
    lcd.print("Hello,world!");		//LCD displays "Hello, world!"
    lcd.setCursor(2,1);	
    lcd.print("keyestudio!");		//LCD displays "keyestudio!"
}

void loop()
{
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, zet je het LCD aan. "Hello, world!" en "keyestudio!" worden op het LCD weergegeven.

![](media/A46.png)

Als de tekens onduidelijk zijn, stel dan de backlight-potentiometer af met een kleine schroevendraaier met sleuf (gebruik gepaste kracht bij het afstellen). Sluit indien nodig een externe voeding aan.

![](media/A47.png)

![](media/A48.png)