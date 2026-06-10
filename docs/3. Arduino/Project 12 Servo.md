### Projet 12 Servo

**1. Description**

Ce servo offre des performances élevées et une grande précision avec un angle de rotation maximal de 180°. Pesant seulement 9g, il est parfaitement adapté à tout mini dispositif dans de multiples occasions. De plus, il bénéficie d’un temps de démarrage court, d’un faible bruit et d’une grande stabilité.

**2. Principe de fonctionnement**

**Plage d’angle :** 180° (360°, 180° et 90°)

**Tension d’alimentation :** 3.3V ou 5V

**Broche :** Trois fils

![](media/A49.png)

**GND :** Masse (marron)

**VCC :** Broche rouge connectée à une alimentation +5V (3.3V)

**S :** Broche signal orange contrôlée via un signal PWM

![](media/A50.png)

**Principe de contrôle** : L’angle de rotation est contrôlé via le rapport cyclique du PWM. Théoriquement, le cycle PWM standard est de 20ms (50Hz), donc la largeur d’impulsion doit se situer entre 1ms et 2ms. Cependant, la largeur d’impulsion réelle varie de 0.5ms à 2.5ms, ce qui correspond à 0°～180°. Notez que, pour un même signal, l’angle de rotation peut varier selon les marques de servo.

**3. Schéma de câblage**

![](media/A51.png)

Ajoutez une source d’alimentation externe au lieu d’utiliser uniquement l’USB pour l’alimentation.

![](media/A52.png)

**4. Code de test**

```
int servoPin = 4;//servo PIN

void setup() 
{
  pinMode(servoPin, OUTPUT);//servo pin is set to output
}

void loop() 
{
  for(int i = 0 ; i <= 180 ; i++) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 0° to 180°
  delay(10);//delay 10ms
  }
  for(int i = 180 ; i >= 0 ; i--) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 180° to 0°
  delay(10);//delay 10ms
  }
}

void servopulse(int pin, int myangle) 
{ //Impulse function
  int pulsewidth = map(myangle, 0, 180, 500, 2500); //Map Angle to pulse width
  for (int i = 0; i < 10; i++) 
  { //Output a few more pulses
    digitalWrite(pin, HIGH);//Set the servo interface level to high
    delayMicroseconds(pulsewidth);//The number of microseconds of delayed pulse width value
    digitalWrite(pin, LOW);//Lower the level of servo interface
  }
}
```

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, le servo commence à tourner de 0° à 180° puis inverse sa rotation.