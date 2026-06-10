### Projekt 20 Lichtsäule

**1. Beschreibung**

Der Widerstand (weniger als 1KΩ) des Fotowiderstands variiert mit dem Licht, wodurch die Helligkeit der Punktmatrix gesteuert werden kann. Beim Steuern verbinden wir diesen Widerstand mit einem analogen Pin auf dem Board, um die Widerstandsänderung zu überwachen. Auf diese Weise steuert das Licht automatisch die Helligkeit der Anzeige.

Außerdem wird der Fotowiderstand in unserem täglichen Leben häufig eingesetzt. Zum Beispiel öffnet oder schließt sich ein Vorhang automatisch entsprechend der äußeren Lichtintensität.

**2. Funktionsprinzip**

![](media/B8.png)

![](media/B9.png)

Wenn es völlig dunkel ist, beträgt der Widerstand 0,2MΩ, und die Spannung am Signalausgang (Punkt 2) nähert sich 0V an. Je stärker das Licht ist, desto kleiner werden Widerstand und Spannung.

**3. Schaltplan**

![](media/B10.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.1 Light Pillar
  http://www.keyestudio.com
*/
int light = 34;      //Define light to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(light);	//Read IO34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. Testergebnis**

Nach dem Verbinden der Schaltung und Hochladen des Codes öffnen Sie den seriellen Monitor und stellen die Baudrate auf 9600 ein. Der analoge Wert wird im Bereich von 0-4095 angezeigt. Durch Ändern der Lichtintensität in der Umgebung ändert sich der Wert.

![](media/B11.png)

**6. Wissensvertiefung**

Wir verwenden diesen Fotowiderstand, um die Umgebungslichtintensität zu erfassen. Die beiden mittleren Spalten sind in diesem Experiment enthalten, um die Lichtintensität darzustellen. Je stärker sie ist, desto mehr LEDs leuchten. So entsteht eine „Lichtsäule“.

- **Schaltplan：**

![](media/B12.png)

- **Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.2 Light Pillar
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x01,0x03,0x07,0x0F,0x1F,0x3F,0x7F,0xFF}; //Data of light pillar

int light = 34;

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);
  pinMode(light,INPUT);  
}

void loop()
{
  int value = analogRead(light);
  int temp = map(value,0,4095,0,7);  //Convert the range of analog values to 0-7
  lc.setRow(0,3,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 3
  lc.setRow(0,4,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 4
}
```

- **Testergebnis**

Je stärker das Licht in der Nähe des Fotowiderstands ist, desto höher ist die Lichtsäule der LED-Matrix.

![](media/B13.png)