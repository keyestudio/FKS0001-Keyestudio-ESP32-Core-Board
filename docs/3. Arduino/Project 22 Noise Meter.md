### Projet 22 Compteur de Bruit

**1. Description**

Le compteur de bruit pourra utiliser le nombre de points sur la matrice LED pour refléter l'intensité du bruit.

**2. Schéma de câblage**

![](media/B20.png)

**3. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 22 Noisemeter
  http://www.keyestudio.com
*/
#include <LedControl.h>  
  
int DIN = 23;
int CLK = 18;
int CS = 15;
int sensor = 34;

LedControl lc=LedControl(DIN,CLK,CS,1);  
byte data_val[8][8]= {
  {0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x01},
  {0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x03, 0x01},
  {0x00, 0x00, 0x00, 0x00, 0x00, 0x07, 0x03, 0x01},
  {0x00, 0x00, 0x00, 0x00, 0x0f, 0x07, 0x03, 0x01},
  {0x00, 0x00, 0x00, 0x1f, 0x0f, 0x07, 0x03, 0x01},
  {0x00, 0x00, 0x3f, 0x1f, 0x0f, 0x07, 0x03, 0x01},
  {0x00, 0x7f, 0x3f, 0x1f, 0x0f, 0x07, 0x03, 0x01},
  {0xff, 0x7f, 0x3f, 0x1f, 0x0f, 0x07, 0x03, 0x01}
  };


void setup()
{  
 lc.shutdown(0,false);       //Lorsque l'alimentation est activée, le MAX72XX est en mode économie d'énergie. 
 lc.setIntensity(0,8);       //Réglez la luminosité au maximum
 lc.clearDisplay(0);         //Effacez l'affichage 
}  
  
void loop()
{   
  int val = analogRead(sensor);
  Serial.println(val);
  int temp = map(val,0,800,0,7);  //La plage des valeurs analogiques entre 0 et 800 est la plus appropriée
  for(int i=0;i<8;i++)  
  {  
    lc.setRow(0,7-i,data_val[temp][i]);  
  } 
}  
```

**4. Code de test**

Plus la valeur sonore détectée par le capteur de son est élevée, plus de points s'allument sur la matrice LED.

![](media/B21.png)![](media/B22.png)