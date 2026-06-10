### Projet 26 Piano Corps Humain

**1. Description**

Le piano analogique comprend une carte de développement et un capteur ultrasonique. Il permet de jouer différentes notes en détectant la position de vos doigts. Ainsi, ce module est capable de stimuler un piano pour interpréter de la musique et des chansons.

**2. Organigramme**

![](media/B33.png)

**3. Schéma de câblage**

![](media/B34.png)

**4. Code de test**

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

**5. Résultat du test**

Connectez les câblages et téléversez le code.

- Jouez Do lorsque la distance est inférieure à 10.
- Jouez Ré lorsque la distance est comprise entre 10 et 20.
- Jouez Mi lorsque la distance est comprise entre 20 et 30.
- Jouez Fa lorsque la distance est comprise entre 30 et 40.
- Jouez Sol lorsque la distance est comprise entre 40 et 50.
- Jouez La lorsque la distance est comprise entre 50 et 60.
- Jouez Si lorsque la distance est comprise entre 60 et 70.