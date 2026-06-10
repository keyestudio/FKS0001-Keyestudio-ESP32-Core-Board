### Project 20 Lichtzuil

**1. Beschrijving**

De weerstand (minder dan 1KΩ) van de fotoweerstand varieert met het licht, waardoor het de helderheid van de dotmatrix kan regelen. Bij het aansturen verbinden we deze weerstand met een analoge pin op de board om de verandering in weerstand te monitoren. Op deze manier regelt het licht automatisch de helderheid van het display.

Daarnaast wordt de fotoweerstand veel toegepast in ons dagelijks leven. Bijvoorbeeld, een gordijn dat automatisch opent of sluit afhankelijk van de lichtintensiteit buiten.

**2. Werking**

![](media/B8.png)

![](media/B9.png)

Wanneer het volledig donker is, is de weerstand gelijk aan 0,2MΩ en nadert de spanning op het signaalknooppunt (punt 2) 0V. Hoe sterker het licht is, hoe kleiner de weerstand en spanning zullen zijn.

**3. Aansluitschema**

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

**5. Testresultaat**

Na het aansluiten van de bedrading en uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600. De analoge waarde wordt weergegeven binnen het bereik van 0-4095. Door de lichtintensiteit rondom te veranderen, verandert ook de waarde.

![](media/B11.png)

**6. Kennisuitbreiding**

We gebruiken deze fotoweerstand om de omgevingslichtintensiteit te meten. De twee middelste kolommen zijn opgenomen in dit experiment om de lichtintensiteit weer te geven. Hoe sterker het licht, hoe meer LEDs oplichten. Dit vormt een "lichtzuil".

- **Aansluitschema：**

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

- **Testresultaat**

Hoe sterker het licht nabij de fotoweerstand, hoe hoger de lichtzuil van de LED-matrix.

![](media/B13.png)