### Progetto 26 Pianoforte Corpo Umano

**1. Descrizione**

Il pianoforte analogico include una scheda di sviluppo e un sensore a ultrasuoni. Permette di suonare diverse tonalità rilevando la posizione delle tue dita. Pertanto, questo modulo è in grado di stimolare un pianoforte per eseguire musica e canzoni.

**2. Diagramma di Flusso**

![](media/B33.png)

**3. Schema di Collegamento**

![](media/B34.png)

**4. Codice di Test**

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

**5. Risultato del Test**

Collega i cablaggi e carica il codice.

- Suona Do quando la distanza è inferiore a 10.
- Suona Re quando la distanza è compresa tra 10 e 20.
- Suona Mi quando la distanza è compresa tra 20 e 30.
- Suona Fa quando la distanza è compresa tra 30 e 40.
- Suona So quando la distanza è compresa tra 40 e 50.
- Suona La quando la distanza è compresa tra 50 e 60.
- Suona Si quando la distanza è compresa tra 60 e 70.