### Projet 25 Télémètre Ultrasonique

**1. Description**

Ce télémètre ultrasonique mesure la distance des obstacles en émettant des ondes sonores puis en recevant l’écho. Autrement dit, la distance n’est pas une valeur immédiate, mais une valeur observée par un calcul théorique de la différence de temps entre l’émetteur et le récepteur.

L’ultrason permet de détecter la forme des objets, de commander des portes automatiques et d’estimer la vitesse d’écoulement et la pression.

De plus, il supporte le travail en coopération avec des ordinateurs. Ainsi, la valeur mesurée peut être transmise aux ordinateurs via une carte Arduino.

Dans la vie quotidienne, il est largement utilisé pour les moteurs, servomoteurs et LEDs ainsi que dans des systèmes (navigation automatique, contrôle et systèmes de surveillance de sécurité).

**2. Principe de fonctionnement**

![](media/B29.png)

Comme nous le savons tous, l’ultrason est un type d’onde sonore inaudible à haute fréquence. À l’image d’une chauve-souris, ce module mesure la distance des obstacles en calculant la différence de temps entre l’émission de l’onde et la réception de l’écho.

**Distance maximale :** 3M

**Distance minimale :** 5cm

**Angle de détection :** ≤15°

**3. Schéma de câblage**

![](media/B30.png)

**4. Code de test**

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

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série et réglez la vitesse à 9600 bauds, le port série affiche la valeur de la distance.

![](media/B31.png)

**6. Extension des connaissances**

Faisons un télémètre.

Nous affichons des caractères sur un LCD 1602. Le programme affiche "Keyestudio" en (3,0) et “distance:” en (0,1) suivi de la valeur de la distance en (9,1).

Lorsque la valeur est inférieure à 100 (ou 10), un résidu du troisième (ou du deuxième) chiffre subsiste encore. Par conséquent, un test "if" est nécessaire pour déterminer une certaine condition.

**Schéma de câblage :**

![](media/B32.png)

**Code :**

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