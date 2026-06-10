### Project 12 Servo

**1. Beschrijving**

Deze servo biedt hoge prestaties en hoge precisie met een maximale rotatiehoek van 180°. Met een gewicht van slechts 9g is hij perfect geschikt voor elk mini-apparaat in diverse toepassingen. Bovendien heeft hij een korte opstarttijd, weinig geluid en sterke stabiliteit.

**2. Werking**

**Hoekbereik:** 180° (360°, 180° en 90°)

**Aandrijfspanning:** 3.3V of 5V

**Pin:** Drie draden

![](media/A49.png)

**GND:** Aarde (bruin)

**VCC:** Een rode pin die verbonden wordt met +5V (3.3V) voeding

**S:** Een oranje signaalpin die wordt aangestuurd via PWM-signaal

![](media/A50.png)

**Bedieningsprincipe**: De rotatiehoek wordt geregeld via de duty cycle van PWM. Theoretisch is de standaard PWM-cyclus 20ms (50Hz), dus de pulsbreedte moet liggen tussen 1ms en 2ms. In de praktijk varieert de pulsbreedte echter van 0,5ms tot 2,5ms, wat overeenkomt met 0° tot 180°. Let op dat bij hetzelfde signaal de rotatiehoek kan verschillen per servomerk.

**3. Aansluitschema**

![](media/A51.png)

Gebruik een externe voeding in plaats van alleen USB-voeding.

![](media/A52.png)

**4. Testcode**

```
int servoPin = 4;//servo PIN

void setup() 
{
  pinMode(servoPin, OUTPUT);//servo pin is set to output
}

void loop() 
{
  for(int i = 0 ; i <= 180 ; i++) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 0° to 180°
  delay(10);//delay 10ms
  }
  for(int i = 180 ; i >= 0 ; i--) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 180° to 0°
  delay(10);//delay 10ms
  }
}

void servopulse(int pin, int myangle) 
{ //Impulse function
  int pulsewidth = map(myangle, 0, 180, 500, 2500); //Map Angle to pulse width
  for (int i = 0; i < 10; i++) 
  { //Output a few more pulses
    digitalWrite(pin, HIGH);//Set the servo interface level to high
    delayMicroseconds(pulsewidth);//The number of microseconds of delayed pulse width value
    digitalWrite(pin, LOW);//Lower the level of servo interface
  }
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code begint de servo te draaien van 0° naar 180° en vervolgens weer terug.