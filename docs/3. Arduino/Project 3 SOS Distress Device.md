### Project 3 SOS Noodapparaat

**1. Beschrijving**

Het Arduino SOS-apparaat kan noodsignalen uitzenden, wat overeenkomt met het principe van de Morse-code. Het is handig voor noodgevallen.

**2. Aansluitschema**

![](media/A20.png)

**3. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 3：SOS Distress Device
  http://www.keyestudio.com
*/
int ledPin = 5;  //Define pin as IO5
 
void setup() 
{
	pinMode(ledPin, OUTPUT);
}
 
void loop() 
{
    //Three quickly blinks mean “S”
    for(int x=0;x<3;x++)
    {
        digitalWrite(ledPin,HIGH);            //Set LED to light up 
        delay(150);                           //Delay 150ms 
        digitalWrite(ledPin,LOW);             //Set LED to turn off 
        delay(100);                           //Delay 100ms 
	}
    delay(200);//delay 200ms to generate the space between letters
 
    //Three slowly blinks mean “O”
    for(int x=0;x<3;x++)
    {
        digitalWrite(ledPin,HIGH);            //Set LED to light up
        delay(400);                           //Delay 400ms
        digitalWrite(ledPin,LOW);             //Set LED to turn off
        delay(200);                           //Delay 200ms
    }
	delay(100);//Delay 100ms to generate the space between letters
 
    // Three quickly blinks mean “S”
    for(int x=0;x<3;x++)
    {
        digitalWrite(ledPin,HIGH);            //Set LED to light up
        delay(150);                           //Delay 150ms
        digitalWrite(ledPin,LOW);             //Set LED to turn off 
        delay(100);                           //Delay 100ms
    } 
	delay(5000);// Wait 5s before repeating S.0.S
}
```

**4. Testresultaat**

Nadat de code succesvol is geüpload, zien we dat de LED 3 keer snel knippert, daarna 3 keer langzaam knippert en vervolgens weer 3 keer snel knippert, afwisselend tussen snel en langzaam.