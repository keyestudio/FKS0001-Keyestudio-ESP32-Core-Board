### Project 17 Inbraakalarm

**1. Beschrijving**

Dit inbraakalarmsysteem kan indringers in huizen of kleine kantoren detecteren en de bewoner waarschuwen om tijdig maatregelen te nemen.

In dit project bewaakt de sensor een bepaald gebied. Een apparaat op de Arduino-board zal een LED laten oplichten en een buzzer laten piepen als er beweging wordt gedetecteerd in die zone.

In feite kenmerkt deze module zich door praktische bruikbaarheid, eenvoudige installatie en lage kosten. Naast thuis en kantoor is het ook toepasbaar in fabrieken, magazijnen en markten, wat in grote mate de eigendomsveiligheid beschermt.

**2. Werking**

![](media/A64.png)

Het menselijk lichaam (37°C) zendt altijd infraroodstraling uit met een golflengte van 10μm, wat ongeveer overeenkomt met die van de sensor.

Hierdoor kan deze module menselijke beweging detecteren. Als die er is, geeft de PIR-sensor ongeveer 3 seconden een hoog signaal. Zo niet, dan geeft hij een laag signaal.

**3. Aansluitschema**

![](media/A65.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.1 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;    //Define IO5 as PIR sensor pin 

void setup() 
{
  pinMode(pir,INPUT);   //Set IO5 pin to input 
  Serial.begin(9600);
}

void loop() 
{
  int pir_val = digitalRead(pir); 	//Read the PIR result and assign it to pir_val 
    Serial.print("pir_val:"); //Print “pir_val”
	Serial.println(pir_val);
    delay(500);
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De seriële poort toont de PIR-waarde. Als de PIR-sensor een persoon detecteert, wordt 1 weergegeven.

![](media/A66.png)

**6. Kennisuitbreiding**

Laten we een inbraakalarm maken. Wanneer de PIR-sensor een mens detecteert, gaat de LED branden en geeft de buzzer geluid. Anders gaat de LED uit en blijft de buzzer stil.

- **Stroomschema：**

![](media/A67.png)

- **Aansluitschema：**

![](media/A68.png)

- **Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.2 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;		//Set PIR sensor pin to IO5
int red_led = 18;	//Set red LED to pin IO18
int buzz = 19;		//Set buzzer to pin IO19

void setup() 
{
  // put your setup code here, to run once:
  pinMode(pir,INPUT);		//Set PIR pin to input mode 
  pinMode(red_led,OUTPUT);	//Set LED pin to output mode  
  pinMode(buzz,OUTPUT);		//Set buzzer pin to output mode 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int pir_val = digitalRead(pir);
  if(pir_val == 1)
  {
    digitalWrite(red_led,HIGH);
    digitalWrite(buzz,HIGH);
  }
  else
  {
    digitalWrite(red_led,LOW);
    digitalWrite(buzz,LOW);
  }
}
```

**Testresultaat**

Als de PIR-sensor een persoon in de buurt detecteert, gaat de rode LED branden en klinkt de buzzer.