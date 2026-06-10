### Project 1 LED Knipperen

**1. Beschrijving**

LED knipperen is een eenvoudig project ontworpen voor beginners. Je hoeft alleen een LED op de Arduino board te installeren en de code te uploaden via de Arduino IDE. Dit project versterkt het begrip van het Arduino conceptuele kader en het gebruik van methoden voor beginners.

**2. Werking**

![](media/A16.png)

- **LED:** Bovenstaand is het schakelschema van de LED. Over het algemeen kan een beperkte uitgangsstroom van IO-poorten zorgen voor een lage helderheid van de LED, daarom wordt een NPN-transistor (Q2) in het circuit toegepast als schakelaar. In dit geval zal de LED oplichten als de basis(pin 1) van de transistor op een hoog niveau staat. Omgekeerd gaat de LED uit wanneer de basis laag is.

- **Transistor schakelaar:** Om het principe duidelijk te krijgen is enige kennis van elektronische schakelingen vereist. Raadpleeg hiervoor zelf aanvullende materialen. Kort gezegd, het aan- en uitgaan van de LED hangt af van de hoge en lage niveaus van de transistorbasis, die worden bepaald door de pin op de ontwikkelboard. De LED gaat aan wanneer de basis(pin 1) op een hoog niveau staat, en gaat uit wanneer de basis laag is.

**3. Aansluitschema：**

![](media/A17.png)

**4. Code Uploaden**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 1: LED Blinking
  http://www.keyestudio.com
*/
int ledPin = 5; //Define LED to connect with pin IO5
void setup() 
{
  pinMode(ledPin, OUTPUT);//Set the mode to output
}

void loop() 
{
  digitalWrite(ledPin, HIGH); //Output a high level, LED lights up
  delay(1000);//Delay 1000ms 
  digitalWrite(ledPin, LOW); //Output a low level, LED goes off
  delay(1000);
}
```

**5. Testresultaat**

Na het uploaden van de code en het inschakelen zal de LED 1 seconde branden en 1 seconde uitgaan.