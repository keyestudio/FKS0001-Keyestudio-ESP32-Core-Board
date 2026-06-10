### Project 19 Dimmen van Lamp

**1. Beschrijving**

De dimlamp past de helderheid van een LED aan via een potentiometer en een Arduino-controller. De helderheid is afhankelijk van de weerstandwaarde, die kan worden uitgelezen en aangepast door de uiteinden van de potentiometer te verbinden met digitale of analoge pinnen op het bord. Bovendien wordt dit systeem toegepast om de spanning of stroom van andere apparaten zoals ventilatoren, lampen en verwarmingselementen te regelen.

**2. Werking**

![](media/B3.png)

![](media/B4.png)

In wezen is een potentiometer een element dat de waarde van de weerstand kan veranderen. Volgens de wet van Ohm (U=I*R) beïnvloedt de weerstand de spanning. Onze potentiometer is 10K.

In dit project is de maximale weerstand 10K. Het ESP32-bord verdeelt de spanning van 3V gelijkmatig in 4095 delen (3/4095=0.0007326007326). De analoge spanning wordt verkregen door de uitgelezen waarde te vermenigvuldigen met 0.0007326007326.

**3. Aansluitschema**

![](media/B5.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.1 Dimming Lamp
  http://www.keyestudio.com
*/
int pot = 34;      //Define variable pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);	//Read io34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De analoge waarde wordt weergegeven binnen het bereik van 0-4095. Door aan de potentiometer te draaien, verandert de grootte van de analoge waarde.

![](media/B6.png)

**6. Kennisuitbreiding**

We zullen de helderheid van de LED regelen via een potentiometer. Zoals we weten, wordt dit beïnvloed door PWM. Echter, het bereik van de analoge waarde is 0-4095 terwijl dat van PWM 0-255 is. Daarom is een functie "map(value, fromLow, fromHigh, toLow, toHigh)" nodig.

**Aansluitschema：**

![](media/B7.png)

**Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.2 Dimming Lamp
  http://www.keyestudio.com
*/
int led = 25;		//Define LED to IO25
int pot = 34;		//Define pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  pinMode(led,OUTPUT);		//Set LED pin to output 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);
  int led_val = map(value,0,4095,0,255);  //Convert the range of potentiometer analog value to the range we need  
  analogWrite(led,led_val);
}
```

**7. Testresultaat**

Na het succesvol uploaden van de code zal het draaien aan de potentiometer de helderheid van de rode LED veranderen.