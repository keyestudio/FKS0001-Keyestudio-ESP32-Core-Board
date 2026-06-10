### Project 6 Water Flow Light

**1. Beschrijving**

Dit eenvoudige waterstroomlicht-project helpt je bij het leren van elektronische verpakking. In dit project zullen we LEDs aansturen om van kleur te veranderen met een bepaalde snelheid via een Arduino-board.

**2. Bedradingsschema**

![](media/A25.png)

**3. Testcode**

Een waterstroomlicht betekent dat de LED-lampjes van links naar rechts gaan en daarna van rechts naar links.
In dit experiment gebruiken we aaneengesloten pinnen, zodat de "for"-lus niet alleen kan worden gebruikt om de uitgangsmodus in te stellen (vervang pinnen door een circulaire variabele in de code), maar ook om uit te voeren.

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

**4. Testresultaat**

Na het uploaden van de code en het inschakelen, gaan de LEDs van links naar rechts en daarna van rechts naar links.