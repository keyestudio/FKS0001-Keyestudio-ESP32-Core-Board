### Projekt 6 Wasserflusslicht

**1. Beschreibung**

Dieses einfache Wasserflusslicht-Projekt hilft Ihnen, die elektronische Verpackung zu erlernen. In diesem Projekt steuern wir LEDs, die die Farbe mit einer vorgegebenen Geschwindigkeit über ein Arduino-Board ändern.

**2. Schaltplan**

![](media/A25.png)

**3. Testcode**

Ein Wasserflusslicht bedeutet, dass die LED-Leuchten von links nach rechts und dann von rechts nach links laufen.  
In diesem Experiment verwenden wir aufeinanderfolgende Pins, sodass die „for“-Schleife nicht nur zum Setzen des Ausgangsmodus (Ersetzen der Pins durch eine zirkuläre Variable im Code) sondern auch zur Ausgabe genutzt werden kann.

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 6 Water Flow Light
  http://www.keyestudio.com
*/
void setup() 
{
  for(int i = 12;i <= 15 ;i++) //Use "for" loop statement to set IO12-IO15 pin to output mode
  {  
    pinMode(i,OUTPUT);
  }
}

void loop() 
{
  for(int i = 12; i <= 15; i++)//Use "for" loop statement to light up LED on IO12-IO15 pin in sequence 
  {		
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
  for(int i = 15; i >= 12; i--)//Use "for" loop statement to light up LED on IO15-IO12 pin in sequence 
  {		  
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
}
```

**4. Testergebnis**

Nach dem Hochladen des Codes und Einschalten leuchten die LEDs von links nach rechts und dann von rechts nach links.