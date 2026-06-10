### Progetto 25 Misuratore di Distanza Ultrasonico

**1. Descrizione**

Questo misuratore di distanza ultrasonico misura la distanza degli ostacoli emettendo onde sonore e poi ricevendo l'eco. Cioè, la distanza non è un valore immediato, ma uno osservato tramite un calcolo teorico della differenza di tempo tra emettitore e ricevitore.

L'ultrasuono è in grado di rilevare la forma degli oggetti, attivare porte automatiche e stimare la velocità di flusso e la pressione.

Inoltre, supporta lavori cooperativi con computer. Di conseguenza, il valore misurato può essere trasmesso ai computer tramite scheda Arduino.

Nella vita quotidiana, è ampiamente utilizzato per motori, servocomandi e LED così come per sistemi (navigazione automatica, controllo e sistemi di monitoraggio della sicurezza).

**2. Principio di Funzionamento**

![](media/B29.png)

Come tutti sappiamo, l'ultrasuono è un tipo di segnale sonoro ad alta frequenza non udibile. Simile a un pipistrello, questo modulo misura la distanza degli ostacoli calcolando la differenza di tempo tra l'emissione dell'onda e la ricezione dell'eco.

**Distanza massima:** 3M

**Distanza minima:** 5cm

**Angolo di rilevamento:** ≤15°

**3. Schema di Collegamento**

![](media/B30.png)

**4. Codice di Test**

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

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale impostando la velocità di trasmissione a 9600, la porta seriale stampa il valore della distanza.

![](media/B31.png)

**6. Approfondimento**

Creiamo un misuratore di distanza.

Visualizziamo i caratteri su LCD 1602. Programmare per mostrare "Keyestudio" in (3,0) e “distance:” in (0,1) seguito dal valore della distanza in (9,1).

Quando il valore è inferiore a 100 (o 10), rimane un residuo della terza (o della seconda) cifra. Pertanto, è necessario un controllo "if" per determinare una certa condizione.

**Schema di Collegamento：**

![](media/B32.png)

**Codice：**

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