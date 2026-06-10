### Projekt 25 Ultraschall-Entfernungsmesser

**1. Beschreibung**

Dieser Ultraschall-Entfernungsmesser misst die Entfernung von Hindernissen, indem er Schallwellen aussendet und dann das Echo empfängt. Das heißt, die Entfernung ist kein unmittelbarer Wert, sondern ein beobachteter, der durch eine theoretische Berechnung der Zeitdifferenz zwischen Sender und Empfänger ermittelt wird.

Ultraschall kann die Form von Objekten erkennen, automatische Türen steuern sowie Fließgeschwindigkeit und Druck schätzen.

Außerdem unterstützt er die Zusammenarbeit mit Computern. Dadurch kann der gemessene Wert über ein Arduino-Board an Computer übertragen werden.

Im Alltag wird er häufig für Motoren, Servos und LEDs sowie für Systeme (automatische Navigation, Steuerung und Sicherheitsüberwachungssysteme) eingesetzt.

**2. Funktionsprinzip**

![](media/B29.png)

Wie allgemein bekannt ist, handelt es sich bei Ultraschall um eine Art unhörbares Schallwellensignal mit hoher Frequenz. Ähnlich wie eine Fledermaus misst dieses Modul die Entfernung von Hindernissen, indem es die Zeitdifferenz zwischen der Aussendung der Welle und dem Empfang des Echos berechnet.

**Maximale Entfernung:** 3M

**Minimale Entfernung:** 5cm

**Erfassungswinkel:** ≤15°

**3. Schaltplan**

![](media/B30.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 25.1：Ultrasonic Rangefinder
  http://www.keyestudio.com
*/
int distance = 0; //Define a variable to receive the diatance value 
int EchoPin = 14; //Connect Echo pin to io14
int TrigPin = 13; //Connect Trig pin to io13

float checkdistance() { //Acquire the distance 
  // preserve a short low level to ensure a clear high pulse:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);    //Delay 2um
  //Trigger the sensor by a high pulse of 10um or longer 
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);		//Delay 10um
  digitalWrite(TrigPin, LOW);
  //Read the signal from the sensor: a high level pulse
  //Duration is detected from the point sending "ping" command to the time receiving echo signal (unit: um).
  float distance = pulseIn(EchoPin, HIGH) / 58.00;  //Convert into distance
  delay(10);
  return distance; //Return the diatance value
}

void setup() 
{
  Serial.begin(9600);//Set the baud rate to 9600
  pinMode(TrigPin, OUTPUT);//Set Trig pin to output
  pinMode(EchoPin, INPUT);  //Set Echo pin to input 
}

void loop() 
{
  distance = checkdistance();   //Assign the read value to "distance" 
  if (distance < 4 || distance >= 400) //Display "-1" if exceeding the detection range 
  {  
    distance = -1;
  }
  Serial.print("ditance: ");
  Serial.print(distance);
  Serial.println(" CM");
  delay(200);
}
```

**5. Testergebnis**

Nach dem Anschluss der Verkabelung und dem Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein. Der serielle Port gibt dann den Entfernungswert aus.

![](media/B31.png)

**6. Wissensvertiefung**

Lassen Sie uns einen Entfernungsmesser bauen.

Wir zeigen Zeichen auf dem LCD 1602 an. Das Programm zeigt „Keyestudio“ bei (3,0) und „distance:“ bei (0,1) gefolgt vom Entfernungswert bei (9,1).

Wenn der Wert kleiner als 100 (oder 10) ist, bleibt ein Rest der dritten (bzw. zweiten) Stelle sichtbar. Daher ist eine „if“-Abfrage notwendig, um eine bestimmte Bedingung zu prüfen.

**Schaltplan：**

![](media/B32.png)

**Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 25.2：Ultrasonic Rangefinder
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); //set the LCD address to 0x27 for a 16 chars and 2 line display

int distance = 0; //Define a variable to receive the diatance value 
int EchoPin = 14; //Connect Echo pin to io14
int TrigPin = 13; //Connect Trig pin to io13
float checkdistance() { //Acquire the distance 
  // preserve a short low level to ensure a clear high pulse:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);
  //Trigger the sensor by a high pulse of 10um or longer 
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
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();
    lcd.setCursor(3,0);
    lcd.print("Keyestudio");
}

void loop() 
{
  distance = checkdistance();
 
  if (distance < 2 || distance >= 400) //Display "-1" if exceeding the detection range 
  {  
    distance = -1;
  }
  if(distance < 100 && distance > 10){             //Eliminate the shadow of the third digit when the value drops to two digits
    lcd.setCursor(11,1);
    lcd.print(" ");
  }
  if(distance < 10)//Eliminate two-digit shadows when the value drops to one digit
  {              
    lcd.setCursor(10,1);
    lcd.print(" ");
  }
  lcd.setCursor(0,1);
  lcd.print("distance:");
  lcd.setCursor(9,1);
  lcd.print(distance);
  delay(200);
}