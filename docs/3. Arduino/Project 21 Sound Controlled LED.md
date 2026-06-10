### Projekt 21 Soundgesteuerte LED

**1. Beschreibung**

Die soundgesteuerte LED ist ein Gerät, das Schall erkennt und die Helligkeit der LED steuert. Es besteht aus einem Arduino-Board und einigen Komponenten. Es kann mit mehreren Sensoren wie Mikrofonen verbunden werden. Es wandelt Schall in ein sich änderndes Spannungssignal um, das vom Arduino empfangen wird, um die LED ein- und auszuschalten.

**2. Funktionsprinzip**

![](media/B14.png)

Beim Erkennen eines Tons vibriert die Elektretfolie im Mikrofon, was die Kapazität ändert und eine subtile Spannungsänderung erzeugt.

Anschließend verwenden wir den LM3-Chip, um eine geeignete Schaltung zum Verstärken des erfassten Tons aufzubauen, die mit einem Potentiometer eingestellt werden kann. Drehen Sie es im Uhrzeigersinn, um die Verstärkung zu erhöhen.

**3. Schaltplan**

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

**5. Testergebnis**

Nach dem Verbinden der Verkabelung und Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein, der analoge Wert wird angezeigt.

![](media/B16.png)

**Empfindlichkeitseinstellung:**

Wenn Sie das Gefühl haben, dass die Empfindlichkeit des Schallsensors passend ist, können wir das Potentiometer des Schallsensors einstellen (rechts für höchste Empfindlichkeit, links für niedrigste Empfindlichkeit).

![](media/B17.png)

**6. Wissensvertiefung**

Das häufig zu sehende Flurlicht ist eine Art soundgesteuertes Licht. Gleichzeitig enthält es auch einen Fotowiderstand. Anders als dort bauen wir hier ein Modell auf, bei dem eine LED nur vom Schall beeinflusst wird. Wenn die analoge Lautstärke 100 überschreitet, leuchtet die LED für 2 Sekunden und geht dann aus.

- **Flussdiagramm:**

![](media/B18.png)

- **Schaltplan:**

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

- **Testergebnis**

Wenn der vom Schallsensor erkannte Wert größer als 100 ist, leuchtet die rote LED.