### Project 21 Geluidsgestuurde LED

**1. Beschrijving**

De geluidsgestuurde LED is een apparaat dat geluid detecteert om daarmee de helderheid van een LED te regelen. Het bestaat uit een Arduino-board en enkele componenten. Het kan worden aangesloten op meerdere sensoren zoals microfoons. Het zet geluid om in een veranderend spanningssignaal dat door de Arduino wordt ontvangen om de LED aan en uit te schakelen.

**2. Werking**

![](media/B14.png)

Bij het detecteren van geluid trilt de elektretfilm in de microfoon, wat de capaciteit verandert en een subtiele spanningsverandering genereert.

Vervolgens gebruiken we de LM3-chip om een geschikte schakeling te bouwen die het gedetecteerde geluid versterkt, wat kan worden aangepast met een potentiometer. Draai deze met de klok mee om de versterking te vergroten.

**3. Aansluitschema**

![](media/B15.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.1：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33; //Define sound as IO33

void setup()
{
  Serial.begin(9600);
  pinMode(sound,INPUT);
}

void loop()
{
  int value = analogRead(sound);
  Serial.println(value);
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De analoge waarde wordt dan weergegeven.

![](media/B16.png)

**Gevoeligheidsinstelling:**

Als je vindt dat de gevoeligheid van de geluidsensor geschikt is, kun je de potentiometer van de geluidsensor aanpassen (rechts voor de hoogste gevoeligheid, links voor de laagste gevoeligheid).

![](media/B17.png)

**6. Kennisuitbreiding**

De vaak voorkomende gangverlichting is een soort geluidsgestuurde verlichting. Tegelijkertijd bevat deze ook een fotoweerstand. Anders dan dat, bouwen we hier een model waarbij een LED alleen door geluid wordt beïnvloed. Wanneer het analoge volume boven de 100 komt, gaat de LED 2 seconden aan en daarna weer uit.

- **Stroomschema:**

![](media/B18.png)

- **Aansluitschema:**

![](media/B19.png)

- **Code:**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.2：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33;   //Define sound to IO33
int led = 25;      //Define led to IO25

void setup()
{
  pinMode(led,OUTPUT);   //Set IO25 to output 
}

void loop()
{
  int value = analogRead(sound);    //Read analog value of IO33 and assign it to value
  if(value > 100)
  {                  //Judge whether value is greater than 100
    digitalWrite(led,HIGH);         //If IO25 pin outputs high level, LED lights up
    delay(2000);
  }
  else
  {
    digitalWrite(led,LOW);          //If IO25 pin outputs low level, LED lights off
  }
}
```

- **Testresultaat**

Wanneer de waarde die door de geluidsensor wordt gedetecteerd groter is dan 100, gaat de rode LED branden.