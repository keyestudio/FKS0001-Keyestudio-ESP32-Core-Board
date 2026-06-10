### Projet 20 Colonne de Lumière

**1. Description**

La résistance (inférieure à 1KΩ) de la photorésistance varie en fonction de la lumière, ce qui permet de contrôler la luminosité de la matrice de points. Lors du contrôle, nous connectons cette résistance à une broche analogique de la carte pour surveiller la variation de résistance. De cette façon, la lumière contrôle automatiquement la luminosité de l'affichage.

De plus, la photorésistance est largement utilisée dans notre vie quotidienne. Par exemple, un rideau s'ouvre ou se ferme automatiquement en fonction de l'intensité lumineuse extérieure.

**2. Principe de fonctionnement**

![](media/B8.png)

![](media/B9.png)

Lorsqu'il fait totalement sombre, la résistance est égale à 0,2MΩ, et la tension au niveau de la broche signal (point 2) tend vers 0V. Plus la lumière est forte, plus la résistance et la tension seront faibles.

**3. Schéma de câblage**

![](media/B10.png)

**4. Code de test**

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

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série et réglez le débit en bauds à 9600, la valeur analogique s'affichera, dans une plage de 0 à 4095. En modifiant l'intensité lumineuse autour, cette valeur changera.

![](media/B11.png)

**6. Extension des connaissances**

Nous allons utiliser cette photorésistance pour détecter l'intensité lumineuse ambiante. Les deux colonnes centrales sont incluses dans cette expérience pour représenter l'intensité lumineuse. Plus elle est forte, plus le nombre de LED allumées sera élevé. Cela forme une "colonne de lumière".

- **Schéma de câblage :**

![](media/B12.png)

- **Code :**

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

- **Résultat du test**

Plus la lumière proche de la photorésistance est forte, plus la colonne lumineuse de la matrice LED est haute.

![](media/B13.png)