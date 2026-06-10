### Project 2 Ademend LED

**1. Beschrijving**

Arduino ademend LED maakt gebruik van on-board programmeerbare PWM om een analoge golfvorm uit te voeren. Na het inschakelen kan de helderheid van de LED worden aangepast via de duty cycle van de golfvorm om uiteindelijk het effect van een ademend LED te realiseren.

Op deze manier kan omgevingslicht worden gesimuleerd door de helderheid van de LED in de loop van de tijd te veranderen. Bovendien kan een ademend LED een kleurrijk mini-licht vormen om een rustige en warme sfeer te creëren.

**2. Wat is PWM?**

PWM bestuurt analoge uitgang via digitale middelen, waarmee de duty cycle van de golf (een signaal dat cyclisch wisselt tussen hoog niveau en laag niveau) kan worden aangepast.

Voor Arduino zijn digitale poorten met spanningsuitgang LOW en HIGH, die respectievelijk overeenkomen met 0V en 5V. Over het algemeen definiëren we LOW als 0 en HIGH als 1. Arduino zal binnen 1 seconde 500 signalen van 0 of 1 uitgeven. Als ze "1" zijn, wordt 5V uitgegeven. Omgekeerd, als ze allemaal 0 zijn, is de uitgang 0V. Of als ze 010101010101... zijn, is de gemiddelde uitgang 2,5V.

Met andere woorden, de verhouding van 0 en 1 in de output beïnvloedt de spanningswaarde; hoe meer 0- en 1-signalen per tijdseenheid worden uitgegeven, hoe nauwkeuriger de regeling zal zijn.

De GPIO34, 35, 36 en 39 van ESP32 kunnen geen PWM gebruiken.

![](media/A18.png)

**3. Aansluitschema**

![](media/A19.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. Testresultaat**

Na het uploaden van de code zal de LED langzaam helderder en donkerder worden, net als het ritme van ademhaling.