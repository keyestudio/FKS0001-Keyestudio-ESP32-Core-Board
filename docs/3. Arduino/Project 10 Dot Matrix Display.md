### Projekt 10 Punktmatrix-Display

**1. Beschreibung**

Dieses Modul besteht aus einer 8x8 LED-Punktmatrix mit jeweils einem Steuerpin für jede Reihe sowie jede Spalte, um die Helligkeit der LEDs anzupassen. In Verbindung mit einem Arduino-Board wird die Helligkeit der LEDs über Arduino-Programmierung gesteuert, um Zeichen und Figuren anzuzeigen. Auf diese Weise können einfache Zeichen, Zahlen und Figuren dargestellt werden. Es kann auch in Spielgeräten oder Bildschirmen eingesetzt werden.

**2. Funktionsprinzip**

![](media/A37.png)

Der MAX7219 ist ein IC mit SPI-Kommunikation und kann zur Steuerung der 8x8 Punktmatrix verwendet werden. Die MAX7219 SPI-Kommunikation ist in unseren Bibliotheken integriert und kann direkt aufgerufen werden.

**Punktmatrix-Moduloperation**

Klicken Sie auf den Link für das Modul ：[http://dotmatrixtool.com/#](http://dotmatrixtool.com/#)

**Schritte:**

1. Klicken Sie auf den Link und stellen Sie die Höhe und Breite der Punktmatrix ein. Hier setzen wir beide auf 8.

![](media/A38.png)

2. Stellen Sie "Byte Order" auf "Column Major".

![](media/A39.png)

3. Stellen Sie "Endian" auf "Big Endian".

![](media/A40.png)

4. Klicken Sie auf die weißen Kacheln, um ein Muster zu erstellen (erneut klicken zum Abwählen), und klicken Sie dann auf "Generate", um ein Array für dieses Symbol zu erzeugen. Kopieren Sie dieses Array und fügen Sie es in den Code ein, dann wird das Muster auf der Punktmatrix angezeigt.

![](media/A41.png)

**3. Schaltplan**

![](media/A42.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 10 Dot Matrix Display
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x30, 0x78, 0x7c, 0x3e, 0x3e, 0x7c, 0x78, 0x30};

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
      lc.setRow(0,i,IMAGES[i]);
  }
}
```

**5. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes wird ein Herz auf der Punktmatrix angezeigt, wie unten dargestellt.

![](media/A43.png)