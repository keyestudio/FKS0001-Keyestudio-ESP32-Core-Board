### Projet 18 Cœur Battant

**1. Description**

Dans ce projet, un cœur battant sera présenté via une carte Arduino, un écran matriciel 8X8, une carte de circuit imprimé et quelques composants électroniques. Grâce à la programmation, vous pouvez contrôler la fréquence des battements, la taille du cœur et sa luminosité.

**2. Schéma de câblage**

![](media/B1.png)

**3. Code de test**

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

**4. Résultat du test**

Après avoir connecté le câblage et téléversé le code, les deux tailles de cœurs s’affichent alternativement.

![image-20251013113903734](media/B2.png)