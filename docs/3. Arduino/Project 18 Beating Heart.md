### Projekt 18 Schlagendes Herz

**1. Beschreibung**

In diesem Projekt wird ein schlagendes Herz über ein Arduino-Board, ein 8x8 Punktmatrix-Display, eine Leiterplatte und einige elektronische Bauteile dargestellt. Durch Programmierung können Sie die Schlagfrequenz, die Herzgröße und die Helligkeit steuern.

**2. Schaltplan**

![](media/B1.png)

**3. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 18 Beating Heart
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES1[] = {0x30, 0x78, 0x7c, 0x3e, 0x3e, 0x7c, 0x78, 0x30};  // a big heart
const byte IMAGES2[] = {0x00, 0x10, 0x38, 0x1c, 0x1c, 0x38, 0x10, 0x00};  //a small heart

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);  
}

void loop()
{
  for(int i=0; i < 8; i++)
  {
      lc.setRow(0,i,IMAGES1[i]);
  }
  delay(1000);
  for(int i=0; i < 8; i++)
  {
    lc.setRow(0,i,IMAGES2[i]);
  }
  delay(1000);
}
```

**4. Testergebnis**

Nach dem Verbinden der Verkabelung und Hochladen des Codes werden die beiden Herzgrößen abwechselnd angezeigt.

![image-20251013113903734](media/B2.png)