### Projet 14 Compteur

**1. Description**

Le compteur à tube numérique Arduino 4 bits peut enregistrer des nombres de 0 à 9999. Il dispose d’une vitesse d’affichage, d’un réglage du mode de comptage ainsi que d’une fonction de réinitialisation. Ce module est largement utilisé dans les compteurs en temps réel (comme le comptage d’appuis sur bouton et la rotation de moteur DC), les équipements de jeu et les expériences.

**2. Schéma fonctionnel**

![](media/A58.png)

**3. Schéma de câblage**

![](media/A59.png)

**4. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 14 Counter
  http://www.keyestudio.com
*/
#include "TM1650.h" //Upload TM1650 library file
int item = 0; //Displayed value
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

int res = 17;     //Reset button
int subtract = 18;   //minus button
int  add = 19;       //plus button

void setup(){
    //set the pin connecting with button to input  
  pinMode(res,INPUT);
  pinMode(add,INPUT);
  pinMode(subtract,INPUT);
  for(char b=0;b<4;b++){
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  DigitalTube.displayFloatNum(item);//Digital tube displays item value 
  int red_key = digitalRead(res);            //Red button is the reset button
  int yellow_key = digitalRead(subtract);    //Yellow button is minus 1
  int green_key = digitalRead(add);           //Green button is plus 1
  if(green_key == 0)
  {
    item++;  //operate to add 1, item = item + 1
    delay(200);
  }
  if(yellow_key == 0)
  {
    item--;		//operate to reduce 1, item = item - 1
    delay(200);
  }
  if(red_key == 0)
  {
    item = 0;
    delay(200);
  }
  if (item > 9999)//return to zero when greater than 9999(excessing the display range)
  {  
    item = 0; 
  }
}
```

**4. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, appuyez sur le bouton vert pour ajouter 1, sur le jaune pour soustraire 1, et sur le rouge pour réinitialiser. Maintenez le bouton enfoncé, et la valeur affichée continuera à augmenter ou diminuer.