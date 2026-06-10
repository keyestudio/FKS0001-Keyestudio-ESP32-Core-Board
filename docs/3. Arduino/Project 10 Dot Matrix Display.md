### Projet 10 Affichage Matrice de Points

**1. Description**

Ce module se compose d'une matrice de points LED 8x8 avec une broche de contrôle pour chaque ligne ainsi que chaque colonne afin de régler la luminosité des LED. Connecté à une carte Arduino, la luminosité des LED est contrôlée pour afficher des caractères et des figures via la programmation Arduino. De cette manière, des caractères simples, des chiffres et des figures peuvent être affichés. Il peut également être utilisé dans des machines de jeu ou des écrans.

**2. Principe de Fonctionnement**

![](media/A37.png)

Le MAX7219 est un circuit intégré avec communication SPI et peut être utilisé pour contrôler la matrice de points 8x8. La communication SPI du MAX7219 est intégrée dans nos bibliothèques et vous pouvez l'appeler directement.

**Fonctionnement du Module Matrice de Points**

Cliquez sur le lien pour le Modulo ：[http://dotmatrixtool.com/#](http://dotmatrixtool.com/#)

**Étapes :**

1. Cliquez sur le lien et définissez la hauteur et la largeur de la matrice de points. Ici, nous réglons les deux à 8.

![](media/A38.png)

2. Réglez "Byte Order" sur "Column Major".

![](media/A39.png)

3. Réglez "Endian" sur "Big Endian".

![](media/A40.png)

4. Cliquez sur les cases blanches pour former le motif souhaité (cliquez de nouveau pour désélectionner), puis cliquez sur "Generate" pour générer un tableau pour cette icône. Copiez ce tableau et collez-le dans le code, puis le motif sera affiché sur la matrice de points.

![](media/A41.png)

**3. Schéma de Câblage**

![](media/A42.png)

**4. Code de Test**

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

**5. Résultat du Test**

Après avoir connecté le câblage et téléchargé le code, un cœur s'affichera sur la matrice de points, comme illustré ci-dessous.

![](media/A43.png)