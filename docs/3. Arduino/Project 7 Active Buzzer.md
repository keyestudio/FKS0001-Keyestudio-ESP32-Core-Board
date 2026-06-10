### Project 7 Actieve Buzzer

**1. Beschrijving**

Een actieve buzzer is een component die wordt gebruikt als alarm, herinnering of als een vermakelijk apparaat, en levert een betrouwbare geluidssignaal. Bovendien maakt het mogelijk om zeer controleerbare geluiden te stimuleren, waardoor onze projecten interessanter worden.

**2. Werkingsprincipe**

![](media/A26.png)

Een actieve buzzer bevat een multivibrator, waardoor hij alleen geluid maakt via DC-spanning. Pin 1 van de buzzer is verbonden met VCC en pin 2 wordt aangestuurd door een triode. Wanneer een hoog niveau wordt aangeboden aan de basis (pin 1) van de triode, verbinden de collector (pin 3) en emitter (pin 2) zich met GND, en dan geeft de buzzer geluid.

Omgekeerd, als we een laag niveau aan de basis geven, worden de overige pinnen losgekoppeld, waardoor de buzzer stil blijft.

**3. Aansluitschema**

![](media/A27.png)

**4. Testcode**

```
 /*
  keyestudio ESP32 Inventor Learning Kit
  Project 7 Active Buzzer
  http://www.keyestudio.com
*/
int buzzer = 5; //Define buzzer connected to IO5 pin 

void setup() 
{
  pinMode(buzzer, OUTPUT);//Set the output mode 
}

void loop() 
{
  digitalWrite(buzzer, HIGH); //IO5 pin outputs a high level to cause the buzzer to emit sound 
  delay(1000);					//Delay 1000ms
  digitalWrite(buzzer, LOW); //IO5 outputs a low level to prevent the buzzer to emit sound 
  delay(1000);
}
```

**5. Testresultaat**

Na het uploaden van de code en het inschakelen, geeft de buzzer 1 seconde geluid en blijft daarna 1 seconde stil.