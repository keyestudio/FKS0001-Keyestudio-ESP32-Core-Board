### Projet 6 Lumière à flux d'eau

**1. Description**

Ce projet simple de lumière à flux d'eau vous permet d'apprendre le montage électronique. Dans ce projet, nous contrôlerons des LEDs pour changer de couleur à une vitesse spécifiée via une carte Arduino.

**2. Schéma de câblage**

![](media/A25.png)

**3. Code de test**

Une lumière à flux d'eau signifie que les LEDs s'allument de gauche à droite puis de droite à gauche.  
Dans cette expérience, nous utilisons des broches consécutives, ce qui permet d'utiliser l'instruction "for" non seulement pour définir le mode sortie (remplacer les broches par une variable circulaire dans le code) mais aussi pour la sortie.

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 6 Water Flow Light
  http://www.keyestudio.com
*/
void setup() 
{
  for(int i = 12;i <= 15 ;i++) //Use "for" loop statement to set IO12-IO15 pin to output mode
  {  
    pinMode(i,OUTPUT);
  }
}

void loop() 
{
  for(int i = 12; i <= 15; i++)//Use "for" loop statement to light up LED on IO12-IO15 pin in sequence 
  {		
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
  for(int i = 15; i >= 12; i--)//Use "for" loop statement to light up LED on IO15-IO12 pin in sequence 
  {		  
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
}
```

**4. Résultat du test**

Après avoir téléversé le code et mis sous tension, les LEDs s'allument de gauche à droite puis de droite à gauche.