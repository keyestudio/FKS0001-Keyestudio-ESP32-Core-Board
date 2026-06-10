### Projekt 26 Körperklavier

**1. Beschreibung**

Das analoge Klavier besteht aus einem Entwicklungsboard und einem Ultraschallsensor. Es ermöglicht das Spielen verschiedener Töne, indem die Position Ihrer Finger erkannt wird. Somit kann dieses Modul ein Klavier stimulieren, um Musik und Lieder zu spielen.

**2. Flussdiagramm**

![](media/B33.png)

**3. Schaltplan**

![](media/B34.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 26 Human Body Piano
  http://www.keyestudio.com
*/
int distance = 0; //Define a variable to receive the distance 
int EchoPin = 14; //Connect Echo pin to io14
int TrigPin = 13; //Connect Trig pin to io13

int beeppin = 5;

float checkdistance() { //Acquire distance
  // preserve a short low level to ensure a clear high pulse:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);
  // Trigger the sensor by a high pulse of 10um or longer 
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(TrigPin, LOW);
  // Read the signal from the sensor: a high level pulse
  //Duration is detected from the point sending "ping" command to the time receiving echo signal (unit: um).
  float distance = pulseIn(EchoPin, HIGH) / 58.00;  //Convert into distance
  delay(10);
  return distance;
}

void setup() 
{
  Serial.begin(9600);//Set the baud rate to 9600
  pinMode(TrigPin, OUTPUT);//Set Trig pin to output
  pinMode(EchoPin, INPUT);  //Set Echo pin to input 
}

void loop() 
{
  distance = checkdistance();
  if(distance < 10)
  {            
    tone(beeppin, 262);//Play DO
    delay(1000);
  }
  if(distance < 20 && distance > 10)
  {            
    tone(beeppin, 294);//Play Re
    delay(1000);
  }
  if(distance < 30 && distance > 20)
  {            
    tone(beeppin, 330);//Play Mi
    delay(1000);
  }
  if(distance < 40 && distance > 30)
  {             
    tone(beeppin, 349);//Play fa
    delay(1000);
  }
  if(distance < 50 && distance > 40)
  {             
    tone(beeppin, 392);//Play So
    delay(1000);
  }
  if(distance < 60 && distance > 50){             
    tone(beeppin, 440);//Play La
    delay(1000);
  }
  if(distance < 70 && distance > 60)
  {             
    tone(beeppin, 494);//Play Si
    delay(1000);
  }
  Serial.println(distance);
  noTone(beeppin);//Stop
}
```

**5. Testergebnis**

Verbinden Sie die Verkabelung und laden Sie den Code hoch.

- Spiele Do, wenn der Abstand kleiner als 10 ist.  
- Spiele Re, wenn der Abstand zwischen 10 und 20 liegt.  
- Spiele Mi, wenn der Abstand zwischen 20 und 30 liegt.  
- Spiele Fa, wenn der Abstand zwischen 30 und 40 liegt.  
- Spiele So, wenn der Abstand zwischen 40 und 50 liegt.  
- Spiele La, wenn der Abstand zwischen 50 und 60 liegt.  
- Spiele Si, wenn der Abstand zwischen 60 und 70 liegt.