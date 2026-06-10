### Projet 11 LCD

**1. Description**

L'écran Arduino I2C 1602 LCD est un dispositif auxiliaire couramment utilisé pour les cartes de développement MCU afin de se connecter à des capteurs et modules externes. Il dispose d'un écran LCD à 16 caractères de large sur 2 lignes avec une luminosité réglable. Ce module programmable est pratique pour l'édition, l'affichage et la gestion des données. De plus, il peut afficher non seulement des caractères et des chiffres, mais aussi des valeurs de capteurs, comme la température, l'humidité ou la pression.

En raison de son utilité, cet affichage est largement utilisé dans de nombreux domaines, notamment les produits domotiques, les systèmes de surveillance industrielle, les systèmes de contrôle robotique et les systèmes électroniques automobiles.

**2. Principe de fonctionnement**

![](media/A44.png)

Il fonctionne selon le même principe que la communication IIC. Les fonctions sous-jacentes ont été encapsulées dans des bibliothèques afin que vous puissiez les appeler directement. Si vous êtes intéressé, vous pouvez approfondir les principes de pilotage sous-jacents.

**3. Schéma de câblage**

![](media/A45.png)

**4. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 11 LCD
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); // set the LCD address to 0x27 for a 16 chars and 2 line display

void setup()
{
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();		//Turn on the LCD backlight 
    lcd.setCursor(2,0);		//Set the display position 
    lcd.print("Hello,world!");		//LCD displays "Hello, world!"
    lcd.setCursor(2,1);	
    lcd.print("keyestudio!");		//LCD displays "keyestudio!"
}

void loop()
{
}
```

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, allumez le LCD, "Hello, world!" et "keyestudio!" s'afficheront sur l'écran LCD.

![](media/A46.png)

Si les caractères sont flous, veuillez ajuster le potentiomètre du rétroéclairage à l'aide d'un petit tournevis plat (Veuillez appliquer une force appropriée pour le réglage). Connectez une alimentation externe si nécessaire.

![](media/A47.png)

![](media/A48.png)