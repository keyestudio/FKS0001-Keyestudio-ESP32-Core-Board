### Projet 2 LED Respirante

**1. Description**

La LED respirante Arduino utilise le PWM programmable intégré pour générer une forme d'onde analogique. Après la mise sous tension, la luminosité de la LED peut être ajustée via le cycle de service de la forme d'onde afin de réaliser l'effet de LED respirante.

De cette manière, la lumière ambiante peut être simulée en modifiant la luminosité de la LED au fil du temps. De plus, la LED respirante peut former une mini lumière colorée pour créer une ambiance tranquille et chaleureuse.

**2. Qu'est-ce que le PWM ?**

Le PWM contrôle la sortie analogique par des moyens numériques, ce qui permet d'ajuster le cycle de service de l'onde (un signal alternant circulairement entre un niveau haut et un niveau bas).

Pour Arduino, les ports numériques de sortie de tension sont LOW et HIGH, correspondant respectivement à 0V et 5V. En général, on définit LOW comme 0 et HIGH comme 1. Arduino émettra 500 signaux de 0 ou 1 en 1 seconde. Si ce sont des "1", 5V seront émis. Inversement, s'ils sont tous à 0, la sortie sera de 0V. Ou si le signal est 010101010101..., la sortie moyenne sera de 2,5V.

En d'autres termes, le rapport de sortie entre 0 et 1 influence la valeur de la tension, plus le nombre de signaux 0 et 1 émis par unité de temps est élevé, plus le contrôle sera précis.

Les GPIO34, 35, 36 et 39 de l'ESP32 ne peuvent pas utiliser le PWM.

![](media/A18.png)

**3. Schéma de câblage**

![](media/A19.png)

**4. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. Résultat du test**

Après avoir téléversé le code, nous verrons la LED s'éclaircir et s'assombrir lentement, comme le rythme de la respiration.