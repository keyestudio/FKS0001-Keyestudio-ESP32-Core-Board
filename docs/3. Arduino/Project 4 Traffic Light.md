### Project 4 Verkeerslicht

**1. Beschrijving**

De verkeerslichtmodule is een apparaat dat wordt gebruikt om de route van voetgangers en voertuigen te regelen. Het bevat een rood, een geel en een groen licht, die verschillende instructies impliceren.

**Rood voor Stop:** Voetgangers en voertuigen stoppen met doorgaan.

**Geel voor Voorzichtigheid:** Voetgangers en voertuigen maken zich klaar om te stoppen. Als het rijden al bezig is, moet de snelheid laag zijn.

**Groen voor Doorgaan:** Voetgangers en voertuigen gaan door met inachtneming van de verkeersregels.

In dit project kun je Arduino gebruiken om code te schrijven om verkeerslichten te bedienen. Bijvoorbeeld, stel de duur van elk licht en de intervaltijd ertussen in. Daarnaast kun je ook een timer toevoegen om de lichtkleuren volgens een schema te wijzigen.

**2. Aansluitschema**

![](media/A21.png)

**3. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 4 Traffic Light
  http://www.keyestudio.com
*/
int greenPin = 27;   //Green LED connects to IO27
int yellowPin = 26; //Yellow LED connects to IO26
int redPin = 25;   //Red LED connects to IO25

void setup() 
{
  //Set all LED interfaces to output mode
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(redPin, OUTPUT);
}

void loop() 
{
  digitalWrite(greenPin, HIGH); //Light green LED up 
  delay(5000);  //Delay 5s
  digitalWrite(greenPin, LOW); //Turn green LED off 
  for (int i = 1; i <= 3; i++) //Execute for 3 times
  {  
    digitalWrite(yellowPin, HIGH); //Light yellow LED up
    delay(500); //Delay 0.5s
    digitalWrite(yellowPin, LOW); // Turn yellow LED off
    delay(500); //Delay 0.5s
  }
  digitalWrite(redPin, HIGH); //Light red LED up 
  delay(5000);  //Delay 5s 
  digitalWrite(redPin, LOW); //Turn red LED off 

}
```

**4. Testresultaat**

Na het uploaden van de code zal de groene LED 5 seconden branden, de gele LED 3 keer knipperen, en de rode LED 5 seconden branden, in een cyclus.